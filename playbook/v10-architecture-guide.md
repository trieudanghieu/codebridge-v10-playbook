# 📖 SỔ TAY KIẾN TRÚC & QUY TRÌNH VẬN HÀNH V10 (DELTA & GITINGEST BRIDGE)

> **Đối tượng sử dụng:** Tech Lead / Chủ dự án vận hành **100% trên trình duyệt Web** (`Google AI Studio` + `GitHub` + `Gitingest` + `vscode.dev` + `Coolify Webhook`), không dùng VS Code/Cursor hay terminal trên laptop.

---

## PHẦN A: 4 MỤC TIÊU & 6 TRỤ CỘT GIẢI PHÁP V10

### 🎯 4 Mục tiêu cốt lõi
1. **Bảo toàn 100% sức mạnh gốc của từng Tab:** Giữ nguyên khả năng phản biện (7 Powers, Pre-Mortem) của Tab 0, khả năng quét AST sâu và quyền Phủ quyết của Tab 1, Audit 5 Gates độc lập của Tab 2, và độ chính xác code tuyệt đối của Tab 3.
2. **Triệt tiêu thao tác chắp vá SSOT bằng tay:** Không bao giờ phải mở file `PID.md` cũ dài hàng nghìn dòng ra dò chỗ nhét chữ khi nâng cấp hay sửa lỗi app đang chạy (*Brownfield*).
3. **Giảm 60–70% số lần copy-paste giữa các Tab:** Loại bỏ Tab trung gian dư thừa, gom file tự động bằng `gitingest.com`, và đóng gói code theo cụm thông minh để dán cực nhanh vào `vscode.dev`.
4. **An toàn tuyệt đối cho VPS Production:** Tách biệt quá trình vá code (trên nhánh phụ) với nhịp build của Coolify (trên nhánh `main`), đảm bảo app chỉ deploy khi đã vượt qua cả 2 chìa khóa kiểm định (Tab 2 + Tab 1).

---

### 🏛️ Trụ cột 1: Tinh gọn từ 5 Tab xuống còn 4 Tab khép kín (Loại bỏ Tab ⭐)
- **Khai tử Tab ⭐ trung gian:** Loại bỏ hoàn toàn bước copy sang Tab ⭐ để nhờ viết prompt chuyển tiếp. Dây chuyền chuẩn rút gọn thành **4 Buồng Lái khép kín**:
  `Tab 0 (Chiến lược & SSOT) ➔ Tab 1 (Trinh sát AST) ➔ Tab 2 (Architect & Audit 5 Gates) ➔ Tab 3 (Builder Vô trùng) ➔ Tab 2 (Audit) ➔ Tab 1 (Hậu kiểm đóng Sprint)`
- **Tích hợp sẵn Prompt chuyển Tab:** Cuối mỗi kết quả hoàn chỉnh của **Tab 0, Tab 1 và Tab 2**, AI tự động xuất sẵn một khung **`📋 [NEXT-TAB READY PROMPT]`**. Bạn chỉ cần bấm 1 nút Copy và dán thẳng sang Tab kế tiếp.
- *(Riêng **Tab 3** giữ 100% kỷ luật **Zero-Chat** — chỉ xuất code — vì xong bước này bạn copy code dán thẳng lại vào Tab 2 đang mở sẵn để Audit).*

---

### 🏛️ Trụ cột 2: "Cổng vào Tab 0 Thông Minh" (2 Lộ trình A/B) & Nạp Trọn Bộ SSOT
1. **Nạp trọn bộ SSOT + `package.json` vào Tab 0:**
   - Toàn bộ tài liệu mô tả hệ thống được lưu ngay trên repo GitHub (`docs/ssot/`) gồm: `PID.md`, `Topology & repo map.txt`, `codebridge.md`, `.codebridgerules`, `CHANGELOG.md`, `DECISION_LOG.md`, cộng với `prisma/schema.prisma` và `package.json`.
   - Tổng cả gói này chỉ nặng ~15k–30k tokens. Dùng `gitingest.com` gom thành **01 file phẳng `ssot-bundle.txt`** trong 5 giây giúp Tab 0 nắm đủ Tech Stack, thư viện đang cài, lịch sử quyết định (ADR) và ràng buộc Coolify.
