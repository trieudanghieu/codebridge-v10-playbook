--- # [MACHINE-READABLE METADATA] ---
project_name: "[TÊN DỰ ÁN]"
version: "9.0.0-MODULAR-FORTRESS"
architecture_type: "SINGLE_SOVEREIGN_VFS"
platform_type: "WEB_SAAS_FULLSTACK"
tech_stack:
  frontend: "Next.js 14 App Router (Standalone) + TailwindCSS + Zustand"
  backend: "Node.js / Express API Gateway (TypeScript Strict)"
  database: "PostgreSQL 16 + pgvector (Prisma ORM v6)"
  cache_queue: "Redis + BullMQ"
  infra: "VPS Self-hosted Coolify + Traefik (Clean HTTPS 443)"
---

# BỘ TÀI LIỆU KHỞI TẠO DỰ ÁN (PID) - [TÊN DỰ ÁN]
> ⚠️ **NGUỒN CHÂN LÝ DUY NHẤT (SSOT):** Tài liệu này là hiến pháp tối cao cho toàn bộ dây chuyền AI & Tech Lead. Mọi thay đổi/nâng cấp theo từng đợt (Brownfield) phải đi qua tệp `docs/changes/CR-xxx.md` trước khi hợp nhất vào đây cuối Sprint.

---

## ⚙️ PHẦN 1: GIAO THỨC THỰC THI ĐA MÔI TRƯỜNG (UNIVERSAL EXECUTION PROTOCOL)
- 🔵 **Phân nhánh CodeBridge App:** Thực thi qua Két Sắt Đơn Nhất Chủ Quyền (`ContextVault`), tích hợp Sandpack + `@electric-sql/pglite` WASM Client Preview, triển khai container `codebridge-app-${projectId}`.
- 🟠 **Phân nhánh Web-Only (AI Studio + Gitingest + vscode.dev + Coolify):** Vận hành theo Dây chuyền 4 Buồng Lái V10 (`Tab 0 ➔ Tab 1 ➔ Tab 2 ➔ Tab 3 ➔ Tab 2 ➔ Tab 1`). Code được đóng gói qua `gitingest.com`, dán lên nhánh làm việc tại `vscode.dev` và tự động publish qua Webhook Coolify khi Merge `main`.

---

## 🎯 PHẦN 1.5: TẦM NHÌN, PHẠM VI DỰ ÁN & CHÂN DUNG KHÁCH HÀNG (TẦNG 1 - SINGULARITY SEED)
### 1.1 Tầm nhìn & Nỗi đau cốt lõi
- [Mô tả bài toán cốt lõi sản phẩm đang giải quyết]

### 1.2 Chân dung khách hàng mục tiêu (ICP)
- [Đối tượng sử dụng chính, hành vi, mức độ sẵn sàng chi trả]

### 1.3 Giá trị độc bản & Long mạch cạnh tranh (7 Powers Moat)
- **Killer Feature (10x Better):** [Tính năng sát thủ duy nhất]
- **7 Powers Moat:** [Scale Economies / Network Effects / Counter-Positioning / Switching Costs / Branding / Cornered Resource / Process Power]

### 1.3.1 Bảng Đối soát Đối thủ Thực tế
| Đối thủ | Điểm mạnh | Điểm yếu / Nỗi đau chưa giải quyết | Lợi thế bất đối xứng của ta |
| :--- | :--- | :--- | :--- |
| [Đối thủ A] | [...] | [...] | [...] |

### 1.4 Phân nhánh Nền tảng & Phạm vi MVP
- **In-Scope:** [...]
- **Out-of-Scope (Cấm vẽ voi):** [...]

---

