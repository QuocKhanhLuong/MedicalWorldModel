# Knowledge base — khung khái niệm và bằng chứng nghiên cứu

Cập nhật: **2026-09-12**.

**Trạng thái:** các mục 1–8 là khung vận hành từ thảo luận, không phải tuyên bố đồng thuận duy nhất của lĩnh vực. Ví dụ là minh họa, không phải kết quả thực nghiệm. Mục 9 bổ sung nguồn và diễn giải từ survey 2026-09-12; metadata/mức đọc ở [REFERENCES.md](REFERENCES.md).

## 1. State của cái gì?

Đặt tên hệ thống và câu hỏi tương lai trước khi đặt tên latent.

| Hệ đang mô hình hóa | Input → state → transition → output |
| --- | --- |
| Chuyển động theo hô hấp | Lịch sử cine và mục tiêu đã xác định → hình dạng/vị trí, hướng chuyển động, bất định → diễn tiến theo thời gian → contour/tâm mục tiêu tương lai |
| Co bóp tim | Các frame quá khứ → hình dạng buồng tim, hướng co/giãn, tốc độ biến đổi → tiến triển động học → hình dạng/thể tích tương lai |
| Thu nhận ảnh | Các ảnh đã thấy và pose đã đo → giải phẫu đã biết, pose tương đối, vùng chưa biết → thay đổi pose/thao tác → quan sát dự kiến |
| Diễn biến tổn thương | Các lần khám quá khứ và khoảng thời gian thực → gánh nặng, phân bố không gian, xu hướng, bất định → diễn biến trong bối cảnh chăm sóc → tổn thương hoặc endpoint tương lai |

Chuyển động của tổn thương trong một đoạn cine không phải cùng bài toán với tăng trưởng bệnh qua nhiều lần khám. Dự án không cần mô hình hóa toàn bộ bệnh nhân; cần giới hạn hệ và những câu hỏi state phải trả lời.

## 2. Observation, state và latent

**Observation** là phép đo nhận được: ảnh, contour, pose, xét nghiệm, timestamp hoặc metadata. **State** là mô tả hiện tại của hệ đủ hữu ích cho phần tương lai đang quan tâm.

Biến state có thể đo/ước lượng trực tiếp, như vị trí hoặc thể tích; có thể ẩn, như vận tốc biến dạng không được đo; hoặc được biểu diễn bằng latent học từ lịch sử. Một latent dự đoán tốt không tự chứng minh nó tương ứng với trạng thái sinh học, một dấu ấn bệnh hoặc một hệ tọa độ có ý nghĩa lâm sàng.

Khi nhiều trạng thái tương thích với cùng một quan sát, nên nghĩ tới **niềm tin có bất định về state**, không mặc định quan sát xác định duy nhất trạng thái thật.

## 3. Vì sao cần lịch sử?

Ví dụ minh họa: cùng thể tích hiện tại nhưng trước đó tăng lên hoặc giảm xuống có thể dẫn đến hai dự báo khác nhau. Cùng hình dạng tức thời nhưng đang co hoặc giãn cũng tạo mơ hồ về tương lai.

Đó là lý do đặt giả thuyết cần history, không phải bằng chứng rằng mọi history đều có ích. So sánh current-only với history-aware prediction bằng cùng thông tin không gian, thời gian và chia tập. Nếu history không giúp, cần xem lại endpoint, dữ liệu hoặc nhu cầu mô hình động học.

## 4. Tự diễn tiến, hành động và thời gian

Không-action nghĩa là mô hình không nhận hành động điều khiển tường minh; không có nghĩa hệ hoàn toàn không chịu tác động bên ngoài. Trong cohort được chăm sóc, bỏ treatment khỏi input không biến dữ liệu thành bệnh sử tự nhiên không điều trị.

Khoảng thời gian `Δt` là điều kiện dự báo; nó không tự động là action. Chuyển vị đầu dò đã đo cũng khác lệnh điều khiển được gửi tới thiết bị. Dữ liệu của điều đã xảy ra không tự xác nhận đáp ứng dưới mọi lệnh có thể chọn.

## 5. Định nghĩa vận hành các loại mô hình

| Loại | Cam kết để phân loại trong dự án |
| --- | --- |
| Next-frame predictor | Dự đoán observation kế tiếp; chưa tự chứng minh state tái sử dụng hoặc rollout nhiều bước |
| Mô hình chuỗi thời gian | Mô hình hóa phụ thuộc theo thời gian; có thể hoặc không có state phù hợp với hệ đã định nghĩa |
| World model | Có state cập nhật từ quan sát, mô hình chuyển state theo thời gian/action nếu có, dự báo nhiều bước và kiểm chứng state cho mục tiêu đã đặt |
| Policy | Chọn hành động theo mục tiêu; không đồng nhất với mô hình dự đoán hậu quả |