2. **Phân luồng 2 Lộ trình thông minh trước khi vào Tab 0:**
   - **Lộ trình A (Vào thẳng Tab 0 – Fast-Track):**
     - *Khi nào dùng?* App đang chạy ổn định, tài liệu SSOT khớp với code thật, bạn chỉ muốn **thêm tính năng mới**.
     - *Cách làm:* Nạp thẳng `ssot-bundle.txt` vào **Tab 0** + yêu cầu tính năng mới (bỏ qua bước Tab 1 quét trước).
   - **Lộ trình B (Qua Tab 1 `MODE-0` trước $\rightarrow$ rồi mới vào Tab 0 – Deep-Diagnostic):**
     - *Khi nào dùng?* Khi **app đang có BUG phức tạp, chạy chậm, nghi lệch SSOT so với code thật (*Code-Spec Drift*), hoặc cần đại phẫu/tối ưu lại luồng**. Vì `repo_map.txt` và `PID.md` chỉ là bản vẽ tĩnh, không phản ánh được file nào đang phình $\ge 1.000$ dòng hay lỗi race condition ẩn trong code thật.
     - *Cách làm:* Nạp toàn bộ codebase (`full-codebase.txt` từ `gitingest.com`) vào **Tab 1** kèm lệnh **`MODE-0: STRATEGIC-RECON-FOR-TAB-0`** + mô tả lỗi. Tab 1 chụp X-quang đối chiếu Code thật vs SSOT và trả về bản **`# 🩺 [STRATEGIC HEALTH & ROOT-CAUSE BRIEF]`** (1–2 trang). Bạn mang bản Brief đó + `ssot-bundle.txt` nạp vào **Tab 0** để thiết kế giải pháp đột phá sát thực tế 100%.

---

### 🏛️ Trụ cột 3: Dẹp bỏ việc "Sửa tay vào `PID.md` cũ" bằng Giao thức `DELTA-SSOT` (`CR-xxx.md`)
- **Chế độ Dự án mới (Greenfield):** Tab 0 xuất đủ Bộ 4 File Hạt Giống (`PID.md` 10 phần, `schema.prisma`, `Topology & repo map.txt`, `codebridge.md`).
- **Chế độ App đang chạy (Brownfield):** Tuyệt đối KHÔNG viết lại `PID.md` tổng. Tab 0 chỉ xuất duy nhất **01 tệp Thay Đổi Độc Lập: `CR-[Số]-[Tên].md`** gồm `[ADDED]`, `[MODIFIED]`, `[REMOVED]`, `[UI TOUCHPOINT]`, `[DATABASE & INFRA DELTA]`, `[AVSA WARNING]` và `[SPRINT TASKS]`.
- **Lợi ích:** `PID.md` gốc được đóng băng an toàn. Bạn lưu `CR-xxx.md` vào `docs/changes/` trên `vscode.dev`. Chỉ đến **cuối Sprint**, sau khi Tab 1 đóng dấu `🟢 SPRINT CLEAN`, Tab 2 mới xuất đoạn chốt sổ để bạn cập nhật `CHANGELOG.md` / `PID.md` **1 lần duy nhất**.

---