## ⚖️ PHẦN 2: MA TRẬN QUYẾT ĐỊNH KIẾN TRÚC & TRỤ CỘT CÔNG NGHỆ (ARCHITECTURE PILLARS)
- **Kiến trúc lưu trữ:** Khóa cứng `SINGLE_SOVEREIGN_VFS` (1-1 `@unique projectId` với `ContextVault` nếu thuộc hệ sinh thái CodeBridge) / Tổ chức theo Lát cắt dọc AVSA.
- **Phân bổ cổng mạng bất biến:**
  - Web Ingress: Clean HTTPS Port `443` FQDN qua Traefik Reverse Proxy.
  - Frontend (Next.js Standalone): Port `3000`.
  - Backend (Express API Gateway): Port `3001`.
- **Client Preview:** Sovereign Client Preview WASM (Sandpack React + `@electric-sql/pglite` in-browser, không cần COOP/COEP).

### 2.1 Dự toán Kinh tế học Đơn vị (Unit Economics & Chi phí Server/Token)
- **Mô hình doanh thu:** [Freemium / Subscription / Usage-based]
- **Chi phí biên / User / Tháng:** [Ước tính RAM/CPU VPS + LLM Token/API cost + Biên lợi nhuận gộp]

---

## 🏗️ PHẦN 2.5: ĐẶC TẢ THUẬT TOÁN & HIẾN CHƯƠNG AVSA V9.0 (DIRECTIVE-V9-MODULAR-FORTRESS)
1. **Vùng Đóng Băng Di Sản (Legacy Freeze):** Mọi tệp tin có kích thước $\ge 1.000$ dòng bước vào trạng thái `READ-ONLY`. Tuyệt đối CẤM viết thêm logic nghiệp vụ tại chỗ; chỉ được phép cấy **Delegation Adapter tối đa 3–5 dòng** chuyển tiếp sang module mới.
2. **Bức Tường Lửa Kích Thước:** Mọi file mới sinh ra BẮT BUỘC gọn **$< 120$ dòng** (trần cứng `300` dòng; chạm `250` dòng phải phân tách).
3. **Lát Cắt Dọc Tự Trị (Vertical Slices):** Tổ chức mã nguồn mới theo cấu trúc module độc lập tại `src/modules/[feature]/` (`types.ts`, `service.ts`, `controller.ts`, `routes.ts`).

---

## 🕸️ PHẦN 3: RÀNG BUỘC HỆ SINH THÁI CHỦ QUYỀN (SOVEREIGN ECOSYSTEM BINDING)
- **Database:** PostgreSQL 16 + `pgvector` quản lý qua Coolify.
- **Object Storage:** Cloudflare R2 hoặc MinIO (S3-compatible).
- **Git & Reverse Proxy:** GitHub / CodeBridge Hub Forgejo v9 qua **Clean HTTPS Port 443 FQDN**. **TUYỆT ĐỐI CẤM dùng SSH cổng 2222** đối với luồng Coolify Ingress/Clone.

---

## 🛡️ PHẦN 4: HIẾN PHÁP CHỐNG HARDCODE TUYỆT ĐỐI (ZERO-HARDCODE FORTRESS)
1. **Tầng 1 (Env-Only Secrets):** 100% API Keys, DB URI, JWT Secret lấy từ `process.env`. Cấm hardcode.
2. **Tầng 2 (Strict TypeScript):** Zero-`any`, strict null checks, khai báo rõ DTO/Interface.
3. **Tầng 3 (IDOR & Auth Shield):** Mọi API truy xuất tài nguyên phải qua `verifyProjectAccess` / ownership check.
4. **Tầng 4 (Data-Mirror Invariant):** Mọi thao tác cây thư mục phải đồng bộ nguyên tử Bộ Ba Đồng Thể: SQL `FileNode` = JSON `ContextVault.directoryTree` = Text `repo-map.txt`.
5. **Tầng 5 (Exhaustive Tool Lock):** Default-Deny đối với các tool gọi ngoại vi trong luồng chẩn đoán.
6. **Tầng 6 (Memory Safety & Anti-OOM):** Timeout `15s` cho runner/external calls, dọn sạch `clearTimeout`/`clearInterval`/listeners trong `finally` chống OOM 137 (512MB RAM).
7. **Tầng 7 (Zero-Regression):** Cấm `// ... existing code ...`, bảo toàn 100% chữ ký hàm cũ xung quanh.
8. **Tầng 8 (Anti-Bleed Context Chunking):** Đóng gói ngữ cảnh sạch `< 80k` tokens cho Architect (Tab 2) và `< 8k–15k` tokens cho Builder (Tab 3).
9. **Tầng 9 (Immutable PID Delta-Guard):** Trong quá trình làm Sprint nâng cấp (Brownfield), `PID.md` gốc giữ nguyên trạng thái bất biến; mọi thay đổi viết vào `docs/changes/CR-xxx.md` và chỉ hợp nhất cuối Sprint sau `🟢 SPRINT CLEAN`.
10. **Tầng 10 (Fossilization Protocol):** Khi chuyển pha hoặc đóng băng PoC tại `/.poc/`, bắt buộc hóa thạch quyết định kiến trúc vào `docs/ssot/DECISION_LOG.md`.

