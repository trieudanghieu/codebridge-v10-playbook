# ⚡ SỔ TAY 7 CÂU LỆNH MỞ KHÓA NHANH (TECH LEAD PROMPT CHEAT-SHEET)

> **Cách dùng:** Khi bắt đầu một bước mới trên `gitingest.com` hoặc `AI Studio` (mà chưa có sẵn `[NEXT-TAB READY PROMPT]` từ Tab trước), hãy copy đúng mẫu câu lệnh dưới đây, điền phần trong ngoặc `[...]` rồi gửi đi.

---

## 1️⃣ Chuỗi Include cho `gitingest.com` — Gom Gói SSOT (Dùng cho Tab 0)
*(Dán dòng này vào ô **Include** trên `gitingest.com`, tải/copy thành file `ssot-bundle.txt`)*:
```text
docs/ssot/*, prisma/schema.prisma, package.json
```
*(Nếu dự án có file `CR-xxx.md` đang làm dở muốn Tab 0 đọc luôn thì thêm `, docs/changes/CR-*.md` ở cuối).*

---

## 2️⃣ Lệnh mở Tab 1 — `MODE-0` Khám bệnh tổng thể cho App đang lỗi *(Bước 0.5 - Lộ trình B)*
*(Dán kèm **file phẳng toàn bộ codebase** `full-codebase.txt` từ `gitingest.com` vào một hội thoại Tab 1)*:
```text
MODE-0: STRATEGIC-RECON-FOR-TAB-0
Bối cảnh: App đang chạy thực tế và gặp các vấn đề/lỗi sau:
- [Mô tả ngắn triệu chứng / Dán 10-20 dòng log lỗi từ Coolify vào đây]
- [Nêu mong muốn cải tiến/tính năng muốn nâng cấp thêm]

Nhiệm vụ: Hãy chụp X-quang đối chiếu code thật với SSOT, tìm nguyên nhân gốc rễ, chỉ rõ các file di sản >= 1.000 dòng liên quan và xuất [# 🩺 STRATEGIC HEALTH & ROOT-CAUSE BRIEF] để tôi mang sang Tab 0. Tuyệt đối KHÔNG viết code.
```

---

## 3️⃣ Lệnh mở Tab 0 — Bắt đầu phản biện & thiết kế giải pháp *(Chọn Lộ trình A hoặc B)*
*(Dán kèm file `ssot-bundle.txt` vào hội thoại Tab 0)*:
```text
Tôi nạp Gói SSOT đầy đủ của app hiện tại (`ssot-bundle.txt`).
[NẾU ĐI LỘ TRÌNH B, DÁN THÊM BẢN BRIEF TỪ TAB 1 MODE-0 VÀO ĐÂY]

Vấn đề thực tế / Mục tiêu đợt nâng cấp này của tôi là:
- [Ghi rõ lỗi cần sửa triệt để và tính năng đột phá muốn làm]

Hãy phản biện theo kỷ luật 7 Powers, chạy bài test Pre-Mortem và cùng tôi chốt phương án tối ưu trước khi xuất hồ sơ Delta Spec `CR-xxx.md`.
```

---

## 4️⃣ Lệnh chốt Tab 0 — Xuất hồ sơ bàn giao *(Chặng 4)*
*(Dùng khi đã thảo luận và thống nhất xong phương án với Tab 0)*:

- **Nếu là App đang chạy (Brownfield):**
```text
Tôi chốt phương án vừa thống nhất. Hãy chuyển sang Chặng 4 (Nhánh 4B - Brownfield), xuất trọn vẹn tệp `CR-001-[ten-ngan].md` (Delta Spec) kèm hướng dẫn lưu lên `vscode.dev` và khối `[NEXT-TAB READY PROMPT]` để tôi chuyển sang Tab 1 Pha 1.
```

- **Nếu là Dự án mới tinh 100% (Greenfield):**
```text
Tôi chốt phương án. Hãy chuyển sang Chặng 4 (Nhánh 4A - Greenfield), xuất trọn vẹn Bộ 4 File Hạt Giống (`PID.md` chuẩn 10 phần, `schema.prisma`, `Topology & repo map.txt`, `codebridge.md`) không cắt xén, kèm khối `[NEXT-TAB READY PROMPT]` sang Tab 1.
```

---

## 5️⃣ Lệnh khởi tạo Tab 2 sạch (`< 80k tokens`)
*(Mở cuộc hội thoại Tab 2 mới, dán file phẳng `context-for-tab2.txt` lấy từ `gitingest.com` theo chuỗi Include ở Mục 6 của Tab 1, kèm lệnh này)*:
```text
Tôi nạp file `context-for-tab2.txt` (chứa đủ 6 tài liệu SSOT + `CR-xxx.md` + nguyên văn code gốc các file đích) cùng báo cáo `[BOUNDED CONTEXT MANIFEST]` từ Tab 1 bên dưới.
Hãy kiểm tra xác nhận `🟢 [WAR_ROOM_READY]`, sau đó phân tích tác động qua SRE Paranoia Engine, đề xuất Option 1 (Tinh gọn) và Option 2 (Bọc thép) rồi dừng lại hỏi tôi chọn trước khi đúc Blueprint.

--- DÁN MỤC 1 ĐẾN MỤC 5 CỦA [BOUNDED CONTEXT MANIFEST] VÀO ĐÂY ---
```

---

## 6️⃣ Lệnh trong Tab 2 — Báo đã dán code xong lên `vscode.dev` & gọi file tiếp theo
*(Dùng sau khi Tab 2 Audit báo `🟢 [PASS]` và bạn đã commit file đó lên nhánh `feat/cr-xxx` của `vscode.dev`)*:
```text
Tôi đã áp dụng code vừa đạt [PASS] và commit lên nhánh làm việc trên `vscode.dev`.
Hãy chuyển sang đúc Blueprint tiếp theo cho các file `[PENDING ⏸️]` còn lại trong bảng tiến độ (nếu thiếu nguyên văn file gốc nào trong ngữ cảnh chat này, hãy báo tôi để tôi copy bổ sung).
```

---

## 7️⃣ Lệnh cuối cùng ở Tab 2 — Nhận Gói Chốt Sổ SSOT sau khi Tab 1 báo `🟢 SPRINT CLEAN`
*(Dùng khi Tab 1 Pha 2 đã nghiệm thu thành công toàn cục)*:
```text
Tab 1 Pha 2 đã nghiệm thu toàn cục và cấp chứng chỉ: 🟢 SPRINT CLEAN cho đợt `CR-xxx`.
Hãy xuất cho tôi Gói Chốt Sổ SSOT cuối Sprint (1 lần duy nhất):
1. Đoạn cập nhật cho `docs/ssot/CHANGELOG.md` (kèm ADR).
2. Đoạn cập nhật cho `docs/ssot/DECISION_LOG.md` và `docs/ssot/Topology & repo map.txt` (nếu có module/file mới).
3. Chỉ dẫn cập nhật/lưu trữ cho `docs/ssot/PID.md` (dạng Search/Replace ngắn gọn nếu cần sửa) để tôi dán vào `vscode.dev`, Commit và Merge vào `main` cho Coolify Auto-Deploy.
```