Không bắt buộc world model sinh ảnh, có robot, có action hoặc dùng một họ kiến trúc nhất định. Một mô hình trạng thái–không gian đơn giản có thể đáp ứng quy ước này. Các nhóm khái niệm có thể giao nhau; tên gọi không thay thế thiết kế kiểm chứng.

## 6. Ký hiệu tối thiểu

Gọi `h_t` là lịch sử được phép biết ở thời điểm dự báo. Niềm tin về state là `b_t(s) = p(s_t = s | h_t)`. Biểu diễn học được có thể viết `z_t = E(h_t)`; không mặc định `z_t` bằng trạng thái sinh học thật.

Mô hình quan sát: `o_t ~ p(o_t | s_t, m_t)`, với `m_t` là metadata thu nhận.

Mô hình chuyển tiếp: `s_(t+Δ) ~ p(s_(t+Δ) | s_t, Δ, a_[t,t+Δ))`. Bỏ biến action nếu thiết lập không dùng action. Không đưa thông tin thực tế chỉ có trong tương lai vào điều kiện dự báo mà không nêu rõ đó là kịch bản được cung cấp trước.

Đầu ra có thể là ảnh, contour, vị trí hoặc chỉ số: `y_(t+Δ) ~ p(y | s_(t+Δ))`.

Câu hỏi kiểm tra state: sau khi có `z_t`, phần history bị bỏ đi còn giúp dự báo endpoint không? Đây là kiểm tra thực nghiệm có giới hạn, không phải chứng minh state đầy đủ cho mọi truy vấn.

## 7. Ba mức tuyên bố phải tách

**Dự đoán:** dự báo những diễn biến phù hợp với phân phối dữ liệu được đánh giá.

**Can thiệp:** dự báo hậu quả của việc chủ động thay đổi hành động. Không mặc định `p(Y | H, A=a) = p(Y | H, do(A=a))`. Treatment-conditioned prediction trên dữ liệu quan sát chưa tự xác lập hiệu ứng nhân quả.

**Hỗ trợ quyết định:** chứng minh dự báo làm lựa chọn tốt hơn theo utility, chi phí, rủi ro và bất định đã định nghĩa. Giảm sai số ảnh không tự chứng minh mức này. Policy được đánh giá chỉ trong chính world model của nó chưa đủ xác nhận giá trị ngoài hệ mô phỏng đó.

## 8. Hợp đồng đánh giá đề xuất

| Kiểm tra | Yêu cầu |
| --- | --- |
| Forecasting thực sự | Chỉ dùng prefix ở thời điểm suy luận; tách reconstruction/interpolation với dự báo |
| Nhiều bước | Báo cáo sai số theo horizon; tách rollout không nhận quan sát tương lai với tracking có cập nhật |
| Giá trị history | So với current-only và state đơn giản; dùng ablation phù hợp |
| Giá trị state | Kiểm tra nhiều endpoint độc lập; so với biến tường minh; không chỉ latent prediction error hoặc hình chiếu latent |
| Bất định | Đo hiệu chuẩn, độ bao phủ và độ rộng đồng thời |
| Tránh leakage | Chia theo bệnh nhân/người được quét; kiểm tra chuẩn hóa, registration, atlas và tạo map không dùng tương lai trái với thiết lập |
| Khái quát hóa | Đánh giá người/bệnh nhân chưa thấy; cơ sở/thiết bị mới nếu dữ liệu cho phép |
| Giá trị sử dụng | Metric gắn với hình học, chức năng hoặc endpoint đã định trước, không chỉ độ đẹp ảnh sinh |

Chưa có thực nghiệm nào xác nhận các giả thuyết của dự án. Quy trình này dùng để quyết định mô hình có cần thiết hay không trước khi tăng độ phức tạp.

## 9. Cập nhật sau đối chiếu nguồn 2026-09-12