---

## 🎨 PHẦN 4.8: BẢN ĐỒ TẦM NHÌN THẨM MỸ & TÂM LÝ HỌC HÀNH VI (TẦNG 2 - VISIONARY BLUEPRINT)
- **Design Tokens:** [Dark/Light Mode, Font, Bảng màu chủ đạo, Border Radius]
- **UX Core Principles:** [Phản hồi tức thì Optimistic/Skeleton, tối đa 3 click tới giá trị cốt lõi]
- **Must-Haves & Excluded:** [...]

---

## 📚 PHẦN 4.9: TÀI LIỆU NGOẠI LAI (EXTERNAL KNOWLEDGE BASE)
- [Link docs chính thức: Coolify v4 API, Prisma v6, Next.js 14 Standalone, PGlite, v.v.]

---

## 🧩 PHẦN 5: PHÂN HỆ NGHIỆP VỤ & LUỒNG VẬN HÀNH (DOMAIN-DRIVEN MODULES & BUSINESS FLOW)
### DOMAIN 0: Core Authentication & Access Shield
- `[Bước 1 - Giao diện]` Người dùng gửi thông tin đăng nhập / truy cập tài nguyên.
- `[Bước 2 - API Gateway]` Middleware xác thực JWT/Session và kiểm tra IDOR (`verifyProjectAccess`).
- `[Bước 3 - Database/Xử lý]` Đối chiếu Prisma User/Session, kiểm tra quyền sở hữu.
- `[Bước 4 - Phản hồi UI]` Trả HTTP 200 kèm Context hoặc 401/403 redirect an toàn.

### DOMAIN 1: [Tên Phân Hệ Nghiệp Vụ Chính]
- `[Bước 1 - Giao diện]` [...]
- `[Bước 2 - API Gateway]` [...]
- `[Bước 3 - Database/Xử lý]` [...]
- `[Bước 4 - Phản hồi UI]` [...]

---

## 🖥️ PHẦN 6: MA TRẬN ĐIỂM CHẠM GIAO DIỆN (UI TOUCHPOINT MATRIX)
| Màn hình / Route | Nút bấm / Trigger | Hành động API / State | Trạng thái FSM (`Idle / Loading / Success / Error`) |
| :--- | :--- | :--- | :--- |
| `/dashboard` | `[Nút hành động]` | `POST /api/...` | `Idle` -> Spinner -> Toast Success / Error Banner |

---