### 🏛️ Trụ cột 4: Biến `gitingest.com` thành "Cây cầu tự động" giữa Tab 1 $\rightarrow$ Tab 2
- **Vấn đề được giải quyết:** Tab 1 chỉ trích 5–10 dòng mỏ neo, trong khi Tab 2 (`[INV-01]`) bắt buộc phải thấy nguyên văn toàn bộ file đích mới được thiết kế và Audit.
- **Giải pháp:** Ở **Tab 1 (Pha 1)**, ngoài bản `[BOUNDED CONTEXT MANIFEST]`, Tab 1 xuất thêm **Mục 6: `📦 [GITINGEST INCLUDE PATTERN]`** — một dòng đường dẫn chuẩn xác gom cả `docs/ssot/*, docs/changes/CR-*.md, prisma/schema.prisma, package.json` và các file code mục tiêu.
- **Thao tác của bạn:** Copy 1 dòng đó $\rightarrow$ dán vào ô **Include** trên `gitingest.com` $\rightarrow$ tải/copy **01 file phẳng `context-for-tab2.txt`** (dưới `80k tokens`) $\rightarrow$ dán 1 lần duy nhất vào **Tab 2**.

---

### 🏛️ Trụ cột 5: Tối ưu cho `vscode.dev` bằng "2 Làn Thi Công" (Giảm 60–70% Copy-Paste)
- **Làn 1 — Bọc Thép (`SURGICAL SEARCH/REPLACE`, làm 1 file/lượt):**
  - *Áp dụng cho:* **File Di Sản $\ge 1.000$ dòng** (vùng đóng băng Read-Only, chỉ sửa 1 khối Delegation Adapter 3–5 dòng), `schema.prisma`, hoặc file lõi nhạy cảm $> 300$ dòng.
  - *Trên `vscode.dev`:* Bấm `Ctrl+F` tìm đúng dòng đầu khối `SEARCH` và dán đè khối `REPLACE` — an toàn tuyệt đối.
- **Làn 2 — Tốc Độ Cao (`VERTICAL SLICE FULL-FILE`, gom cụm 2–4 file/lượt):**
  - *Áp dụng cho:* Các module Lát cắt dọc mới (`src/modules/[feature]/`) hoặc file nhỏ `< 120–300` dòng/file.
  - *Phối hợp:* Tab 2 đúc 1 Blueprint gộp cả cụm (`types.ts` + `service.ts` + `route.ts`), Tab 3 xuất liền **Full-File** hoàn chỉnh cho từng file trong 1 lượt, Tab 2 Audit cả cụm 1 lần.
  - *Trên `vscode.dev`:* Mở từng file bấm **`Ctrl+A` $\rightarrow$ `Ctrl+V`** (3 giây/file, không cần dò từng dòng).

---

### 🏛️ Trụ cột 6: Nhịp Nhánh Git An Toàn, Đồng Bộ Tab 1 Pha 2 & Coolify Auto-Deploy
1. **Cô lập nhánh làm việc trên `vscode.dev`:** Trước khi code một `CR-xxx`, tạo nhánh phụ (VD: `feat/cr-001`) ở góc dưới trái `vscode.dev`. Commit code vá lên nhánh này để không làm Coolify (đang nối với `main`) rebuild dở dang giữa chừng.
2. **Làm mới Codebase qua `gitingest.com` trước Hậu kiểm:** Khi Tab 2 cấp `🟡 [CONDITIONAL PASS]` ở task cuối Sprint, mở `gitingest.com` trỏ đúng vào nhánh `feat/cr-001` để xuất lại **file phẳng codebase MỚI NHẤT**, nạp vào **Tab 1 (Pha 2)** chạy lệnh `RADAR-RECON-SPRINT-X-VERIFICATION` (chống lỗi quét nhầm code cũ).
3. **Publish lên VPS:** Chỉ khi Tab 1 cấp **`🟢 SPRINT CLEAN`**, quay lại Tab 2 lấy gói chốt sổ `CHANGELOG.md` / `PID.md` dán vào `vscode.dev`, rồi **Merge Pull Request vào `main`** trên GitHub để **Coolify Webhook tự động build & deploy 1 lần duy nhất**. *(Nếu Sprint có sửa `schema.prisma`, vào Coolify $\rightarrow$ Terminal của container chạy `npx prisma migrate deploy`)*.

---

## PHẦN B: QUY TRÌNH THỰC HÀNH TỪNG BƯỚC (END-TO-END BƯỚC 0 $\rightarrow$ BƯỚC 7)

