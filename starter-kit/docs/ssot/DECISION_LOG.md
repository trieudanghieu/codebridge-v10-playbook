# ARCHITECTURAL DECISION RECORD (DECISION LOG / ADR)
> Ghi lại các quyết định kỹ thuật quan trọng (và lý do chọn/bỏ) để Tab 0 và Tab 2 không lặp lại sai lầm cũ.

---

## ADR-001: Áp dụng Kiến trúc Quy trình V10 Web-Only (Delta Spec + AVSA V9.0)
- **Ngày:** YYYY-MM-DD
- **Trạng thái:** `ACCEPTED`
- **Bối cảnh:** Quản trị dự án 100% trên trình duyệt (`AI Studio + gitingest.com + vscode.dev + Coolify`), cần nâng cấp/vá lỗi app đang chạy mà không phá vỡ cấu trúc cũ.
- **Quyết định:**
  1. Đóng băng các file di sản $\ge 1.000$ dòng (chỉ cấy Delegation Adapter 3–5 dòng), tách tính năng mới ra `src/modules/[feature]/` (`< 300` dòng/file).
  2. Mọi đợt nâng cấp viết thành tệp độc lập `docs/changes/CR-xxx.md` thay vì sửa tay trực tiếp vào `PID.md` giữa chừng.
- **Hệ quả / Trade-off:** Cần chạy `gitingest.com` cập nhật ngữ cảnh trước khi Hậu kiểm Pha 2 ở Tab 1.