**VERIFIED:** medical prior art đã có continuous-time future segmentation, stochastic trajectories, patient-history adaptation, explicit motion state và một số robot policy evaluations. Ví dụ: [Petersen 2021](PAPER_MATRIX.md#m17), [Lachinov TMI 2024](PAPER_MATRIX.md#m18), [ImageFlowNet](PAPER_MATRIX.md#m05), [PCA respiratory forecasting](PAPER_MATRIX.md#m09), [Cosmos-Surg-dVRK](PAPER_MATRIX.md#m16). Không còn cơ sở cho gap rộng “y học chưa có state/uncertainty/planning”.

**INTERPRETATION / HYPOTHESIS:** định nghĩa dùng cho đợt nghiên cứu này là: **Medical Visual World Model mô hình hóa một hệ y khoa xác định, suy state/belief từ thông tin thị giác và lịch sử khả dụng, dùng transition theo thời gian/input để dự báo đại lượng tương lai có mục đích, và kiểm tra nhiều horizon cùng giá trị của state/transition cho mục đích đó.** Đây là quy ước đề xuất, không chọn clinical state hoặc kiến trúc cụ thể.

**VERIFIED:** [Pohl §2.3.3](https://arxiv.org/abs/2410.05882v3) dùng separate direct predictor theo horizon; [cardiac ODE](https://arxiv.org/html/2606.26718) encode whole cycle; [EchoWorld](https://arxiv.org/html/2504.13065) dùng observed history cho guidance. **INTERPRETATION:** phải tách direct multi-horizon, recursive rollout, filtering với ảnh mới và full-sequence reconstruction; không dùng chung nhãn “long rollout”.

**VERIFIED:** [Fan et al. §II-D/IV](https://arxiv.org/html/2607.21918v2) có low-level force control nhưng WM input là image/pose. **INTERPRETATION:** pose-conditioned observation prediction, commanded-action transition và contact-induced deformation là ba claim khác nhau.

**VERIFIED:** [BrLP §5.6](https://arxiv.org/html/2502.08560) đã đo uncertainty–error association; [Petersen](https://arxiv.org/html/2106.12917) có oracle future-volume-conditioned selection metric. **INTERPRETATION:** distribution diversity, correlation với error, calibration và deployable selection utility phải chấm riêng.

Hợp đồng dữ liệu, các rủi ro prefix preprocessing và map năng lực CV → cơ hội y khoa ở [medical survey](surveys/MEDICAL_WORLD_MODELS_SURVEY.md), [transfer gaps](surveys/TRANSFER_GAPS.md). Chưa có gap nào được xác nhận novel hoặc trở thành quyết định của chủ dự án.

## 10. Nghiên cứu sâu đợt 2 — state sufficiency và uncertainty của trajectory

**VERIFIED:** [Predictive Representations of State, NeurIPS 2001](https://proceedings.neurips.cc/paper/2001/hash/1e4d36177d71bbb3558e43af9577d70e-Abstract.html) đã định nghĩa state thông qua future tests và sufficiency; đây không phải ý tưởng mới của video foundation models. [WorldArena §3.4](https://arxiv.org/html/2602.08971v2) gộp video metrics thành EWMScore và chấm functional utility riêng. [Conformal surgical forecasting, MICCAI 2025](https://papers.miccai.org/miccai-2025/0168-Paper0260.html) đã chấm calibrated joint endpoint uncertainty; [CAFHT, ICML 2024](https://proceedings.mlr.press/v235/zhou24l.html) đã có simultaneous trajectory bands với giả định exchangeability ở cấp trajectory.

**INTERPRETATION / HYPOTHESIS:** đánh giá state cần chỉ rõ đủ cho target/query nào; history-residual test có thể bác bỏ sufficiency trong phạm vi test, không chứng minh clinical-state identification. Tách uncertainty theo horizon, uncertainty của cả đường đi và uncertainty của event/decision. Phải ghi budget quan sát: nhận truth từng bước khác forecast toàn bộ từ prefix cố định. Bản [kiểm toán state/evaluation](surveys/deep_dives/STATE_AND_EVALUATION_AUDIT.md) đưa ra các phép bác bỏ, matched-information comparisons và giới hạn của metric proxies; tất cả là protocol đề xuất, chưa thực nghiệm.

## 11. Đợt 2: temporal contract và bằng chứng dữ liệu cụ thể

**VERIFIED.** [Audit A](surveys/deep_dives/FAMILY_A_FORECASTING_AUDIT.md) có prior art về manifold/PCA state, probabilistic deformation, online state-space learning và Gaussian-process gating; [audit B](surveys/deep_dives/FAMILY_B_ACQUISITION_AUDIT.md) có trackerless sequence memory, nonrigid reconstruction và protocol confounding; [audit C](surveys/deep_dives/FAMILY_C_LONGITUDINAL_AUDIT.md) kiểm tra exact context/target, preprocessing, uncertainty và external evaluation. Không coi component tồn tại là bằng chứng đã giải mọi question, cũng không gọi component đó mới trong medical.

**VERIFIED / derived audit.** Metadata LUMIERE được đếm từ ZIP directory, không đọc ảnh: 62 patients có ≥4 nominal weeks với đủ bốn sequence; [artifact](research_artifacts/2026-09-12_metadata_audit.json) ghi source version, hashes, counting rule và root recount. Số usable 2-past/2-future với label/horizon cụ thể vẫn UNKNOWN. Figshare CC0 và README non-commercial là conflict cần giải quyết khi dùng data, không tự phân xử license trong survey.

**INTERPRETATION / HYPOTHESIS.** Phân biệt (i) fixed-prefix dự báo trực tiếp nhiều target times; (ii) transition recursive không nhận quan sát mới; (iii) prediction sau mỗi assimilation; (iv) reconstruction dùng toàn chuỗi. Cả (i) và (ii) có thể là phép kiểm tra world model; (ii) không bắt buộc. Chấm joint trajectory khi claim temporal coherence; patient-disjoint calibration khi claim uncertainty; independent geometry/clinical readout khi claim state vượt representation phục vụ một head.

**Giới hạn thực tế:** mới có source/method/metadata audit; chưa baseline replication, pixel/label reliability audit, training hoặc clinical validation. Không chọn A/B/C.