### 🔹 Bước 0: Chuẩn bị kho SSOT & Gom dữ liệu ban đầu
- **Tại `github.com` / `vscode.dev`:** Đảm bảo thư mục `docs/ssot/` chứa đủ 6 file SSOT (`PID.md`, `.codebridgerules`, `codebridge.md`, `Topology & repo map.txt`, `CHANGELOG.md`, `DECISION_LOG.md`) và `docs/changes/` sẵn sàng.
- **Tại `gitingest.com`:**
  - Xuất `ssot-bundle.txt` bằng ô **Include**: `docs/ssot/*, prisma/schema.prisma, package.json`.
  - *(Nếu đi Lộ trình B)*: Xuất thêm `full-codebase.txt` (toàn bộ code repo, bỏ `node_modules`, `.next`, `dist`).

### 🔹 Bước 0.5: Khám bệnh tổng thể ở Tab 1 — `MODE-0` *(Chỉ chạy nếu đi Lộ trình B)*
- **Đầu vào Tab 1:** `full-codebase.txt` + Lệnh `MODE-0: STRATEGIC-RECON-FOR-TAB-0` (copy từ `prompt-cheatsheet.md`) + mô tả triệu chứng/log lỗi Coolify.
- **Đầu ra Tab 1:** Bản **`# 🩺 [STRATEGIC HEALTH & ROOT-CAUSE BRIEF]`** (5 mục) + Prompt chuyển sang Tab 0.
- **Chuyển tiếp:** Mang Brief này + `ssot-bundle.txt` sang **Tab 0**.

### 🔹 Bước 1: Chiến lược & Đột phá tại Tab 0
- **Đầu vào Tab 0:** `ssot-bundle.txt` (+ Brief từ Bước 0.5 nếu Lộ trình B) + bài toán cần giải quyết.
- **Thao tác:** Phản biện cùng Tab 0 qua 7 Powers & Pre-Mortem đến khi chốt phương án $\rightarrow$ Gửi lệnh chốt Chặng 4.
- **Đầu ra Tab 0:** Tệp **`CR-xxx.md` (Delta Spec)** *(hoặc 4 file gốc nếu Greenfield)* + **`📋 [NEXT-TAB READY PROMPT]`** sang Tab 1.
- **Chuyển tiếp:**
  1. Mở `vscode.dev`, tạo nhánh mới `feat/cr-xxx`, lưu `CR-xxx.md` vào `docs/changes/CR-xxx.md` và Commit.
  2. Vào `gitingest.com` (trỏ nhánh `feat/cr-xxx`) lấy `full-codebase.txt` mới nhất (nếu chưa có `CR-xxx.md` trong file cũ).
  3. Mở **Tab 1** (hoặc phiên mới), dán `full-codebase.txt` + Prompt từ Tab 0.

### 🔹 Bước 2: Tiền Trinh Sát AST tại Tab 1 (Pha 1)
- **Đầu vào Tab 1:** `full-codebase.txt` + `CR-xxx.md` + Prompt từ Tab 0.
- **Đầu ra Tab 1:** **`# 📡 [BOUNDED CONTEXT MANIFEST]`** (5 mục) + **Mục 6: `📦 [GITINGEST INCLUDE PATTERN]`** + **`📋 [NEXT-TAB READY PROMPT]`** sang Tab 2.
- **Chuyển tiếp:**
  1. Copy dòng ở **Mục 6** dán vào ô **Include** trên `gitingest.com` $\rightarrow$ tải/copy **01 file phẳng `context-for-tab2.txt`**.
  2. Mở **Tab 2 mới (sạch `< 80k tokens`)**, dán `context-for-tab2.txt` + Manifest + Prompt từ Tab 1.

