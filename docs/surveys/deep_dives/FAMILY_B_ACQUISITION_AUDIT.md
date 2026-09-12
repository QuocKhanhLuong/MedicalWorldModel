# Family B — audit acquisition dynamics and pose-conditioned view prediction

Ngày đối chiếu: 2026-09-12 (Asia/Bangkok). Phạm vi của dossier là Family B. Đây là audit prior art, methods, evaluation và feasibility; chưa chọn
modality, architecture, paper topic hay họ A/B/C.

## Cách đọc bằng chứng

### VERIFIED

Một mệnh đề được ghi là VERIFIED khi có thể truy về paper gốc, proceedings/publisher,
official project page/code, hoặc metadata/chính sách chính thức của dataset. Với paper
trung tâm, tôi đã đọc phần phương pháp và đánh giá trong PDF/HTML; abstract-only
evidence được ghi rõ khi chưa đọc toàn văn. Năm/venue/status được tách khỏi claims
phương pháp và không suy ra từ tên file.

### INTERPRETATION / HYPOTHESIS

Đây là phép tổng hợp cho MedicalWorldModel: cách ánh xạ observation → state →
transition → output → use case, đề xuất protocol, gap, baseline và falsifier. Các
điểm này không phải kết quả thực nghiệm của repository và không được coi là quyết
định của researcher. Dữ liệu TUS-REC chưa được bulk-download; không có thỏa thuận
truy cập nào được chấp nhận.

## Kết luận sớm có ảnh hưởng trực tiếp đến tính khả thi

### VERIFIED

