# 🚀 CodeBridge V10 Playbook — Web-Only AI Engineering Cockpit

> **Trung tâm Chỉ huy & Bộ não Quy trình Phát triển Phần mềm 4 Buồng Lái V10**  
> Vận hành **100% trên trình duyệt Web** (`Google AI Studio` + `GitHub` + `Gitingest` + `vscode.dev` + `Coolify Webhook`) — Không cần IDE hay Terminal trên máy cá nhân.

---

## ⚡ 1. Trạm Mở Nhanh Công Cụ (Web Cockpit)

| Công cụ | Vai trò trong dây chuyền V10 | Truy cập nhanh |
| :--- | :--- | :--- |
| **Google AI Studio** | Nơi chạy 4 Tab hội thoại (`Tab 0`, `Tab 1`, `Tab 2`, `Tab 3`) | [Mở AI Studio](https://aistudio.google.com/) |
| **Gitingest** | Nén toàn bộ codebase hoặc lọc theo danh sách thành 1 file phẳng | [Mở Gitingest](https://gitingest.com/) |
| **vscode.dev** | Sửa/dán đè code trực tiếp trên trình duyệt & Commit nhánh | Bấm phím **`.`** ngay tại trang repo GitHub cần sửa |
| **Coolify VPS** | Tự động Build & Deploy container khi Merge PR vào nhánh `main` | *(Dán URL Coolify Dashboard của bạn vào đây)* |

> 💡 **Mẹo thao tác nhanh trên GitHub:** Bấm vào bất kỳ link file nào bên dưới, sau đó bấm biểu tượng **Copy raw file** (hai ô vuông xếp chồng ở góc trên bên phải khung xem code) để copy trọn vẹn nội dung dán sang AI Studio trong 1 giây.

---

## 🧠 2. Khu Vực 1: Bộ Não 4 Tab (`instructions/`)

*Dán nội dung từng file vào mục **System Instructions** của 4 cuộc hội thoại tương ứng trên Google AI Studio:*

| Tab | Danh tính & Vai trò | Ngưỡng Ngữ cảnh | File System Instruction |
| :---: | :--- | :---: | :--- |
| **Tab 0** | **Founding CTO & Product Strategist** — Phản biện 7 Powers, Pre-Mortem, xuất `CR-xxx.md` (Brownfield) hoặc 4 file gốc (Greenfield) | Sạch (`SSOT + Brief`) | [tab-0-strategist-cto.md](./instructions/tab-0-strategist-cto.md) |
| **Tab 1** | **Radar Scanner AST (Tri-Mode)** — `Mode 0` khám tổng thể cho Tab 0; `Pha 1` xuất Manifest + chuỗi Gitingest; `Pha 2` Hậu kiểm giữ quyền VETO | Lớn (`500k–1M tokens`) | [tab-1-radar-scanner.md](./instructions/tab-1-radar-scanner.md) |
| **Tab 2** | **Chief AI Architect & Supreme Judge** — Đúc Blueprint 2 Làn (`S&R` / `Full-File`) & Audit 5 Cửa ải Tử thần | Sạch (`< 80k tokens`) | [tab-2-architect-judge.md](./instructions/tab-2-architect-judge.md) |
| **Tab 3** | **Sterile Execution Builder** — Sinh code chính xác 100%, Zero-Chat, tuân thủ AVSA `< 120–300` dòng/file | Vô trùng (`< 8k–15k tokens`) | [tab-3-sterile-builder.md](./instructions/tab-3-sterile-builder.md) |

---

## 📖 3. Khu Vực 2: Sổ Tay Quy Trình & Câu Lệnh (`playbook/`)

| Tài liệu | Mục đích sử dụng | Mở nhanh |
| :--- | :--- | :--- |
| **Sổ tay Kiến trúc V10** | Bản đồ quy trình tổng thể, 6 Trụ cột V10, 2 Lộ trình A/B và bảng điều phối | [v10-architecture-guide.md](./playbook/v10-architecture-guide.md) |
| **Sổ tay 7 Lệnh Mở Khóa** | 7 prompt copy-paste nhanh để khởi động từng Tab & chuỗi Include Gitingest | [prompt-cheatsheet.md](./playbook/prompt-cheatsheet.md) |

### 🗺️ Sơ đồ Luồng Vận Hành Khép Kín V10 (Đã loại bỏ Tab ⭐)

```text
[LỘ TRÌNH A - App khỏe, thêm tính năng]: Gitingest (ssot-bundle) ───────────────────────► [TAB 0]
[LỘ TRÌNH B - App lỗi nặng, đại phẫu] : Gitingest (full-codebase) ➔ [TAB 1: MODE-0] ────► [TAB 0]
                                                                                              │
                                         (Xuất CR-xxx.md + Prompt) ◄──────────────────────────┘
                                                     │
                                                     ▼
[TAB 1: PHA 1] ──(Manifest + Chuỗi Include)──► [Gitingest.com] ──(1 file context-for-tab2.txt)
                                                                             │
                                                                             ▼
[TAB 2: ARCHITECT] ──(Blueprint 2 Làn)──► [TAB 3: BUILDER] ──(Code)──► [TAB 2: AUDIT 5 GATES]
                                                                             │
                                             (🟢 PASS ➔ Dán vào vscode.dev & Commit nhánh feat/cr-xxx)
                                                                             │
                                             (Xong Sprint: 🟡 CONDITIONAL PASS)
                                                                             │
                                                                             ▼
                     [Gitingest lấy code MỚI NHẤT] ➔ [TAB 1: PHA 2 HẬU KIỂM]
                                                             │
                                 ┌───────────────────────────┴───────────────────────────┐
                                 ▼                                                       ▼
                    🔴 SPRINT DEFECT VETOED                                       🟢 SPRINT CLEAN
                  (Quay lại Tab 2 vá nốt lỗi)                       (Tab 2 chốt CHANGELOG/PID ➔ Merge main)
                                                                                         │
                                                                                         ▼
                                                                           🚀 COOLIFY AUTO-DEPLOY VPS
```

---

## 📦 4. Khu Vực 3: Bộ Khung Gốc Starter Kit (`starter-kit/`)

*Copy toàn bộ thư mục `docs/` bên trong `starter-kit/` bỏ vào gốc Repo của **từng dự án App cụ thể**:*

| Tệp tin trong App Repo | Vai trò SSOT | Link mẫu gốc |
| :--- | :--- | :--- |
| `docs/ssot/PID.md` | Hiến pháp & Đặc tả tổng thể 10 phần (V9.0/V10) | [PID.md](./starter-kit/docs/ssot/PID.md) |
| `docs/ssot/.codebridgerules` | Luật code AVSA ($\ge 1.000$ dòng đóng băng, trần 300 dòng) & Bảo mật | [.codebridgerules](./starter-kit/docs/ssot/.codebridgerules) |
| `docs/ssot/codebridge.md` | Runbook hạ tầng Coolify, biến môi trường, cổng `3000/3001` & lệnh Migrate | [codebridge.md](./starter-kit/docs/ssot/codebridge.md) |
| `docs/ssot/Topology & repo map.txt` | Sơ đồ cây thư mục chuẩn & phân bổ cổng mạng | [Topology & repo map.txt](<./starter-kit/docs/ssot/Topology & repo map.txt>) |
| `docs/ssot/CHANGELOG.md` | Sổ nhật ký thay đổi (cập nhật 1 lần cuối Sprint) | [CHANGELOG.md](./starter-kit/docs/ssot/CHANGELOG.md) |
| `docs/ssot/DECISION_LOG.md` | Sổ cái quyết định kiến trúc (ADR) | [DECISION_LOG.md](./starter-kit/docs/ssot/DECISION_LOG.md) |
| `docs/changes/` | Nơi lưu các tệp Delta Spec `CR-xxx.md` cho từng đợt nâng cấp | [.gitkeep](./starter-kit/docs/changes/.gitkeep) |

---

## 🛡️ 5. Checklist Kỷ Luật Vàng Khi Vận Hành

1. **Lấy Gói SSOT cho Tab 0 trong 5 giây:** Dán chuỗi sau vào ô **Include** trên `gitingest.com`:
   ```text
   docs/ssot/*, prisma/schema.prisma, package.json
   ```
2. **Không bao giờ sửa tay vào `PID.md` giữa Sprint:** Mọi thay đổi ở app đang chạy chỉ viết vào `docs/changes/CR-xxx.md`. Chỉ cập nhật `CHANGELOG.md` / `PID.md` **1 lần duy nhất** sau khi Tab 1 Pha 2 cấp `🟢 SPRINT CLEAN`.
3. **Không commit code dở dang lên `main`:** Luôn tạo nhánh `feat/cr-xxx` trên `vscode.dev` để tránh kích hoạt Coolify rebuild liên tục giữa chừng.
4. **Chống lỗi "Bóng ma code cũ" ở Tab 1 Pha 2:** Trước khi chạy lệnh `RADAR-RECON-SPRINT-X-VERIFICATION`, bắt buộc phải bấm Ingest lại trên `gitingest.com` (trỏ đúng nhánh `feat/cr-xxx`) để lấy codebase mới nhất.
5. **Nếu Sprint có sửa `prisma/schema.prisma`:** Sau khi Merge `main` và Coolify deploy xong, nhớ vào **Coolify $\rightarrow$ Container Terminal** chạy `npx prisma migrate deploy` (tuyệt đối không chạy `db push` trên Production).

---

## 📝 6. Lịch Sử Phiên Bản Playbook

| Phiên bản | Ngày | Thay đổi chính |
| :--- | :--- | :--- |
| **V10.0** | 2026-11-25 | Chốt kiến trúc 4 Tab (bỏ Tab ⭐), bổ sung `Mode 0` cho Tab 1, Delta Spec `CR-xxx.md`, cầu nối `gitingest.com` và 2 Làn thi công tối ưu cho `vscode.dev`. |