### 🔹 Bước 3: Thiết kế Blueprint tại Tab 2 (Architect)
- **Thao tác:** Tab 2 kiểm tra đủ SSOT + code gốc $\rightarrow$ đề xuất **Option 1 (Tinh gọn)** và **Option 2 (Bọc thép)** $\rightarrow$ Bạn nhắn chọn Option.
- **Đầu ra Tab 2:** **`[BLUEPRINT V10]`** (11 khối, đánh dấu file/cụm làm trước là `[WIP ⏳]`, chỉ rõ **Làn 1 `S&R`** hay **Làn 2 `Full-File`**).
- **Chuyển tiếp:** Copy toàn bộ `[BLUEPRINT]` (Mục 1–10) + *(nếu Blueprint sửa file cũ: copy thêm nguyên văn file gốc của file `[WIP ⏳]` đó)* dán sang **Tab 3**.

### 🔹 Bước 4: Sinh mã nguồn tại Tab 3 (Sterile Builder)
- **Đầu vào Tab 3 (phiên sạch `< 8k–15k tokens`):** `[BLUEPRINT]` + nguyên văn file gốc (nếu sửa file cũ).
- **Đầu ra Tab 3:** Chỉ 100% mã nguồn (`Full-File` cho cụm Làn 2, hoặc `<<<< SEARCH / >>>> REPLACE` cho Làn 1).
- **Chuyển tiếp:** Copy toàn bộ code vừa sinh quay ngược lại **Tab 2** để Audit *(Chưa dán lên `vscode.dev` vội!)*.

### 🔹 Bước 5: Kiểm định 5 Gates tại Tab 2 (Supreme Judge) & Dán lên `vscode.dev`
- **Nếu `🔴 [AUDIT FAILED]`:** Copy thông báo lỗi + Prompt quay lại **Tab 3** sửa lại đúng chỗ sai, rồi đưa lại Tab 2.
- **Nếu `🟢 [PASS]` (còn `[PENDING ⏸️]`):**
  1. Mở **`vscode.dev`** (trên nhánh `feat/cr-xxx`): `Ctrl+A ➔ Ctrl+V` (nếu Full-File) hoặc `Ctrl+F` dán đè đoạn `Search/Replace` (nếu Làn 1) $\rightarrow$ **Commit**.
  2. Quay lại Tab 2 gọi Blueprint tiếp theo cho các file `[PENDING ⏸️]` (lặp lại Bước 3 $\rightarrow$ Bước 5).
- **Nếu `🟡 [CONDITIONAL PASS]` (đã xong task cuối Sprint):**
  1. Dán & Commit file cuối cùng lên nhánh `feat/cr-xxx` trên `vscode.dev`.
  2. Chuyển sang **Bước 6**.

### 🔹 Bước 6: Hậu Trinh Sát Đóng Sprint tại Tab 1 (Pha 2 - Chìa khóa thứ 2)
- **Chuẩn bị:** Vào **`gitingest.com`** (trỏ đúng nhánh `feat/cr-xxx`), bấm Ingest lại để tải **01 file phẳng `full-codebase-latest.txt` MỚI NHẤT**.
- **Đầu vào Tab 1 (nên mở phiên Tab 1 mới cho sạch):** `full-codebase-latest.txt` + Prompt **`RADAR-RECON-SPRINT-X-VERIFICATION`** từ Tab 2.
- **Kết quả:**
  - Nếu **`🔴 SPRINT DEFECT VETOED`**: Dùng chuỗi Include mới ở Mục 6 của Tab 1 lọc lại qua `gitingest.com` và quay về **Bước 3 (Tab 2)** vá nốt lỗi.
  - Nếu **`🟢 SPRINT CLEAN`**: Chuyển sang **Bước 7**.

### 🔹 Bước 7: Chốt sổ SSOT & Coolify Auto-Deploy lên VPS
1. Quay lại **Tab 2** (hoặc copy Prompt cuối từ Tab 1) báo đã đạt `🟢 SPRINT CLEAN` $\rightarrow$ Nhận gói cập nhật 1 lần cho `CHANGELOG.md`, `DECISION_LOG.md`, `Topology & repo map.txt` và `PID.md` (chuyển `CR-xxx.md` vào `docs/changes/archived/`).
2. Dán gói cập nhật vào `vscode.dev` trên nhánh `feat/cr-xxx` và **Commit**.
3. Lên **`github.com`** tạo và **Merge Pull Request từ `feat/cr-xxx` vào `main`**.
4. **Coolify Webhook** tự động kéo code từ `main`, build lại Docker container và publish lên VPS. *(Nếu có sửa `prisma/schema.prisma`, vào Coolify $\rightarrow$ Container Terminal chạy `npx prisma migrate deploy`)*.