1. EchoWorld là precedent medical gần nhất cho một tên gọi world model: nó dùng
   lịch sử ảnh/pose và các cặp pose tương đối để dự báo feature của target plane, rồi
   đánh giá guidance bằng lỗi tịnh tiến/xoay trong setting tuần tự. Tuy vậy paper
   không báo cáo rollout ảnh/feature nhiều bước với ground truth tương lai, calibration
   uncertainty, metric hình học/anatomy, hay thử nghiệm closed-loop trên robot. Xem
   EchoWorld, phần 4.1–4.2 và Tables 1–2, Appendix B.2, tại
   [arXiv HTML](https://arxiv.org/html/2504.13065) và
   [CVPR PDF](https://openaccess.thecvf.com/content/CVPR2025/papers/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.pdf).

2. Hu et al. 2017 đã làm pose-conditioned ultrasound image synthesis trong tọa độ
   vật lý 3D. Họ điều kiện generator/discriminator trên các lưới tọa độ x/y/z đã
   calibrated, nhưng paper không có temporal state, transition, future-query
   forecasting hay action conditioning. Đây là prior art chống claim rộng “lần đầu
   pose-conditioned ultrasound prediction”, không tự nó chống một protocol
   prefix-only future-query có state sufficiency test. Xem §2.1–2.3 và §3 trong
   [bản PDF UCL](https://discovery.ucl.ac.uk/id/eprint/1566574/1/Vercauteren_1707.05392v1.pdf).

3. TUS-REC2024 công bố dữ liệu có 85 healthy volunteers, 2,040 scans, 24 scans
   mỗi subject, 20 fps, 480×640, optical tracker, transform ma trận 4×4 theo frame
   và calibration CSV. Official split là 50/3/32 subjects, tương ứng 1,200/72/768
   scans. Các thông tin này nằm trên [official data page](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/data.html),
   [challenge paper, §2](https://arxiv.org/html/2506.21765) và các record Zenodo
   [Part 1](https://zenodo.org/records/11178509), [Part 2](https://zenodo.org/records/11180795)
   và [validation](https://zenodo.org/records/12979481).

4. TUS-REC task hiện tại là reconstruction toàn scan từ frames/transforms, output
   global/local displacement và metrics landmark/pixel. Official task không yêu cầu
   cắt prefix rồi dự báo một query pose tương lai; challenge paper mô tả đánh giá
   với toàn bộ input scan. Do đó, data release không tự chứng minh rằng một
   prefix→future-query benchmark đã tồn tại. Xem [task](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/task.html),
   [assessment](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/assessment.html)
   và challenge paper §3–§4.

5. TUS-REC optical pose là measured geometry. Public schema/policy và challenge
   paper không ghi command log, robot controller action, force/contact signal hay
   intervention assignment. Vì vậy một model nhận pose có thể là
   query-conditioned observation prediction hoặc tracker-assisted reconstruction;
   không được gọi là action-conditioned causal world model chỉ vì có 4×4 pose.
   Challenge paper §2 nêu optical tracker, calibration và pressure-induced skin
   deformation như nguồn sai số; paper không tách được deformation do contact khỏi
   sinh lý bằng nhãn lực công khai.

6. Cardiac Copilot cũng gọi state hiện tại là ảnh và dùng probe pose tương đối để
   dự báo hướng dẫn 6D cho target standard plane. Dữ liệu là expert demonstrations
   với probe trên Franka Panda và pose từ cảm biến arm, nhưng đánh giá chỉ là
   one-step translation/rotation MAE trên ba planes; không có future image rollout,
   uncertainty, hay physical closed-loop trial trong paper. Xem [MICCAI official
   page](https://papers.miccai.org/miccai-2024/118-Paper0053.html),
   [paper PDF](https://papers.miccai.org/miccai-2024/paper/0053_paper.pdf), §2–§3.

7. Fan et al. 2026 là precedent gần nhất cho action-conditioned medical WM:
   latent VAE/diffusion dự báo frame tương lai từ context và relative 6DoF action,
   actor dùng imagined one-step reward, rồi có real-robot test. Nhưng đây là
   arXiv v2 với peer-reviewed venue UNKNOWN, dữ liệu tự thu của 20 người và robot
   riêng; paper tự giới hạn rằng learned dynamics nằm trong observed distribution
   và không phân biệt đầy đủ probe-induced dynamics với physiology/contact.
   Xem [arXiv HTML v2](https://arxiv.org/html/2607.21918v2), §§II–IV.

8. Trackerless sequence models và nonrigid reconstruction đã tồn tại trước một
   claim mới rộng về “memory”, “trackerless acquisition” hoặc “nonrigid state”.
   Li et al. 2023 dùng past/future frames để dự báo rigid transform; Li et al. 2024
   phân tích history length/protocol dependence; Li et al. 2023 dùng auxiliary
   anatomy/protocol discrimination; Li et al. 2024 thêm dense deformation field
   nhưng supervision deformation vẫn dựa trên rigid tracker labels và landmarks.
   Xem các paper ở mục prior art đối kháng bên dưới.

### INTERPRETATION / HYPOTHESIS

Residual gap có thể nghiên cứu được (chưa xác nhận novelty) là một protocol hẹp:
prefix chỉ dùng các ảnh và measured poses đã thấy; query pose được đưa vào rõ ràng;
model xuất target-view feature/landmark kèm support và uncertainty; đánh giá
multi-step direct query và autoregressive rollout tách riêng; state phải chứng minh
đủ qua readout độc lập và phải thắng các baseline pose/coverage-matched. Protocol
này có thể kiểm tra “memory có biết anatomy đã quan sát đủ để dự báo view mới không?”
mà không cần giả định command, lực, robot hoặc causal intervention.

## Operational audit: observation → state → transition → output → purpose

### Hu et al. 2017 — RAMBO

**VERIFIED.** Hệ được mô hình hóa là phân bố ảnh ultrasound có điều kiện theo vị
trí vật lý 3D. Observation là query coordinate grids x/y/z và Gaussian noise;
state temporal không được định nghĩa. “State” nếu dùng ngôn ngữ dự án chỉ là
location-conditioned appearance, không phải latent anatomy state đã được kiểm chứng.
Transition không có; output là ảnh tổng hợp tại vị trí được hỏi. Mục tiêu là mô phỏng
freehand ultrasound spatially, không phải forecasting hay planning. Mô hình lấy
một scan phantom fetal khoảng một giờ, tracker Polaris Spectra và 26,396 selected
frames; đánh giá same-location held-out frames và landmark/reader realism, không có
multi-step horizon. Các chi tiết này ở [PDF, §§2.1–2.3, §3](https://discovery.ucl.ac.uk/id/eprint/1566574/1/Vercauteren_1707.05392v1.pdf).

**INTERPRETATION.** Đây là learned observation field hơn là world model theo nghĩa
state-transition. Nó là baseline quan trọng cho pose/query conditioning và cho thấy
tọa độ 3D có thể encode vị trí tốt hơn concatenated rotation/translation trong
thiết kế gốc; không nên suy ra rằng output image giữ state vật lý của mô.

### Cardiac Copilot 2024

**VERIFIED.** Hệ là probe guidance cho echocardiography. Observation hiện tại là
ảnh; state được paper gọi là current image feature/state. Input bổ sung là relative
probe pose giữa các frame. Transition được dùng một lần để map feature của frame
hiện tại sang feature target, sau đó guidance head dự báo 6D movement (3 translation,
3 rotation). Dữ liệu là 125 scans (~188K pairs) expert-operated trên Franka Panda;
split 110 train/15 test, unseen individuals. Output chính là movement, không phải
ảnh tương lai. Evaluation là MAE/std của translation (mm) và rotation (degree)
trên PLAX, PSAX-AV, PSAX-MV; không có rollout horizon/uncertainty/planning trial.
Nguồn: [MICCAI page](https://papers.miccai.org/miccai-2024/118-Paper0053.html),
[PDF §2–§3](https://papers.miccai.org/miccai-2024/paper/0053_paper.pdf).

**INTERPRETATION.** Feature hiện tại được chứng minh qua guidance error, chưa qua
independent anatomical readout. Vì vậy nó là predictive representation có downstream
utility, không mặc nhiên là clinically meaningful state. Measured relative pose
giúp geometry conditioning; measured pose tự nó không xác lập causal action effect; cần thiết kế nhận dạng và các giả định phù hợp.

### EchoWorld 2025

**VERIFIED.** Hệ là motion-aware echocardiography probe guidance. Observation gồm
history images và measured poses; representation gồm masked-spatial feature,
motion feature từ cặp ảnh và relative pose, rồi history tokens/pairwise pose
differences. “Transition” là feature prediction từ source/image-pose pair tới
target frame feature; target encoder dùng EMA, objective có InfoNCE. Guidance head
xuất target-plane probe movement. Dataset có 356 scans, khoảng một triệu frames,
284 train/72 test, 30 fps, probe trên Franka Panda, healthy adult males; scans kéo
dài vài phút; ten planes được annotate theo frame/time. Nguồn: [arXiv
Appendix A, §4](https://arxiv.org/html/2504.13065), [CVF PDF](https://openaccess.thecvf.com/content/CVPR2025/papers/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.pdf).

Đánh giá gồm translation/rotation MAE cho single-frame và sequential guidance. Appendix B.2 có history N=8 và unvisited-plane protocol. Một diffusion decoder riêng tạo hình minh họa từ predicted features; đây không phải định lượng multi-step rollout. [Official repository](https://github.com/LeapLabTHU/EchoWorld) nói dataset không thể public vì privacy/institutional restrictions.

**INTERPRETATION / HYPOTHESIS.** Đây là prior art trực tiếp về temporal/pose memory cho guidance. Nó chưa chứng minh state đủ cho anatomy, feature accuracy sau nhiều bước dự báo không nhận ảnh thật, calibration hoặc physical closed-loop success. Q4 phải hỏi phần khác có thể bị bác bỏ: prefix-query prediction với matched coverage/protocol và independent state readout.

### Fan et al. 2026

**VERIFIED.** [Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound, arXiv:2607.21918v2](https://arxiv.org/html/2607.21918v2), §§II–IV, mô hình hóa quá trình partially observed qua history ảnh/pose → VAE latent → transition điều kiện relative 6DoF motion và elapsed time → future latent/frame. Actor dùng frozen world model dự báo một bước để chấm reward/progress/action smoothness rồi thực hiện chuyển động. Paper báo dữ liệu tự thu ở 20 người, carotid/thyroid trajectories, future image LPIPS/SSIM ở 0.5–30 s, forward–inverse consistency và real-robot evaluation. Mức horizon đó là các future-query evaluations, không tự chứng minh recursive rollout liên tục 30 s.

Phần robot có force/torque sensor; điều này không chứng minh lực là input của transition hoặc là public measurement. §IV thừa nhận chưa tách đầy đủ probe-induced dynamics khỏi physiology/contact và thiếu bảo đảm ngoài observed distribution. **Publication status:** chỉ xác minh arXiv v2; peer-reviewed venue UNKNOWN. Đây là kết luận audit, không phải lời paper tự tuyên bố venue UNKNOWN.

**INTERPRETATION / HYPOTHESIS.** Bài có bằng chứng simulator/policy mạnh hơn image-only synthesis vì có action, imagined transition, reward và physical closed-loop test trong thiết lập tác giả. Không suy khả năng tái lập với public data, causal effect mọi command hoặc clinical utility. TUS-REC measured poses không cung cấp tương đương bộ dữ liệu/hardware đó.

## TUS-REC2024 — schema thực có và thời gian chưa xác minh

### VERIFIED: nguồn public đã đọc

[Data page](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/data.html) và [challenge paper arXiv:2506.21765v2, §§2–4](https://arxiv.org/html/2506.21765) mô tả 85 healthy volunteers, 2,040 scans, 24 scans/person, split 50/3/32 subjects = 1,200/72/768 scans. Homepage có mô tả 100 volunteers; không gộp version. Acquisition 20 fps, 480×640, NDI Polaris Vicra; forearm sweeps thẳng/C/S, hai chiều distal/proximal và hai hướng mặt phẳng. HDF5 schema `frames` [N,H,W], `tforms` [N,4,4] tool-to-camera; `calib_matrix.csv` chứa pixel-to-mm và image-to-tool spatial calibration. [Zenodo Part 1](https://zenodo.org/records/11178509), [Part 2](https://zenodo.org/records/11180795), [validation](https://zenodo.org/records/12979481).

**Access/license:** [policy 2024](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/policies.html) liên kết **CC BY-NC-SA 4.0**, giới hạn research/non-commercial và yêu cầu không mở rộng use/redistribution ngoài phạm vi khi intended use còn mơ hồ. Đây là xác minh terms, không chấp nhận điều khoản thay researcher. Training/validation được mô tả public; test thông qua evaluation submission được mô tả ở Zenodo, quyền tải test hiện tại UNKNOWN. Không dùng terms 2025 thay 2024.

**Đối chiếu packaging:** Part 1/2 đều mô tả **toàn bộ training dataset** 50 subject folders/1,200 scans và có link tới Part 3; riêng dung lượng archive được trang báo 43.4/40.4 GB. Không có căn cứ rằng Part 1 là 50 subjects còn Part 2 thêm 40 subjects. Chưa đọc archive manifest, nên số subject duy nhất trong từng part UNKNOWN; không cộng descriptions trùng nhau thành cohort lớn hơn.

Paper nói ảnh/transform được đồng bộ và loại invalid transforms thường do occlusion; records còn lại được sắp theo thời gian. Paper cũng nêu pressure-induced skin deformation, calibration và intra-observer error như nguồn lỗi. Công bố synchronized acquisition **không chứng minh** timestamp/gap map còn đủ trong HDF5 release sau lọc: public schema được đọc chỉ liệt kê `frames/tforms`. Exact timestamp fields, N/duration, dropped-frame intervals, alignment và calibration residuals theo scan: **UNKNOWN**.

[Task](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/task.html) và [assessment](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/assessment.html) đánh giá full-scan transform/reconstruction với local/global displacement và landmark/pixel metrics. Không mô tả benchmark prefix→future query. Reconstruction landmarks không tự là nhãn anatomy đủ để chấm một query chưa quan sát; availability/provenance/reliability của target landmarks cần audit.

### INTERPRETATION / HYPOTHESIS: thiết lập B nào được phép nghiên cứu?

| Mức claim | Dữ liệu tối thiểu | TUS-REC hiện hỗ trợ tới đâu? |
| --- | --- | --- |
| Pose-conditioned observation prediction | Prefix images/poses, calibration, supplied query pose, held-out target | Có schema để điều tra; chưa đóng timestamp/label/support audit |
| Action-conditioned dynamics | Command được định nghĩa, timestamp trước action, realized motion, observation sau action, controller/latency context | Command log chưa xác minh; measured displacement không đủ thay command |
| Contact/tissue dynamics | Geometry/pose cùng force/contact hoặc quan sát đủ nhận dạng deformation và physiology | Không xác minh lực/contact; không gán mọi thay đổi ảnh cho viewpoint |
| Probe guidance | Goal/target-plane criterion, permissible movements, offline hoặc physical evaluation có ground truth riêng | Có thể đề xuất offline proxy nếu nhãn đủ; chưa có public clinical plane labels được xác minh |
| Closed-loop planning | Môi trường thực/simulator đã kiểm định, feedback, action support, reward và safety constraints phù hợp | Không được suy từ reconstruction dataset; cần evidence/data mới |

Query pose tương lai có thể được đưa vào **như biến điều kiện đã khai báo**, nhưng không được lén dùng future pose path để suy state hiện tại. Task lúc đó là dự báo observation dưới query, chưa chọn action. Nominal Δframe=5/10 ở 20 fps tương ứng 0.25/0.50 s chỉ khi không có dropped/invalid records giữa hai frame; không gọi đó là measured horizon trước khi audit timing.

## Adversarial prior art — memory, geometry và guidance đã có gì?

### VERIFIED: các nguồn đối nghịch

| Paper canonical / nguồn | Observation → state/operation → output; evaluation thực có | Mức đọc / giới hạn |
| --- | --- | --- |
| Li et al., **Trackerless Freehand Ultrasound with Sequence Modelling and Auxiliary Transformation Over Past and Future Frames**, ISBI 2023; [DOI](https://doi.org/10.1109/ISBI53787.2023.10230773), [arXiv](https://arxiv.org/abs/2211.04867v2) | Image sequence → sequence model → rigid transforms; dùng past/future context trong delayed reconstruction; frame/accumulated error, volume Dice và drift | Methods/evaluation; future context hợp lệ cho reconstruction, không cho forecast prefix |
| Li et al., **Long-Term Dependency for 3D Reconstruction of Freehand Ultrasound Without External Tracker**, TBME 71(3):1033–1042, 2024; [DOI](https://doi.org/10.1109/TBME.2023.3325551), [UCL](https://discovery.ucl.ac.uk/id/eprint/10179008/) | History images → learned sequence state → transforms/reconstruction; history-length và protocol-versus-anatomy analysis | Methods/evaluation; không phải anatomical future-state forecast |
| Li et al., **Privileged Anatomical and Protocol Discrimination in Trackerless 3D Ultrasound Reconstruction**, ASMUS 2023, LNCS14337:142–151; [DOI](https://doi.org/10.1007/978-3-031-44521-7_14), [UCL](https://discovery.ucl.ac.uk/id/eprint/10178259/) | Images + privileged subject/protocol information trong training → discriminative representation → rigid transforms; frame/volume errors | Methods/evaluation; prior về anatomy/protocol shortcuts |
| Li et al., **Nonrigid Reconstruction of Freehand Ultrasound Without a Tracker**, MICCAI 2024, LNCS15004:689–699; [DOI](https://doi.org/10.1007/978-3-031-72083-3_64), [official paper](https://papers.miccai.org/miccai-2024/568-Paper2245.html) | Images → rigid transform + dense deformation field → reconstructed geometry; GPE/GLE/LPE/LLE | Methods/evaluation; rigid tracker/landmarks không thành dense physical deformation ground truth |
| Droste et al., **Automatic Probe Movement Guidance for Freehand Obstetric Ultrasound**, MICCAI 2020, LNCS12263:583–592; [DOI](https://doi.org/10.1007/978-3-030-59716-0_56), [full text](https://pmc.ncbi.nlm.nih.gov/articles/PMC7116254/) | Ultrasound video + IMU in routine scans → representation → movement guidance; guidance accuracy | Nguồn mô tả 464 examinations/17 sonographers; không cần world-model framing để có guidance |
| Luo et al., **RecON: Online learning for sensorless freehand 3D ultrasound reconstruction**, Medical Image Analysis87:102810, 2023; [DOI](https://doi.org/10.1016/j.media.2023.102810), [code](https://github.com/Lmy0217/RecON) | Images → motion-weighted/local-to-global pseudo-supervision, shape prior, online adaptation → reconstruction | Metadata/abstract; không dùng để khẳng định future forecasting, causal mechanics hoặc chi tiết rollout UNKNOWN |

**INTERPRETATION / HYPOTHESIS.** Các bài này bác bỏ claim rộng rằng medical acquisition chưa có sequence memory, online patient adaptation hoặc nonrigid geometry. Chúng chưa tự bác bỏ Q4: prefix-only future-view state có thêm giá trị ngoài measured pose, coverage và protocol hay không. Muốn giữ gap đó cần baseline reconstruction/history mạnh, independent target và tests nhận biết unsupported query.

### GenNBV: prior về active evaluation, không phải learned world simulator

**VERIFIED.** Chen et al., **GenNBV: Generalizable Next-Best-View Policy for Active 3D Reconstruction**, CVPR 2024:16436–16445; [CVF](https://openaccess.thecvf.com/content/CVPR2024/html/Chen_GenNBV_Generalizable_Next-Best-View_Policy_for_Active_3D_Reconstruction_CVPR_2024_paper.html), [arXiv v3 methods §3–4](https://arxiv.org/html/2402.16174v3), [project](https://gennbv.tech/). History RGB-D/poses → probabilistic occupancy grid (occupied/free/unknown), image/action embeddings → **PPO policy chọn 5D camera viewpoint** → simulator Isaac Gym trả observation mới → update map. Metrics gồm coverage/AUC và geometric accuracy/Chamfer với view budgets, held-out/cross-dataset geometry.

Đây là learned policy sử dụng một simulator được cung cấp, **không có learned transition tạo imagined future observations để policy search qua đó**. Log-odds occupancy update nhận depth observation mới là mapping/assimilation. Theo nghĩa rộng paper gọi NBV là view planning, nhưng không được đồng nhất với planning through a learned world model. Probabilistic occupancy cũng không phải calibrated medical uncertainty.

**INTERPRETATION / HYPOTHESIS.** Có thể chuyển ý tưởng budgeted coverage, unknown-space support và cross-scene evaluation. Không nhập simulator/camera-action semantics này vào TUS-REC nếu chưa có command/environment. Đây là boundary example để tránh gọi mọi hệ có state, RL hoặc robot là world model.

## Q4 — protocol đề xuất, chưa chạy

**Câu hỏi:** Given prefix medical images, measured poses, calibration và thời gian khả dụng, can a model infer state về anatomy đã quan sát và support, whose transition predicts landmark/feature ở supplied query views sau Δframe=5/10 (physical horizon chỉ chốt sau timing audit), better than nearest-view, local pose-kernel, prefix reformat/fusion và current-image-plus-query-pose, for offline view anticipation?

Tất cả dưới đây là **INTERPRETATION / HYPOTHESIS**; không chọn ultrasound cho cả dự án.

| Thành phần | Thiết kế/falsifier |
| --- | --- |
| Information contract | Chỉ prefix để fit state, map, crop, normalization/adaptation. Query pose được khai báo riêng; không cho future images vào state. |
| State readouts | Chấm target feature bằng encoder frozen, thêm landmark/anatomy hoặc correspondence đáng tin. Freeze state để kiểm tra readout thứ hai; cùng training head tốt hơn không chứng minh anatomy state. |
| Rollout | Tách direct query tại nhiều thời điểm cùng prefix; recursive prediction; assimilation nhận ảnh thật mới; full-sweep reconstruction. Direct multi-query là hợp lệ, không bắt buộc recursive. |
| Strong baselines | Current-only + query, nearest observed view, pose-kernel/kNN, calibrated rigid reformat, prefix multi-view fusion, tracker/landmark transport khi nhãn cho phép; pose/protocol-only placebo. Không dùng full-sweep oracle làm baseline chính. |
| Matched-information test | Match pose distance, coverage, direction/protocol và observed support. Nếu memory gain mất khi match, bỏ claim anatomy memory vượt coverage. |
| Geometry/uncertainty | Target landmark/feature error theo query/horizon, revisit consistency, calibration/width/abstention risk. Convex hull chỉ là proxy support; acoustic visibility, slice coverage và deformation có thể khác. |
| Falsification | Hoán đổi query pose, đổi protocol/direction, giữ patient-disjoint split, audit temporal gaps. Nếu query không ảnh hưởng output hoặc baseline ngang bằng, hạ claim predictive state. |
| Data risk | Pose/frame misalignment, invalid record filtering, sparse/no landmarks, contact/physiology bị trộn, terms/access chưa đóng. |
| Scientific risk | State học protocol/subject identity hoặc coverage; anatomy không dự báo thêm; future labels không chấm được. |
| Allowed causal claim | Conditional prediction trong observed support. Không có intervention identification từ pose conditioning; randomization không phải điều kiện bắt buộc duy nhất, nhưng cần thiết kế/giả định nhận dạng phù hợp để mở causal claim. |
| MICCAI scope | Có thể là protocol/state-value study vừa nếu public data và endpoint đủ; chưa có bằng chứng đủ để cam kết novelty hoặc paper. Closed-loop planning cần scope/data khác. |

## Những thông tin còn thiếu và việc tiếp theo

1. Tải metadata nhỏ được phép, xác minh exact N, timestamps/gaps, frame-transform alignment, calibration, subject overlap giữa archive parts; không cần tải bulk ảnh để chốt các câu hỏi schema có thể đọc độc lập.
2. Xác minh target landmark/anatomy labels và geometry error floor; không dùng auto-label như clinical truth chưa kiểm tra.
3. Chốt pose query/horizon/use case; kiểm tra terms cho intended research use. Chưa chấp nhận DUA thay researcher.
4. Chạy strong simple baselines sau data gate, rồi lặp prior-art search theo đúng state+endpoint+release+cutoff. Chưa thiết kế backbone.
5. Chỉ mở action/contact/planning claim khi có command/control/feedback và evaluation độc lập phù hợp.

## Search và citation-integrity log

Academic-research-suite/deep-research dùng để trích system/state/transition/purpose và source verification; literature-review dùng có chọn lọc cho adversarial queries về sequence memory, trackerless reconstruction, nonrigid state, next-best-view và guidance. Đã đọc methods/evaluation của Hu, Cardiac Copilot, EchoWorld, Fan và các Li papers; RecON giữ abstract-depth. Root đọc thêm GenNBV §3–4 và official TUS-REC/Zenodo policies để kiểm tra lại phân loại và packaging.

Backward/forward tracing thủ công qua EchoWorld và TUS-REC references dẫn đến Li/RecON/Hu/Droste; không tuyên bố có đầy đủ citation graph. Metadata ở [paper matrix](../../PAPER_MATRIX.md) và [REFERENCES](../../REFERENCES.md), một hàng mỗi paper. Canonical venue của Fan/TUS-REC paper vẫn UNKNOWN ngoài arXiv khi chưa xác minh publication mới; challenge participation không phải peer-reviewed paper venue. Crossref xác minh các DOI có sẵn, không bịa DOI cho GenNBV.

Root integrity pass đã sửa suy luận sai về số subjects theo Zenodo parts và phân biệt GenNBV policy-in-simulator với learned world-model planning. Không chạy model, không mở ảnh người bệnh, không xác nhận data approval hoặc clinical utility.
