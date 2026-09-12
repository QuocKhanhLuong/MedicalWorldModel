# Toàn cảnh Visual World Models

Ngày đối chiếu: **2026-09-12** (Asia/Bangkok). Phạm vi: lịch sử chọn lọc và frontier 2023–2026 có ích cho định nghĩa bài toán y khoa. Đây là nghiên cứu nguồn, **không lựa chọn kiến trúc hoặc họ A/B/C**. Hồ sơ từng paper, tác giả, venue, phiên bản, input, rollout và mức đọc ở [PAPER_MATRIX](../PAPER_MATRIX.md); quy trình và giới hạn ở [RESEARCH_LOG](RESEARCH_LOG.md).

## Quy tắc bằng chứng

**VERIFIED** dưới đây là phát biểu được paper/trang sơ cấp hỗ trợ, trong phạm vi đã đọc; số đo là tác giả báo cáo, không phải kết quả nhóm tái lập. **INTERPRETATION / HYPOTHESIS** là tổng hợp hoặc điều kiện nghiên cứu do survey đề xuất. “UNKNOWN” không đồng nghĩa “không có”. Tên gọi world model trong paper và việc đáp ứng định nghĩa vận hành của dự án là hai trường khác nhau.

## VERIFIED — lịch sử qua các cam kết thực nghiệm

