# Transfer gaps — kiểm tra prior art để bác bỏ novelty

Đối chiếu **2026-09-12**. Mục tiêu là tìm câu hỏi có thể bảo vệ, không chứng minh một khoảng trống bằng việc “chưa thấy paper”. **Tất cả gap còn lại là INTERPRETATION / HYPOTHESIS**, chưa được tuyên bố novel. Nguồn trong cột VERIFIED là phản chứng trực tiếp hoặc prior art gần; chúng không khẳng định kết quả của repo.

## VERIFIED — nhiều năng lực đã chuyển sang y khoa

| Năng lực từ CV | Prior art y khoa được xác minh | Claim rộng bị bác bỏ / làm yếu | INTERPRETATION / HYPOTHESIS: câu hỏi hẹp còn đáng kiểm tra |
| --- | --- | --- | --- |
| Explicit predictive state | [PCA respiratory dynamics](https://arxiv.org/abs/2410.05882), [Lachinov spatial NeuralODE](https://arxiv.org/html/2211.04234) | “Y học chưa có explicit/anatomical predictive state” sai | State có tăng giá trị dự báo ngoài last geometry + velocity/history ở cùng horizon? |
| Long-horizon dynamics | [Petersen continuous glioma growth](https://arxiv.org/html/2106.12917), [Pash digital twin](https://arxiv.org/html/2505.08927) | “Medical models chỉ next frame” quá rộng | Tách direct queries, recursive rollout và assimilation; đánh giá nhiều **future observations** từ cùng prefix |
| Uncertainty-aware transition | [EKF+GP respiratory gating](https://pubmed.ncbi.nlm.nih.gov/25489980/), [neural SDE clinical trajectories](https://arxiv.org/html/2406.12807), [Pash](https://arxiv.org/html/2505.08927) | “Đưa uncertainty vào medical dynamics lần đầu” bị bác bỏ | Calibration theo horizon/shift và endpoint risk, so baseline probabilistic mạnh |
| Multiple futures | [Petersen](https://arxiv.org/html/2106.12917), [ImageFlowNet SDE](https://arxiv.org/html/2406.14794), [BrLP](https://arxiv.org/html/2502.08560) | “Medical imaging chỉ có một tương lai” sai | Distribution quality và patient-conditional coverage có đúng, hay chỉ diverse appearance? |
| Object/anatomy-centric dynamics | [Lachinov](https://arxiv.org/html/2211.04234), [CardioSynth](https://papers.miccai.org/miccai-2025/0004-Paper2701.html), [Pash](https://arxiv.org/html/2505.08927) | “Anatomy-centric là novelty tự thân” bị bác bỏ | Identity/burden/deformation được kiểm tra độc lập với segmentation và future registration? |
| Geometry-aware acquisition | [Hu spatial US synthesis](https://arxiv.org/abs/1707.05392), [EchoWorld](https://arxiv.org/html/2504.13065), [X-WIN](https://openaccess.thecvf.com/content/CVPR2026/html/Yang_X-WIN_Building_Chest_Radiograph_World_Model_via_Predictive_Sensing_CVPR_2026_paper.html) | “Pose/view-conditioned medical prediction mới” bị bác bỏ | Partial anatomy state dự báo vùng có/không có support thế nào, vượt nearest view/prefix volume ra sao? |
| Memory dưới partial observation | [EchoWorld history guidance](https://arxiv.org/html/2504.13065), [ImageFlowNet history adaptation](https://arxiv.org/html/2406.14794), [Δ-LFM](https://arxiv.org/html/2512.09185) | “Thêm memory/patient history là gap” bị làm yếu mạnh | Incremental predictive value của history sau khi khống chế current state, elapsed time và coverage |
| Active acquisition / imagined planning | [Cardiac Copilot](https://papers.miccai.org/miccai-2024/118-Paper0053.html), [Fan robot US](https://arxiv.org/html/2607.21918v2) | “Chưa có medical WM probe guidance/closed loop” sai | Public-data reproducibility, feasible command support và model-error-aware ranking trong hệ đã định |
| Counterfactual actions | [MeWM protocol search](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html), [RCT neural SDE](https://arxiv.org/html/2406.12807), [RMSN](https://papers.nips.cc/paper_files/paper/2018/hash/56e6a93212e4482d99c84a639d254b67-Abstract.html) | Không thể claim chưa ai mô phỏng treatment; nhưng strength of identification khác nhau | Phải chọn estimand và data assumptions trước; dự án hiện chưa có căn cứ để đặt causal treatment question |
| Continuous time | [Petersen 2021](https://arxiv.org/html/2106.12917), [Lachinov](https://arxiv.org/html/2211.04234), [ImageFlowNet](https://arxiv.org/html/2406.14794) | “ODE/irregular-time medical forecasting đầu tiên” sai | Generalization theo actual Δt và missingness có hơn direct time-conditioned predictor/mixed effects? |
| Cross-patient / individualized state | [BrLP](https://arxiv.org/html/2502.08560), [Δ-LFM](https://arxiv.org/html/2512.09185), [Stowers breast response](https://pubs.rsna.org/doi/pdf/10.1148/ryai.240124) | “Patient-specific dynamics mới” sai | Mức history tối thiểu và lợi ích adaptation có vượt individual trend, với prefix-only fitting? |
| Representation reuse | [EchoWorld guidance](https://arxiv.org/html/2504.13065), [X-WIN tasks](https://openaccess.thecvf.com/content/CVPR2026/html/Yang_X-WIN_Building_Chest_Radiograph_World_Model_via_Predictive_Sensing_CVPR_2026_paper.html), [MedDream](https://arxiv.org/abs/2609.07719) | “World-model representation chưa dùng downstream trong y khoa” sai | Một state forecasting có dùng được cho nhiều endpoint mà không dựa future labels/retraining toàn bộ? |
| Simulator evaluation ngoài perceptual quality | [Cosmos-Surg-dVRK](https://arxiv.org/html/2510.16240v2), [Fan](https://arxiv.org/html/2607.21918v2), [Li respiratory gating](https://doi.org/10.1186/s13014-023-02341-1) | “Y học chỉ đo SSIM” sai | Joint state accuracy, uncertainty và ranking/outcome dưới shift còn cần đánh giá theo từng hệ |
| Hierarchical temporal abstraction | [Cardiac phase-aware dynamics](https://arxiv.org/html/2606.26718), [Δ-LFM patient trajectory](https://arxiv.org/html/2512.09185) là adjacent, không chứng minh cùng một hierarchy | Không đủ bằng chứng để khẳng định y khoa chưa có hierarchy | Chưa thấy bằng chứng đủ mạnh trong tập đã đọc để xác lập gap; cần truy tìm riêng trước khi biến thành proposal |
| State sufficiency tests | Memory/predictive-state papers trên là prior art gần; không xác minh một theorem hay benchmark thống nhất cho medical state sufficiency | Không được dùng “không tìm thấy exact phrase” để claim đầu tiên | Kiểm tra operational sufficiency có thể làm contribution đánh giá; chưa phải chứng minh Markov/sufficient statistic sinh học |

## INTERPRETATION / HYPOTHESIS — phần chuyển giao có giá trị nhất

Phần có thể học từ CV là **cách buộc state/transition chịu kiểm tra**, không phải một backbone. Các comparator rõ gồm policy return ở Dreamer; goal-reaching ở DINO-WM/V-JEPA 2; trajectory errors ở NWM; simulator-versus-real policy ranking ở DreamDojo. Y khoa đã có một phần tương đương, nên cơ hội hẹp nằm ở tính công bằng của information contract, multiple future labels, state-level uncertainty và utility trong **một hệ/dataset cụ thể**. [General landscape](VISUAL_WORLD_MODELS_LANDSCAPE.md).

Không có bằng chứng trong review này để phát biểu “medical world models generally chưa làm X” với một tỉ lệ định lượng. Tập paper được chọn để kiểm tra các capability, không phải random sample toàn lĩnh vực. Nếu muốn claim prevalence, cần protocol systematic review và denominator độc lập.

### Kiểm tra state sufficiency có thể thực hiện

Đây là đề xuất thực nghiệm, không phải kết quả hay theorem:

1. Với s(t) cố định, xem thêm history H(t−k:t) có cải thiện future quantity đáng kể không; cùng decoder capacity, tuning và data.
2. Giữ current image/pose/shape gần nhau, phân nhóm history/velocity khác nhau. Nếu state nhập hai trường hợp có tương lai khác thành một, nó chưa đủ cho task/horizon đó.
3. So state learned với state đơn giản có đo đạc được; kiểm tra residual chứa thông tin về future ngoài simple state hay chỉ reconstruct appearance.
4. Thử đổi downstream readout mà giữ inference/transition cố định; kiểm tra ích lợi riêng của prediction state so representation từ reconstruction/classification.
5. Report theo horizon và population; “đủ” chỉ là operational sufficiency cho đại lượng đã thử. Không suy ra state đầy đủ của sinh học, Markov property phổ quát hay causal representation.

### Yêu cầu tối thiểu để một gap qua vòng phản biện

| Nội dung | Tiêu chí đề xuất |
| --- | --- |
| Ranh giới | Hệ, observable, latent semantics, influence/action và time scale rõ |
| Baseline | Persistence/linear/periodic/PCA/Kalman hoặc mixed effects phù hợp; cùng prefix và preprocessing |
| Forecast protocol | Future frame/covariate không đi vào encoder, registration, normalization, ROI, model selection |
| Multi-step | Cùng prefix, ≥2 horizons có ground truth; direct vs recursive báo riêng |
| Probability | Chấm coverage/sharpness hoặc proper score phù hợp, không dùng best-of-N như metric chính |
| Task utility | Endpoint state/geometry/change hoặc decision proxy thực sự dùng future quantity; không suy clinical benefit từ proxy |
| Causal | Nếu chỉ observational, wording “under observed care”; muốn intervention phải có identification plan |
| Falsification | Một kết quả âm cụ thể khiến bỏ giả thuyết hoặc hạ claim, không đổi metric sau khi thua |

## Nhật ký adversarial search — VERIFIED về công việc đã làm

Các query dưới đây là các lượt truy tìm đã thực hiện, kết quả được đọc ở nguồn gốc. Đây là các ví dụ có ý nghĩa, không phải export exhaustive của mọi search result. Không báo PRISMA counts không được lưu.

| Giả thuyết bị tấn công | Formulations đã dùng | Phản chứng và kết quả |
| --- | --- | --- |
| Memory/continuous medical state là mới | “latent dynamics medical imaging”; “longitudinal imaging prediction”; “patient-specific disease dynamics”; “Petersen continuous glioma growth” | Petersen → Lachinov → ImageFlowNet; BrLP/Δ-LFM. Hủy claim rộng |
| Uncertainty medical forecast chưa được đánh giá | “longitudinal imaging calibrated uncertainty”; “respiratory motion prediction conformal uncertainty gating”; “probabilistic framework respiratory prediction” | EKF+GP gating, BrLP error association, Bayesian digital twin. Đổi sang calibration/decision test cụ thể |
| Pose-conditioned US/world-model guidance mới | “ultrasound world model”; “robotic ultrasound world model”; “pose conditioned prediction memory uncertainty tracked freehand” | Hu 2017, Cardiac Copilot, EchoWorld, Fan 2026. Hủy claim “first” |
| Medical WM chỉ images đẹp | “medical video world model”; “surgical world model policy evaluation”; tìm backward references từ DreamDojo | Cosmos-Surg-dVRK và medical navigation; không chấp nhận blanket critique |
| Biological patient-specific treatment response mới | “anatomical dynamics model”; “physiological dynamics”; “disease trajectory imaging”; “Combining Biology-based and MRI Data-driven Modeling” | Pash digital twin và Stowers tumor-response forecasting. Giữ chỉ scope hẹp về measured state/forecast evaluation |
| State sufficiency/hierarchy là khoảng trống chắc chắn | “medical imaging forecasting state sufficiency history latent”; các formulation memory/partial observation/temporal abstraction | Tìm được adjacent methods, chưa đủ xác lập absence. Gắn UNKNOWN novelty và không đặt làm claim chính |

### Backward / forward tracing có giới hạn

- EchoWorld → Cardiac Copilot: đọc nguồn MICCAI 2024, sửa lịch sử “medical WM bắt đầu 2025”.
- ImageFlowNet/Lachinov related work → continuous-time glioma forecasting: đọc bản 2021.
- DreamDojo → Cosmos-Surg-dVRK: kiểm tra medical robotics policy-evaluation prior art.
- BrLP → exact-title/citing-paper search → technical assessment SPIE: đọc phản chứng về image metrics.
- TUS-REC references → spatial US synthesis và trackerless reconstruction: giữ reconstruction khác forecasting.

Đây là manual chaining, không claim đã duyệt toàn bộ citing graph hay mọi paper 2026. Preprint mới, access errors và các trường UNKNOWN còn được ghi trong [research log](RESEARCH_LOG.md).

## Kết luận nghiên cứu — INTERPRETATION / HYPOTHESIS

Không gap nào được “accepted as novel” trong đợt này. Tám câu hỏi ở [OPEN_QUESTIONS](../OPEN_QUESTIONS.md) là **candidate questions with falsifiers**, không phải tám novelty claims. Ưu tiên tiếp theo là tìm một dataset/endpoint làm phép thử rõ ràng, rồi thử xem baseline đã giải quyết bài toán chưa. Một kết quả cho thấy state learned không thêm lợi ích là lý do hợp lệ để bỏ hướng, không phải lý do tăng độ phức tạp mô hình.
