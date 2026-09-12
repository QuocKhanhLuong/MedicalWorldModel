# Medical World Models — bằng chứng và ba họ ứng viên

Đối chiếu **2026-09-12**. **A/B/C đều chưa được chọn.** Những kết luận khoa học tổng hợp dưới đây không phải quyết định của chủ dự án. [Matrix](../PAPER_MATRIX.md) chứa metadata và mức đọc; [dataset feasibility](../DATASET_FEASIBILITY.md) chứa nguồn dữ liệu, không suy khả năng truy cập từ paper.

## Định nghĩa vận hành đề xuất — INTERPRETATION / HYPOTHESIS

**Medical Visual World Model là mô hình của một hệ y khoa xác định, suy ra state hoặc belief từ thông tin thị giác và lịch sử khả dụng, dùng transition theo thời gian và/hoặc input ngoại sinh để dự báo các đại lượng tương lai có mục đích cụ thể, và được kiểm tra bằng dự báo nhiều horizon cùng giá trị của state/transition đối với mục đích đó.**

Đây là quy ước nghiên cứu, chưa phải lựa chọn bài toán. State có thể là hình học, tham số vật lý, biological hypothesis hoặc latent thuần dự đoán; không gán nghĩa lâm sàng chỉ vì một latent có khả năng phân loại. Không bắt buộc pixel, robot, policy hoặc action. Simulation, planning, intervention analysis và decision support là **claim bổ sung**, không mặc nhiên đi cùng forecasting.

