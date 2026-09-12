# Paper matrix — hệ, state, transition và bằng chứng

Đối chiếu: **2026-09-12**, Asia/Bangkok. **55 paper**, một hàng/paper trong [CSV](paper_matrix.csv). Tập chọn có chủ đích, không phải danh mục toàn bộ lĩnh vực.

**VERIFIED**: metadata và mô tả trong nguồn sơ cấp, giới hạn theo `read_depth`/vị trí. Kết quả tác giả báo cáo, chưa tái lập. **INTERPRETATION / HYPOTHESIS**: đánh giá contribution, limitation, relevance. `UNKNOWN` không có nghĩa không tồn tại; `N/A` không áp dụng. Tên phương pháp chỉ mô tả prior art, không chọn kiến trúc. Authors rút gọn được ghi rõ; full lists tại nguồn. Canonical publication và arXiv version được giữ riêng; URL publisher bị chặn được ghi cùng nguồn corroboration.

## Mục lục bằng chứng

| ID | Paper / nguồn | Năm / venue canonical | Status | Tự framing WM? | Mức đọc |
| --- | --- | --- | --- | --- | --- |
| [G01](#g01) | [Recurrent World Models Facilitate Policy Evolution](https://proceedings.neurips.cc/paper/2018/hash/2de5d16682c3c35007e4e92982f1a2ba-Abstract.html) | 2018; NeurIPS 31 | Published | yes | metadata + abstract |
| [G02](#g02) | [Learning Latent Dynamics for Planning from Pixels](https://proceedings.mlr.press/v97/hafner19a.html) | 2019; ICML; PMLR 97 | Published | yes | full-text methods/evaluation và supplement |
| [G03](#g03) | [Mastering diverse control tasks through world models](https://www.nature.com/articles/s41586-025-08744-2) | 2025; Nature 640:647–653 | Published | yes | full-text methods/evaluation |
| [G04](#g04) | [Mastering Atari, Go, chess and shogi by planning with a learned model](https://www.nature.com/articles/s41586-020-03051-4) | 2020; Nature 588:604–609 | Published | no | metadata + abstract |
| [G05](#g05) | [Unsupervised Learning for Physical Interaction through Video Prediction](https://papers.nips.cc/paper/6161-unsupervised-learning-for-physical-interaction-through-video-prediction) | 2016; NeurIPS 29 | Published | no | metadata + abstract |
| [G06](#g06) | [Stochastic Video Generation with a Learned Prior](https://proceedings.mlr.press/v80/denton18a.html) | 2018; ICML; PMLR 80:1174–1183 | Published | no | metadata + abstract |
| [G07](#g07) | [Transformers are Sample-Efficient World Models](https://openreview.net/pdf?id=vhFu1Acb0xb) | 2023; ICLR | Published | yes | PDF methods/evaluation |
| [G08](#g08) | [Diffusion for World Modeling: Visual Details Matter in Atari](https://proceedings.neurips.cc/paper_files/paper/2024/hash/6bdde0373d53d4a501249547084bed43-Abstract-Conference.html) | 2024; NeurIPS 37 | Published | yes | PDF methods/evaluation |
| [G09](#g09) | [TD-MPC2: Scalable, Robust World Models for Continuous Control](https://openreview.net/pdf?id=Oxh5CstDJU) | 2024; ICLR | Published | yes | PDF methods/evaluation |
| [G10](#g10) | [SlotFormer: Unsupervised Visual Dynamics Simulation with Object-Centric Models](https://openreview.net/pdf?id=TFbwV6I0VLg) | 2023; ICLR | Published | yes | PDF methods; evaluation overview |
| [G11](#g11) | [DINO-WM: World Models on Pre-trained Visual Features enable Zero-shot Planning](https://proceedings.mlr.press/v267/zhou25t.html) | 2025; ICML; PMLR 267:79115–79135 | Published | yes | full-text methods/evaluation/appendix |
| [G12](#g12) | [V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Planning](https://arxiv.org/abs/2506.09985) | 2025; arXiv; venue peer-reviewed UNKNOWN | Preprint verified | yes | full-text §3 and §4.3 |
| [G13](#g13) | [Genie: Generative Interactive Environments](https://proceedings.mlr.press/v235/bruce24a.html) | 2024; ICML; PMLR 235:4603–4623 | Published | yes | proceedings metadata/abstract |
| [G14](#g14) | [Learning Interactive Real-World Simulators](https://openreview.net/pdf/ebbd0d77e65c2e2ffb1eef300c8c55e4f2f27c86.pdf) | 2024; ICLR | Published | yes | metadata + abstract |
| [G15](#g15) | [Navigation World Models](https://openaccess.thecvf.com/content/CVPR2025/html/Bar_Navigation_World_Models_CVPR_2025_paper.html) | 2025; CVPR:15791–15801 | Published | yes | full-text methods/evaluation |
| [G16](#g16) | [DriveDreamer: Towards Real-world-driven World Models for Autonomous Driving](https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/6416_ECCV_2024_paper.php) | 2024; ECCV | Published | yes | metadata + abstract |
| [G17](#g17) | [Vista: A Generalizable Driving World Model with High Fidelity and Versatile Controllability](https://proceedings.neurips.cc/paper_files/paper/2024/hash/a6a066fb44f2fe0d36cf740c873b8890-Abstract-Conference.html) | 2024; NeurIPS | Published | yes | full-text methods/evaluation/appendix |
| [G18](#g18) | [Learning to Simulate Complex Physics with Graph Networks](https://proceedings.mlr.press/v119/sanchez-gonzalez20a.html) | 2020; ICML; PMLR119:8459–8468 | Published | no | metadata + abstract |
| [G19](#g19) | [PhysGaussian: Physics-Integrated 3D Gaussians for Generative Dynamics](https://openaccess.thecvf.com/content/CVPR2024/html/Xie_PhysGaussian_Physics-Integrated_3D_Gaussians_for_Generative_Dynamics_CVPR_2024_paper.html) | 2024; CVPR:4389–4398 | Published | no | metadata + abstract |
| [G20](#g20) | [4D Gaussian Splatting for Real-Time Dynamic Scene Rendering](https://openaccess.thecvf.com/content/CVPR2024/html/Wu_4D_Gaussian_Splatting_for_Real-Time_Dynamic_Scene_Rendering_CVPR_2024_paper.html) | 2024; CVPR:20310–20320 | Published | no | metadata + abstract |
| [G21](#g21) | [GeoWorld: Geometric World Models](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_GeoWorld_Geometric_World_Models_CVPR_2026_paper.html) | 2026; CVPR:30952–30963 | Published | yes | metadata + abstract |
| [G22](#g22) | [Cosmos World Foundation Model Platform for Physical AI](https://research.nvidia.com/publication/2025-01_cosmos-world-foundation-model-platform-physical-ai) | 2025; Technical report | Technical report / preprint | yes | metadata + abstract |
| [G23](#g23) | [DreamDojo: A Generalist Robot World Model from Large-Scale Human Videos](https://arxiv.org/abs/2602.06949) | 2026; ICML 2026 theo official repository; proceedings record UNKNOWN | Accepted/venue reported by authors; version read is preprint | yes | full-text §3–4.7 and limitations |
| [G24](#g24) | [Dyna-style planning with linear function approximation and prioritized sweeping](https://proceedings.mlr.press/r6/sutton08a.html) | 2008; UAI; PMLR R6:528–536 | Published; PMLR reissue 2024 | yes | metadata + abstract |
| [G25](#g25) | [Deep Predictive Coding Networks for Video Prediction and Unsupervised Learning](https://arxiv.org/abs/1605.08104v5) | 2017; ICLR | Published; author lab confirms ICLR 2017 | no | metadata + abstract |
| [G26](#g26) | [Revisiting Feature Prediction for Learning Visual Representations from Video](https://arxiv.org/abs/2404.08471v1) | 2024; arXiv; peer-reviewed venue UNKNOWN | Preprint verified | no | metadata + abstract |
| [K01](#k01) | [Challenging Common Assumptions in the Unsupervised Learning of Disentangled Representations](https://proceedings.mlr.press/v97/locatello19a.html) | 2019; ICML; PMLR97:4114–4124 | Published | no | metadata + abstract |
| [K02](#k02) | [Forecasting Treatment Responses Over Time Using Recurrent Marginal Structural Networks](https://papers.nips.cc/paper_files/paper/2018/hash/56e6a93212e4482d99c84a639d254b67-Abstract.html) | 2018; NeurIPS31 | Published | no | official abstract + original PDF |
| [M01](#m01) | [Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model](https://papers.miccai.org/miccai-2024/118-Paper0053.html) | 2024; MICCAI; LNCS15001:190–199 | Published | yes | official abstract, paper information and author response |
| [M02](#m02) | [EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance](https://openaccess.thecvf.com/content/CVPR2025/html/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.html) | 2025; CVPR | Published | yes | full-text §3–5 and appendix; PDF visual inspection p4 |
| [M03](#m03) | [Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound](https://arxiv.org/abs/2607.21918v2) | 2026; arXiv; peer-reviewed venue UNKNOWN | Preprint | yes | full-text §II–IV |
| [M04](#m04) | [Medical World Model](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html) | 2025; ICCV:8319–8329 | Published | yes | full-text §3 and evaluation/appendix |
| [M05](#m05) | [ImageFlowNet: Forecasting Multiscale Image-Level Trajectories of Disease Progression with Irregularly-Sampled Longitudinal Medical Images](https://doi.org/10.1109/ICASSP49660.2025.10890535) | 2025; ICASSP | Published | no | full-text methods/evaluation/Appendix D,F |
| [M06](#m06) | [Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction](https://doi.org/10.1109/TMI.2025.3533038) | 2025; IEEE Transactions on Medical Imaging 44(6):2449–2462 | Published | no | full-text methods; §IV-A/B evaluation |
| [M07](#m07) | [Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation](https://openreview.net/pdf/a1558b2e7d9494789fdd3057059dfbe2add8737e.pdf) | 2026; ICLR | Published | no | camera-ready metadata; full arXiv methods/evaluation |
| [M08](#m08) | [Brain Latent Progression: Individual-based spatiotemporal disease progression on 3D Brain MRIs via latent diffusion](https://doi.org/10.1016/j.media.2025.103734) | 2025; Medical Image Analysis 106:103734 | Published | no | full-text methods §4; evaluation §5.6 |
| [M09](#m09) | [Frame forecasting in cine MRI using the PCA respiratory motion model: comparing recurrent neural networks trained online and transformers](https://www.sciencedirect.com/science/article/abs/pii/S0895611126000583) | 2026; Computerized Medical Imaging and Graphics 131:102755 | Published | no | PDF methods/evaluation; visually inspected Table2 |
| [M10](#m10) | [A Latent ODE Approach to Spatiotemporal Modeling of Cine Cardiac MRI](https://arxiv.org/abs/2606.26718) | 2026; arXiv; venue UNKNOWN | Preprint | no | full-text §3.5, evaluation and AppendixB |
| [M11](#m11) | [4D CardioSynth: Synthesising Dynamic Virtual Heart Populations Through Spatiotemporal Disentanglement](https://papers.miccai.org/miccai-2025/0004-Paper2701.html) | 2025; MICCAI 2025:3–12 | Published | no | metadata + abstract |
| [M12](#m12) | [MRI Contrast Enhancement Kinetics World Model](https://openaccess.thecvf.com/content/CVPR2026/html/Kong_MRI_Contrast_Enhancement_Kinetics_World_Model_CVPR_2026_paper.html) | 2026; CVPR:1288–1299 | Published | yes | full-text §3–4 |
| [M13](#m13) | [X-WIN: Building Chest Radiograph World Model via Predictive Sensing](https://openaccess.thecvf.com/content/CVPR2026/html/Yang_X-WIN_Building_Chest_Radiograph_World_Model_via_Predictive_Sensing_CVPR_2026_paper.html) | 2026; CVPR:6920–6930 | Published | yes | metadata + abstract |
| [M14](#m14) | [Surgical Vision World Model](https://doi.org/10.1007/978-3-032-08009-7_1) | 2025; DEMI workshop at MICCAI:1–10 | Published workshop chapter | yes | metadata + abstract |
| [M15](#m15) | [SAW: Toward a Surgical Action World Model via Controllable and Scalable Video Generation](https://arxiv.org/abs/2603.13024) | 2026; arXiv; venue UNKNOWN | Preprint | yes | metadata + abstract |
| [M16](#m16) | [Cosmos-Surg-dVRK: World Foundation Model-based Automated Online Evaluation of Surgical Robot Policy Learning](https://arxiv.org/abs/2510.16240v2) | 2025; arXiv; venue UNKNOWN | Preprint | yes | full-text system/evaluation; §5.2–5.3 |
| [M17](#m17) | [Continuous-Time Deep Glioma Growth Models](https://doi.org/10.1007/978-3-030-87199-4_8) | 2021; MICCAI; LNCS12903:83–92 | Published | no | full-text methods/evaluation |
| [M18](#m18) | [Learning Spatio-Temporal Model of Disease Progression With NeuralODEs From Longitudinal Volumetric Data](https://doi.org/10.1109/TMI.2023.3330576) | 2024; IEEE TMI 43(3):1165–1179 | Published; online 2023, issue 2024 | no | full-text §II and evaluation design |
| [M19](#m19) | [Probabilistic Temporal Prediction of Continuous Disease Trajectories and Treatment Effects Using Neural SDEs](https://papers.miccai.org/miccai-2024/619-Paper3431.html) | 2024; MICCAI; LNCS15003:400–410 | Published | no | full-text §2–3 |
| [M20](#m20) | [Predictive digital twins with quantified uncertainty for patient-specific decision making in oncology](https://www.sciencedirect.com/science/article/pii/S0021999126002901) | 2026; Journal of Computational Physics 560:114937 | Published 2026-09-01 | no | full-text §3–5 |
| [M21](#m21) | [Online prediction for respiratory movement compensation: a patient-specific gating control for MRI-guided radiotherapy](https://doi.org/10.1186/s13014-023-02341-1) | 2023; Radiation Oncology 18:149 | Published | no | original paper PDF abstract/method overview |
| [M22](#m22) | [Real-time prediction and gating of respiratory motion using an extended Kalman filter and Gaussian process regression](https://pubmed.ncbi.nlm.nih.gov/25489980/) | 2015; Physics in Medicine & Biology 60(1):233–252 | Published; epub 2014 | no | indexed original abstract/metadata |
| [M23](#m23) | [Freehand Ultrasound Image Simulation with Spatially-Conditioned Generative Adversarial Networks](https://arxiv.org/abs/1707.05392) | 2017; RAMBO at MICCAI | Accepted/published chapter DOI recorded | no | metadata + abstract |
| [M24](#m24) | [A technical assessment of latent diffusion for Alzheimer's disease progression](https://pmc.ncbi.nlm.nih.gov/articles/PMC12726967/) | 2025; SPIE Medical Imaging; Proc SPIE13406:1340621 | Published proceedings | no | original full-text search extraction methods/abstract |
| [M25](#m25) | [A radiographic world model for clinical reasoning and evidence generation](https://arxiv.org/abs/2609.07719) | 2026; arXiv; venue UNKNOWN | Preprint | yes | metadata + abstract |
| [M26](#m26) | [World Model for AI Autonomous Navigation in Mechanical Thrombectomy](https://papers.miccai.org/miccai-2025/1021-Paper3014.html) | 2025; MICCAI; LNCS15968:680–690 | Published | yes | official metadata/abstract; methods details not used |
| [M27](#m27) | [Combining Biology-based and MRI Data-driven Modeling to Predict Response to Neoadjuvant Chemotherapy in Patients with Triple-Negative Breast Cancer](https://pubs.rsna.org/doi/10.1148/ryai.240124) | 2025; Radiology: Artificial Intelligence 7(1):e240124 | Published; online 2024, issue 2025 | no | original PDF methods/evaluation pp2–5 |

<a id="g01"></a>

## G01 — Recurrent World Models Facilitate Policy Evolution

**VERIFIED — hồ sơ nguồn:** David Ha; Jürgen Schmidhuber. 2018, NeurIPS 31; Published. DOI: UNKNOWN; arXiv: [1809.01999](https://arxiv.org/abs/1809.01999). [Nguồn chính](https://proceedings.neurips.cc/paper/2018/hash/2de5d16682c3c35007e4e92982f1a2ba-Abstract.html). World Models (1803.10122) là bản sớm; NeurIPS dùng tên và ID 1809.01999

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | game/control |
| Observation → state | pixels và action history → VAE code + recurrent memory |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | game controls |
| Transition | MDN-RNN next latent |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; latent; termination |
| Horizon / rollout | episode trong dream; số bước tùy task; latent recurrent rollout, dream episodes |
| Evaluation / downstream | return khi policy chuyển sang môi trường gốc; học policy trong mô hình |
| Dataset | CarRacing; VizDoom |
| Uncertainty | mixture density; không phải calibrated safety |
| Planning đã xác minh | policy evolution trong dream, không đồng nhất online tree search |
| Project/repository | [official](https://worldmodels.github.io) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: kiểm tra chuyển policy từ imagined environment. Giới hạn: policy có thể khai thác sai số mô hình. Liên quan MedicalWorldModel: state phải kiểm chứng qua tác vụ.

<a id="g02"></a>

## G02 — Learning Latent Dynamics for Planning from Pixels

**VERIFIED — hồ sơ nguồn:** Danijar Hafner; Timothy Lillicrap; Ian Fischer; Ruben Villegas; David Ha; Honglak Lee; James Davidson. 2019, ICML; PMLR 97; Published. DOI: UNKNOWN; arXiv: [1811.04551](https://arxiv.org/abs/1811.04551). [Nguồn chính](https://proceedings.mlr.press/v97/hafner19a.html). Không coi overshooting bắt buộc: supplement ghi không cần trong cấu hình cuối

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | visual continuous control |
| Observation → state | pixels, past actions → deterministic + stochastic recurrent belief |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | continuous controls |
| Transition | latent state transition + observation/reward heads |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future latent; reward |
| Horizon / rollout | MPC hữu hạn; task-dependent; latent action rollouts; MPC reobserves |
| Evaluation / downstream | control return; representation/overshooting ablations; planning từ pixels |
| Dataset | DeepMind Control Suite |
| Uncertainty | stochastic latent |
| Planning đã xác minh | CEM MPC; thực thi action đầu rồi quan sát lại |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text methods/evaluation và supplement; §2–4; supplement latent overshooting |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: học dynamics trong không gian nhỏ. Giới hạn: quan sát thiếu và rollout error vẫn tồn tại. Liên quan MedicalWorldModel: belief/history có thể có ích, cần kiểm tra.

<a id="g03"></a>

## G03 — Mastering diverse control tasks through world models

**VERIFIED — hồ sơ nguồn:** Danijar Hafner; Jurgis Pasukonis; Jimmy Ba; Timothy Lillicrap. 2025, Nature 640:647–653; Published. DOI: [10.1038/s41586-025-08744-2](https://doi.org/10.1038/s41586-025-08744-2); arXiv: [2301.04104](https://arxiv.org/abs/2301.04104). [Nguồn chính](https://www.nature.com/articles/s41586-025-08744-2). arXiv tên Mastering Diverse Domains through World Models; published title canonical

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | general control / DreamerV3 |
| Observation → state | observations, actions, rewards → recurrent stochastic latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | task controls |
| Transition | learned latent dynamics; reward; continuation |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; imagined returns and states |
| Horizon / rollout | multi-step imagination; numeric horizon UNKNOWN trong extraction; latent imagined sequences for actor/value learning |
| Evaluation / downstream | return nhiều task/domain; học actor–critic bằng imagined futures |
| Dataset | Atari; DMLab; Minecraft; control suites |
| Uncertainty | stochastic latent; không báo clinical calibration |
| Planning đã xác minh | imagination để train policy; không mặc định MPC lúc chạy |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text methods/evaluation; Methods: world model; actor–critic; benchmarks |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: reuse thuật toán across domains. Giới hạn: return cao không chứng minh physical identification. Liên quan MedicalWorldModel: mô hình và policy là hai thành phần.

<a id="g04"></a>

## G04 — Mastering Atari, Go, chess and shogi by planning with a learned model

**VERIFIED — hồ sơ nguồn:** Julian Schrittwieser; Ioannis Antonoglou; Thomas Hubert; Karen Simonyan; Laurent Sifre; Simon Schmitt; Arthur Guez; Edward Lockhart; Demis Hassabis; Thore Graepel; Timothy Lillicrap; David Silver. 2020, Nature 588:604–609; Published. DOI: [10.1038/s41586-020-03051-4](https://doi.org/10.1038/s41586-020-03051-4); arXiv: [1911.08265](https://arxiv.org/abs/1911.08265). [Nguồn chính](https://www.nature.com/articles/s41586-020-03051-4). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | games / MuZero |
| Observation → state | game observations and history → task-relevant hidden state |
| Loại state / thông tin suy ra | latent phục vụ value/reward; không explicit world geometry; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | legal/game actions |
| Transition | iterable recurrent model |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; reward; value; policy |
| Horizon / rollout | search tree; depth varies; recurrent latent tree expansion |
| Evaluation / downstream | game return / playing strength; search without supplied simulator |
| Dataset | Atari; Go; chess; shogi |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | MCTS |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: không cần tái tạo pixels để planning. Giới hạn: task sufficiency không bảo đảm state dùng cho mọi truy vấn. Liên quan MedicalWorldModel: định nghĩa medical WM không bắt buộc pixels.

<a id="g05"></a>

## G05 — Unsupervised Learning for Physical Interaction through Video Prediction

**VERIFIED — hồ sơ nguồn:** Chelsea Finn; Ian Goodfellow; Sergey Levine. 2016, NeurIPS 29; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://papers.nips.cc/paper/6161-unsupervised-learning-for-physical-interaction-through-video-prediction). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | robot pushing video |
| Observation → state | images và robot motion → hidden visual features; pixel motion transformations |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | robot actions |
| Transition | predict transformations/masks của pixels |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future images |
| Horizon / rollout | multi-frame; numeric horizon UNKNOWN; recurrent transformed-pixel prediction |
| Evaluation / downstream | image prediction; learn visual physical interaction |
| Dataset | robot pushing |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | Không được xác minh trong phần đã đọc |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: action-conditioned video ancestor. Giới hạn: paper prediction không tự chứng minh planner. Liên quan MedicalWorldModel: tách acquisition transition với appearance generation.

<a id="g06"></a>

## G06 — Stochastic Video Generation with a Learned Prior

**VERIFIED — hồ sơ nguồn:** Emily Denton; Rob Fergus. 2018, ICML; PMLR 80:1174–1183; Published. DOI: UNKNOWN; arXiv: [1802.07687](https://arxiv.org/abs/1802.07687). [Nguồn chính](https://proceedings.mlr.press/v80/denton18a.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | stochastic video prediction |
| Observation → state | past frames → recurrent deterministic features + stochastic code |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | learned time-varying latent prior; recurrent decoder |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future frame distribution |
| Horizon / rollout | multi-frame; numeric horizon UNKNOWN; sampled stochastic recurrent future frames |
| Evaluation / downstream | image/video prediction; plausible diverse future video |
| Dataset | UNKNOWN trong phần abstract đã đọc |
| Uncertainty | learned stochastic prior; calibration UNKNOWN |
| Planning đã xác minh | Không được xác minh trong phần đã đọc |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: explicit stochastic futures. Giới hạn: diversity và sharpness không bảo đảm task-valid simulator. Liên quan MedicalWorldModel: bất định tương lai có trước WM frontier.

<a id="g07"></a>

## G07 — Transformers are Sample-Efficient World Models

**VERIFIED — hồ sơ nguồn:** Vincent Micheli; Eloi Alonso; François Fleuret. 2023, ICLR; Published. DOI: UNKNOWN; arXiv: [2209.00588](https://arxiv.org/abs/2209.00588). [Nguồn chính](https://openreview.net/pdf?id=vhFu1Acb0xb). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Atari / IRIS |
| Observation → state | tokenized frames; actions → token history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | discrete game actions |
| Transition | autoregressive token dynamics + reward/end |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; pixels/tokens; reward; termination |
| Horizon / rollout | multi-step imagined episodes; numeric UNKNOWN; autoregressive observation/action tokens |
| Evaluation / downstream | Atari 100k returns; sample-efficient policy learning |
| Dataset | Atari 100k |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | actor–critic learning in imagined environment |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | PDF methods/evaluation; §2–4 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: token world model evaluated by return. Giới hạn: tokenization can lose small task-critical objects. Liên quan MedicalWorldModel: compression must preserve endpoint evidence.

<a id="g08"></a>

## G08 — Diffusion for World Modeling: Visual Details Matter in Atari

**VERIFIED — hồ sơ nguồn:** Eloi Alonso; Adam Jelley; Vincent Micheli; Anssi Kanervisto; Amos Storkey; Tim Pearce; François Fleuret. 2024, NeurIPS 37; Published. DOI: [10.52202/079017-1873](https://doi.org/10.52202/079017-1873); arXiv: [2405.12399](https://arxiv.org/abs/2405.12399). [Nguồn chính](https://proceedings.neurips.cc/paper_files/paper/2024/hash/6bdde0373d53d4a501249547084bed43-Abstract-Conference.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Atari / DIAMOND |
| Observation → state | frames; actions → recent pixel history / denoising features |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | game actions |
| Transition | conditional next-image diffusion |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; image; reward/end via auxiliary models |
| Horizon / rollout | autoregressive multi-step; numeric UNKNOWN; autoregressive frame sampling with action history |
| Evaluation / downstream | Atari100k return, not only perceptual quality; policy training |
| Dataset | Atari 100k |
| Uncertainty | diffusion sampling; clinical calibration not evaluated |
| Planning đã xác minh | policy learned in model |
| Project/repository | [official](https://diamond-wm.github.io) |
| Mức đọc / vị trí | PDF methods/evaluation; World model and Atari evaluation |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: fine visual details linked to reward behavior. Giới hạn: stochastic generation does not equal calibrated epistemic uncertainty. Liên quan MedicalWorldModel: tiny anatomy changes may matter; verify endpoint.

<a id="g09"></a>

## G09 — TD-MPC2: Scalable, Robust World Models for Continuous Control

**VERIFIED — hồ sơ nguồn:** Nicklas Hansen; Hao Su; Xiaolong Wang. 2024, ICLR; Published. DOI: UNKNOWN; arXiv: [2310.16828](https://arxiv.org/abs/2310.16828). [Nguồn chính](https://openreview.net/pdf?id=Oxh5CstDJU). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | continuous control |
| Observation → state | state observations or images; action → task-oriented latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | continuous action |
| Transition | latent consistency, reward and value models |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; latent; reward; value |
| Horizon / rollout | short imagined plans plus value bootstrap; short imagined latent trajectories in MPC |
| Evaluation / downstream | control success/return across tasks; online MPC |
| Dataset | 104-task benchmark reported |
| Uncertainty | value ensemble; no generic calibrated transition guarantee |
| Planning đã xác minh | online model predictive control |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | PDF methods/evaluation; §3–4 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: task-oriented predictive representation. Giới hạn: privileged state settings do not establish visual inference. Liên quan MedicalWorldModel: evaluate prediction through meaningful costs.

<a id="g10"></a>

## G10 — SlotFormer: Unsupervised Visual Dynamics Simulation with Object-Centric Models

**VERIFIED — hồ sơ nguồn:** Ziyi Wu; Nikita Dvornik; Klaus Greff; Thomas Kipf; Animesh Garg. 2023, ICLR; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://openreview.net/pdf?id=TFbwV6I0VLg). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | object interactions |
| Observation → state | video prefix → temporally aligned object slots |
| Loại state / thông tin suy ra | latent object slots, inferred; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none for passive prediction; candidate actions in planning task |
| Transition | autoregressive slot dynamics |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future slots and decoded objects |
| Horizon / rollout | multi-step; exact horizon task-dependent; autoregressive future slots |
| Evaluation / downstream | video; future VQA; goal-conditioned planning; reasoning and planning |
| Dataset | CLEVRER; PHYRE (paper task suite) |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | goal-conditioned planning tested |
| Project/repository | [official](https://github.com/pairlab/SlotFormer) |
| Mức đọc / vị trí | PDF methods; evaluation overview; §3 and downstream tasks |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: object-level rollout reusable downstream. Giới hạn: slots may swap/collapse; not guaranteed anatomical entities. Liên quan MedicalWorldModel: anatomy-centric forecast has prior CV basis.

<a id="g11"></a>

## G11 — DINO-WM: World Models on Pre-trained Visual Features enable Zero-shot Planning

**VERIFIED — hồ sơ nguồn:** Gaoyue Zhou; Hengkai Pan; Yann LeCun; Lerrel Pinto. 2025, ICML; PMLR 267:79115–79135; Published. DOI: UNKNOWN; arXiv: [2411.04983](https://arxiv.org/abs/2411.04983). [Nguồn chính](https://proceedings.mlr.press/v267/zhou25t.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | robot/object manipulation |
| Observation → state | image history; proprioception/actions → frozen DINOv2 patch features |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | recorded controls |
| Transition | predict future patch features |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; goal-relevant future embeddings |
| Horizon / rollout | autoregressive; MPC and open-loop ablated; iterated feature prediction under candidate action sequences |
| Evaluation / downstream | goal/control success over six environments; image-goal planning |
| Dataset | Maze; Wall; PushT; Reach; Rope; Granular |
| Uncertainty | deterministic feature prediction; calibration not established |
| Planning đã xác minh | CEM MPC; GD/open-loop ablations |
| Project/repository | [official](https://dino-wm.github.io) |
| Mức đọc / vị trí | full-text methods/evaluation/appendix; §3–4; Appendix A.5.3 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: planning without pixel decoder training. Giới hạn: feature distance can miss critical small details. Liên quan MedicalWorldModel: test reuse of predictive state without requiring pixel output.

<a id="g12"></a>

## G12 — V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Planning

**VERIFIED — hồ sơ nguồn:** Mido Assran (Mahmoud Assran trong PDF); Adrien Bardes; David Fan; Quentin Garrido; Russell Howes; Mojtaba Komeili; Matthew Muckley; Ammar Rizvi; Claire Roberts; Koustuv Sinha; Artem Zholus; Sergio Arnaud; Abha Gejji; Ada Martin; Francois Robert Hogan; Daniel Dugas; Piotr Bojanowski; Vasil Khalidov; Patrick Labatut; Francisco Massa; Marc Szafraniec; Kapil Krishnakumar; Yong Li; Xiaodong Ma; Sarath Chandar; Franziska Meier; Yann LeCun; Michael Rabbat; Nicolas Ballas. 2025, arXiv; venue peer-reviewed UNKNOWN; Preprint verified. DOI: UNKNOWN; arXiv: [2506.09985v1](https://arxiv.org/abs/2506.09985v1). [Nguồn chính](https://arxiv.org/abs/2506.09985). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | video representation + robot AC model |
| Observation → state | pretraining video; AC images + end-effector state/actions → frozen visual patch features; robot state |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | AC uses robot controls; pretraining no action |
| Transition | masked prediction then causal action-conditioned latent prediction |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future feature patches; goal proximity |
| Horizon / rollout | training rollout T=2; teacher-forced T=15; MPC task-dependent; masked pretraining; action-conditioned recursive prediction for MPC |
| Evaluation / downstream | video understanding and real robot goal tasks; representation reuse and image-goal MPC |
| Dataset | web video; DROID; two robot labs |
| Uncertainty | no calibrated belief distribution established |
| Planning đã xác minh | CEM MPC for V-JEPA 2-AC |
| Project/repository | [official](https://github.com/facebookresearch/vjepa2) |
| Mức đọc / vị trí | full-text §3 and §4.3; §3 action-conditioned model; §4.3 limitations |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: separates broad representation from action grounding. Giới hạn: camera sensitivity; long-horizon errors; staged subgoals. Liên quan MedicalWorldModel: masked pretraining alone is not prefix forecasting.

<a id="g13"></a>

## G13 — Genie: Generative Interactive Environments

**VERIFIED — hồ sơ nguồn:** Jake Bruce; Michael D Dennis; Ashley Edwards; Jack Parker-Holder; Yuge Shi; Edward Hughes; Matthew Lai; Aditi Mavalankar; Richie Steigerwald; Chris Apps; Yusuf Aytar; Sarah Maria Elisabeth Bechtle; Feryal Behbahani; Stephanie C.Y. Chan; Nicolas Heess; Lucy Gonzalez; Simon Osindero; Sherjil Ozair; Scott Reed; Jingwei Zhang; Konrad Zolna; Jeff Clune; Nando De Freitas; Satinder Singh; Tim Rocktäschel. 2024, ICML; PMLR 235:4603–4623; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://proceedings.mlr.press/v235/bruce24a.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | interactive game-like video |
| Observation → state | unlabeled videos / initial image → video tokens + latent action codes |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | inferred discrete latent action |
| Transition | conditioned token dynamics |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; next video tokens |
| Horizon / rollout | interactive autoregressive rollout; latent-action autoregressive video |
| Evaluation / downstream | controllability; policy-transfer evidence; video quality; interactive learned environments |
| Dataset | internet platform-game videos |
| Uncertainty | stochastic generation |
| Planning đã xác minh | interactive simulation; not universal physical planner |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | proceedings metadata/abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: learn action vocabulary without action labels. Giới hạn: latent action not identified physical command. Liên quan MedicalWorldModel: pose/action distinction is indispensable.

<a id="g14"></a>

## G14 — Learning Interactive Real-World Simulators

**VERIFIED — hồ sơ nguồn:** Sherry Yang; Yilun Du; Kamyar Ghasemipour; Jonathan Tompson; Leslie Kaelbling; Dale Schuurmans; Pieter Abbeel. 2024, ICLR; Published. DOI: UNKNOWN; arXiv: [2310.06114](https://arxiv.org/abs/2310.06114). [Nguồn chính](https://openreview.net/pdf/ebbd0d77e65c2e2ffb1eef300c8c55e4f2f27c86.pdf). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | interactive real-world video / UniSim |
| Observation → state | video history; text or low-level controls → video generative latent/history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | high-level instructions and low-level action |
| Transition | conditional video generation chained through time |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future observations |
| Horizon / rollout | multi-step; numeric horizon UNKNOWN; conditioned recurrent video generation |
| Evaluation / downstream | sim-trained policy transfer in studied tasks; simulation for RL/planning |
| Dataset | mixed web and robot datasets |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | RL trained in simulation; task-specific transfer |
| Project/repository | [official](https://universal-simulator.github.io) |
| Mức đọc / vị trí | metadata + abstract; ICLR published PDF; abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: unified high/low-level conditions. Giới hạn: distribution coverage; limited transfer is not general physics proof. Liên quan MedicalWorldModel: data grounding needed for medical actions.

<a id="g15"></a>

## G15 — Navigation World Models

**VERIFIED — hồ sơ nguồn:** Amir Bar; Gaoyue Zhou; Danny Tran; Trevor Darrell; Yann LeCun. 2025, CVPR:15791–15801; Published. DOI: UNKNOWN; arXiv: [2412.03572](https://arxiv.org/abs/2412.03572). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2025/html/Bar_Navigation_World_Models_CVPR_2025_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | egocentric navigation |
| Observation → state | image prefix + motion and elapsed time → visual latent history; no explicit metric map |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | relative translation/yaw; Δt |
| Transition | conditional video model |
| Thời gian; future quantity | seconds; future egocentric observations |
| Horizon / rollout | 8 steps ×0.25 s for planning; 4 s video evaluation; autoregressive view generation; goal MPC/ranking |
| Evaluation / downstream | ATE/RPE; candidate trajectory ranking; image metrics; image-goal navigation |
| Dataset | RECON; TartanDrive; SCAND; HuRoN; Ego4D; GoStanford |
| Uncertainty | generative sampling; calibration UNKNOWN |
| Planning đã xác minh | CEM; rank NoMaD trajectories |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text methods/evaluation; Planning implementation; navigation evaluation |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: trajectory metrics complement perceptual quality. Giới hạn: image-goal cost may ignore unseen obstacles. Liên quan MedicalWorldModel: queryable view predictions require explicit information boundary.

<a id="g16"></a>

## G16 — DriveDreamer: Towards Real-world-driven World Models for Autonomous Driving

**VERIFIED — hồ sơ nguồn:** Xiaofeng Wang; Zheng Zhu; Guan Huang; Xinze Chen; Jiagang Zhu; Jiwen Lu. 2024, ECCV; Published. DOI: UNKNOWN; arXiv: [2309.09777](https://arxiv.org/abs/2309.09777). [Nguồn chính](https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/6416_ECCV_2024_paper.php). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | autonomous driving |
| Observation → state | driving video; structured road/box conditions → latent driving scene conditioned on structure |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | driving conditions/actions |
| Transition | structured conditional video dynamics |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; video; driving actions |
| Horizon / rollout | multi-frame; numeric UNKNOWN; conditioned video generation; long recursive mechanism UNKNOWN from abstract |
| Evaluation / downstream | video fidelity and driving-action prediction; driving simulation |
| Dataset | nuScenes |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | not established by abstract-level evidence |
| Project/repository | [official](https://drivedreamer.github.io) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: structured controls constrain image generation. Giới hạn: future supplied layouts must not be mistaken for forecasted state. Liên quan MedicalWorldModel: distinguish known future acquisition query from unknown future anatomy.

<a id="g17"></a>

## G17 — Vista: A Generalizable Driving World Model with High Fidelity and Versatile Controllability

**VERIFIED — hồ sơ nguồn:** Shenyuan Gao; Jiazhi Yang; Li Chen; Kashyap Chitta; Yihang Qiu; Andreas Geiger; Jun Zhang; Hongyang Li. 2024, NeurIPS; Published. DOI: [10.52202/079017-2906](https://doi.org/10.52202/079017-2906); arXiv: [2405.17398](https://arxiv.org/abs/2405.17398). [Nguồn chính](https://proceedings.neurips.cc/paper_files/paper/2024/hash/a6a066fb44f2fe0d36cf740c873b8890-Abstract-Conference.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | driving video |
| Observation → state | recent frames; motion conditions → video latent/history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | trajectory; command; angle/speed; goal |
| Transition | conditional denoising; history-based extension |
| Thời gian; future quantity | 10 Hz video; seconds; future video; variance-derived action score |
| Horizon / rollout | 15 s qualitative long rollout; quantitative task-dependent; iterative future video chunks; candidate-trajectory reward sampling |
| Evaluation / downstream | control consistency; reward versus perturbed trajectories; FVD; simulation/action assessment |
| Dataset | OpenDV-YouTube; nuScenes; Waymo |
| Uncertainty | conditional sample variance; calibration not established |
| Planning đã xác minh | reward assessment evaluated; MPC listed as possible use |
| Project/repository | [official](https://github.com/OpenDriveLab/Vista) |
| Mức đọc / vị trí | full-text methods/evaluation/appendix; §3.3; §4.3; Appendix A/C/D |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: uncertainty used as action-score signal. Giới hạn: low variance is not correctness or safety; MPC suggested not demonstrated here. Liên quan MedicalWorldModel: validate uncertainty against independent endpoint.

<a id="g18"></a>

## G18 — Learning to Simulate Complex Physics with Graph Networks

**VERIFIED — hồ sơ nguồn:** Alvaro Sanchez-Gonzalez; Jonathan Godwin; Tobias Pfaff; Rex Ying; Jure Leskovec; Peter Battaglia. 2020, ICML; PMLR119:8459–8468; Published. DOI: UNKNOWN; arXiv: [2002.09405](https://arxiv.org/abs/2002.09405). [Nguồn chính](https://proceedings.mlr.press/v119/sanchez-gonzalez20a.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | particle physical dynamics |
| Observation → state | particle trajectories and material/boundary information → positions, motion history, particle attributes |
| Loại state / thông tin suy ra | explicit geometric/physical input state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | boundary/forcing conditions |
| Transition | message passing predicts acceleration; numerical integration |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future particle states |
| Horizon / rollout | thousands of steps reported; learned acceleration followed by numerical integration |
| Evaluation / downstream | state rollout error and generalization; physical simulation |
| Dataset | simulated fluids/solids/granular systems |
| Uncertainty | deterministic; training noise improves robustness |
| Planning đã xác minh | not primary objective |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Paper simulation framework and rollout results |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: direct state-based multi-step evaluation. Giới hạn: privileged particle states; visual inverse problem unsolved. Liên quan MedicalWorldModel: geometry must be inferred and independently validated.

<a id="g19"></a>

## G19 — PhysGaussian: Physics-Integrated 3D Gaussians for Generative Dynamics

**VERIFIED — hồ sơ nguồn:** Tianyi Xie; Zeshun Zong; Yuxing Qiu; Xuan Li; Yutao Feng; Yin Yang; Chenfanfu Jiang. 2024, CVPR:4389–4398; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2024/html/Xie_PhysGaussian_Physics-Integrated_3D_Gaussians_for_Generative_Dynamics_CVPR_2024_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | 3D material dynamics and rendering |
| Observation → state | multiview images; assigned physical parameters → 3D Gaussians linked to continuum state |
| Loại state / thông tin suy ra | geometric and physical; partly specified rather than learned; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | external force/boundary settings |
| Transition | material-point physics; deformation and rendering |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; deformed geometry and images |
| Horizon / rollout | physics integration; numeric horizon UNKNOWN; material-point simulation and rendering |
| Evaluation / downstream | dynamic rendering/physical scenarios; render physical simulation |
| Dataset | reconstructed scenes; material simulations |
| Uncertainty | UNKNOWN |
| Planning đã xác minh | not primary objective |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: explicit physical state under assumptions. Giới hạn: material identification from images not automatically solved. Liên quan MedicalWorldModel: tissue mechanics needs constitutive and contact evidence.

<a id="g20"></a>

## G20 — 4D Gaussian Splatting for Real-Time Dynamic Scene Rendering

**VERIFIED — hồ sơ nguồn:** Guanjun Wu; Taoran Yi; Jiemin Fang; Lingxi Xie; Xiaopeng Zhang; Wei Wei; Wenyu Liu; Qi Tian; Xinggang Wang. 2024, CVPR:20310–20320; Published. DOI: UNKNOWN; arXiv: [2310.08528](https://arxiv.org/abs/2310.08528). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2024/html/Wu_4D_Gaussian_Splatting_for_Real-Time_Dynamic_Scene_Rendering_CVPR_2024_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | dynamic scene reconstruction |
| Observation → state | observed dynamic views/timestamps → 4D Gaussian scene representation |
| Loại state / thông tin suy ra | geometric scene representation; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | camera query; not environmental intervention |
| Transition | time-indexed deformation/rendering |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; novel-view render |
| Horizon / rollout | observed temporal domain; future forecasting UNKNOWN; query time-conditioned scene deformation; forecasting not established |
| Evaluation / downstream | rendering fidelity/speed; reconstruction/rendering |
| Dataset | dynamic scene datasets; exact extraction UNKNOWN |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | no demonstrated control |
| Project/repository | [official](https://github.com/hustvl/4DGaussians) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: efficient dynamic representation. Giới hạn: held-out view/time interpolation is not future dynamics validation. Liên quan MedicalWorldModel: negative control for calling 4D reconstruction a WM.

<a id="g21"></a>

## G21 — GeoWorld: Geometric World Models

**VERIFIED — hồ sơ nguồn:** Zeyu Zhang; Danning Li; Ian Reid; Richard Hartley. 2026, CVPR:30952–30963; Published. DOI: UNKNOWN; arXiv: [2602.23058](https://arxiv.org/abs/2602.23058). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_GeoWorld_Geometric_World_Models_CVPR_2026_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | instructional procedure planning |
| Observation → state | video procedure observations → hyperbolic latent hierarchy |
| Loại state / thông tin suy ra | latent hyperbolic geometry; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | procedure action sequence |
| Transition | latent dynamics for procedure plans |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future procedural states/actions |
| Horizon / rollout | 3/4-step task planning; latent procedural-step prediction; recursive mechanism UNKNOWN from abstract |
| Evaluation / downstream | procedure success metrics; procedure planning |
| Dataset | CrossTask; COIN |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | procedure planning |
| Project/repository | [official](https://steve-zeyu-zhang.github.io/GeoWorld) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: geometric latent organization. Giới hạn: geometric means hyperbolic representation, not metric 3D tissue. Liên quan MedicalWorldModel: do not equate latent geometry with anatomy.

<a id="g22"></a>

## G22 — Cosmos World Foundation Model Platform for Physical AI

**VERIFIED — hồ sơ nguồn:** NVIDIA: Niket Agarwal et al. (danh sách rút gọn; toàn bộ contributors tại arXiv). 2025, Technical report; Technical report / preprint. DOI: UNKNOWN; arXiv: [2501.03575v3](https://arxiv.org/abs/2501.03575v3). [Nguồn chính](https://research.nvidia.com/publication/2025-01_cosmos-world-foundation-model-platform-physical-ai). Technical report; original v1 January 2025, metadata/abstract v3 July 2025; peer-reviewed publication UNKNOWN.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | general physical-AI video |
| Observation → state | video; text and other task conditions → tokenized/generative visual representation |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | depends on downstream adaptation |
| Transition | video generation/prediction platform |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future video |
| Horizon / rollout | model-specific; numeric UNKNOWN; conditional video generation; model-dependent rollout |
| Evaluation / downstream | video and downstream platform demonstrations; pretrain then adapt |
| Dataset | large video corpus; licenses task-specific |
| Uncertainty | generative sampling; calibration UNKNOWN |
| Planning đã xác minh | downstream-dependent |
| Project/repository | [official](https://github.com/NVIDIA/Cosmos) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: foundation-model tooling and scale. Giới hạn: platform availability does not validate a medical simulator. Liên quan MedicalWorldModel: transfer capabilities; not blanket physics/clinical validity.

<a id="g23"></a>

## G23 — DreamDojo: A Generalist Robot World Model from Large-Scale Human Videos

**VERIFIED — hồ sơ nguồn:** Shenyuan Gao; William Liang; Kaiyuan Zheng; Ayaan Malik; Seonghyeon Ye; Sihyun Yu; Wei-Cheng Tseng; Yuzhu Dong; Kaichun Mo; Chen-Hsuan Lin; Qianli Ma; Seungjun Nah; Loic Magne; Jiannan Xiang; Yuqi Xie; Ruijie Zheng; Dantong Niu; You Liang Tan; K. R. Zentner; George Kurian; Suneel Indupuru; Pooya Jannaty; Jinwei Gu; Jun Zhang; Jitendra Malik; Pieter Abbeel; Ming-Yu Liu; Yuke Zhu; Joel Jang; Linxi Jim Fan. 2026, ICML 2026 theo official repository; proceedings record UNKNOWN; Accepted/venue reported by authors; version read is preprint. DOI: UNKNOWN; arXiv: [2602.06949v1](https://arxiv.org/abs/2602.06949v1). [Nguồn chính](https://arxiv.org/abs/2602.06949). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | robot manipulation simulator |
| Observation → state | human videos then target-robot trajectories → video latent history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | latent proxy actions pretraining; robot action post-training |
| Transition | conditional video dynamics; distilled autoregressive chunks |
| Thời gian; future quantity | seconds; future video and task success |
| Horizon / rollout | ~80 s policy-evaluation rollout; >1 min interactive demo; causal short-chunk generation / distilled streaming |
| Evaluation / downstream | real-vs-sim policy rank/correlation; physical policy steering; policy evaluation and action proposal selection |
| Dataset | DreamDojo-HV; GR-1; AgiBot; G1 |
| Uncertainty | sampling, but no calibrated success probabilities |
| Planning đã xác minh | select proposals using imagined video and external value model |
| Project/repository | [official](https://github.com/NVIDIA/DreamDojo) |
| Mức đọc / vị trí | full-text §3–4.7 and limitations; §4.7; §5; Table6 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: external policy rank agreement beyond video quality. Giới hạn: overestimates absolute success; uncommon actions and multiview limitations. Liên quan MedicalWorldModel: medical simulator must reproduce failures, not only rank.

<a id="g24"></a>

## G24 — Dyna-style planning with linear function approximation and prioritized sweeping

**VERIFIED — hồ sơ nguồn:** Richard S. Sutton; Csaba Szepesvári; Alborz Geramifard; Michael Bowling. 2008, UAI; PMLR R6:528–536; Published; PMLR reissue 2024. DOI: UNKNOWN; arXiv: [1206.3285](https://arxiv.org/abs/1206.3285). [Nguồn chính](https://proceedings.mlr.press/r6/sutton08a.html). Original UAI 2008; arXiv upload 2012; PMLR reissue 2024 không đổi canonical year

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | model-based reinforcement learning |
| Observation → state | environment features and transitions → linear feature state/model |
| Loại state / thông tin suy ra | observed/engineered feature state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | environment action |
| Transition | linear model → imagined transitions → value updates |
| Thời gian; future quantity | environment steps; future features/rewards/value |
| Horizon / rollout | imaginary transition updates; horizon details UNKNOWN; imaginary model transitions used in value updates |
| Evaluation / downstream | convergence analysis; Mountain Car/Boyan Chain; online value/control learning |
| Dataset | Mountain Car; Boyan Chain |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | Dyna-style imagined updates, prioritized sweeping |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: mô hình tạo experience để học, có trước pixel world models. Giới hạn: feature/state setup khác inference từ ảnh. Liên quan MedicalWorldModel: world model không cần neural visual generator.

<a id="g25"></a>

## G25 — Deep Predictive Coding Networks for Video Prediction and Unsupervised Learning

**VERIFIED — hồ sơ nguồn:** William Lotter; Gabriel Kreiman; David Cox. 2017, ICLR; Published; author lab confirms ICLR 2017. DOI: UNKNOWN; arXiv: [1605.08104v5](https://arxiv.org/abs/1605.08104v5). [Nguồn chính](https://arxiv.org/abs/1605.08104v5). ICLR status: https://klab.tch.harvard.edu/resources/lotteretal_prednet.html ; original arXiv 2016, v5 2017

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | visual predictive representation |
| Observation → state | video history → recurrent representations and prediction-error hierarchy |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | recurrent frame prediction |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future frame; reusable representation |
| Horizon / rollout | next-frame; extended rollout horizon UNKNOWN in extraction; recurrent next-frame inference; extended rollout UNKNOWN |
| Evaluation / downstream | pixel prediction; object parameter/steering readout; unsupervised visual representation |
| Dataset | synthetic objects; car-mounted video |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | không có planning được xác minh |
| Project/repository | [official](https://coxlab.github.io/prednet/) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: nối prediction và representation usefulness trước frontier gần đây. Giới hạn: readout tốt chưa chứng minh simulator/planning. Liên quan MedicalWorldModel: baseline lineage: predictive latent không tự interpretable.

<a id="g26"></a>

## G26 — Revisiting Feature Prediction for Learning Visual Representations from Video

**VERIFIED — hồ sơ nguồn:** Adrien Bardes; Quentin Garrido; Jean Ponce; Xinlei Chen; Michael Rabbat; Yann LeCun; Mahmoud Assran; Nicolas Ballas. 2024, arXiv; peer-reviewed venue UNKNOWN; Preprint verified. DOI: UNKNOWN; arXiv: [2404.08471v1](https://arxiv.org/abs/2404.08471v1). [Nguồn chính](https://arxiv.org/abs/2404.08471v1). V-JEPA 2024; không gán ECCV khi proceedings chưa xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | representation-centric video prediction |
| Observation → state | visible video regions → video features |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | masked feature prediction |
| Thời gian; future quantity | within clip; actual-time transition UNKNOWN; features in masked regions; downstream representations |
| Horizon / rollout | masked clip context; temporal rollout not established in extraction; masked feature prediction; no temporal rollout verified |
| Evaluation / downstream | frozen image/video task readouts; learn reusable visual representation |
| Dataset | public video datasets; evaluation Kinetics/SSv2/ImageNet |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | không có planning được xác minh |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: feature prediction không cần pixel reconstruction. Giới hạn: masking có thể thấy future context; không automatic prefix forecast. Liên quan MedicalWorldModel: tách representation learning khỏi temporal dynamics contract.

<a id="k01"></a>

## K01 — Challenging Common Assumptions in the Unsupervised Learning of Disentangled Representations

**VERIFIED — hồ sơ nguồn:** Francesco Locatello; Stefan Bauer; Mario Lucic; Gunnar Raetsch; Sylvain Gelly; Bernhard Schölkopf; Olivier Bachem. 2019, ICML; PMLR97:4114–4124; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://proceedings.mlr.press/v97/locatello19a.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | representation identification theory |
| Observation → state | unsupervised samples → latent factors |
| Loại state / thông tin suy ra | latent factors; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | N/A |
| Transition | N/A: not a dynamics model |
| Thời gian; future quantity | N/A: identifiability theory; N/A |
| Horizon / rollout | N/A; N/A: representation-identifiability paper, not future simulator |
| Evaluation / downstream | theoretical identifiability; benchmark study; test disentanglement assumptions |
| Dataset | seven representation datasets |
| Uncertainty | N/A |
| Planning đã xác minh | N/A |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: inductive biases/supervision necessary under theorem setting. Giới hạn: does not prove every medically supervised latent uninterpretable. Liên quan MedicalWorldModel: require external semantics tests.

<a id="k02"></a>

## K02 — Forecasting Treatment Responses Over Time Using Recurrent Marginal Structural Networks

**VERIFIED — hồ sơ nguồn:** Bryan Lim. 2018, NeurIPS31; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://papers.nips.cc/paper_files/paper/2018/hash/56e6a93212e4482d99c84a639d254b67-Abstract.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | causal longitudinal treatment response |
| Observation → state | longitudinal covariates, treatments, outcomes → recurrent covariate history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | planned treatment sequence |
| Transition | propensity weighting plus sequence model |
| Thời gian; future quantity | treatment steps; treatment-response trajectory |
| Horizon / rollout | multiple treatment steps; weighted recurrent treatment-response prediction |
| Evaluation / downstream | known-effects PK-PD simulation; policy shift; adjust time-dependent confounding |
| Dataset | simulated tumor growth |
| Uncertainty | identification distinct from uncertainty |
| Planning đã xác minh | response forecasts, not automatically evaluated treatment policy |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | official abstract + original PDF; time-dependent confounding; causal assumptions and simulation |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: distinguishes prediction from identified intervention. Giới hạn: requires assumptions/data, not transferable by adding action input. Liên quan MedicalWorldModel: do not infer do-effect from observational care.

<a id="m01"></a>

## M01 — Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model

**VERIFIED — hồ sơ nguồn:** Haojun Jiang; Zhenguo Sun; Ning Jia; Meng Li; Yu Sun; Shaqi Luo; Shiji Song; Gao Huang. 2024, MICCAI; LNCS15001:190–199; Published. DOI: [10.1007/978-3-031-72378-0_18](https://doi.org/10.1007/978-3-031-72378-0_18); arXiv: [2406.13165](https://arxiv.org/abs/2406.13165). [Nguồn chính](https://papers.miccai.org/miccai-2024/118-Paper0053.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | B: echocardiography acquisition |
| Observation → state | ultrasound image; tracked probe motion → cardiac plane features |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | measured relative motion; proposed guidance |
| Transition | predict nearby plane feature; refine guidance |
| Thời gian; future quantity | spatial pose change; elapsed-time horizon UNKNOWN; target-plane displacement |
| Horizon / rollout | one imagined correction; reactive updates possible; one imagined guidance correction reported |
| Evaluation / downstream | navigation displacement errors; probe guidance |
| Dataset | 110 train scans; 15 test per source; public release UNKNOWN |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | one-step imagined guidance refinement; not validated long-horizon MPC |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | official abstract, paper information and author response; Abstract; author response items1,2,7; code/data N/A |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: world-model framing in medicine before 2025. Giới hạn: offline guidance error does not establish novice clinical success. Liên quan MedicalWorldModel: invalidates broad first-medical-WM claims.

<a id="m02"></a>

## M02 — EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance

**VERIFIED — hồ sơ nguồn:** Yang Yue; Yulin Wang; Haojun Jiang; Pan Liu; Shiji Song; Gao Huang. 2025, CVPR; Published. DOI: UNKNOWN; arXiv: [2504.13065v1](https://arxiv.org/abs/2504.13065v1). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2025/html/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | B: cardiac view acquisition |
| Observation → state | image pairs; tracked poses; historical image-pose sequence → spatial and motion-aware features |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | relative measured 6-DoF probe transform |
| Transition | target-feature prediction plus masked spatial prediction |
| Thời gian; future quantity | pose-query spatial transition; physical-time forecast horizon UNKNOWN; visual target feature; downstream guidance vector |
| Horizon / rollout | pairwise pretraining; historical sequential guidance ≠ free rollout; pairwise predictive pretraining; real observed history in guidance |
| Evaluation / downstream | translation/rotation guidance errors; probe guidance |
| Dataset | 356 scans; 284 train/72 test; release UNKNOWN |
| Uncertainty | latent relationship variable; no calibrated predictive uncertainty demonstrated |
| Planning đã xác minh | supervised guidance; closed-loop planning not established |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §3–5 and appendix; PDF visual inspection p4; §4.1–4.2; sequential protocol; Appendix dataset |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: motion conditioning and memory improve task representation. Giới hạn: no proved clinical latent or calibrated long-horizon simulator. Liên quan MedicalWorldModel: strong prior art against merely adding pose or history.

<a id="m03"></a>

## M03 — Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound

**VERIFIED — hồ sơ nguồn:** Siqi Fan; Mingcong Chen; Ran Liu; Zixuan Yang; Xiaoyu Fu; Xiaoqing Gao; Yunhui Liu; Hongbin Liu. 2026, arXiv; peer-reviewed venue UNKNOWN; Preprint. DOI: UNKNOWN; arXiv: [2607.21918v2](https://arxiv.org/abs/2607.21918v2). [Nguồn chính](https://arxiv.org/abs/2607.21918v2). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | B: robotic neck ultrasound |
| Observation → state | recent images; synchronized measured poses; Δt → image latent/history |
| Loại state / thông tin suy ra | predictive visual latent; no explicit tissue/contact state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | relative pose during learning; discrete motion commands at deployment |
| Transition | conditional future latent; frozen-model policy reward |
| Thời gian; future quantity | seconds; future observation and goal-plane progress |
| Horizon / rollout | 0.5–30 s offset tests; physical trials ≤100 s/goal; time-offset-conditioned prediction; imagined policy learning and real closed-loop evaluation |
| Evaluation / downstream | SSIM/LPIPS; inverse recovery; real goal success 20 trials/task; train goal-guidance policy |
| Dataset | self-collected 20 people; public release UNKNOWN |
| Uncertainty | sampling; no calibration shown |
| Planning đã xác minh | policy learned with model reward; physical closed-loop execution |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §II–IV; Fig4; TableI; TableIV; Discussion |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: real closed-loop evaluation beyond pixels. Giới hạn: force used only in low-level control; not model input; limited local action support. Liên quan MedicalWorldModel: planning transfer is possible but requires grounded data.

<a id="m04"></a>

## M04 — Medical World Model

**VERIFIED — hồ sơ nguồn:** Yijun Yang; Zhao-Yang Wang; Qiuping Liu; Shuwen Sun; Kang Wang; Rama Chellappa; Zongwei Zhou; Alan Yuille; Lei Zhu; Yu-Dong Zhang; Jieneng Chen. 2025, ICCV:8319–8329; Published. DOI: UNKNOWN; arXiv: [2506.02327](https://arxiv.org/abs/2506.02327). [Nguồn chính](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html). arXiv title adds Generative Simulation of Tumor Evolution for Treatment Planning; ICCV title canonical

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: HCC under TACE / MeWM |
| Observation → state | pre-treatment CT; masks; clinical treatment candidates → CT latent; survival-risk representation |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | TACE drug/embolic protocol condition |
| Transition | conditional post-treatment image generation; survival scorer |
| Thời gian; future quantity | post-treatment event; actual per-case delay UNKNOWN; post-CT and predicted survival risk |
| Horizon / rollout | pre→post event; tree search over protocols, not multi-visit validation; protocol-conditioned post-treatment generation + protocol tree search |
| Evaluation / downstream | image quality; radiologist assessment; retrospective treatment agreement/survival; treatment candidate search |
| Dataset | local HCC-TACE pairs; HCC-TACE-Seg |
| Uncertainty | generative sampling; calibrated treatment-effect uncertainty UNKNOWN |
| Planning đã xác minh | tree search with predicted survival scorer |
| Project/repository | [official](https://github.com/scott-yjyang/MeWM) |
| Mức đọc / vị trí | full-text §3 and evaluation/appendix; §3 forward/inverse dynamics; retrospective evaluation |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: explicit planning interface over generated medical futures. Giới hạn: observational agreement does not identify counterfactual treatment benefit. Liên quan MedicalWorldModel: separate computational search from clinical causal utility.

<a id="m05"></a>

## M05 — ImageFlowNet: Forecasting Multiscale Image-Level Trajectories of Disease Progression with Irregularly-Sampled Longitudinal Medical Images

**VERIFIED — hồ sơ nguồn:** Chen Liu; Ke Xu; Liangbo L. Shen; Guillaume Huguet; Zilong Wang; Alexander Tong; Danilo Bzdok; Jay Stewart; Jay C. Wang; Lucian V. Del Priore; Smita Krishnaswamy. 2025, ICASSP; Published. DOI: [10.1109/ICASSP49660.2025.10890535](https://doi.org/10.1109/ICASSP49660.2025.10890535); arXiv: [2406.14794v6](https://arxiv.org/abs/2406.14794v6). [Nguồn chính](https://doi.org/10.1109/ICASSP49660.2025.10890535). Canonical ICASSP 2025 short version; methods dùng extended arXiv v6. DOI/title/authors corroborated by Duke institutional record and official repository; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: retinal/MS/GBM image trajectories |
| Observation → state | prior image(s); actual visit intervals → multiscale visual latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | ODE/SDE latent flow; patient history adaptation |
| Thời gian; future quantity | irregular clinical intervals; future image and derived lesion geometry |
| Horizon / rollout | arbitrary Δt query; multi-visit trajectories; dense GT UNKNOWN; continuous-time latent integration/query; history adaptation uses available past |
| Evaluation / downstream | PSNR/SSIM; Dice/HD; adaptation and stochastic ablations; image-level forecast |
| Dataset | retinal GA; ISBI MS; LUMIERE |
| Uncertainty | SDE sampled futures; calibration not established |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/KrishnaswamyLab/ImageFlowNet) |
| Mức đọc / vị trí | full-text methods/evaluation/Appendix D,F; §5.5–5.6; AppendixD.1/D.3 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: continuous-time, multiscale, patient-specific, stochastic prior art. Giới hạn: retinal anchor/crop chosen from full series; strict prefix needs re-audit. Liên quan MedicalWorldModel: not novel to add continuous time or multi-hypothesis.

<a id="m06"></a>

## M06 — Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction

**VERIFIED — hồ sơ nguồn:** Qinghui Liu; Elies Fuster-Garcia; Ivar Thokle Hovden; Bradley J. MacIntosh; Edvard O. S. Grødem; Petter Brandal; Carles Lopez-Mateu; Donatas Sederevičius; Karoline Skogen; Till Schellhorn; Atle Bjørnerud; Kyrre Eeg Emblem. 2025, IEEE Transactions on Medical Imaging 44(6):2449–2462; Published. DOI: [10.1109/TMI.2025.3533038](https://doi.org/10.1109/TMI.2025.3533038); arXiv: [2309.05406v5](https://arxiv.org/abs/2309.05406v5). [Nguồn chính](https://doi.org/10.1109/TMI.2025.3533038). Canonical TMI 2025; arXiv v5 dùng cho methods. DOI metadata corroborated by UPV institutional record and PubMed 40031286; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: glioma / TaDiff |
| Observation → state | past MRI/masks; time; recorded treatment → image/lesion latent conditioned on history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | observed treatment condition |
| Transition | conditional stochastic future generation |
| Thời gian; future quantity | irregular clinical visits; MRI and tumor segmentation |
| Horizon / rollout | longitudinal future query; interpolation/reconstruction training also used; time/treatment-conditioned diffusion sampling; temporal target selection |
| Evaluation / downstream | image and lesion metrics; external MRI evaluation; forecast under treatment context |
| Dataset | local 23 patients/225 exams; external LUMIERE subset |
| Uncertainty | multiple diffusion samples; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/samleoqh/TaDiff-Net) |
| Mức đọc / vị trí | full-text methods; §IV-A/B evaluation; §IV-A 18/5 patient split; external labels; training sampling |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: joint future MRI and tumor burden. Giới hạn: external automated masks not expert ground truth; observational treatment not causal. Liên quan MedicalWorldModel: strong treatment-aware baseline; label provenance critical.

<a id="m07"></a>

## M07 — Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation

**VERIFIED — hồ sơ nguồn:** Hao Chen; Rui Yin; Yifan Chen; Qi Chen; Chao Li. 2026, ICLR; Published. DOI: UNKNOWN; arXiv: [2512.09185v4](https://arxiv.org/abs/2512.09185v4). [Nguồn chính](https://openreview.net/pdf/a1558b2e7d9494789fdd3057059dfbe2add8737e.pdf). v4 2026-06-17; ICLR publication verified in camera-ready header

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: neurodegeneration / Δ-LFM |
| Observation → state | MRI and visit time/history → patient-specific ordered latent trajectory |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | time-conditioned latent flow; ArcRank constraints |
| Thời gian; future quantity | months/years; future MRI and regional change |
| Horizon / rollout | irregular longitudinal queries; numeric clinical range UNKNOWN; patient trajectory-conditioned generation at target time |
| Evaluation / downstream | SSIM/PSNR; regional MAE and ΔRMAE; individual future imaging |
| Dataset | ADNI; OASIS-3; AIBL |
| Uncertainty | generative variability; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | camera-ready metadata; full arXiv methods/evaluation; §3; §4.1; regional-change experiments |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: patient-specific direction and anatomical change evaluation. Giới hạn: monotonic ordering not generally valid for treated lesions. Liên quan MedicalWorldModel: regional/patient-specific states already studied.

<a id="m08"></a>

## M08 — Brain Latent Progression: Individual-based spatiotemporal disease progression on 3D Brain MRIs via latent diffusion

**VERIFIED — hồ sơ nguồn:** Lemuel Puglisi; Daniel C. Alexander; Daniele Ravì. 2025, Medical Image Analysis 106:103734; Published. DOI: [10.1016/j.media.2025.103734](https://doi.org/10.1016/j.media.2025.103734); arXiv: [2502.08560v2](https://arxiv.org/abs/2502.08560v2). [Nguồn chính](https://doi.org/10.1016/j.media.2025.103734). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Canonical author metadata lists Puglisi, Alexander, Ravì; ADNI/AIBL study-group acknowledgement is not expanded as additional named authors.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: brain aging / BrLP |
| Observation → state | baseline MRI; metadata; earlier regional volumes → MRI latent plus predicted regional covariates |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none; cognitive-status condition is not treatment |
| Transition | auxiliary regional trajectory + conditional generation; latent averaging |
| Thời gian; future quantity | years; future MRI and regional anatomy |
| Horizon / rollout | target age queries; longitudinal variants; auxiliary regional progression prediction + conditioned MRI sampling |
| Evaluation / downstream | regional volume error; image metrics; uncertainty-error association; personalized image forecast |
| Dataset | ADNI; OASIS-3; AIBL; external cohort |
| Uncertainty | sample latent dispersion; global/voxel error correlations evaluated |
| Planning đã xác minh | none; clinical-trial use explored as application |
| Project/repository | [official](https://github.com/LemuelPuglisi/BrLP) |
| Mức đọc / vị trí | full-text methods §4; evaluation §5.6; §4.3–4.6; §5.5–5.7 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: regional progression priors and assessed uncertainty. Giới hạn: association with error not calibrated future coverage; subgroup conditioning needs information audit. Liên quan MedicalWorldModel: invalidates broad uncertainty/history/regional novelty.

<a id="m09"></a>

## M09 — Frame forecasting in cine MRI using the PCA respiratory motion model: comparing recurrent neural networks trained online and transformers

**VERIFIED — hồ sơ nguồn:** Michel Pohl; Mitsuru Uesaka; Hiroyuki Takahashi; Kazuyuki Demachi; Ritu Bhusal Chhatkuli. 2026, Computerized Medical Imaging and Graphics 131:102755; Published. DOI: [10.1016/j.compmedimag.2026.102755](https://doi.org/10.1016/j.compmedimag.2026.102755); arXiv: [2410.05882v3](https://arxiv.org/abs/2410.05882v3). [Nguồn chính](https://www.sciencedirect.com/science/article/abs/pii/S0895611126000583). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | A: respiratory cine-MRI |
| Observation → state | past images → optical-flow PCA scores → fixed deformation basis + time-varying coefficients/history |
| Loại state / thông tin suy ra | inferred geometric DVF coefficients; hidden RNN memory predictive; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | direct horizon-specific weight regression then warp |
| Thời gian; future quantity | 0.32 s ETH cadence / 6 Hz OvGU; h≤2.2 s; future DVF and frame |
| Horizon / rollout | h up to 2.2 s; separate model per h; not recursive rollout; separate direct predictor for each horizon; no recursive rollout |
| Evaluation / downstream | PCA error; geometry; image similarity; simple vs learned baselines; latency compensation |
| Dataset | 12 sagittal sequences: ETH Zürich/OvGU |
| Uncertainty | across-run confidence intervals; not predictive calibration |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/pohl-michel/2D-MR-image-prediction) |
| Mức đọc / vị trí | PDF methods/evaluation; visually inspected Table2; §2.2–2.4; Table2; §2.3.3 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: strong PCA+linear/online learned comparison. Giới hạn: small data; stable basis; out-of-plane and scanner shift. Liên quan MedicalWorldModel: learned dynamics must beat simple state under matched context.

<a id="m10"></a>

## M10 — A Latent ODE Approach to Spatiotemporal Modeling of Cine Cardiac MRI

**VERIFIED — hồ sơ nguồn:** David Brüggemann; Ekaterina Krymova; Firat Özdemir; Jochen von Spiczak; Sebastian Kozerke; Samia Mora; Robert Manka; Mathieu Salzmann; Olga V. Demler. 2026, arXiv; venue UNKNOWN; Preprint. DOI: UNKNOWN; arXiv: [2606.26718v1](https://arxiv.org/abs/2606.26718v1). [Nguồn chính](https://arxiv.org/abs/2606.26718). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | A: cardiac shape dynamics |
| Observation → state | full-cycle meshes; patient covariates → posterior latent initial condition inferred from full cycle |
| Loại state / thông tin suy ra | latent of measured/inferred meshes; not identified biological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | phase-aware latent ODE and mesh decoder |
| Thời gian; future quantity | normalized cardiac phase; reconstructed cycle; risk association |
| Horizon / rollout | whole observed cardiac cycle; prefix forecast not established; whole-cycle encoding then ODE cycle reconstruction |
| Evaluation / downstream | mesh reconstruction; physiological features; HF risk model; spatiotemporal representation and risk association |
| Dataset | UK Biobank; project access not assumed |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §3.5, evaluation and AppendixB; §3.5 encoder; downstream Cox analysis |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: geometry-based temporal representation reuse. Giới hạn: full-cycle encoder sees future of a putative prefix task. Liên quan MedicalWorldModel: not evidence of future forecasting despite ODE.

<a id="m11"></a>

## M11 — 4D CardioSynth: Synthesising Dynamic Virtual Heart Populations Through Spatiotemporal Disentanglement

**VERIFIED — hồ sơ nguồn:** Haoran Dou; Jinghan Huang; Arezoo Zakeri; Zherui Zhou; Tingting Mu; Jinming Duan; Alejandro F. Frangi. 2025, MICCAI 2025:3–12; Published. DOI: [10.1007/978-3-032-04947-6_1](https://doi.org/10.1007/978-3-032-04947-6_1); arXiv: UNKNOWN. [Nguồn chính](https://papers.miccai.org/miccai-2025/0004-Paper2701.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Crossref: online 2025-09-21, print 2026; canonical conference year giữ 2025.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | A: virtual cardiac anatomy |
| Observation → state | cardiac mesh sequences; ED anatomy → spatial and temporal generative codes |
| Loại state / thông tin suy ra | mesh-derived geometric latent; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | generate dynamic deformations |
| Thời gian; future quantity | cardiac cycle; virtual full-cycle cardiac meshes |
| Horizon / rollout | one modeled cardiac cycle; shape-conditioned cycle generation; prefix forecast not established |
| Evaluation / downstream | population generalization/specificity/diversity; shape plausibility; virtual cohorts |
| Dataset | biventricular dynamic shape cohort; exact unit count và public access UNKNOWN |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | Không được xác minh trong phần đã đọc |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: anatomical dynamic synthesis. Giới hạn: population synthesis does not establish patient-prefix future accuracy. Liên quan MedicalWorldModel: object/anatomy-centric dynamics are prior art.

<a id="m12"></a>

## M12 — MRI Contrast Enhancement Kinetics World Model

**VERIFIED — hồ sơ nguồn:** Jindi Kong; Yuting He; Cong Xia; Rongjun Ge; Shuo Li. 2026, CVPR:1288–1299; Published. DOI: UNKNOWN; arXiv: [2602.19285](https://arxiv.org/abs/2602.19285). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2026/html/Kong_MRI_Contrast_Enhancement_Kinetics_World_Model_CVPR_2026_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | A/B: contrast-enhancement dynamics |
| Observation → state | noncontrast image; requested seconds post injection → patient-aligned image latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | elapsed time; injection context not arbitrary treatment action |
| Transition | time-conditioned generation; latent spatial/temporal penalties |
| Thời gian; future quantity | seconds after injection; enhanced image at requested time |
| Horizon / rollout | up to 300 s private protocol; sparse measured phases; target-time kinetics query; dense output between sparse observations |
| Evaluation / downstream | PSNR/SSIM/LPIPS/rMSE; adjacent-frame cSSIM; virtual contrast phases |
| Dataset | private abdominal DCE; Duke Breast DCE-MRI |
| Uncertainty | generative samples; kinetic confidence calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §3–4; §3.1; Eq3–4; §4.1.1 cSSIM; Fig6 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: explicit continuous physical-time query. Giới hạn: cSSIM rewards static output; smoothness not validated missing-time kinetics. Liên quan MedicalWorldModel: define biological time separately from denoising time.

<a id="m13"></a>

## M13 — X-WIN: Building Chest Radiograph World Model via Predictive Sensing

**VERIFIED — hồ sơ nguồn:** Zefan Yang; Ge Wang; James Hendler; Mannudeep K. Kalra; Pingkun Yan. 2026, CVPR:6920–6930; Published. DOI: UNKNOWN; arXiv: [2511.14918](https://arxiv.org/abs/2511.14918). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2026/html/Yang_X-WIN_Building_Chest_Radiograph_World_Model_via_Predictive_Sensing_CVPR_2026_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | B: X-ray acquisition/representation |
| Observation → state | CT-derived projections and real radiographs → predictive sensing latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | 3D geometric transform of projection |
| Transition | predict projection features; align real CXR representation |
| Thời gian; future quantity | view domain; physical time N/A; unseen projection features / downstream tasks |
| Horizon / rollout | view transformation; not disease time rollout; CT-derived view/representation prediction; no disease-time rollout verified |
| Evaluation / downstream | linear/few-shot probes; CT reconstruction; representation learning |
| Dataset | CT/CXR data; dataset specifics UNKNOWN in abstract extraction |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: acquisition world modeling outside ultrasound. Giới hạn: synthetic view transition not future disease nor physical device command. Liên quan MedicalWorldModel: B includes non-ultrasound imaging.

<a id="m14"></a>

## M14 — Surgical Vision World Model

**VERIFIED — hồ sơ nguồn:** Saurabh Koju; Saurav Bastola; Prashant Shrestha; Sanskar Amgain; Yash Raj Shrestha; Rudra P. K. Poudel; Binod Bhattarai. 2025, DEMI workshop at MICCAI:1–10; Published workshop chapter. DOI: [10.1007/978-3-032-08009-7_1](https://doi.org/10.1007/978-3-032-08009-7_1); arXiv: [2503.02904](https://arxiv.org/abs/2503.02904). [Nguồn chính](https://doi.org/10.1007/978-3-032-08009-7_1). DEMI workshop chapter verified author page https://saurabhkoju.com.np/publications/ + Springer book; chapter resolver error; methods scope from arXiv. Not MICCAI main. Crossref DOI metadata matched after retry 2026-09-12. Crossref online 2025-10-12 / print 2026; giữ workshop 2025.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | surgical video |
| Observation → state | unlabeled surgical videos → video tokens + inferred latent actions |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | latent action code; not robot command |
| Transition | interactive generative video dynamics |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; next surgical frames |
| Horizon / rollout | multi-frame; numeric UNKNOWN; latent-action autoregressive surgical video |
| Evaluation / downstream | video generation and action controllability; controllable surgery video simulation |
| Dataset | SurgToolLoc2022 |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | UNKNOWN |
| Project/repository | [official](https://github.com/bhattarailab/Surgical-Vision-World-Model) |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: latent-action surgical simulator. Giới hạn: unlabeled code does not identify tissue/action physics. Liên quan MedicalWorldModel: strictly separate visual controllability from intervention.

<a id="m15"></a>

## M15 — SAW: Toward a Surgical Action World Model via Controllable and Scalable Video Generation

**VERIFIED — hồ sơ nguồn:** Sampath Rapuri; Lalithkumar Seenivasan; Dominik Schneider; Roger Soberanis-Mukul; Yufan He; Hao Ding; Jiru Xu; Chenhao Yu; Chenyan Jing; Pengfei Guo; Daguang Xu; Mathias Unberath. 2026, arXiv; venue UNKNOWN; Preprint. DOI: UNKNOWN; arXiv: [2603.13024](https://arxiv.org/abs/2603.13024). [Nguồn chính](https://arxiv.org/abs/2603.13024). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | surgical video |
| Observation → state | reference image; prompts; tool trajectory → generative video/depth representation |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | 2D tool-tip trajectory and affordance conditions |
| Transition | controlled video generation |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; surgical clip |
| Horizon / rollout | clip-based; numeric UNKNOWN; trajectory-conditioned video generation; no command-control rollout verified |
| Evaluation / downstream | depth consistency; downstream action recognition using augmentation; data augmentation/recognition |
| Dataset | 12,044 curated clips reported |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | none verified |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: downstream test beyond image quality. Giới hạn: 2D trajectory is not force-grounded surgical action. Liên quan MedicalWorldModel: medical models already use geometry and downstream evaluation.

<a id="m16"></a>

## M16 — Cosmos-Surg-dVRK: World Foundation Model-based Automated Online Evaluation of Surgical Robot Policy Learning

**VERIFIED — hồ sơ nguồn:** Lukas Zbinden; Nigel Nelson; Juo-Tung Chen; Xinhao Chen; Ji Woong Kim; Mahdi Azizian; Axel Krieger; Sean Huver. 2025, arXiv; venue UNKNOWN; Preprint. DOI: UNKNOWN; arXiv: [2510.16240v2](https://arxiv.org/abs/2510.16240v2). [Nguồn chính](https://arxiv.org/abs/2510.16240v2). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | surgical robotics |
| Observation → state | images; kinematic actions → video latent/history |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | robot kinematics |
| Transition | conditioned video rollout + success classifier |
| Thời gian; future quantity | robot trajectory; future video; predicted task success |
| Horizon / rollout | closed-loop model evaluation; numeric horizon UNKNOWN; online policy interacts with generated video observations |
| Evaluation / downstream | real-vs-sim policy outcome agreement; human-classifier agreement; evaluate policies without physical reruns |
| Dataset | tabletop suture pad; ex-vivo porcine cholecystectomy |
| Uncertainty | success-rank alignment measured; model positively biases success; calibrated probabilities UNKNOWN |
| Planning đã xác minh | policy evaluation; not treatment planning |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text system/evaluation; §5.2–5.3; Table1–3; §5.2.3 hallucinations; §5.3 ex-vivo |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: medical policy-evaluation prior art. Giới hạn: positive success bias; physical anomalies; small ex-vivo evaluation; no patient benefit evidence. Liên quan MedicalWorldModel: invalidates claim that medical WM never evaluate decisions.

<a id="m17"></a>

## M17 — Continuous-Time Deep Glioma Growth Models

**VERIFIED — hồ sơ nguồn:** Jens Petersen; Fabian Isensee; Gregor Köhler; Paul F. Jäger; David Zimmerer; Ulf Neuberger; Wolfgang Wick; Jürgen Debus; Sabine Heiland; Martin Bendszus; Philipp Vollmuth; Klaus H. Maier-Hein. 2021, MICCAI; LNCS12903:83–92; Published. DOI: [10.1007/978-3-030-87199-4_8](https://doi.org/10.1007/978-3-030-87199-4_8); arXiv: [2106.12917v2](https://arxiv.org/abs/2106.12917v2). [Nguồn chính](https://doi.org/10.1007/978-3-030-87199-4_8). Canonical MICCAI 2021; full methods read in arXiv 2106.12917v2; publisher book metadata corroborated by DKFZ institutional repository. Crossref DOI metadata matched after retry 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: glioma spatial progression |
| Observation → state | 2–5 past MRI/mask/time observations during training → multiscale context + global stochastic trajectory code |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none; treatment ignored as stochasticity |
| Transition | continuous-time conditional Neural Process |
| Thời gian; future quantity | days; future tumor segmentation distribution |
| Horizon / rollout | arbitrary time queries; training/eval single target after context; global stochastic trajectory sampled; query future time segmentation |
| Evaluation / downstream | test loss; surprise; Query Volume Dice best-volume of100 samples; plausible spatial growth trajectories |
| Dataset | 379 patients; 3–13 visits; proprietary trial data |
| Uncertainty | shared global sample yields consistent futures; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/MIC-DKFZ/deep-glioma-growth) |
| Mức đọc / vị trí | full-text methods/evaluation; §2.1–2.2; Query Volume Dice |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: continuous, multi-context, coherent stochastic prior art. Giới hạn: oracle future-volume selection not deployable forecast metric; zero-overlap cases excluded. Liên quan MedicalWorldModel: state/horizon innovation must exceed 2021 baseline.

<a id="m18"></a>

## M18 — Learning Spatio-Temporal Model of Disease Progression With NeuralODEs From Longitudinal Volumetric Data

**VERIFIED — hồ sơ nguồn:** Dmitrii Lachinov; Arunava Chakravarty; Christoph Grechenig; Ursula Schmidt-Erfurth; Hrvoje Bogunović. 2024, IEEE TMI 43(3):1165–1179; Published; online 2023, issue 2024. DOI: [10.1109/TMI.2023.3330576](https://doi.org/10.1109/TMI.2023.3330576); arXiv: [2211.04234](https://arxiv.org/abs/2211.04234). [Nguồn chính](https://doi.org/10.1109/TMI.2023.3330576). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: geographic atrophy / brain ventricles |
| Observation → state | baseline OCT/MRI; future elapsed time → voxel embedding/logit initial state |
| Loại state / thông tin suy ra | predictive voxel embeddings; decoded anatomical masks; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | autonomous ODE; optional nondecreasing constraints |
| Thời gian; future quantity | years; future anatomical segmentation |
| Horizon / rollout | continuous time; multiple requested visits; latent voxel dynamics integrated to target time; segmentation readout |
| Evaluation / downstream | temporal Dice; volume prediction; TADPOLE; anatomical progression prediction |
| Dataset | private GA; ADNI/TADPOLE |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §II and evaluation design; §II initial value problem; temporal Dice; TADPOLE evaluation |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: state transition without future pixel synthesis. Giới hạn: ODE autonomy is modeling assumption not identified biological mechanism. Liên quan MedicalWorldModel: anatomy-centric continuous-time prediction already exists.

<a id="m19"></a>

## M19 — Probabilistic Temporal Prediction of Continuous Disease Trajectories and Treatment Effects Using Neural SDEs

**VERIFIED — hồ sơ nguồn:** Joshua Durso-Finley; Berardino Barile; Jean-Pierre Falet; Douglas L. Arnold; Nick Pawlowski; Tal Arbel. 2024, MICCAI; LNCS15003:400–410; Published. DOI: [10.1007/978-3-031-72384-1_38](https://doi.org/10.1007/978-3-031-72384-1_38); arXiv: [2406.12807v1](https://arxiv.org/abs/2406.12807v1). [Nguồn chính](https://papers.miccai.org/miccai-2024/619-Paper3431.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh Crossref DOI metadata matched after retry 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: MS disability trajectories |
| Observation → state | baseline MRI + clinical/demographic variables → joint latent state |
| Loại state / thông tin suy ra | predictive multimodal latent; EDSS observed clinical endpoint; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | randomized treatment assignment |
| Transition | treatment-conditioned stochastic differential equation |
| Thời gian; future quantity | clinical visits; future EDSS; treatment-group contrasts |
| Horizon / rollout | continuous clinical time; exact horizon extraction UNKNOWN; sample stochastic continuous latent path and EDSS readout |
| Evaluation / downstream | factual error; uncertainty-selected subgroups; treatment contrasts; personalized progression/treatment analysis |
| Dataset | six proprietary RCTs |
| Uncertainty | sampled trajectory and treatment-contrast variance |
| Planning đã xác minh | effect estimation, no closed-loop policy evaluation |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §2–3; §2.2 potential outcomes/RCT independence; §3 trials |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: image-conditioned stochastic clinical outcomes without pixels. Giới hạn: individual counterfactual never observed; pooled-trial transport assumptions matter. Liên quan MedicalWorldModel: causal route exists with stronger data; cannot borrow assumptions.

<a id="m20"></a>

## M20 — Predictive digital twins with quantified uncertainty for patient-specific decision making in oncology

**VERIFIED — hồ sơ nguồn:** Graham Pash; Umberto Villa; David A. Hormuth II; Thomas E. Yankeelov; Karen Willcox. 2026, Journal of Computational Physics 560:114937; Published 2026-09-01. DOI: [10.1016/j.jcp.2026.114937](https://doi.org/10.1016/j.jcp.2026.114937); arXiv: [2505.08927](https://arxiv.org/abs/2505.08927). [Nguồn chính](https://www.sciencedirect.com/science/article/pii/S0021999126002901). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh Crossref DOI metadata matched after retry 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: mechanistic glioma digital twin |
| Observation → state | longitudinal MRI-derived cellularity; anatomy; treatment schedule → cell-density field and posterior spatial model parameters |
| Loại state / thông tin suy ra | physical/biological model state inferred from image proxies; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | specified chemoradiation model |
| Transition | reaction-diffusion PDE; Bayesian parameter assimilation |
| Thời gian; future quantity | days; solver step1 day; tumor volume/cellularity distributions |
| Horizon / rollout | one-month virtual experiment; held-out last clinical scan; PDE forward solution under parameter posterior; final-scan holdout separate from calibration path |
| Evaluation / downstream | posterior prediction; Dice/cellularity; imaging-frequency study; forecast and experimental-design analysis |
| Dataset | virtual patient; IvyGAP subset |
| Uncertainty | Bayesian posterior; low-rank Laplace approximation; propagation |
| Planning đã xác minh | optimal experimental-design question on virtual patient; no clinical treatment trial |
| Project/repository | [official](https://github.com/gtpash/dt4co) |
| Mức đọc / vị trí | full-text §3–5; §4.3; §5.1–5.3; AppendixC |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: uncertainty and data assimilation already in mechanistic medicine. Giới hạn: fixed therapy response; model inadequacy; long rollout through calibration is not all unseen. Liên quan MedicalWorldModel: essential adversarial comparator to learned visual WM.

<a id="m21"></a>

## M21 — Online prediction for respiratory movement compensation: a patient-specific gating control for MRI-guided radiotherapy

**VERIFIED — hồ sơ nguồn:** Yang Li; Zhenjiang Li; Jian Zhu; Baosheng Li; Huazhong Shu; Di Ge. 2023, Radiation Oncology 18:149; Published. DOI: [10.1186/s13014-023-02341-1](https://doi.org/10.1186/s13014-023-02341-1); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1186/s13014-023-02341-1). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh Crossref DOI metadata matched after retry 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | A: respiratory gating |
| Observation → state | cine-derived motion trace → recent motion regression state |
| Loại state / thông tin suy ra | measured/inferred position trace history; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | adaptive linear / recurrent trace prediction |
| Thời gian; future quantity | subsecond; threshold crossing / gating signal |
| Horizon / rollout | 0.4 and0.6 s; online direct respiratory-position prediction |
| Evaluation / downstream | gating/prediction comparison; linear beats RNN in studied setting; latency-aware gating |
| Dataset | 21 liver +10 lung cancer patients |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | gating-rule assessment |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | original paper PDF abstract/method overview; https://d-nb.info/1318665426/34; Methods |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: simple predictor tested on downstream surrogate. Giới hạn: retrospective gating result not prospective benefit. Liên quan MedicalWorldModel: do not assume learned latent beats adaptive linear.

<a id="m22"></a>

## M22 — Real-time prediction and gating of respiratory motion using an extended Kalman filter and Gaussian process regression

**VERIFIED — hồ sơ nguồn:** W. Bukhari; S.-M. Hong. 2015, Physics in Medicine & Biology 60(1):233–252; Published; epub 2014. DOI: [10.1088/0031-9155/60/1/233](https://doi.org/10.1088/0031-9155/60/1/233); arXiv: UNKNOWN. [Nguồn chính](https://pubmed.ncbi.nlm.nih.gov/25489980/). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | A: respiratory prediction and gating |
| Observation → state | respiratory traces → EKF state + GP residual |
| Loại state / thông tin suy ra | explicit estimated motion state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | state transition and probabilistic residual correction |
| Thời gian; future quantity | subsecond; future displacement; high-error warning |
| Horizon / rollout | short look-ahead; exact range UNKNOWN; filter update + prediction/gating; fresh observations distinct from open-loop |
| Evaluation / downstream | prediction error and variance-based gating; gate high-risk prediction periods |
| Dataset | clinical respiratory traces; access UNKNOWN |
| Uncertainty | EKF covariance and GP predictive variance |
| Planning đã xác minh | gating rather than policy search |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | indexed original abstract/metadata; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: uncertainty-based gating predates deep WM. Giới hạn: Gaussian assumptions; transport to cine anatomy unproven. Liên quan MedicalWorldModel: invalidates generic uncertainty-aware gating novelty.

<a id="m23"></a>

## M23 — Freehand Ultrasound Image Simulation with Spatially-Conditioned Generative Adversarial Networks

**VERIFIED — hồ sơ nguồn:** Yipeng Hu; Eli Gibson; Li-Lin Lee; Weidi Xie; Dean C. Barratt; Tom Vercauteren; J. Alison Noble. 2017, RAMBO at MICCAI; Accepted/published chapter DOI recorded. DOI: [10.1007/978-3-319-67564-0_11](https://doi.org/10.1007/978-3-319-67564-0_11); arXiv: [1707.05392v1](https://arxiv.org/abs/1707.05392v1). [Nguồn chính](https://arxiv.org/abs/1707.05392). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | B: ultrasound observation simulator |
| Observation → state | tracked phantom ultrasound; calibrated spatial coordinates → implicit anatomical appearance model |
| Loại state / thông tin suy ra | implicit spatial field; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | probe spatial query, not commanded force |
| Transition | position-conditioned generation |
| Thời gian; future quantity | N/A spatial query; ultrasound at unseen location |
| Horizon / rollout | spatial held-out query; no time dynamics; spatial-coordinate query synthesis; not temporal recursive forecast |
| Evaluation / downstream | landmark distances and reader realism; procedure simulation |
| Dataset | fetal phantom; optical tracker |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: pose-conditioned anatomical landmark evaluation. Giới hạn: static phantom mapping not tissue dynamics. Liên quan MedicalWorldModel: pose-conditioned ultrasound is not new.

<a id="m24"></a>

## M24 — A technical assessment of latent diffusion for Alzheimer's disease progression

**VERIFIED — hồ sơ nguồn:** Elyssa M. McMaster; Lemuel Puglisi; Chenyu Gao; Aravind R. Krishnan; Adam M. Saunders; Daniele Ravi; Lori L. Beason-Held; Susan M. Resnick; Lianrui Zuo; Daniel Moyer; Bennett A. Landman. 2025, SPIE Medical Imaging; Proc SPIE13406:1340621; Published proceedings. DOI: [10.1117/12.3047135](https://doi.org/10.1117/12.3047135); arXiv: UNKNOWN. [Nguồn chính](https://pmc.ncbi.nlm.nih.gov/articles/PMC12726967/). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: external BrLP assessment |
| Observation → state | baseline T1 MRI; age/status condition → inherited BrLP state |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | cognitive-status condition; not intervention |
| Transition | BrLP generation evaluated externally |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; future MRI/regional volumes |
| Horizon / rollout | follow-up; exact horizon UNKNOWN; external assessment of conditioned BrLP generation |
| Evaluation / downstream | image metrics vs conditional/unconditional regions; external validity assessment |
| Dataset | Baltimore Longitudinal Study of Aging |
| Uncertainty | not a new uncertainty model |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | original full-text search extraction methods/abstract; Abstract; §2 methodology; diagnostic-condition comparison |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: shows similarity and disease-conditioned behavior can disagree. Giới hạn: pilot study; not proof all image synthesis useless. Liên quan MedicalWorldModel: evaluate actual change, not SSIM alone.

<a id="m25"></a>

## M25 — A radiographic world model for clinical reasoning and evidence generation

**VERIFIED — hồ sơ nguồn:** Suyang Xi; Songtao Hu; Shansong Wang; Mojtaba Safari; Luke del Balzo; Ehsan Ul Karim; Mingzhe Hu; Kuo Zhang; Tonghe Wang; Ralph R. Weichselbaum; Xiaofeng Yang. 2026, arXiv; venue UNKNOWN; Preprint. DOI: UNKNOWN; arXiv: [2609.07719](https://arxiv.org/abs/2609.07719). [Nguồn chính](https://arxiv.org/abs/2609.07719). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | radiographic reasoning / MedDream |
| Observation → state | radiograph and text → shared image-text latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | text condition; not time/action dynamics |
| Transition | cross-modal predictive/generative mapping |
| Thời gian; future quantity | N/A temporal transition absent in reviewed evidence; diagnostic evidence/radiograph representation |
| Horizon / rollout | temporal rollout not established; radiograph/text representation and reasoning; no temporal transition verified |
| Evaluation / downstream | reported reasoning/reader/augmentation tasks; clinical reasoning representation |
| Dataset | CXR data; release specifics UNKNOWN in extraction |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | not demonstrated |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | metadata + abstract; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: explicit WM label extends beyond temporal simulators. Giới hạn: clinical interpretability not guaranteed by naming. Liên quan MedicalWorldModel: classification contrast: not evidence of disease forecasting.

<a id="m26"></a>

## M26 — World Model for AI Autonomous Navigation in Mechanical Thrombectomy

**VERIFIED — hồ sơ nguồn:** Harry Robertshaw; Han-Ru Wu; Alejandro Granados; Thomas C. Booth. 2025, MICCAI; LNCS15968:680–690; Published. DOI: [10.1007/978-3-032-05114-1_65](https://doi.org/10.1007/978-3-032-05114-1_65); arXiv: [2509.25518](https://arxiv.org/abs/2509.25518). [Nguồn chính](https://papers.miccai.org/miccai-2025/1021-Paper3014.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Crossref: online 2025-09-21, print 2026; canonical conference year giữ 2025.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | embodied interventional navigation |
| Observation → state | navigation observations; exact sensor contract UNKNOWN → TD-MPC2 latent |
| Loại state / thông tin suy ra | latent dự đoán; ý nghĩa vật lý/sinh học chưa tự xác lập; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | navigation controls |
| Transition | latent model predictive control |
| Thời gian; future quantity | bước môi trường; đổi sang giây UNKNOWN; navigation state/value |
| Horizon / rollout | task rollout; exact horizon UNKNOWN; TD-MPC2 latent rollouts; deployment details UNKNOWN in extraction |
| Evaluation / downstream | navigation success and duration; thrombectomy navigation |
| Dataset | patient-derived vasculatures; deployment setting not extracted |
| Uncertainty | UNKNOWN: chưa xác minh hiệu chuẩn xác suất |
| Planning đã xác minh | TD-MPC2 model predictive control |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | official metadata/abstract; methods details not used; Trang nguồn/abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: control-oriented medical WM example. Giới hạn: abstract alone insufficient to claim in-patient success. Liên quan MedicalWorldModel: medical WM need not output images.

<a id="m27"></a>

## M27 — Combining Biology-based and MRI Data-driven Modeling to Predict Response to Neoadjuvant Chemotherapy in Patients with Triple-Negative Breast Cancer

**VERIFIED — hồ sơ nguồn:** Casey E. Stowers; Chengyue Wu; Zhan Xu; Sidharth Kumar; Clinton Yam; Jong Bum Son; Jingfei Ma; Jonathan I. Tamir; Gaiane M. Rauch; Thomas E. Yankeelov. 2025, Radiology: Artificial Intelligence 7(1):e240124; Published; online 2024, issue 2025. DOI: [10.1148/ryai.240124](https://doi.org/10.1148/ryai.240124); arXiv: UNKNOWN. [Nguồn chính](https://pubs.rsna.org/doi/10.1148/ryai.240124). RSNA PDF ghi issue 2025, copyright/online 2024

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | C: breast tumor response |
| Observation → state | pretreatment multiparametric MRI → cellularity map + inferred net proliferation/drug-death parameter |
| Loại state / thông tin suy ra | MRI-derived cellularity proxy + inferred mechanistic parameter; not directly observed living-cell count; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | care regimen; not randomized action comparisons in this analysis |
| Transition | biology-based growth equation with predicted patient parameters |
| Thời gian; future quantity | days, aligned to treatment visits; cellularity/volume at visits 2 and 3; pCR association |
| Horizon / rollout | two future visits: after 2/4 treatment cycles; baseline parameters → biological equation → visits 2 and 3 |
| Evaluation / downstream | voxel change; volume/cellularity agreement; pCR discrimination; anticipate observed-regimen response |
| Dataset | ARTEMIS subset: 118 included; 94 training/24 test |
| Uncertainty | confidence intervals across evaluation; calibrated future distribution UNKNOWN |
| Planning đã xác minh | không có prospective treatment planning evaluation |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | original PDF methods/evaluation pp2–5; Mathematical Model; CNN Inputs and Outputs; Patient Demographics; pCR subset |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: kiểm tra state-level response từ baseline MRI. Giới hạn: calibration-quality selection; pCR subset; not causal treatment optimization. Liên quan MedicalWorldModel: phản chứng trực tiếp novelty broad biological/patient-specific dynamics.
