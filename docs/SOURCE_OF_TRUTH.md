# Source of truth — tình trạng và ràng buộc dự án

Cập nhật: **2026-09-12** · Múi giờ: **Asia/Bangkok**.

Nguồn khởi tạo: yêu cầu định hình paper Medical World Model và yêu cầu chỉ định repo của chủ dự án trong cuộc thảo luận ngày 07/09/2026. Đây là hồ sơ quyết định/phạm vi, không phải bằng chứng rằng một giả thuyết khoa học đã đúng.

## 1. Những điều đã xác nhận

| Mục | Tình trạng đã xác nhận |
| --- | --- |
| Repo chính thức | `QuocKhanhLuong/MedicalWorldModel` |
| Loại dự án | Nghiên cứu một paper Medical World Model |
| Nền tảng của người nghiên cứu | AI/Computer Vision |
| Giai đoạn | Làm rõ bản chất và lựa chọn thiết lập nghiên cứu trước kiến trúc |
| Hồ sơ nghiên cứu mới | Hai đợt nghiên cứu 2026-09-12: 90 paper, 13 hồ sơ chính, 8 câu hỏi; thêm 4 deep-audit dossiers và aggregate metadata recount. Chưa đọc ảnh/nhãn bệnh nhân hoặc chạy mô hình |
| Câu hỏi trung tâm | Dự đoán trạng thái tiếp theo của cái gì, từ thông tin nào, chuyển tiếp như thế nào, phục vụ mục tiêu gì? |
| Quan hệ với paper dataset | Dự án dataset riêng đã chọn siêu âm; paper world model không bắt buộc dùng siêu âm hoặc dùng chung dữ liệu |
| Quy ước lưu trữ | Khi source of truth hoặc knowledge base có thay đổi có ý nghĩa, chủ động viết/cập nhật docs và đẩy vào repo trong lượt làm việc tương ứng |

## 2. Ràng buộc nghiên cứu do chủ dự án đặt ra

- Giải thích trực giác và ví dụ input → state → transition → output trước công thức.
- Phân biệt observation, state, lịch sử, latent, động học tự diễn tiến, action-conditioned dynamics, next-frame prediction, time-series model, world model và policy bằng định nghĩa vận hành.
- So sánh ít nhất A: sinh lý/hình dạng cơ quan; B: thu nhận ảnh; C: bệnh/tổn thương qua các lần khám hoặc điều trị.
- Mỗi thiết lập cần có thời gian, dữ liệu/nhãn, baseline, đánh giá nhiều bước, kiểm tra state, công trình gần, gap ứng viên, rủi ro và thí nghiệm bác bỏ.
- Đối chiếu paper gốc và trạng thái công bố. Không gọi mọi video predictor là world model; không bắt buộc world model phải có robot hoặc action.
- Không coi latent feature tự động là trạng thái lâm sàng có ý nghĩa; không suy diễn nhân quả từ tương quan trong dữ liệu quan sát.
- Chưa chọn backbone, diffusion, Transformer hoặc kiến trúc phức tạp.

## 3. Những điều CHƯA xác nhận

Chưa chốt cơ quan, bệnh, modality, dataset, quy mô, nhãn, metadata, horizon, endpoint sử dụng, định nghĩa state cuối cùng, baseline cuối cùng hoặc kiến trúc.

Chưa xác nhận quyền truy cập dữ liệu longitudinal, lịch điều trị, chuyển động đầu dò, robot hoặc dữ liệu từ cộng tác viên. Một nguồn dữ liệu được nhắc tới trong survey không đồng nghĩa với dữ liệu đã được tải, đã audit hoặc đã đủ quyền sử dụng.

Chưa có kết quả thực nghiệm, benchmark đã chạy hoặc bằng chứng về tính mới. Việc repo được khởi tạo không có nghĩa pipeline nghiên cứu đã triển khai.

## 4. Đề xuất hiện có — chưa phải quyết định của chủ dự án

Trong thảo luận ngày 2026-09-07, trợ lý đề xuất khảo sát sâu trước hai thiết lập:

- **A1:** dự báo trạng thái chuyển động/hình dạng mục tiêu trên cine-MRI, không cần action.
- **C1:** dự báo tổn thương longitudinal dưới bối cảnh chăm sóc quan sát được, không tuyên bố nhân quả điều trị.

**B vẫn là ứng viên**, không bị loại. Chủ dự án chưa chọn A1, C1 hoặc B. Chi tiết và tiêu chí dừng ở [RESEARCH_SETUPS.md](RESEARCH_SETUPS.md).

Ngày 2026-09-12, nghiên cứu nguồn mở rộng thành [8 câu hỏi và ranking để ưu tiên audit](OPEN_QUESTIONS.md), bao phủ cả A/B/C. Ranking là **INTERPRETATION / HYPOTHESIS của survey**, không thay thế lịch sử bằng một quyết định mới của chủ dự án. Không chọn backbone, modality hoặc đề tài cuối.

## 5. Câu hỏi mở quyết định bước tiếp theo

1. Có thể tiếp cận nguồn dữ liệu nào, với điều kiện sử dụng và thông tin thời gian/nhãn thực tế ra sao?
2. Horizon và đầu ra nào có mục tiêu sử dụng rõ ràng, thay vì chỉ dự báo ảnh kế tiếp?
3. Lịch sử có thông tin dự báo bổ sung so với quan sát hiện tại và state đơn giản không?
4. Baseline nào đủ mạnh để bác bỏ nhu cầu mô hình phức tạp?
5. Có thể kiểm tra nhiều bước, bất định và giá trị state mà không nhìn tương lai hoặc rò rỉ bệnh nhân không?

## 6. Thứ tự công việc đề xuất

Xác minh nguồn → audit khả thi dữ liệu → định nghĩa endpoint/horizon → baseline nhỏ → đánh giá lợi ích lịch sử và state → quyết định thiết lập → mới xem xét kiến trúc. Đây là trình tự đề xuất; chưa ghi nhận thí nghiệm nào đã thực hiện.

Đã hoàn thành đợt survey có giới hạn ở [landscape](surveys/VISUAL_WORLD_MODELS_LANDSCAPE.md), [medical survey](surveys/MEDICAL_WORLD_MODELS_SURVEY.md) và [adversarial gap analysis](surveys/TRANSFER_GAPS.md). **Đã có metadata-only recount giới hạn cho LUMIERE/BreastDCEDL; chưa hoàn thành usable trajectory/label/time/access audit, baseline headroom hoặc xác nhận novelty.** Các trường chưa rõ giữ UNKNOWN tại [DATASET_FEASIBILITY](DATASET_FEASIBILITY.md); phạm vi kiểm chứng nguồn ở [research log](surveys/RESEARCH_LOG.md).

## 7. Trạng thái sau yêu cầu tiếp tục nghiên cứu sâu — 2026-09-12

**Thực tế đã thực hiện:** mở rộng prior art và đọc methods/evaluation ở [bốn deep dossiers](surveys/RESEARCH_LOG.md#đợt-2--audit-methods-temporal-contract-và-metadata); kiểm tra lại DOI/publication status và các giới hạn forecast/simulation/planning. [Metadata audit](research_artifacts/2026-09-12_metadata_audit.json) lưu aggregate count, URL/version/checksum; không lưu patient-level records hoặc ảnh trong repo.

**Thực tế chưa thực hiện:** chưa chạy baseline/mô hình, audit nội dung ảnh/contour, xác lập usable cohort, chấp nhận DUA, thực nghiệm clinical hoặc xác nhận novelty. Metadata availability không được đổi thành “dự án đã có dữ liệu”.

**Quyết định giữ nguyên:** cả A/B/C chưa chọn; modality/data/backbone chưa chọn. Các phép kiểm tra state/calibration và ranking sửa trong OPEN_QUESTIONS là tổng hợp/đề xuất nghiên cứu, không phải quyết định của chủ dự án.