Viết hợp đồng trước mỗi nghiên cứu: history khả dụng H(t) → state/belief s(t) → transition T(s, Δt, u nếu có) → future y(t+Δt) → endpoint U. Nếu latent chỉ là công cụ dự báo, gọi rõ là “predictive latent”. Kết quả về bất định của unsupervised disentanglement cảnh báo cần giả định/bằng chứng bổ sung; nó không chứng minh mọi state y khoa đều bất khả giải thích. [Locatello et al., ICML 2019](https://proceedings.mlr.press/v97/locatello19a.html).

## VERIFIED — ba loại văn liệu, không đồng nhất với ba họ bài toán

Ký hiệu **E**: paper tự framing world model; **T**: state-transition prediction dưới tên khác; **G/R**: generation, representation hoặc reconstruction có liên quan nhưng chưa đủ bằng chứng cho temporal forecasting. Một paper E vẫn có thể thuộc G/R theo hợp đồng của repo.

| Loại | Nguồn | Observation → state → transition → future/output → purpose | Bằng chứng và biên claim |
| --- | --- | --- | --- |
| E | [Cardiac Copilot, MICCAI 2024](https://papers.miccai.org/miccai-2024/118-Paper0053.html) | Echo + pose → visual predictive features → motion-conditioned imagination → guidance correction → probe guidance | Có trước MeWM 2025; author response mô tả một bước imagined correction, không phải chứng minh rollout dài. |
| E | [EchoWorld, CVPR 2025](https://arxiv.org/html/2504.13065) | Image pairs + relative pose → spatial features → latent prediction → target-view features → guidance | Đánh giá translation/rotation guidance error; history có quan sát thật, không đồng nhất closed-loop autonomous scanning. |
| E | [Fan et al., 2026 preprint](https://arxiv.org/html/2607.21918v2) | US history + measured pose → predictive latent → displacement/time-conditioned dynamics → future image/features → policy training và goal-plane scanning | Có robot experiments; force-control phần cứng không có nghĩa world model nhận force input. |
| E | [Medical World Model, ICCV 2025](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html) | Pretreatment CT/mask + protocol → latent → protocol-conditioned generation → post-treatment CT/risk score → protocol search | Retrospective agreement/risk scoring không xác lập hiệu quả điều trị counterfactual. |
| E | [MRI Contrast Enhancement Kinetics World Model, CVPR 2026](https://arxiv.org/html/2602.19285) | Noncontrast image + post-injection time → spatial latent kinetics → continuous-time generation → contrast images → synthesis | Intravisit kinetics, khác tiến triển bệnh qua visits. Dense output không đồng nghĩa dense measured future. |
| E; G/R dưới định nghĩa temporal | [X-WIN, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Yang_X-WIN_Building_Chest_Radiograph_World_Model_via_Predictive_Sensing_CVPR_2026_paper.html), [MedDream, 2026 preprint](https://arxiv.org/abs/2609.07719) | X-WIN: CT-derived views → geometry-related representation → view prediction → CXR tasks. MedDream: radiographs/text → shared representation → evidence/reasoning outputs | Bằng chứng đã đọc hỗ trợ representation/reasoning; không dùng để khẳng định longitudinal disease transition. |
| E | [Surgical Vision World Model, DEMI 2025](https://arxiv.org/abs/2503.02904), [SAW, 2026 preprint](https://arxiv.org/abs/2603.13024) | Surgical video → implicit dynamics → latent actions hoặc trajectory-conditioned generation → videos → interactive generation/augmentation | Latent action hay tool-tip trajectory không tự là robot command/force. SAW đánh giá thêm action-recognition augmentation. |
| E | [Cosmos-Surg-dVRK, 2025 preprint](https://arxiv.org/html/2510.16240v2), [thrombectomy WM, MICCAI 2025](https://papers.miccai.org/miccai-2025/1021-Paper3014.html) | Robot observations + actions → dynamics → imagined future → policy evaluation/navigation | Có prior art nối medical robotics với policy objective. Không suy ra thử nghiệm trên bệnh nhân từ task success. |
| T | [Continuous-Time Deep Glioma Growth Models, MICCAI 2021](https://arxiv.org/html/2106.12917), [Lachinov et al., TMI 2024](https://arxiv.org/html/2211.04234) | MRI/OCT + time, segmentation/history → trajectory/voxel latent → continuous query → future segmentation → growth prediction | Continuous time, spatial state và stochastic multi-futures đã có trước các paper gần đây tự gọi WM. |
| T | [ImageFlowNet, ICASSP 2025](https://arxiv.org/html/2406.14794), [TaDiff, TMI 2025](https://arxiv.org/html/2309.05406) | Longitudinal images (+ treatment ở TaDiff) → predictive representation → time-conditioned progression → future image/lesion → observed-care forecasting | ImageFlowNet có stochastic option và history adaptation; TaDiff có điều kiện điều trị, không đồng nghĩa identification causal. |
| T | [BrLP, MedIA 2025](https://arxiv.org/html/2502.08560), [Δ-LFM, ICLR 2026](https://arxiv.org/html/2512.09185) | Brain MRI/history/covariates → regional progression/patient trajectory → future-time image generation → anatomy/image measures → progression modeling | Patient-specific dynamics, anatomy conditioning, error-related uncertainty đã có prior art. |
| T | [Pohl et al., CMIG 2026](https://arxiv.org/abs/2410.05882), [Li et al., Radiation Oncology 2023](https://doi.org/10.1186/s13014-023-02341-1) | Cine motion history → PCA deformation hoặc respiratory coordinates → prediction → future deformation/position → latency compensation/gating | Cần vượt PCA/linear và patient-specific temporal baselines. |
| T | [Neural SDE disease trajectories, MICCAI 2024](https://papers.miccai.org/miccai-2024/619-Paper3431.html), [Pash et al., JCP 2026](https://doi.org/10.1016/j.jcp.2026.114937) | Baseline MRI + clinical/RCT variables → latent stochastic disease → EDSS; hoặc serial MRI → estimated cellularity/parameter posterior → PDE → tumor burden | State không phải pixel và uncertainty-aware dynamics không mới trong y khoa. |
| G/R | [Cardiac latent ODE, 2026 preprint](https://arxiv.org/html/2606.26718), [4D CardioSynth, MICCAI 2025](https://papers.miccai.org/miccai-2025/0004-Paper2701.html) | Whole-cycle meshes/shape → cycle representation → continuous phase dynamics/deformation → reconstructed/generated cardiac cycle → phenotype/virtual populations | Không chuyển full-cycle encoding hoặc population synthesis thành bằng chứng prefix-only future forecasting. |

## A — Physiological / anatomical dynamics

### VERIFIED — hệ đã được mô hình hóa

Pohl et al. biểu diễn respiratory deformation bằng optical flow và PCA; suy hệ số tương lai rồi warp ảnh. §2.2–2.3 của PDF fit basis từ đoạn training, và §2.3.3 dùng mô hình riêng cho từng horizon tới 2.2 s để tránh lỗi recursive; đây là direct multi-horizon prediction, không phải free-running rollout. Nghiên cứu gồm 12 sequences, không được đổi thành “12 bệnh nhân”. Li et al. cung cấp đối chứng khác với patient-specific linear prediction cho gating, so với RNN tại cửa sổ ngắn. [Pohl, methods/Table 2](https://arxiv.org/abs/2410.05882v3), [Li, original PDF](https://d-nb.info/1318665426/34).

Extended Kalman filter + Gaussian process regression đã dùng cả prediction và uncertainty-related gating từ paper issue 2015. Vì vậy “uncertainty-aware respiratory gating” không phải khoảng trống mới. [Bukhari & Hong](https://pubmed.ncbi.nlm.nih.gov/25489980/).

Cardiac latent ODE hiện đọc suy initial latent từ meshes của cả cycle; kết quả reconstruction và association với heart-failure risk không trả lời “chỉ thấy đầu cycle thì dự báo phần sau tốt đến đâu”. CardioSynth tạo các dynamic virtual heart populations; không nên xếp cùng giao thức forecasting nếu không kiểm tra lại input thời gian. [Cardiac ODE, §3.5/Appendix B](https://arxiv.org/html/2606.26718), [CardioSynth](https://papers.miccai.org/miccai-2025/0004-Paper2701.html).

### INTERPRETATION / HYPOTHESIS — hợp đồng ứng viên A

| Câu hỏi trung tâm | Định nghĩa cần kiểm tra |
| --- | --- |
| 1. Hệ | Chuyển động nhìn thấy của organ/target trong một acquisition liên tục, không mặc định toàn bộ cơ thể |
| 2–3. State | Geometry/contour + phase/velocity hoặc deformation coefficients; phần không thấy biểu diễn bằng belief. Các biến này là suy ra, không phải ground-truth physiology |
| 4. Thông tin | Chỉ cine prefix, cadence, calibration và nhãn có sẵn trước cutoff; static patient covariates nếu thực sự có |
| 5–6. Cái làm đổi state | Nhịp tim/hô hấp, drift, chuyển động; có thể dùng autonomous model với ngoại lực chưa quan sát. “Không có action” không nghĩa cơ thể không chịu tác động |
| 7. Thời gian | Phần giây–vài giây; phải gắn với cadence và latency task cụ thể |
| 8. Tương lai | Centroid, contour, deformation, regional volume và uncertainty; pixel chỉ phụ trợ nếu có ích |
| 9. Mục đích | Đo khả năng bù latency/ước lượng motion trong thí nghiệm retrospective |
| 10. Mức claim | Forecasting; chỉ gọi gating/planning utility nếu đánh giá mục tiêu đó. Chưa có bằng chứng clinical deployment cho dự án |

Một learned state đáng nghiên cứu khi cải thiện được một nhu cầu xác định: velocity ambiguity, nonperiodic drift, biến dạng vùng, hoặc khả năng mang history qua occlusion. Nó phải thắng **last state, constant velocity, periodic/Fourier, PCA+linear/AR, Kalman/GP và temporal predictor trực tiếp**, với cùng prefix và budget tuning. “State” không tạo ưu thế nếu task chỉ cần centroid tuyến tính. Cần so state có cấu trúc với history trực tiếp và kiểm tra bỏ phase/shape/history lần lượt.

**Dữ liệu:** TrackRAD là điểm xuất phát có nguồn public cho cine; cần xác minh continuity và nhãn ở các future horizon. EchoNet có video nhưng sparse cardiac tracings; ACDC/4D-LUNG không được mặc định là continuous multi-cycle trajectories. Xem [D01–D04](../DATASET_FEASIBILITY.md). Chưa có manifest hoặc dữ liệu ảnh nào được tải để chứng minh số trajectory phù hợp.

## B — Image acquisition dynamics

### VERIFIED — phân biệt pose, action và contact từ prior art

Pose-conditioned US synthesis đã có ở Hu et al. 2017 trên phantom. EchoWorld dùng measured relative poses và feature prediction cho probe guidance. Đây là prior art trực tiếp chống tuyên bố “đầu tiên predict ultrasound từ pose” hay “đầu tiên học acquisition state bằng future feature”. [Hu et al.](https://arxiv.org/abs/1707.05392), [EchoWorld, §3–5](https://arxiv.org/html/2504.13065).

Fan et al. 2026 mô tả robot dùng force/torque sensing và low-level force control, nhưng world-model input là US images/poses. §IV thừa nhận không mô phỏng đầy đủ pressure và physiological motion. Độ dài trajectory trong Table I không phải forecast horizon; Figure 4 kiểm tra temporal offsets. Kết quả robot goal scanning là bằng chứng mạnh hơn offline pose MAE trong đúng hệ tác giả, không chuyển thành bằng chứng access/data/closed-loop cho repo này. [Fan et al., §II-D, §III–IV](https://arxiv.org/html/2607.21918v2).

### INTERPRETATION / HYPOTHESIS — hợp đồng và bậc dữ liệu B

| Claim | Chuỗi đúng | Dữ liệu tối thiểu cần thêm | Claim không suy được |
| --- | --- | --- | --- |
| Pose-conditioned observation prediction | Past views/poses → partial anatomy/view state → query pose transform → expected image/features → view prediction | Calibrated synchronized image–pose pairs; hệ tọa độ, spatial support, acquisition settings | Query pose không chứng minh robot làm được chuyển động đó |
| Action-conditioned transition | Image/pose/history → belief → **command** + controller/contact dynamics → future pose/tissue/view → action prediction | Command logs, measured response, Δt, control mode, latency; force/contact nếu claim về deformation | Measured end displacement không tương đương commanded action |
| Probe guidance | History → goal-relevant state → candidate motion scores → recommended feasible motion → đạt view | Goal annotation, accessible motion constraints; đánh giá progression/success và failure | Offline expert-action agreement không phải closed-loop success |
| Closed-loop planning | Belief → feasible action rollouts → chọn action → thực hiện và cập nhật belief → goal/constraint outcome | Interactive environment hoặc robot, command semantics, objective và independent outcome evaluation | Chọn action trong một generator không tự kiểm chứng simulator |

State có thể là một partial 3D map, history features hoặc belief về view/coverage; không nhất thiết tái dựng toàn bộ cơ quan. Measured pose là **observed geometry**; giải phẫu ngoài view vẫn **inferred/unobserved**. Ngoại sinh gồm camera/probe/scanner settings, patient motion; contact có thể đổi mô mềm chứ không chỉ camera. Time scale thường intravisit; Q4 đề xuất horizon theo frame/giây cụ thể sau khi audit.

TUS-REC2024 có measured optical tracking, phù hợp đánh giá pose-conditioned prediction có giới hạn sau khi đổi giao thức; nó không cung cấp căn cứ để gọi command-conditioned tissue simulator. Tracked reconstruction dùng cả sweep cũng có thể nhìn thấy vùng “tương lai”; xây volume baseline phải chỉ dùng prefix. Không ép B hoặc cả dự án dùng ultrasound: X-WIN và MRI-CEK cho thấy acquisition-related modeling còn có geometry/view và contrast kinetics. Nguồn dữ liệu cụ thể: [D05](../DATASET_FEASIBILITY.md#d05), [M13](../PAPER_MATRIX.md#m13), [M12](../PAPER_MATRIX.md#m12).

## C — Longitudinal disease / lesion dynamics

### VERIFIED — bằng chứng vượt future-frame generation

Petersen et al. 2021 dùng nhiều context scans với stochastic continuous-time future segmentation. Lachinov et al. dự báo spatial disease state bằng NeuralODE, có bài toán atrophy/ventricular evolution. ImageFlowNet có multi-scale dynamics, stochastic futures và adaptation theo history; BrLP kết hợp regional progression và MRI synthesis, đánh giá quan hệ uncertainty–error; Δ-LFM mô hình patient-specific trajectory. Do đó memory, continuous time, anatomy-centric state và multi-hypothesis không phải khoảng trống còn nguyên. [Petersen](https://arxiv.org/html/2106.12917), [Lachinov](https://arxiv.org/html/2211.04234), [ImageFlowNet §5.5–5.6](https://arxiv.org/html/2406.14794), [BrLP §5.6](https://arxiv.org/html/2502.08560), [Δ-LFM](https://arxiv.org/html/2512.09185).

Pash et al. xây patient-specific Bayesian reaction–diffusion digital twins. Dự báo từ scan áp chót tới scan cuối giữ lại phải phân biệt với đường cong dài đi qua các thời điểm đã dùng calibration. Stowers et al. dùng pretreatment MRI suy tham số rồi giải mô hình tumor response; paper đánh giá future cellularity/volume và pCR. Đây là prior art chống “biological state, uncertainty, patient-specific simulation hoặc endpoint beyond SSIM đều mới”. [Pash §5](https://arxiv.org/html/2505.08927), [Stowers, methods/evaluation](https://pubs.rsna.org/doi/pdf/10.1148/ryai.240124).

TaDiff nghiên cứu observational treatment-conditioned MRI; neural SDE MICCAI 2024 dùng MRI/clinical variables và randomized-trial treatment cho EDSS trajectories. Nguồn thứ hai có thiết kế nhận diện khác nguồn thứ nhất; cũng không thể giả định dự án truy cập được các RCT đó. [TaDiff](https://arxiv.org/html/2309.05406), [Durso-Finley et al.](https://arxiv.org/html/2406.12807).

### INTERPRETATION / HYPOTHESIS — hợp đồng ứng viên C

| Câu hỏi trung tâm | Định nghĩa cần kiểm tra |
| --- | --- |
| 1. Hệ | Imaging phenotype của bệnh dưới quá trình chăm sóc quan sát được, có ranh giới bệnh/cơ quan/điều trị cụ thể |
| 2–3. State | Regional morphology, lesion burden, tốc độ thay đổi và uncertainty; có thể thêm predictive latent. Segmentation-derived burden không phải số tế bào sống |
| 4. Thông tin | Scans/clinical covariates/treatment đã có trước cutoff, ngày đo thực và history có thiếu |
| 5–6. Điều làm state đổi | Tiến triển, điều trị, biến thiên acquisition, biến đổi không quan sát. Autonomous prediction có thể hấp thụ care policy lịch sử, không phải untreated natural history |
| 7. Thời gian | Ngày/tháng/năm theo timestamp thực, không theo chỉ số visit |
| 8. Tương lai | Region/lesion state, change map, volume hoặc clinical trajectory đã định nghĩa |
| 9. Mục đích | Đo ability to anticipate burden/trajectory; decision-support utility là nghiên cứu tiếp nếu endpoint thích hợp |
| 10. Mức claim | Forecasting under observed care; không suy individual treatment effect từ conditional synthesis |

**Irregular intervals:** dùng Δt thực; dự báo 90 ngày chỉ đánh giá bằng ground truth trong cửa sổ đã định trước, hoặc đổi sang actual-visit horizon. Interpolation không tạo label. Phân tầng horizon phải giữ số bệnh nhân và missingness, không báo hàng nghìn slice là independent patients.

**Missing visits:** complete-case cohort có thể khác quần thể gốc; dropout và lịch tái khám có thể phụ thuộc tình trạng bệnh. Audit lý do thiếu nếu có; nếu UNKNOWN phải giới hạn estimand. Không tự bù visit thiếu rồi coi là ground truth.

**Treatment confounding:** một treatment token có thể encode indication, severity hoặc center. Để nghiên cứu causal cần định nghĩa intervention, treatment history/time, consistency, support/positivity, confounder strategy và assumptions có thể bảo vệ. Randomization hỗ trợ một số nhận diện ở trial tương ứng, không giải quyết mọi dropout, selection hoặc cross-trial transport. RMSN là prior art về time-varying treatment response; kết quả trên simulation có ground-truth causal khác dữ liệu bệnh nhân thông thường. [RMSN](https://papers.nips.cc/paper_files/paper/2018/hash/56e6a93212e4482d99c84a639d254b67-Abstract.html).

**Segmentation reliability:** cần phân biệt manual labels, automated labels và expert correction. Dự báo một pipeline segmentation có thể học bias của pipeline. TaDiff chỉ dùng external LUMIERE để đánh giá MRI generation khi automated masks không đủ cho đánh giá lesion đáng tin cậy; không diễn giải external image score thành external tumor-forecast validation. [TaDiff §IV](https://arxiv.org/html/2309.05406).

**Patient-specific state:** history adaptation phải chỉ dùng quá khứ; so population model, simple individualized trend và adaptation cùng lượng history. Sự đa dạng giữa người và ambiguity tương lai trong cùng người là hai nguồn khác nhau.

## VERIFIED và INTERPRETATION tách riêng — các phát hiện làm đổi giao thức

| VERIFIED: nguồn mô tả | INTERPRETATION / HYPOTHESIS: hệ quả cần thử |
| --- | --- |
| ImageFlowNet Appendix D.1 chọn registration anchor/common crop dựa trên chuỗi retinal images. [Nguồn](https://arxiv.org/html/2406.14794) | Có nguy cơ preprocessing nhìn tương lai khi đánh giá từ prefix. Cần chạy lại prefix-only; chưa đo mức lạc quan và không kết luận mọi dataset của paper bị cùng lỗi. |
| PCA respiratory basis của Pohl fit training segment. [Nguồn](https://arxiv.org/abs/2410.05882v3) | Không được cáo buộc basis fit toàn chuỗi. Cần match training-prefix length giữa online/offline baseline. |
| Petersen có Query Volume Dice chọn mẫu theo true future volume. [Nguồn](https://arxiv.org/html/2106.12917) | Đây là oracle-conditioned measure, không phải chất lượng chọn future có thể triển khai. Báo cùng unconditional distribution score. |
| MRI-CEK định nghĩa cSSIM từ các predicted adjacent frames. [Nguồn §4.1.1](https://arxiv.org/html/2602.19285) | Theo công thức, constant predicted sequence tối ưu độ giống nhau giữa frame; smoothness tự nó không chứng minh kinetics đúng. |
| BrLP đã đo uncertainty–error association; SPIE assessment cho thấy conditioning phù hợp diagnosis không luôn tối ưu SSIM. [BrLP](https://arxiv.org/html/2502.08560), [assessment](https://pmc.ncbi.nlm.nih.gov/articles/PMC12726967/) | Không claim “chưa có uncertainty evaluation”; khoảng hẹp hơn là calibration/coverage và endpoint-specific decision validity. |
| Stowers loại các ca calibration chất lượng thấp và chỉ phân tích pCR ở nhánh tiếp paclitaxel. [Nguồn pp2–5](https://pubs.rsna.org/doi/pdf/10.1148/ryai.240124) | Performance bị giới hạn bởi cohort selection và endpoint subset; chưa chứng minh causal treatment optimization ở quần thể rộng. |

## INTERPRETATION / HYPOTHESIS — so sánh A/B/C

| Tiêu chí | A | B | C |
| --- | --- | --- | --- |
| Hệ/state dễ định nghĩa | Motion/geometry khá trực tiếp; ngoài mặt phẳng khó quan sát | Pose đo được; anatomy/contact chỉ một phần | Burden/morphology đo qua pipeline; latent biology khó định danh |
| Mức public-data được nguồn hỗ trợ | Cine có nguồn; dense future labels cần audit | Tracked sweep có nguồn; command/force/closed-loop chưa được xác minh | Có longitudinal releases/DUA; đủ sâu và nhãn đáng tin phải đếm |
| Baseline quyết định | Periodic/PCA/linear/Kalman/GP | Nearest view, prefix reconstruction/reformat, pose-only/current-frame prediction | Last observation, linear/mixed-effects regional trend, deformation persistence, direct temporal prediction |
| Evaluation mạnh có thể thiết kế | Geometric error theo horizon; gating proxy đúng mục tiêu | Pose-query consistency, landmark error; physical success chỉ khi có môi trường | Δvolume/change error, calibration, multiple future visits, patient-level validation |
| Rủi ro khoa học chính | Chu kỳ đơn giản đã đủ; out-of-plane | View changes bị lẫn tissue deformation; future pose oracle | Sparse visits, segmentation, care confounding, selection |
| Rủi ro phạm vi | Biến tracking thành “forecast” bằng tên gọi | Biến pose conditioning thành causal action simulator | Biến natural-care forecast thành treatment effect |
| Phù hợp CV hiện tại | Có thể kiểm tra geometry và temporal baselines | Có thể kiểm tra representation/geometry nếu pose access xác nhận | Cần thêm longitudinal statistics và domain expertise |
| Kết luận | Có cơ sở nghiên cứu, chưa chọn | Có cơ sở nghiên cứu, chưa chọn | Có cơ sở nghiên cứu, chưa chọn |

Bốn câu hỏi chưa giải quyết mạnh nhất là: **state hình học có thêm predictive value so với motion baseline; memory của acquisition có ích ngoài coverage/pose; lesion trajectory có được kiểm chứng qua nhiều visits với label đáng tin; patient-specific morphology state có cải thiện change prediction hơn simple individual trend?** Đây là ưu tiên điều tra, không thứ tự chọn topic. Chi tiết Q1/Q4/Q5/Q6 và các phương án khác ở [OPEN_QUESTIONS](../OPEN_QUESTIONS.md).

Thông tin ngăn chọn topic hôm nay: chưa audit sample-level temporal manifests; chưa biết số bệnh nhân đủ history và future; chưa có nhãn lỗi/uncertainty được định lượng; chưa chốt downstream endpoint/horizon với chuyên gia; chưa xác nhận command/contact hoặc treatment-time completeness; chưa đo baseline headroom. Bước tiếp theo là kiểm tra dữ liệu và giao thức như [DATASET_FEASIBILITY](../DATASET_FEASIBILITY.md), **chưa chọn backbone**.
