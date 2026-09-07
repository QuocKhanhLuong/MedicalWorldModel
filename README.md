# Medical World Model

Repo chính thức của dự án nghiên cứu **Medical World Model**.

**Giai đoạn hiện tại:** làm rõ hệ thống được mô hình hóa, trạng thái, chuyển tiếp, mục tiêu sử dụng và điều kiện dữ liệu. Chưa chốt bài toán, modality, dataset hoặc kiến trúc.

**Câu hỏi trung tâm:** Mô hình dự đoán trạng thái tiếp theo của **cái gì**, từ **thông tin nào**, chuyển trạng thái **như thế nào**, để phục vụ **mục tiêu gì**?

## Tài liệu dự án

| Tài liệu | Nội dung |
| --- | --- |
| [Source of truth](docs/SOURCE_OF_TRUTH.md) | Phạm vi, ràng buộc đã xác nhận, trạng thái hiện tại và câu hỏi còn mở |
| [Knowledge base](docs/KNOWLEDGE_BASE.md) | Định nghĩa vận hành, ví dụ, khung đánh giá và giới hạn suy luận |
| [Các thiết lập nghiên cứu](docs/RESEARCH_SETUPS.md) | Ba họ A/B/C, hai hướng đề xuất khảo sát và điều kiện bác bỏ |
| [Sổ nguồn tham khảo](docs/REFERENCES.md) | Nguồn ứng viên, trạng thái xác minh và việc cần kiểm tra |
| [Nhật ký thay đổi](docs/CHANGELOG.md) | Những thay đổi có ý nghĩa về phạm vi, kiến thức, dữ liệu và thí nghiệm |
| [Quy ước cho tác nhân làm việc](AGENTS.md) | Cách đọc, cập nhật và đồng bộ docs vào GitHub |

## Nguyên tắc

- Paper world model độc lập với dự án dataset siêu âm; không bắt buộc dùng chung modality hoặc dữ liệu.
- Không giả định đã có longitudinal data, thông tin điều trị, pose đầu dò hoặc robot.
- Làm rõ thiết lập và baseline trước khi chọn kiến trúc.
- Tách **quyết định đã chốt**, **đề xuất/giả thuyết**, **kiến thức đã kiểm chứng** và **nội dung cần xác minh**.
- Đánh giá dự đoán nhiều bước và giá trị của state, không chỉ độ đẹp của ảnh sinh; không suy diễn nhân quả từ tương quan quan sát.

## Quy ước cập nhật

Theo yêu cầu của chủ dự án ngày **07/09/2026**, mỗi khi có thay đổi có ý nghĩa về source of truth hoặc knowledge base trong một lượt làm việc, cập nhật tài liệu tương ứng và commit/push vào repo này trong chính lượt đó. Báo commit hoặc lỗi đồng bộ thực tế. Không tạo commit cho nội dung trùng hoặc không thay đổi.

Đây là quy trình làm việc có chủ động cập nhật docs, **không phải dịch vụ theo dõi cuộc trò chuyện hay đồng bộ nền đã được triển khai**.

Repo công khai chỉ chứa tài liệu phù hợp để công bố. Không commit dữ liệu nhận diện bệnh nhân, hồ sơ lâm sàng riêng tư, thông tin truy cập hay dữ liệu bị hạn chế phân phối.

Cập nhật hồ sơ: **2026-09-07** · Múi giờ: **Asia/Bangkok**.