## 🚨 PHẦN 6.5: MA TRẬN RỦI RO & NGOẠI LỆ (ERROR TAXONOMY & SRE RED-TEAMING)
| Mã lỗi | Kịch bản sự cố | Hành vi xử lý chuẩn (Graceful Degradation) |
| :--- | :--- | :--- |
| `ERR-01` | Mất kết nối DB / Timeout `> 8000ms` | AbortController ngắt request, trả HTTP 503 + UI nút Retry. |
| `ERR-02` | Payload rỗng / Sai kiểu dữ liệu | Zod validation chặn tại Gateway, trả HTTP 400 chi tiết field. |
| `ERR-03` | Xung đột đồng thời (Race Condition) | Redis Mutex Lock khóa theo `resourceId`, trả HTTP 409 nếu đang xử lý. |
| `ERR-04` | Truy cập trái phép chéo tài nguyên (IDOR) | Chặn ở `verifyProjectAccess`, log ẩn token, trả HTTP 403. |
| `SRE-01` | Tràn RAM Container (OOM Exit 137) | Stream xử lý, cleanup timer/listener trong `finally`, giới hạn payload. |
| `SRE-02` | Lỗi Build-time Env Next.js trên Coolify | Đọc runtime config qua API/Server Component, khai báo `HOSTNAME=0.0.0.0`. |

### Kịch bản Tiên tri Tử địa 6 tháng (Pre-Mortem Stress-Test)
1. **Rủi ro Công nghệ:** [Nguyên nhân & Phòng thủ]
2. **Rủi ro Hành vi Người dùng:** [Nguyên nhân & Phòng thủ]
3. **Rủi ro Dòng tiền / Chi phí API:** [Nguyên nhân & Phòng thủ]

---

## 📋 PHẦN 7: TIÊU CHUẨN ĐẦU RA BLUEPRINT V3.0/V10 (DÀNH CHO AI ARCHITECT)
- Tuân thủ đủ 11 khối Blueprint (Bệnh án $\rightarrow$ Giải pháp $\rightarrow$ Nguyên lý $\rightarrow$ Tech Stack $\rightarrow$ Rules $\rightarrow$ Tọa độ & Mỏ neo $\rightarrow$ Logic $\rightarrow$ Chaos Defense $\rightarrow$ Chỉ thị 2 Làn $\rightarrow$ Bảng Tiến Độ `[WIP ⏳]/[PENDING ⏸️]` $\rightarrow$ Gói Bàn Giao Tab 3).
- Đóng Sprint bắt buộc qua 2 chìa khóa: Tab 2 Audit 5 Gates + Tab 1 `RADAR-RECON-SPRINT-X-VERIFICATION`.

---

## 📍 PHẦN 8: BẢN ĐỒ TIẾN ĐỘ, MASTER CHECKLIST & MA TRẬN THI CÔNG (ROADMAP)
- [ ] [⚙️ OPS] Khởi tạo hạ tầng Coolify, PostgreSQL 16 (pgvector), Redis và `.env`
- [ ] [🗄️ DB] Khởi tạo `prisma/schema.prisma` và chạy `prisma migrate deploy`
- [ ] [📦 PKG] Cài đặt dependencies lõi và cấu hình TypeScript Strict Mode
- [ ] [💻 CODE] Thi công DOMAIN 0 (Auth & IDOR Shield)
- [ ] [🚀 DEPLOY] Hậu kiểm Tab 1 `🟢 SPRINT CLEAN` và Merge `main` Auto-Deploy

---

## 🚨 PHẦN 9: SỔ CÁI NỢ KỸ THUẬT & LỖI HỒI QUY (TECH DEBT & REGRESSION LEDGER)
| Ngày | Mã lỗi / Hạng mục | File liên quan | Trạng thái | Ghi chú xử lý |
| :--- | :--- | :--- | :---: | :--- |
| - | *(Trống - chờ ghi nhận)* | - | - | - |

---

## 🤖 PHẦN 10: GIAO THỨC TỰ KIỂM TOÁN DÀNH CHO AI (THE DELTA-CHECK PROTOCOL)
- Trước khi chốt bất kỳ task nào, AI Architect (Tab 2) bắt buộc xác nhận 0 tham chiếu mồ côi (Gate 4), đồng bộ liên phân hệ & kích thước AVSA (Gate 5), và chỉ chuyển trạng thái `- [x]` ở Phần 8 / `[ĐÃ VÁ]` ở Phần 9 sau khi Tab 1 cấp chứng chỉ `🟢 SPRINT CLEAN`.