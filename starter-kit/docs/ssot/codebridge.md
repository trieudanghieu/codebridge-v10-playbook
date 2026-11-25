# RUNBOOK HẠ TẦNG & TRIỂN KHAI (COOLIFY + DOCKER + NEXT.JS STANDALONE)

## 1. Kiến trúc Triển khai & Cổng Mạng Bất Biến
- **Platform:** Self-hosted VPS chạy **Coolify** + **Traefik Reverse Proxy**.
- **Web Ingress:** Clean HTTPS Port `443` FQDN (SSL tự động qua Let's Encrypt/Traefik).
- **Frontend Port:** `3000` (Next.js 14 App Router `output: 'standalone'`).
- **Backend Port:** `3001` (Express/Node.js API Gateway).
- **Database:** PostgreSQL 16 (bật sẵn extension `pgvector`).
- **Cache/Queue:** Redis (cho BullMQ & Mutex Lock).
- **Git Sync:** GitHub Webhook $\rightarrow$ Coolify Auto-Deploy khi có commit/merge vào nhánh `main`. *(CẤM dùng SSH 2222 cho Coolify Ingress)*.

## 2. Biến Môi Trường Bắt Buộc (Environment Variables)
*(Khai báo trong tab Environment Variables của Coolify — không commit giá trị thật lên Git)*
```env
NODE_ENV=production
HOSTNAME=0.0.0.0
PORT=3000
API_PORT=3001
DATABASE_URL=postgresql://user:pass@postgres-host:5432/dbname?schema=public
REDIS_URL=redis://:pass@redis-host:6379
NEXT_PUBLIC_API_URL=https://api.ten-mien-cua-ban.com
```
*(Lưu ý Next.js: Các biến `NEXT_PUBLIC_*` ăn ở Build-time; nếu đổi giá trị phải Rebuild container trong Coolify).*

## 3. Quy Trình Thao Tác An Toàn Trên Trình Duyệt (Web-Only Ops)
1. **Phát triển tính năng / Vá lỗi:** Làm việc trên nhánh phụ (VD: `feat/cr-001`) tại `vscode.dev`. Chỉ Merge PR vào `main` trên GitHub sau khi Tab 1 Hậu kiểm cấp `🟢 SPRINT CLEAN`.
2. **Chạy Migration Database (Nếu Sprint có sửa `prisma/schema.prisma`):**
   - Sau khi Coolify deploy xong build mới từ `main`, mở **Coolify $\rightarrow$ Chọn Container/Service Backend $\rightarrow$ Terminal**, chạy lệnh:
     ```bash
     npx prisma migrate deploy
     ```
   - *(TUYỆT ĐỐI KHÔNG chạy `npx prisma db push --accept-data-loss` trên Production).*
3. **Kiểm tra sự cố (Log Runtime):** Xem trực tiếp tại mục **Logs** trong Coolify Dashboard để gửi trích đoạn log lỗi cho Tab 1 / Tab 2 khi cần chẩn đoán.