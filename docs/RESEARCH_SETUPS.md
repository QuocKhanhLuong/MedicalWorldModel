# Các thiết lập nghiên cứu ứng viên

Cập nhật: **2026-09-12**.

**Trạng thái:** A/B/C từ thảo luận vẫn chưa được chủ dự án chọn. Đợt survey 2026-09-12 đã đối chiếu nguồn ở [REFERENCES.md](REFERENCES.md), nhưng không xác nhận dữ liệu đã sẵn có, đủ nhãn hoặc đủ quyền sử dụng. Không có claim novelty đã được chứng minh. Các câu hỏi chi tiết, prior art, horizon đề xuất và falsifiers mới ở [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md); feasibility từng nguồn ở [DATASET_FEASIBILITY.md](DATASET_FEASIBILITY.md).

## A. Động học sinh lý/hình dạng cơ quan

**Hệ:** cơ quan hoặc mục tiêu di chuyển/biến dạng trong một chuỗi thu nhận. Phiên bản A1 được đề xuất là chuyển động mục tiêu trên cine-MRI.

**Observation:** cine quá khứ, mask khởi tạo hoặc contour quá khứ nếu thiết lập cho phép, cadence/timestamp. **State ứng viên:** hình dạng, vị trí, hướng/vận tốc, pha hoặc bất định. **Action:** không bắt buộc; A1 khởi đầu không-action.

**Thời gian:** theo cadence thực tế; báo horizon bằng đơn vị thời gian, không chỉ số frame. Kiểm tra gián đoạn, frame mất và thay đổi nhịp lấy mẫu. Không nối các đoạn không liên tục thành một chuỗi đều.

**Input → output:** prefix cine và mục tiêu đã xác định → vị trí/contour và bất định ở nhiều horizon. **Mục tiêu ứng viên:** đánh giá bù trễ ngoại tuyến; chưa tuyên bố điều khiển hoặc an toàn lâm sàng.

**Dữ liệu/nhãn cần:** chuỗi liên tục, thông tin thời gian đáng tin cậy, pixel spacing khi đo mm, định danh bệnh nhân và nhãn mục tiêu phù hợp. **Nguồn ứng viên:** TrackRAD2025; phải kiểm tra split, cadence, phần nhãn thực sự truy cập được và điều kiện sử dụng.

**Baseline:** giữ nguyên contour; vận tốc hằng; bộ lọc trạng thái đơn giản; mô hình chu kỳ. Cùng thông tin quá khứ và cùng split.

**Đánh giá:** sai số tâm/bề mặt, Dice theo horizon, hướng/vận tốc, hiệu chuẩn và độ rộng khoảng dự báo; phân tích đoạn đổi hướng so với chuyển động ổn định. Tách rollout không cập nhật với tracking được nhận frame mới. Kiểm tra cùng state cho cả vị trí lẫn hình dạng.

