# Nhật ký thay đổi tài liệu

Ngày theo múi giờ **Asia/Bangkok**. Chỉ ghi thay đổi có ý nghĩa. Lịch sử commit là dấu vết phiên bản; nhật ký này giải thích nội dung và hệ quả, không thay thế bằng chứng khoa học.

## 2026-09-07 — Khởi tạo repo chính thức và hồ sơ nghiên cứu

**Căn cứ:** chủ dự án cung cấp `QuocKhanhLuong/MedicalWorldModel` làm repo chính thức và yêu cầu chủ động cập nhật docs mỗi khi source of truth hoặc knowledge base thay đổi. Nội dung nền lấy từ yêu cầu định hình paper và phần thảo luận hiện tại.

**Thay đổi:**

- Tạo README và AGENTS.md: mục lục và quy trình đọc/sửa/kiểm tra/commit docs trong cùng lượt làm việc.
- Tạo SOURCE_OF_TRUTH.md: ghi phạm vi đã xác nhận, các ràng buộc và tình trạng chưa chọn bài toán/kiến trúc; không giả định dữ liệu có sẵn.
- Tạo KNOWLEDGE_BASE.md: chuyển khung giải thích observation/state/action/transition/policy và hợp đồng đánh giá thành tài liệu làm việc.
- Tạo RESEARCH_SETUPS.md: lưu ba họ A/B/C và hai hướng A1/C1 dưới nhãn đề xuất chưa được chọn, kèm baseline, rủi ro và phép thử bác bỏ.
- Tạo REFERENCES.md: đưa các đầu mối từ thảo luận vào hàng đợi cần xác minh; không coi metadata và số liệu trong câu trả lời trước là bằng chứng đã kiểm chứng trong repo.

**Quyết định thực sự:** repo này là nơi lưu hồ sơ chính thức; có quy ước chủ động đồng bộ khi có thay đổi có ý nghĩa. Chưa chọn A1, B hoặc C1; chưa triển khai mô hình hay chạy thí nghiệm.

**Giới hạn:** đợt này là khởi tạo và chuẩn hóa docs, không phải lượt kiểm chứng độc lập toàn bộ survey hoặc audit dataset. Chưa thiết lập dịch vụ đồng bộ nền.

**Việc tiếp theo đề xuất:** xác minh nguồn ứng viên, audit điều kiện dữ liệu, định nghĩa endpoint/horizon và chạy baseline nhỏ trước quyết định thiết lập hoặc kiến trúc.

---

## Mẫu cho cập nhật tiếp theo

### YYYY-MM-DD — Tên thay đổi

**Loại:** quyết định / cập nhật kiến thức / nguồn đã xác minh / đính chính / dữ liệu / thí nghiệm / blocker.

**Căn cứ:** yêu cầu của chủ dự án, nguồn đã đọc hoặc artifact/commit/kết quả đo cụ thể.

**Thay đổi:** phần nào đã thay đổi so với bản trước và những file liên quan.

**Hệ quả:** quyết định nào thay đổi; điều nào chỉ là đề xuất; giới hạn và mức độ chắc chắn.

**Còn mở / bước tiếp theo:** chỉ ghi việc thực sự còn thiếu, không trình bày như đã thực hiện.