---

## PHẦN C: PHỤ LỤC ĐỐI CHIẾU CÁC MẪU ĐẦU RA CHỦ LỰC

### 1. Cấu trúc chuẩn của `# 🩺 [STRATEGIC HEALTH & ROOT-CAUSE BRIEF]` (Tab 1 Mode 0 trả ra)
*(Dùng để bạn đối chiếu khi chạy Bước 0.5)*:
1. **🔍 Chẩn đoán Nguyên nhân Gốc rễ (`Root-Cause in Code`):** Lỗi thực tế nằm ở hàm/luồng nào, cơ chế lỗi (Race Condition, N+1, rò rỉ RAM...).
2. **⚖️ Đối soát Độ vênh SSOT vs Code thật (`Code-Spec Drift`):** Những điểm code đang chạy khác với `PID.md`, `repo_map.txt`, `schema.prisma`.
3. **🧱 Bản đồ Điểm nóng AVSA & Bãi mìn Hệ thống:** Liệt kê các File Di Sản $\ge 1.000$ dòng (chỉ được cấy Adapter 3–5 dòng) và các điểm phụ thuộc chéo dễ sập dây chuyền.
4. **📦 Ràng buộc Kỹ thuật Thực tế (`Stack & Infra Reality`):** Thư viện thực tế trong `package.json`, biến `.env`, cổng mạng, Coolify/Docker.
5. **💡 Điểm tựa Hiện hữu để Tái cấu trúc (`Reusable Assets`):** Các service, helper, model đang chạy tốt để Tab 0 tận dụng.

### 2. Bảng tóm tắt Vai trò 4 Tab & Công cụ
| Buồng lái / Công cụ | Đầu vào chính | Đầu ra bàn giao |
| :--- | :--- | :--- |
| **`gitingest.com`** | URL Repo/Nhánh GitHub + chuỗi *Include* (nếu lọc) | `ssot-bundle.txt`, `full-codebase.txt`, hoặc `context-for-tab2.txt` |
| **Tab 1 (`Mode 0`)** | `full-codebase.txt` + `MODE-0` + mô tả lỗi | `# 🩺 [STRATEGIC HEALTH & ROOT-CAUSE BRIEF]` + Prompt sang Tab 0 |
| **Tab 0** | `ssot-bundle.txt` (+ Brief nếu Lộ trình B) | **`CR-xxx.md`** (hoặc 4 file Greenfield) + Prompt sang Tab 1 |
| **Tab 1 (`Pha 1`)** | `full-codebase.txt` + `CR-xxx.md` | `[BOUNDED CONTEXT MANIFEST]` + **Chuỗi Include Gitingest** + Prompt sang Tab 2 |
| **Tab 2** | `context-for-tab2.txt` + Manifest | **`[BLUEPRINT V10]`** $\rightleftarrows$ **Audit 5 Gates (`PASS`/`FAIL`/`CONDITIONAL`)** |
| **Tab 3** | `[BLUEPRINT]` + code gốc file `[WIP ⏳]` | Code **Full-File** (Làn 2) hoặc **`<<<< SEARCH / >>>> REPLACE`** (Làn 1) |
| **`vscode.dev`** | Code đạt `🟢 PASS` từ Tab 2 | Commit sạch trên nhánh `feat/cr-xxx` |
| **Tab 1 (`Pha 2`)** | `full-codebase-latest.txt` + `RADAR-RECON` | **`🟢 SPRINT CLEAN`** *(hoặc Veto `🔴`)* $\rightarrow$ Merge `main` cho **Coolify Deploy** |