Gốc của imagined experience có trước visual generators: [Dyna-style planning, UAI 2008](https://proceedings.mlr.press/r6/sutton08a.html) dùng model tạo transitions để cập nhật value; paper này mở rộng Dyna có trước đó, không được ghi là khởi nguồn đầu tiên. [PredNet, ICLR 2017](https://arxiv.org/abs/1605.08104v5) nối future-frame prediction với object/steering readouts. [V-JEPA 2024](https://arxiv.org/abs/2404.08471v1) tiếp tục nhánh feature prediction với frozen downstream evaluation; đây chưa tự là temporal simulator. Các hồ sơ [G24–G26](../PAPER_MATRIX.md#g24) ghi canonical year và giới hạn xác minh venue.

| Nhánh | Landmark → hướng gần đây | Hệ và chuỗi observation → state → transition → future → mục đích | Cam kết thêm / bằng chứng |
| --- | --- | --- | --- |
| Latent dynamics, model-based RL | [Ha–Schmidhuber, 2018](https://proceedings.neurips.cc/paper/2018/hash/2de5d16682c3c35007e4e92982f1a2ba-Abstract.html) → [PlaNet, 2019](https://proceedings.mlr.press/v97/hafner19a.html) → [Dreamer, Nature 2025](https://www.nature.com/articles/s41586-025-08744-2) | Game/control: pixels + action history → latent và memory → chuyển theo action → latent/reward/termination → học hành vi | Policy được kiểm tra trong môi trường thật của benchmark; PlaNet lập kế hoạch online, Dreamer học actor qua imagined trajectories. |
| Task-oriented learned state | [MuZero, 2020](https://www.nature.com/articles/s41586-020-03051-4) → [TD-MPC2, 2024](https://openreview.net/pdf?id=Oxh5CstDJU) | Quan sát → state phục vụ reward/value → action-conditioned transition → reward/value/policy → search hoặc MPC | Không cần giải mã ảnh; ý nghĩa của state được ràng buộc bởi mục tiêu điều khiển. |
| Visual predictive learning | [Finn et al., 2016](https://papers.nips.cc/paper/6161-unsupervised-learning-for-physical-interaction-through-video-prediction) → [SlotFormer, 2023](https://openreview.net/pdf?id=TFbwV6I0VLg) | Ảnh tương tác → chuyển động pixel hoặc object slots → dynamics → vị trí/ảnh/slots tương lai → dự đoán tương tác, reasoning | SlotFormer dùng future reasoning và planning; không chỉ reconstruction. |
| Stochastic video prediction | [SVG, 2018](https://proceedings.mlr.press/v80/denton18a.html) → [IRIS, 2023](https://openreview.net/pdf?id=vhFu1Acb0xb), [DIAMOND, 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/6bdde0373d53d4a501249547084bed43-Abstract-Conference.html) | Video history → recurrent state/tokens/context → stochastic next observation → chuỗi tương lai → prediction; với IRIS/DIAMOND thêm imagined policy learning | SVG minh họa nhiều tương lai; IRIS/DIAMOND nối prediction với return Atari. Hai mục tiêu này không tương đương. |
| Action-conditioned generators | [Genie, 2024](https://proceedings.mlr.press/v235/bruce24a.html), [UniSim, ICLR 2024](https://arxiv.org/abs/2310.06114) | Video → implicit scene/context + action representation → conditional video dynamics → tương lai tương tác → môi trường sinh và học hành vi | Genie suy latent actions không nhãn; UniSim nhận điều kiện hành động nhiều mức. Latent action chưa tự động là lệnh vật lý được hiệu chuẩn. |
| Embodied/navigation | [Navigation World Models, CVPR 2025](https://openaccess.thecvf.com/content/CVPR2025/html/Bar_Navigation_World_Models_CVPR_2025_paper.html) | Egocentric history + relative motion/time → video context → action-conditioned future view → trajectory consistency/goal matching → xếp hạng đường đi và planning | Relative pose và trajectory error kết nối ảnh dự đoán với khả năng di chuyển. |
| Robot learning / representation-centric | [DINO-WM, ICML 2025](https://proceedings.mlr.press/v267/zhou25t.html), [V-JEPA 2, 2025 preprint](https://arxiv.org/abs/2506.09985), [DreamDojo, 2026](https://arxiv.org/abs/2602.06949) | Images + proprioception/action history → patch features hoặc video context → action-conditioned transition → goal features hoặc video → MPC, đánh giá/chọn policy | DINO-WM lập kế hoạch không cần reconstruction; V-JEPA 2 có adaptation dùng action; DreamDojo so sánh imagined với real robot outcomes. |
| Autonomous driving | [DriveDreamer, ECCV 2024](https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/6416_ECCV_2024_paper.php), [Vista, NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/a6a066fb44f2fe0d36cf740c873b8890-Abstract-Conference.html) | Camera + cấu trúc cảnh/control → video latent/context → conditional future → driving scene → sinh dữ liệu, chấm trajectory | Vista kiểm tra model-based reward/ranking; không đồng nhất với đã chứng minh closed-loop driving safety. |
| Physical/object simulation | [Graph Network Simulator, ICML 2020](https://proceedings.mlr.press/v119/sanchez-gonzalez20a.html), [PhysGaussian, CVPR 2024](https://openaccess.thecvf.com/content/CVPR2024/html/Xie_PhysGaussian_Physics-Integrated_3D_Gaussians_for_Generative_Dynamics_CVPR_2024_paper.html) | Particle/geometry state + vật liệu → explicit physical representation → learned acceleration hoặc numerical physics → chuyển động → mô phỏng | GNS đánh giá state errors qua rollout; PhysGaussian gắn biểu diễn nhìn thấy với phương trình vật lý. State đầu vào/thuộc tính vật liệu là thông tin bổ sung đáng kể. |
| 3D/4D scene representation | [4D Gaussian Splatting, CVPR 2024](https://openaccess.thecvf.com/content/CVPR2024/html/Wu_4D_Gaussian_Splatting_for_Real-Time_Dynamic_Scene_Rendering_CVPR_2024_paper.html) | Multiview video → Gaussians + biến dạng theo thời gian → query camera/time → rendered observation → novel-view rendering | Bài toán mô hình hóa cảnh động không tự xác lập khả năng dự báo ngoài phần thời gian đã quan sát. |
| Generative world simulators / foundation models | [Cosmos, technical report 2025](https://research.nvidia.com/publication/2025-01_cosmos-world-foundation-model-platform-physical-ai), DreamDojo 2026 | Video/context/điều kiện → implicit predictive state → autoregressive/conditional generation → video rollout → physical-AI training/evaluation | Phạm vi huấn luyện và khả năng sinh video rộng; giá trị simulator vẫn phải kiểm tra riêng trên task. |
| Representation geometry | [GeoWorld, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_GeoWorld_Geometric_World_Models_CVPR_2026_paper.html) | Procedure video → hyperbolic latent → bước tương lai → procedure state → anticipation | “Geometric” ở đây là hình học latent; không phải đo đạc 3D metric của cơ quan. |

Lịch sử này không có một thời điểm thuật ngữ thay thế toàn bộ sequence modeling. Các nhánh cùng tồn tại và giao nhau: pixel prediction có thể là thành phần simulator; một latent task model có thể hữu ích mà không sinh pixel. Bản *World Models* arXiv 1803.10122 và bản NeurIPS *Recurrent World Models Facilitate Policy Evolution* dùng tiêu đề/ID khác; Dreamer có preprint 2023 và bản Nature canonical 2025. [G01](../PAPER_MATRIX.md#g01), [G03](../PAPER_MATRIX.md#g03).

## VERIFIED — frontier được đánh giá bằng gì?

Bảng này bổ sung cho toàn bộ trường của từng paper trong matrix. Horizon huấn luyện, số bước lập kế hoạch, độ dài video minh họa và horizon được đo định lượng phải giữ riêng.

| Hướng / nguồn | State, transition, rollout | Đánh giá ngoài chất lượng ảnh | Uncertainty / planning đã kiểm tra |
| --- | --- | --- | --- |
| [PlaNet](https://proceedings.mlr.press/v97/hafner19a.html), [Dreamer](https://www.nature.com/articles/s41586-025-08744-2) | Belief gồm latent stochastic và recurrent history; imagined action transitions | Control return; PlaNet dùng cập nhật belief từ quan sát mới | Stochastic state không phải chứng nhận calibration. Supplement PlaNet cho biết overshooting không cần trong cấu hình cuối; Dreamer actor learning khác online search. |
| [TD-MPC2](https://openreview.net/pdf?id=Oxh5CstDJU) | Latent task dynamics với reward/value; MPC rollout | Hiệu quả điều khiển trên nhiều task | Value ensemble không tự là calibrated distribution của anatomical futures. |
| [SlotFormer](https://openreview.net/pdf?id=TFbwV6I0VLg) | Slots từ encoder có trước; autoregressive object dynamics | Future question answering, physical planning | Object identity/occlusion và sai số tích lũy cần tách khỏi appearance. |
| [DINO-WM](https://arxiv.org/html/2411.04983) | Frozen spatial features + action/proprioception → future features; goal matching qua CEM/MPC | Goal-reaching trên sáu môi trường; ablation representation và planning | Optional decoder không nằm trong yêu cầu planning. Không xác minh calibrated uncertainty. |
| [V-JEPA 2](https://arxiv.org/html/2506.09985) | Pretraining masked prediction; bản action-conditioned thêm proprioception/action. Training có teacher-forced và recursive rollout loss | Robot goal reaching, cùng video understanding | §4.3 dùng CEM và quan sát lại sau hành động; có lựa chọn camera và subgoals. Pretraining tổng quát không tự là prefix-only forecast. |
| [Navigation World Models](https://arxiv.org/html/2412.03572) | Video conditioned relative translation, yaw, Δt; eight-step MPC ở 0.25 s/step trong cấu hình mô tả | ATE/RPE cho trajectory ranking; image-goal planning | Chấm 16/32 proposal trajectories và lập kế hoạch là thiết kế cụ thể; không giả định tồn tại metric 3D map. |
| [Vista](https://arxiv.org/html/2405.17398) | Action-conditioned video; nhiều mẫu denoising tạo conditional variance reward | So sánh ranking với độ gần ground-truth trajectory | §3.3 và §4.3 kiểm tra reward; Appendix A bàn MPC như khả năng dùng, không phải kết quả closed-loop đã thực hiện. |
| [DreamDojo](https://arxiv.org/html/2602.06949) | Latent proxy actions từ human video → adaptation robot actions; causal video chunks | §4.7 so thứ hạng checkpoint policy với robot thật; thử chọn action proposals cho robot | Chính §5 ghi model có thể đánh giá quá cao absolute success. Correlation thứ hạng cao trong tập thử không chứng minh xác suất success đúng ngoài tập đó. |
| [GNS](https://proceedings.mlr.press/v119/sanchez-gonzalez20a.html) | Known particle history, material → learned acceleration → integration | State rollout error, chuyển qua cấu hình/thời gian dài hơn | Đã có state vật lý đầu vào; không chứng minh suy state tương đương từ MRI. |
| [PhysGaussian](https://openaccess.thecvf.com/content/CVPR2024/html/Xie_PhysGaussian_Physics-Integrated_3D_Gaussians_for_Generative_Dynamics_CVPR_2024_paper.html) | Geometry/rendering và simulation gắn với nhau | Tính nhất quán giữa geometry và motion | Physics được chỉ định vẫn cần tham số và điều kiện biên; không suy tissue mechanics chỉ từ video. |

## INTERPRETATION / HYPOTHESIS — khi nào tên world model có ích?

Cam kết hữu ích cho dự án là một **hợp đồng dự đoán có thể kiểm tra**:

1. **Hệ có ranh giới:** cái gì nằm trong state, cái gì là input ngoại sinh, cái gì không được quan sát.
2. **State từ thông tin khả dụng:** tại thời điểm t, inference chỉ dùng lịch sử được phép. State có thể là belief distribution, hình học đo/suy ra, tham số vật lý, biological hypothesis hoặc latent thuần dự đoán; phải ghi loại cụ thể.
3. **Transition có thể truy vấn:** đưa thời lượng Δt và action nếu có; trả về future state/observation/đại lượng tác vụ. Không cần mọi hệ có agent điều khiển.
4. **Dự đoán vượt ngoài reconstruction:** thử nhiều horizon trên phần tương lai thực sự giữ lại, với baseline cùng lượng thông tin.
5. **Mục đích kiểm chứng:** cho thấy state/transition có ích với đại lượng đã chọn, hoặc với simulator/planning trong phạm vi đã đánh giá. Claim planning cần bằng chứng mạnh hơn claim forecasting.

Đây là **quy ước đề xuất để sử dụng trong repo**, không phải định nghĩa phổ quát hay tiêu chuẩn “đúng tên” cho toàn bộ văn liệu. Một state-space/Kalman model đáp ứng hợp đồng có thể là world model; một video generator lớn không tự đáp ứng nó.

### Bốn bài toán thời gian phải tách

| Thiết kế | Input khi kiểm tra | Có thể kết luận |
| --- | --- | --- |
| Direct multi-horizon forecast | Cùng prefix tới t, query t+Δ1, t+Δ2… | Dự đoán nhiều horizon; chưa chứng minh tự hồi quy ổn định |
| Recursive rollout | Prefix ban đầu, sau đó dùng state dự đoán | Sai số tích lũy và giới hạn thời gian tự vận hành |
| Filtering/tracking | Có ảnh thật mới tại mỗi bước | Khả năng cập nhật state; không phải open-loop forecast |
| Reconstruction/interpolation | Encoder hoặc preprocessing thấy cả chuỗi | Mô hình hóa chuỗi đã thấy; không đủ chứng minh dự đoán từ prefix |

Giải ODE ở nhiều mốc không tạo thêm ground truth tương lai; số bước denoising không phải thời gian bệnh; query camera không phải tiến triển bệnh. Thiết kế counterfactual phải chỉ rõ điều kiện can thiệp có ý nghĩa gì trong hệ, chứ không chỉ thay một token.

### Thang bằng chứng cho simulator hữu ích

- **Predictor:** đo sai số tương lai tại horizon đã định.
- **Predictive state model:** kiểm tra memory/state đủ hữu ích, lợi ích so với trực tiếp dùng history và khả năng dùng lại state.
- **Bounded simulator:** rollout có độ tin cậy về state/geometry trong miền input đã kiểm tra; đánh giá distribution shift và sai số tích lũy.
- **Planner-compatible simulator:** action feasible, objective phản ánh task; xếp hạng/chọn hành động trong model được kiểm tra ở môi trường ngoài model.
- **Intervention/decision support:** ngoài các bước trên còn cần thiết kế nhận diện causal và bằng chứng tác động/giá trị quyết định thích hợp.

Các mức này là **rubric của survey**, không phải paper nào cũng phải đạt mức cuối. Nguồn minh họa cho việc tách các mức: [MuZero](https://www.nature.com/articles/s41586-020-03051-4), [Vista](https://arxiv.org/html/2405.17398), [DreamDojo](https://arxiv.org/html/2602.06949). Những lỗi cần thử, không mặc định mọi paper đều mắc: shortcut appearance; drift state; mất object khi occlusion; lựa chọn action ngoài support; model exploitation; uncertainty thấp nhưng sai; target-informed preprocessing; future covariates.

## INTERPRETATION / HYPOTHESIS — map chuyển giao

| General visual WM | Năng lực có thể chuyển | Cơ hội y khoa tương ứng | Điều không được chuyển nguyên xi |
| --- | --- | --- | --- |
| Belief dynamics / recurrent state | Memory dưới quan sát không đầy đủ | A: phase/velocity; B: vùng giải phẫu đã quan sát; C: xu hướng riêng bệnh nhân | Latent không tự mang nghĩa sinh lý |
| Object/particle dynamics | State có cấu trúc và metric task | Contour, deformation, lesion burden và uncertainty theo vùng | Slot tự học không tự là organ/lesion |
| Representation-based planning | Dự báo đại lượng đủ dùng thay vì pixel | Dự báo geometry, view utility, volume change | Goal-feature distance không tự là clinical utility |
| Navigation/robot simulators | Tách action, motion, observation; kiểm tra decision ranking | Pose-conditioned acquisition; guidance nếu có command và closed-loop data | Measured displacement không phải randomized intervention |
| Generative stochastic dynamics | Nhiều giả thuyết tương lai | Phân bố motion/disease change với calibration theo horizon | Đa dạng ảnh không chứng minh phủ đúng tương lai |
| Physical simulators | Ràng buộc state/transition và điều kiện biên | Deformation hoặc tumor dynamics có phép đo thích hợp | Không suy tham số sinh học định danh được nếu dữ liệu không đủ |
| Long rollout và hierarchical time | Kiểm tra ổn định qua các thang thời gian | Beat/respiratory phase; intravisit kinetics; visits | Không ghép ba loại thời gian thành một transition |

Xem [survey y khoa](MEDICAL_WORLD_MODELS_SURVEY.md), [kiểm tra novelty](TRANSFER_GAPS.md) và [câu hỏi chưa chọn](../OPEN_QUESTIONS.md).

## Đợt 2 — kiểm toán các tiêu chuẩn đánh giá của frontier

**VERIFIED:** lineage state còn có [Predictive Representations of State (2001)](../PAPER_MATRIX.md#g27), mô hình hóa tương lai qua core tests. Các benchmark [WorldSimBench](../PAPER_MATRIX.md#g28), [WorldModelBench](../PAPER_MATRIX.md#g29), [WorldArena](../PAPER_MATRIX.md#g30), [WorldArena 2.0](../PAPER_MATRIX.md#g31) và [Physics-IQ](../PAPER_MATRIX.md#g32) đo những khía cạnh khác nhau: human-rated violations, motion pattern, policy ranking, executed success và RL-environment utility. Không có một điểm tổng hợp chung đã xác nhận mọi khía cạnh này.

**INTERPRETATION / HYPOTHESIS:** chuyển giao có giá trị nhất là **cách đặt phép thử có thể thất bại**: state chứa thêm thông tin gì, transition có hơn direct prediction, rollout có nhận truth mới, metric có đo đúng target và task success thuộc thành phần nào. [State and evaluation audit](deep_dives/STATE_AND_EVALUATION_AUDIT.md) đọc sâu methods/appendices, phân biệt physical measurements với proxies và đưa ra hợp đồng kiểm chứng áp dụng cho A/B/C. Không nhận hierarchy theo output modality của một benchmark làm định nghĩa bắt buộc cho dự án.