**Công trình đã đối chiếu trong survey:** [PCA cine forecasting](PAPER_MATRIX.md#m09), [cardiac ODE](PAPER_MATRIX.md#m10), [linear gating](PAPER_MATRIX.md#m21). Phân biệt dự báo từ prefix với tái dựng dùng cả chu kỳ; cần bổ sung PCA+linear/Kalman/GP vào baseline đủ mạnh.

**Gap ứng viên:** history hình dạng có giúp hơn vị trí–vận tốc đơn giản ở đổi hướng hoặc chuyển động không đều không? **Rủi ro:** baseline đã đủ tốt; chỉ học chu kỳ; thời gian không đáng tin; nhãn đại diện khác mục tiêu; rò rỉ người bệnh.

**Thí nghiệm bác bỏ nhỏ:** chọn chuỗi đã audit, tách bệnh nhân, chạy baseline và so thêm thông tin history. Dừng hoặc đổi giả thuyết nếu không có lợi ích ở endpoint/horizon hữu ích, lợi ích chỉ ở pixel nền, hoặc biến mất khi chia đúng bệnh nhân. Kết luận về khả năng phân biệt hiệu ứng còn phụ thuộc độ bất định và cỡ mẫu, không chỉ một điểm số trung bình.

## B. Động học thu nhận ảnh

**Hệ:** giải phẫu–thiết bị–quá trình quan sát. **Observation:** ảnh và pose/thông số đã đo. **State ứng viên:** giải phẫu tích lũy, pose tương đối, vùng đã thấy và bất định vùng chưa biết. **Action:** chuyển động/thao tác nếu thực sự có dữ liệu tương ứng; pose thay đổi đã đo không mặc nhiên là command.

**Thời gian:** frame/thao tác và thời gian thực; đánh giá theo cả quãng dịch chuyển/quỹ đạo. Đồng bộ ảnh–pose và hiệu chuẩn là điều kiện dữ liệu, không phải giả định đã thỏa.

**Input → output:** prefix ảnh và pose → quan sát dưới pose kế tiếp được chỉ định và mức tin cậy. **Mục tiêu ban đầu:** dự đoán quan sát hoặc kiểm tra tính nhất quán thu nhận, chưa mặc định hướng dẫn robot.

**Dữ liệu/nhãn cần:** tracking đồng bộ, calibration, định danh người/quỹ đạo; landmark hoặc nhãn giải phẫu cho đánh giá khi có thể. **Nguồn ứng viên:** TUS-REC2024; phải đối chiếu nội dung công khai và giấy phép. Chưa giả định có lực tiếp xúc, lệnh robot hoặc nhãn mặt cắt lâm sàng.

**Baseline:** giữ ảnh; warp cục bộ; map/tái dựng chỉ từ prefix rồi reslice theo pose khi hình học cho phép. Không dùng scan tương lai dựng map rồi gọi đó là dự báo từ quá khứ.

**Đánh giá:** landmark/cấu trúc giải phẫu, nhất quán khi quay lại vùng đã thấy, rollout qua nhiều thao tác, bất định khi ra ngoài vùng có bằng chứng; chia theo người và quỹ đạo. So state từ một frame với history tại những lát cắt hiện tại mơ hồ.

**Công trình đã đối chiếu trong survey:** [EchoWorld](PAPER_MATRIX.md#m02), [robot US WM](PAPER_MATRIX.md#m03), [Hu pose-conditioned synthesis 2017](PAPER_MATRIX.md#m23). Giữ offline guidance, measured displacement và commanded-action closed-loop evidence riêng; không giả định có public release của cohort tác giả.

**Gap ứng viên:** state tích lũy có phân biệt được vùng có đủ bằng chứng để dự đoán và vùng chưa biết, đồng thời giữ nhất quán nhiều bước không? **Rủi ro:** pose/lực tiếp xúc/sinh lý bị trộn; baseline hình học đã đủ; đánh giá policy chỉ trong mô hình do chính nó tối ưu.

**Thí nghiệm bác bỏ nhỏ:** so current-only, history và baseline hình học trên người/quỹ đạo giữ lại; kiểm tra khi trở về vùng cũ và khi ghép sai pose có kiểm soát. Nếu không sử dụng điều kiện chuyển động hoặc không hơn baseline, xem lại giả thuyết. Ablation pose không chứng minh nhân quả.

## C. Diễn biến bệnh/tổn thương longitudinal

**Hệ:** tổn thương/bệnh qua nhiều lần khám. C1 được đề xuất khởi đầu bằng dự báo quan sát, không tối ưu điều trị.

**Observation:** ảnh các lần khám trước, khoảng thời gian thực, metadata và covariate thực sự có. **State ứng viên:** gánh nặng, phân bố không gian, xu hướng cá thể, bất định. **Action:** chỉ thêm điều trị khi có dữ liệu phù hợp; không từ đó mặc định có mô hình hiệu ứng nhân quả.

**Thời gian:** khoảng cách thực giữa các lần khám; không coi mọi visit kế tiếp có cùng độ dài. Kiểm tra mất theo dõi, số visit hợp lệ, lịch can thiệp và thay đổi protocol ở mức dữ liệu cho phép.

**Input → output:** các lần khám quá khứ và horizon → burden/hình dạng/phân bố tổn thương tương lai. **Mục tiêu:** theo dõi, tiên lượng có bất định dưới bối cảnh chăm sóc quan sát được; chưa chọn phác đồ.

**Dữ liệu/nhãn cần:** chuỗi đủ dài, thời gian sử dụng được, định danh bệnh nhân, đánh giá nhãn và metadata chăm sóc. **Nguồn ứng viên:** LUMIERE; phải audit nguồn gốc segmentation, nhãn chuyên gia, điều kiện truy cập và số chuỗi dùng được. Đánh giá hai visit đầu → hai visit sau cần ít nhất bốn visit hợp lệ ở mỗi bệnh nhân thuộc protocol đó; tổng số scan không chứng minh đủ người bệnh đáp ứng.

**Baseline:** giữ nguyên tổn thương; xu hướng tuyến tính theo thời gian thực; tăng trưởng đơn giản phù hợp endpoint; predictor trực tiếp từ visit cuối. So state hiện tại, state cộng xu hướng và state học từ history.

**Đánh giá:** sai số burden và thay đổi burden, phần không gian thực sự thay đổi, endpoint tiến triển khi có nhãn phù hợp, hiệu chuẩn theo horizon. Không để nền không đổi chi phối metric ảnh. Rollout nhiều visit không được nhận lại ảnh tương lai thật.

**Công trình đã đối chiếu trong survey:** [ImageFlowNet](PAPER_MATRIX.md#m05), [Δ-LFM](PAPER_MATRIX.md#m07), [TaDiff](PAPER_MATRIX.md#m06), [Petersen](PAPER_MATRIX.md#m17), [Lachinov](PAPER_MATRIX.md#m18), [BrLP](PAPER_MATRIX.md#m08), [Bayesian digital twins](PAPER_MATRIX.md#m20). Memory, continuous time và multi-hypothesis không mới tự thân; cần thu hẹp vào endpoint/data/protocol được kiểm tra.

**Gap ứng viên:** history không gian có ích hơn burden hiện tại cộng xu hướng tăng/giảm đơn giản không? **Rủi ro:** ít chuỗi hợp lệ; nhãn tự động không tin cậy; thay đổi hậu điều trị hoặc quy trình bị hiểu sai; confounding; overlap với công trình trước.

**Thí nghiệm bác bỏ nhỏ:** bắt đầu bằng burden/shape thay vì sinh toàn ảnh; audit nhãn trên tập nhỏ và so ba mức thông tin. Dừng hoặc đổi hướng nếu nhãn không phân biệt được tín hiệu thay đổi, thiếu chuỗi đánh giá hoặc history không có lợi ích bổ sung đáng tin cậy.

## Lịch sử: hai thiết lập trợ lý đề xuất ngày 2026-09-07

| Thiết lập | Điều kiện để đi tiếp | Điều chưa được chốt |
| --- | --- | --- |
| A1: chuyển động mục tiêu cine-MRI | Chuỗi liên tục, cadence và nhãn mục tiêu đáng tin, tách được bệnh nhân; baseline có headroom ở horizon hữu ích | Cơ quan, dataset cuối, state cuối, kiến trúc, ứng dụng triển khai |
| C1: tổn thương longitudinal không nhân quả | Đủ chuỗi nhiều visit, thời gian và nhãn audit được; history có tín hiệu hơn current burden/trend | Bệnh cuối, cohort cuối, endpoint cuối, treatment model, kiến trúc |

Đây là ưu tiên khảo sát do trợ lý đề xuất, **không phải quyết định chọn đề tài của chủ dự án**. B vẫn có thể được ưu tiên lại khi điều kiện dữ liệu và mục tiêu sử dụng rõ hơn.

Đợt 2026-09-12 mở rộng thành Q1–Q8 ở [OPEN_QUESTIONS](OPEN_QUESTIONS.md), gồm cả B và các bệnh/cơ quan khác. Bảng cũ được giữ để bảo toàn lịch sử; không mặc định A1/C1 đã được chọn hoặc có ưu thế dữ liệu đã xác nhận.

## Ràng buộc bổ sung sau audit methods đợt 2

Đây là **INTERPRETATION / HYPOTHESIS**, chưa là lựa chọn đề tài. Nguồn kiểm tra: [A](surveys/deep_dives/FAMILY_A_FORECASTING_AUDIT.md), [B](surveys/deep_dives/FAMILY_B_ACQUISITION_AUDIT.md), [C](surveys/deep_dives/FAMILY_C_LONGITUDINAL_AUDIT.md), [state/evaluation](surveys/deep_dives/STATE_AND_EVALUATION_AUDIT.md).

- **A:** same-prefix PCA/linear/Kalman/GP, direct-target và recursive prediction phải được phân biệt; online adaptation chỉ nhận prefix. Giữ uncertainty gating là câu hỏi calibration/risk ranking, không claim component mới.
- **B:** measured query pose là biến điều kiện được khai báo; không lén đưa future poses vào state. Memory phải được so khi coverage/pose/protocol tương đương. Stored frame count không xác định Δt sau loại invalid records. GenNBV là prior về policy/coverage evaluation, không tự cung cấp learned dynamics cho medical.
- **C:** LUMIERE đã có aggregate depth count nhưng chưa usable label/interval intersection; CFB-GBM ba mốc không đáp ứng Q5 bốn visits. TaDiff external evidence chỉ MRI-generation metrics; không dùng làm validation của future tumor masks. Các kịch bản điều trị từ model vẫn bị giới hạn bởi observed-care/data assumptions.
- **Cả ba:** chọn điểm đánh giá sau cutoff rõ ràng; kiểm tra value của history/state bằng strong simple baselines; proper score/coverage/sharpness phải phù hợp endpoint và forecast mode. Không suy clinical benefit từ image similarity.
