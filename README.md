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
| [Visual world model landscape](docs/surveys/VISUAL_WORLD_MODELS_LANDSCAPE.md) | Lineage, frontier và định nghĩa vận hành; CV → năng lực có thể chuyển |
| [Medical world models survey](docs/surveys/MEDICAL_WORLD_MODELS_SURVEY.md) | Phân tích hệ/state/transition/use case và so sánh A/B/C |
| [Transfer gaps](docs/surveys/TRANSFER_GAPS.md) | Adversarial prior-art search và những novelty claims bị bác bỏ |
| [Paper matrix](docs/PAPER_MATRIX.md) · [CSV](docs/paper_matrix.csv) | 55 paper, metadata/phiên bản, methods, evaluation và giới hạn đọc |
| [Dataset feasibility](docs/DATASET_FEASIBILITY.md) | 13 nguồn dữ liệu; access, thời gian/nhãn, UNKNOWN và leakage audit cần làm |
| [Open questions](docs/OPEN_QUESTIONS.md) | 8 câu hỏi chưa chọn, baseline/falsifiers, ranking và thông tin còn thiếu |
| [Sổ nguồn tham khảo](docs/REFERENCES.md) | Nguồn sơ cấp đã đối chiếu, crosswalk từ đầu mối cũ và giới hạn xác minh |
| [Research log](docs/surveys/RESEARCH_LOG.md) | Skills/phương pháp, citation-integrity pass và giới hạn của survey |
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

Cập nhật hồ sơ: **2026-09-12** · Múi giờ: **Asia/Bangkok**. Survey nguồn đã thực hiện; dataset manifest audit và thực nghiệm chưa thực hiện. A/B/C đều chưa chọn.
