# Paper matrix — hệ, state, transition và bằng chứng

Đối chiếu: **2026-09-12**, Asia/Bangkok. **90 paper**, một hàng/paper trong [CSV](paper_matrix.csv). Tập chọn có chủ đích, không phải danh mục toàn bộ lĩnh vực.

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
| [M01](#m01) | [Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model](https://papers.miccai.org/miccai-2024/118-Paper0053.html) | 2024; MICCAI; LNCS15001:190–199 | Published | yes | canonical MICCAI PDF §2–3 methods/evaluation (round2) |
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
| [M21](#m21) | [Online prediction for respiratory movement compensation: a patient-specific gating control for MRI-guided radiotherapy](https://doi.org/10.1186/s13014-023-02341-1) | 2023; Radiation Oncology 18:149 | Published | no | full PMC methods/evaluation (round2) |
| [M22](#m22) | [Real-time prediction and gating of respiratory motion using an extended Kalman filter and Gaussian process regression](https://pubmed.ncbi.nlm.nih.gov/25489980/) | 2015; Physics in Medicine & Biology 60(1):233–252 | Published; epub 2014 | no | indexed original abstract/metadata |
| [M23](#m23) | [Freehand Ultrasound Image Simulation with Spatially-Conditioned Generative Adversarial Networks](https://arxiv.org/abs/1707.05392) | 2017; RAMBO at MICCAI | Accepted/published chapter DOI recorded | no | author PDF §2.1–2.3 and §3 methods/evaluation (round2) |
| [M24](#m24) | [A technical assessment of latent diffusion for Alzheimer's disease progression](https://pmc.ncbi.nlm.nih.gov/articles/PMC12726967/) | 2025; SPIE Medical Imaging; Proc SPIE13406:1340621 | Published proceedings | no | original full-text search extraction methods/abstract |
| [M25](#m25) | [A radiographic world model for clinical reasoning and evidence generation](https://arxiv.org/abs/2609.07719) | 2026; arXiv; venue UNKNOWN | Preprint | yes | metadata + abstract |
| [M26](#m26) | [World Model for AI Autonomous Navigation in Mechanical Thrombectomy](https://papers.miccai.org/miccai-2025/1021-Paper3014.html) | 2025; MICCAI; LNCS15968:680–690 | Published | yes | official metadata/abstract; methods details not used |
| [M27](#m27) | [Combining Biology-based and MRI Data-driven Modeling to Predict Response to Neoadjuvant Chemotherapy in Patients with Triple-Negative Breast Cancer](https://pubs.rsna.org/doi/10.1148/ryai.240124) | 2025; Radiology: Artificial Intelligence 7(1):e240124 | Published; online 2024, issue 2025 | no | original PDF methods/evaluation pp2–5 |
| [G27](#g27) | [Predictive Representations of State](https://proceedings.neurips.cc/paper/2001/hash/1e4d36177d71bbb3558e43af9577d70e-Abstract.html) | 2001; NeurIPS 14 | Published | no | full original PDF §1–3, Theorem 1 |
| [G28](#g28) | [WorldSimBench: Towards Video Generation Models as World Simulators](https://proceedings.mlr.press/v267/qin25f.html) | 2025; ICML; PMLR 267:50338–50362 | Published | yes | canonical proceedings PDF methods/evaluation, rendered page |
| [G29](#g29) | [WorldModelBench: Judging Video Generation Models As World Models](https://proceedings.neurips.cc/paper_files/paper/2025/hash/4ec03ed08a3fcb59e1c815b5598beff1-Abstract-Datasets_and_Benchmarks_Track.html) | 2025; NeurIPS 38, Datasets and Benchmarks Track | Published | yes | canonical NeurIPS PDF §3–4 plus arXiv full HTML |
| [G30](#g30) | [WorldArena: A Unified Benchmark for Evaluating Perception and Functional Utility of Embodied World Models](https://arxiv.org/abs/2602.08971v2) | 2026; arXiv; peer-reviewed venue UNKNOWN | Preprint verified | yes | full HTML §3–4 and Appendix A/B |
| [G31](#g31) | [WorldArena 2.0: Extending Embodied World Model Benchmarking on Modality, Functionality and Platform](https://arxiv.org/abs/2605.17912v1) | 2026; arXiv; peer-reviewed venue UNKNOWN | Preprint verified | yes | full HTML §3–4 and Tables1–3 |
| [G32](#g32) | [Do Generative Video Models Understand Physical Principles?](https://openaccess.thecvf.com/content/WACV2026/html/Motamed_Do_Generative_Video_Models_Understand_Physical_Principles_WACV_2026_paper.html) | 2026; WACV:948–958 | Published | yes | canonical CVF PDF §2.2–2.5, §4; rendered protocol figure |
| [K03](#k03) | [Strictly Proper Scoring Rules, Prediction, and Estimation](https://doi.org/10.1198/016214506000001437) | 2007; Journal of the American Statistical Association 102(477):359–378 | Published | no | author PDF §4.2–4.3, §6 |
| [K04](#k04) | [Variogram-Based Proper Scoring Rules for Probabilistic Forecasts of Multivariate Quantities](https://doi.org/10.1175/MWR-D-14-00269.1) | 2015; Monthly Weather Review 143(4):1321–1334 | Published | no | original NOAA PDF §2–3, §5 |
| [K05](#k05) | [Conformalized Adaptive Forecasting of Heterogeneous Trajectories](https://proceedings.mlr.press/v235/zhou24l.html) | 2024; ICML; PMLR 235:62002–62056 | Published | no | canonical PDF §2–3, Theorem1, Appendix A6 |
| [K06](#k06) | [Metrics reloaded: recommendations for image analysis validation](https://doi.org/10.1038/s41592-023-02151-z) | 2024; Nature Methods 21:195–212 | Published | no | original author-hosted PDF pp195–197; primary Nature metadata |
| [M28](#m28) | [Conformal Forecasting for Surgical Instrument Trajectory](https://papers.miccai.org/miccai-2025/0168-Paper0260.html) | 2025; MICCAI 2025; LNCS 15968:117–127 | Published | no | canonical MICCAI PDF §2–4/Table1; arXiv compared |
| [M29](#m29) | [Recalibration of Aleatoric and Epistemic Regression Uncertainty in Medical Imaging](https://www.melba-journal.org/papers/2021:008.html) | 2021; Machine Learning for Biomedical Imaging 1, MIDL 2020 special issue:1–26 | Published | no | original journal full HTML §2–4 |
| [M30](#m30) | [Online Learning in Motion Modeling for Intra-interventional Image Sequences](https://papers.miccai.org/miccai-2024/paper/1838_paper.pdf) | 2024; MICCAI 2024; Lecture Notes in Computer Science, pp. 706–716 | Published | no | full MICCAI proceedings PDF, methods and evaluation |
| [M31](#m31) | [Prediction of high-dimensional states subject to respiratory motion: a manifold learning approach](https://pmc.ncbi.nlm.nih.gov/articles/PMC4975535/) | 2016; Physics in Medicine and Biology 61(13):4989–4999 | Published | no | full PMC/BioC article, methods and evaluation |
| [M32](#m32) | [Predicting real-time 3D deformation field maps (DFM) based on volumetric cine MRI (VC-MRI) and artificial neural networks for on-board 4D target tracking: a feasibility study](https://pmc.ncbi.nlm.nih.gov/articles/PMC6734921/) | 2019; Physics in Medicine and Biology 64(16):165016 | Published | no | full PMC article, methods and evaluation |
| [M33](#m33) | [Prediction of in-plane organ deformation during free-breathing radiotherapy via discriminative spatial transformer networks](https://pubmed.ncbi.nlm.nih.gov/32580056/) | 2020; Medical Image Analysis 64:101754 | Published | no | PubMed abstract and Crossref metadata; methods details bounded |
| [M34](#m34) | [Probabilistic 4D predictive model from in-room surrogates using conditional generative networks for image-guided radiotherapy](https://pubmed.ncbi.nlm.nih.gov/34601453/) | 2021; Medical Image Analysis 74:102250 | Published | no | PubMed abstract and Crossref metadata; methods detail bounded |
| [M35](#m35) | [Predicting 4D liver MRI for MR-guided interventions](https://doi.org/10.1016/j.compmedimag.2022.102122) | 2022; Computerized Medical Imaging and Graphics 101:102122 | Published | no | Crossref/publisher metadata; adjacent-paper scope only |
| [M36](#m36) | [Respiratory motion prediction using deep convolutional long short-term memory network](https://pmc.ncbi.nlm.nih.gov/articles/PMC7359959/) | 2020; Journal of Medical Signals & Sensors 10(2):69–75 | Published | no | PMC full text/metadata; methods and evaluation details bounded |
| [M37](#m37) | [Benchmarking machine learning-based real-time respiratory signal predictors in 4D SBRT](https://doi.org/10.1002/mp.17038) | 2024; Medical Physics 51(5):3173–3183 | Published | no | full publisher HTML/methods/evaluation and official database/code README |
| [M38](#m38) | [Performance comparison of prediction filters for respiratory motion tracking in radiotherapy](https://doi.org/10.1002/mp.13929) | 2020; Medical Physics 47(2):643–650 | Published | no | official repository metadata and published article record; methods detail bounded |
| [M39](#m39) | [Real-time prediction and gating of respiratory motion in 3D space using extended Kalman filters and Gaussian process regression network](https://pubmed.ncbi.nlm.nih.gov/26878653/) | 2016; Physics in Medicine and Biology 61(5):1947–1967 | Published | no | PubMed record/abstract and primary journal metadata |
| [M40](#m40) | [Prediction of real-time cine-MR images during MRI-guided radiotherapy of liver cancer using a GAN–ConvLSTM network](https://pmc.ncbi.nlm.nih.gov/articles/PMC12082801/) | 2025; Medical Physics 52(5):3161–3172 | Published | no | full PMC article metadata/methods/results bounded |
| [M41](#m41) | [Non-stationary transformers-based model for predicting liver motion for interleaved two-dimensional cine magnetic resonance imaging](https://doi.org/10.1002/mp.70241) | 2026; Medical Physics 53:e70241 | Published; first online 2025-12-29, issue 2026 | no | publisher metadata/abstract and Crossref record; methods detail bounded |
| [M42](#m42) | [Real-time respiratory motion forecasting with online learning of recurrent neural networks for accurate targeting in externally guided radiotherapy](https://doi.org/10.1016/j.cmpb.2025.108828) | 2025; Computer Methods and Programs in Biomedicine 269:108828 | Published | no | published article metadata/abstract and official repository README; methods detail bounded |
| [M43](#m43) | [Dynamic Image Prediction Using Principal Component and Multi-Channel Singular Spectral Analysis: A Feasibility Study](https://www.scirp.org/pdf/ojmi_2015090914071968.pdf) | 2015; Open Journal of Medical Imaging 5:133–142 | Published | no | full official PDF and metadata; methods/evaluation read |
| [M44](#m44) | [Signal-aware deep learning–based respiratory motion prediction for lung tumor management](https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2026.1735140/full) | 2026; Frontiers in Oncology 16:1735140 | Published | no | full official Frontiers HTML methods/results/discussion |
| [M45](#m45) | [Trackerless Freehand Ultrasound with Sequence Modelling and Auxiliary Transformation Over Past and Future Frames](https://doi.org/10.1109/ISBI53787.2023.10230773) | 2023; IEEE ISBI 2023, pp. 1-5 | Peer-reviewed conference paper; arXiv 2211.04867v2 | no | Full paper PDF, §§2-3; official code metadata |
| [M46](#m46) | [Long-Term Dependency for 3D Reconstruction of Freehand Ultrasound Without External Tracker](https://doi.org/10.1109/TBME.2023.3325551) | 2024; IEEE Transactions on Biomedical Engineering 71(3):1033-1042 | Peer-reviewed journal article; arXiv 2310.10248 | no | Full publisher/HTML paper and UCL record |
| [M47](#m47) | [Privileged Anatomical and Protocol Discrimination in Trackerless 3D Ultrasound Reconstruction](https://doi.org/10.1007/978-3-031-44521-7_14) | 2023; ASMUS 2023 / MICCAI LNCS 14337:142-151 | Peer-reviewed workshop/proceedings paper; arXiv 2308.10293 | no | Accepted/full PDF and official UCL record |
| [M48](#m48) | [Nonrigid Reconstruction of Freehand Ultrasound Without a Tracker](https://papers.miccai.org/miccai-2024/568-Paper2245.html) | 2024; MICCAI 2024, LNCS 15004, pp. 689-699 | Peer-reviewed conference paper; arXiv 2407.05767 | no | Full PDF; official MICCAI page and code README |
| [G33](#g33) | [GenNBV: Generalizable Next-Best-View Policy for Active 3D Reconstruction](https://openaccess.thecvf.com/content/CVPR2024/html/Chen_GenNBV_Generalizable_Next-Best-View_Policy_for_Active_3D_Reconstruction_CVPR_2024_paper.html) | 2024; CVPR 2024, pp. 16436-16445 | Peer-reviewed conference paper; arXiv 2402.16174 | no | full methods/evaluation HTML + official CVF/project metadata |
| [M49](#m49) | [Automatic Probe Movement Guidance for Freehand Obstetric Ultrasound](https://pmc.ncbi.nlm.nih.gov/articles/PMC7116254/) | 2020; MICCAI 2020, LNCS 12263, pp. 583-592 | Peer-reviewed conference paper; arXiv 2007.04480 | no | Primary PMC full text and arXiv metadata |
| [M50](#m50) | [RecON: Online learning for sensorless freehand 3D ultrasound reconstruction](https://doi.org/10.1016/j.media.2023.102810) | 2023; Medical Image Analysis 87, 102810 | Peer-reviewed journal article | no | Publisher abstract, official code/README and metadata; not full methods |
| [M51](#m51) | [TUS-REC2024: A Challenge to Reconstruct 3D Freehand Ultrasound Without External Tracker](https://arxiv.org/html/2506.21765) | 2025; UNKNOWN; arXiv 2506.21765v2 | arXiv challenge paper v2; venue UNKNOWN | no | Official data/task/assessment/policy pages, arXiv HTML §§2-4, Zenodo metadata |

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
| Hệ | Probe-to-target-plane guidance process |
| Observation → state | Current echocardiographic image/feature and relative probe pose between frame pairs → Current image is called state; learned feature is predictive guidance representation |
| Loại state / thông tin suy ra | Latent predictive feature; independent anatomical sufficiency not established; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Predicted 6D relative probe movement (3 translation, 3 rotation); demonstration pose is measured |
| Transition | Cardiac Dreamer maps current feature and relative pose to target feature once |
| Thời gian; future quantity | Frame-pair guidance; exact horizon not a forecast benchmark; Guidance movement toward PLAX, PSAX-AV, or PSAX-MV |
| Horizon / rollout | One guidance step; no quantitative multi-step rollout; Single feature prediction from arbitrary frame pair |
| Evaluation / downstream | Translation/rotation MAE and standard deviation on 3 standard planes; inference latency; Automatic standard-plane probe guidance |
| Dataset | 125 scans on expert-operated probe attached to Franka Panda; about 188K pairs; 110/15 train/test unseen individuals |
| Uncertainty | Not reported |
| Planning đã xác minh | No; direct one-step target movement |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | canonical MICCAI PDF §2–3 methods/evaluation (round2); Abstract; author response items1,2,7; code/data N/A; Round2: PDF §§2.1-2.2, 3.1-3.4, Table 1; MICCAI page |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Pose-conditioned predictive feature used for direct 6D guidance. Giới hạn: No future image rollout, uncertainty, geometry metric, causal command intervention, or physical closed-loop trial. Liên quan MedicalWorldModel: Close named-medical-WM precedent; broad pose-conditioned guidance novelty is weakened.

<a id="m02"></a>

## M02 — EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance

**VERIFIED — hồ sơ nguồn:** Yang Yue; Yulin Wang; Haojun Jiang; Pan Liu; Shiji Song; Gao Huang. 2025, CVPR; Published. DOI: [10.1109/CVPR52734.2025.02421](https://doi.org/10.1109/CVPR52734.2025.02421); arXiv: [2504.13065v1](https://arxiv.org/abs/2504.13065v1). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2025/html/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Motion-aware probe guidance over image and pose history |
| Observation → state | History echocardiography frames, measured probe poses and pairwise pose differences → Masked spatial feature plus motion/history tokens; guidance representation |
| Loại state / thông tin suy ra | Latent predictive representation; anatomical state sufficiency not independently validated; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Predicted probe guidance movement; transition conditioned on measured relative pose, with no established intervention semantics |
| Transition | Spatial mask feature prediction and pairwise image/relative-pose feature prediction with InfoNCE/EMA target encoder |
| Thời gian; future quantity | 30 fps video; scans last minutes; exact forecast horizon not reported as target rollout; Target-plane feature and guidance translation/rotation |
| Horizon / rollout | Single-frame and sequential guidance; history N=8; no quantitative multi-step image rollout; History token aggregation and one target feature prediction; diffusion decoder only qualitative |
| Evaluation / downstream | Single-frame/sequential translation and rotation MAE; spatial/motion ablations; unvisited-plane sequential setup; Echocardiography target-plane probe guidance |
| Dataset | 356 scans, about 1M frames, 284 train/72 test, 30 fps, healthy adult males, Franka Panda probe; 10 planes annotated |
| Uncertainty | Not quantitatively evaluated |
| Planning đã xác minh | Guidance decision from history; no imagined multi-step planning |
| Project/repository | [official](https://github.com/LeapLabTHU/EchoWorld) |
| Mức đọc / vị trí | full-text §3–5 and appendix; PDF visual inspection p4; §4.1–4.2; sequential protocol; Appendix dataset; Round2: arXiv §§4.1-5.1, Appendix A-B; CVPR PDF Tables 1-2 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Combines spatial and motion-aware history for sequential guidance. Giới hạn: No calibrated uncertainty, geometry/landmark evaluation, autonomous robot success, or multi-step ground-truth rollout; official README says dataset cannot be publicly released. Liên quan MedicalWorldModel: Strongest close medical precedent; leaves support-aware prefix query and state sufficiency as hypotheses.

<a id="m03"></a>

## M03 — Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound

**VERIFIED — hồ sơ nguồn:** Siqi Fan; Mingcong Chen; Ran Liu; Zixuan Yang; Xiaoyu Fu; Xiaoqing Gao; Yunhui Liu; Hongbin Liu. 2026, arXiv; peer-reviewed venue UNKNOWN; Preprint. DOI: UNKNOWN; arXiv: [2607.21918v2](https://arxiv.org/abs/2607.21918v2). [Nguồn chính](https://arxiv.org/abs/2607.21918v2). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Partially observable action-dependent goal-plane acquisition |
| Observation → state | Image history with synchronized 6DoF probe pose and elapsed time → VAE latent state |
| Loại state / thông tin suy ra | Latent predictive state; not independently validated as anatomy or contact state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Relative 6DoF probe motion; real robot also has force/torque hardware |
| Transition | Conditional diffusion predicts future latent/frame from context, relative action and time |
| Thời gian; future quantity | 0.5-30 second forecast metrics; trajectory durations reported separately; Future frame/latent and imagined goal-plane reward |
| Horizon / rollout | Future-frame LPIPS/SSIM at 0.5-30 seconds; actor uses one-step imagined rollout; Conditional latent diffusion and one-step actor imagination |
| Evaluation / downstream | LPIPS/SSIM, forward-inverse consistency, policy action accuracy and 20-trial real-robot success; Goal-plane probe guidance with imagined reward and physical robot test |
| Dataset | Self-collected 20 people; carotid 184 trajectories and thyroid 150; train/test counts and frame totals in Table I |
| Uncertainty | Diffusion noise but no calibration/coverage evaluation |
| Planning đã xác minh | Yes; actor scores imagined next latent/reward |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §II–IV; Fig4; TableI; TableIV; Discussion; Round2: arXiv v2 §§II-A to II-C, III-A to III-D, IV, Tables I-III |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Connects action-conditioned latent transition to imagined policy reward and robot evaluation. Giới hạn: ArXiv-only status; private/self-collected data and hardware; acknowledges incomplete separation of contact-induced and physiological dynamics. Liên quan MedicalWorldModel: Shows stronger simulator/planning evidence threshold; cannot be reproduced from TUSREC public schema.

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
| Hệ | Irregularly sampled longitudinal medical image change |
| Observation → state | Past image(s), elapsed visit time and registration/foreground preprocessing; test-time patient history can adapt the flow field → Multiscale visual latent/flow |
| Loại state / thông tin suy ra | Imaging proxy latent; biological/clinical state sufficiency not established; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | ODE/SDE latent flow conditioned on elapsed time |
| Thời gian; future quantity | Months to years, modality-dependent; Future image and geometry derived by auxiliary segmentation |
| Horizon / rollout | Irregular pairwise target queries; METforMIN up to 24 months, MS about 5 years, LUMIERE up to 5 years in source description; free multi-step rollout UNKNOWN; Direct target prediction; test-time optimization on past images; stochastic alternative paths |
| Evaluation / downstream | PSNR, SSIM, MAE/MSE, Dice and HD; major/minor atrophy/growth; no calibration/coverage; Image-level disease progression forecast and derived atrophy/growth comparison |
| Dataset | METforMIN 132 eyes; LMSLS MS 79 series average 4.4 time points; LUMIERE 91 patients and 795 series as reported by paper |
| Uncertainty | SDE samples with minimal diversity reported; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/KrishnaswamyLab/ImageFlowNet) |
| Mức đọc / vị trí | full-text methods/evaluation/Appendix D,F; §5.5–5.6; AppendixD.1/D.3; Đợt 2: arXiv HTML preprocessing, datasets, evaluation and test-time optimization sections |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Irregular-time image-level ODE/SDE forecast with history adaptation. Giới hạn: Retinal registration anchor/common crop selected using the full longitudinal series; test-time adaptation and SDE spread do not establish prefix safety or calibration; retinal anchor/common crop uses whole series (Appendix D.1); quantitative inflation unmeasured; brain registration must be audited separately. Liên quan MedicalWorldModel: Invalidates broad novelty of irregular continuous-time and patient-adapted medical visual dynamics.

<a id="m06"></a>

## M06 — Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction

**VERIFIED — hồ sơ nguồn:** Qinghui Liu; Elies Fuster-Garcia; Ivar Thokle Hovden; Bradley J. MacIntosh; Edvard O. S. Grødem; Petter Brandal; Carles Lopez-Mateu; Donatas Sederevičius; Karoline Skogen; Till Schellhorn; Atle Bjørnerud; Kyrre Eeg Emblem. 2025, IEEE Transactions on Medical Imaging 44(6):2449–2462; Published. DOI: [10.1109/TMI.2025.3533038](https://doi.org/10.1109/TMI.2025.3533038); arXiv: [2309.05406v5](https://arxiv.org/abs/2309.05406v5). [Nguồn chính](https://doi.org/10.1109/TMI.2025.3533038). Canonical TMI 2025; arXiv v5 dùng cho methods. DOI metadata corroborated by UPV institutional record and PubMed 40031286; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Glioma MRI/tumor-map evolution under recorded treatment context |
| Observation → state | Past MRI/masks, time and recorded treatment; test uses the latest three historical MRI exams and duplicates the latest if fewer → Joint MRI/tumor latent with segmentation branch |
| Loại state / thông tin suy ra | Predictive imaging proxy; not direct viable-tumor or treatment-mechanism state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Recorded treatment condition; not a validated intervention variable |
| Transition | Treatment/time-conditioned stochastic diffusion |
| Thời gian; future quantity | Treatment/day bins 0–50, 51–220 and 221–365; Future MRI and tumor segmentation |
| Horizon / rollout | One nearest future frame/exam target across treatment/day bins; 2-past→2-future and recursive rollout UNKNOWN; Diffusion sampling at a target time, not demonstrated free-run treatment simulation |
| Evaluation / downstream | Local: SSIM/PSNR/MSE and tumor DSC/RVD/volume correlation; external LUMIERE: ONLY MRI SSIM/PSNR/MSE, no quantitative tumor-mask validation; Forecast under observed treatment context |
| Dataset | Local high-grade glioma treatment cohort; external LUMIERE subset |
| Uncertainty | Multiple diffusion samples; state calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/samleoqh/TaDiff-Net) |
| Mức đọc / vị trí | full-text methods; §IV-A/B evaluation; §IV-A 18/5 patient split; external labels; training sampling; Đợt 2: arXiv HTML methods, local/external evaluation and treatment-day analysis; root re-read arXiv v5 §IV-A and §IV-C2 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Joint image and tumor-map stochastic prediction conditioned on time and treatment. Giới hạn: Treatment conditioning is not causal identification; only latest-three context to a target, no validated two-future free rollout; external expert-mask ground truth unavailable. Liên quan MedicalWorldModel: Direct adverse prior art for treatment-aware longitudinal glioma imaging.

<a id="m07"></a>

## M07 — Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation

**VERIFIED — hồ sơ nguồn:** Hao Chen; Rui Yin; Yifan Chen; Qi Chen; Chao Li. 2026, ICLR; Published. DOI: UNKNOWN; arXiv: [2512.09185v4](https://arxiv.org/abs/2512.09185v4). [Nguồn chính](https://openreview.net/pdf/a1558b2e7d9494789fdd3057059dfbe2add8737e.pdf). v4 2026-06-17; ICLR publication verified in camera-ready header

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Patient-specific latent trajectory for longitudinal 3D brain MRI |
| Observation → state | MRI history, visit time and metadata → Ordered patient-specific latent trajectory with ArcRank constraints |
| Loại state / thông tin suy ra | Predictive latent imaging proxy; clinical/biological meaning not established; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | Arbitrary-time latent flow matching; progression coordinate is not a physical clock |
| Thời gian; future quantity | Longitudinal age/follow-up; exact numeric horizon UNKNOWN; Future MRI and regional change/Δ-RMAE |
| Horizon / rollout | Irregular target-time queries; free multi-step rollout and independent state-reuse evaluation UNKNOWN; Target-time flow matching and decoding |
| Evaluation / downstream | PSNR/SSIM, structure fidelity, regional MAE and Δ-RMAE with image/structure ablations; Individual future imaging and anatomy-change prediction |
| Dataset | ADNI, OASIS-3 and AIBL |
| Uncertainty | Generative variability; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | camera-ready metadata; full arXiv methods/evaluation; §3; §4.1; regional-change experiments; Đợt 2: arXiv HTML methods/evaluation; OpenReview camera-ready metadata |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Patient-specific latent ordering and arbitrary-time flow. Giới hạn: Straight/constant-velocity latent progression assumption; no calibration, planning or state sufficiency; lesion/treatment discontinuities are not resolved. Liên quan MedicalWorldModel: Adverse prior art for patient-specific latent and continuous-time medical image progression.

<a id="m08"></a>

## M08 — Brain Latent Progression: Individual-based spatiotemporal disease progression on 3D Brain MRIs via latent diffusion

**VERIFIED — hồ sơ nguồn:** Lemuel Puglisi; Daniel C. Alexander; Daniele Ravì. 2025, Medical Image Analysis 106:103734; Published. DOI: [10.1016/j.media.2025.103734](https://doi.org/10.1016/j.media.2025.103734); arXiv: [2502.08560v2](https://arxiv.org/abs/2502.08560v2). [Nguồn chính](https://doi.org/10.1016/j.media.2025.103734). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Canonical author metadata lists Puglisi, Alexander, Ravì; ADNI/AIBL study-group acknowledgement is not expanded as additional named authors.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Patient-conditioned anatomical change in brain MRI |
| Observation → state | T1 MRI, metadata and regional-volume auxiliaries depending on variant → Patient-conditioned latent progression plus regional trajectories |
| Loại state / thông tin suy ra | Predictive imaging proxy; not validated biological atrophy state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | Time/metadata-conditioned latent generative progression |
| Thời gian; future quantity | Years/age-conditioned follow-up; Future MRI and regional volumes |
| Horizon / rollout | Target-age/follow-up generation; internal/external 2-year fast-progressor analysis; free multi-step UNKNOWN; Latent sample inference and target-time decoding |
| Evaluation / downstream | MSE/SSIM, regional MAE and uncertainty-error association; internal 154 and external 165 subjects in 2-year fast-progressor analysis; Personalized image forecast and retrospective fast-progressor stratification |
| Dataset | ADNI, OASIS-3 and AIBL |
| Uncertainty | Latent sample variance and global/voxel error association; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/LemuelPuglisi/BrLP) |
| Mức đọc / vị trí | full-text methods §4; evaluation §5.6; §4.3–4.6; §5.5–5.7; Đợt 2: arXiv HTML methods, uncertainty evaluation and fast-progressor analysis |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Patient-specific latent progression with regional anatomy auxiliaries and sampled uncertainty. Giới hạn: Uncertainty-error association is not calibration/coverage; fast-progressor selection is retrospective; state sufficiency and prefix-only preprocessing are not established. Liên quan MedicalWorldModel: Invalidates broad novelty of patient-specific regional latent state and uncertainty.

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
| Horizon / rollout | Direct separately fitted targets up to 2.2 s, no recursive free-run; separate direct predictor for each horizon; no recursive rollout |
| Evaluation / downstream | PCA error; geometry; image similarity; simple vs learned baselines; latency compensation |
| Dataset | 4 ETH sequences + 8 OvGU sequences; not 12 patients |
| Uncertainty | across-run confidence intervals; not predictive calibration |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/pohl-michel/2D-MR-image-prediction) |
| Mức đọc / vị trí | PDF methods/evaluation; visually inspected Table2; §2.2–2.4; Table2; §2.3.3; Round2 A audit §§2.2–2.3.3/Table2: prefix PCA/direct horizons |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: strong PCA+linear/online learned comparison. Giới hạn: Sequence-specific PCA fit on prefix; short within-sequence held-out suffix; direct horizons do not measure recursive accumulation. Liên quan MedicalWorldModel: learned dynamics must beat simple state under matched context.

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
| Hệ | Longitudinal spatial glioma growth between MRI visits |
| Observation → state | 2–5 context MRI/segmentation observations with time; 379 patients and 3–13 visits in the source cohort → Global stochastic trajectory code plus multiscale context representation |
| Loại state / thông tin suy ra | Predictive latent spatial state; not validated as biological cell state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none; treatment effects omitted by the paper and treated as stochasticity |
| Transition | Continuous-time conditional neural process queried at arbitrary target times |
| Thời gian; future quantity | Longitudinal MRI visits; arbitrary continuous target time; Distribution of future tumor segmentation masks |
| Horizon / rollout | Arbitrary query time; one target conditional on 2–5 context observations; free 2-past→2-future rollout UNKNOWN; Global trajectory sampling and target-time query, not demonstrated recursive free-run |
| Evaluation / downstream | Test loss, KL surprise, predictive Dice and Query Volume Dice; Query Volume Dice selects the closest whole-tumor-volume sample among 100 using the future target volume; future-volume oracle selection is not deployable sample selection; endpoint-conditional query is distinct from unconditional forecast; Plausible spatial growth forecasting |
| Dataset | Randomized lomustine+bevacizumab versus chemotherapy glioma trial; 379 patients; 3–13 scans |
| Uncertainty | Stochastic samples; calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | [official](https://github.com/MIC-DKFZ/deep-glioma-growth) |
| Mức đọc / vị trí | full-text methods/evaluation; §2.1–2.2; Query Volume Dice; Đợt 2: arXiv HTML abstract, methods and evaluation; Query Volume Dice |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Continuous-time multi-context stochastic spatial future prediction. Giới hạn: Oracle future-volume sample selection; no calibration/coverage; not evidence of treatment-free natural history or biology. Liên quan MedicalWorldModel: Direct adverse prior art for glioma state/transition and stochastic spatial futures.

<a id="m18"></a>

## M18 — Learning Spatio-Temporal Model of Disease Progression With NeuralODEs From Longitudinal Volumetric Data

**VERIFIED — hồ sơ nguồn:** Dmitrii Lachinov; Arunava Chakravarty; Christoph Grechenig; Ursula Schmidt-Erfurth; Hrvoje Bogunović. 2024, IEEE TMI 43(3):1165–1179; Published; online 2023, issue 2024. DOI: [10.1109/TMI.2023.3330576](https://doi.org/10.1109/TMI.2023.3330576); arXiv: [2211.04234](https://arxiv.org/abs/2211.04234). [Nguồn chính](https://doi.org/10.1109/TMI.2023.3330576). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Anatomical disease progression from longitudinal volumetric imaging |
| Observation → state | Baseline OCT/MRI volume and future elapsed time → Voxel embedding/logit initial state decoded into anatomical segmentation |
| Loại state / thông tin suy ra | Predictive anatomical representation; not proven biological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none |
| Transition | Autonomous NeuralODE with optional nondecreasing disease constraints |
| Thời gian; future quantity | Disease follow-up over years; Future anatomical segmentation and volume |
| Horizon / rollout | Requested future times and multiple evaluation settings; free multi-step patient rollout UNKNOWN; ODE integration to target time with segmentation readout |
| Evaluation / downstream | Temporal Dice, volume R2/r/MAE, MUV-GA 5-fold CV, ADNI 5-fold CV and TADPOLE holdout; Anatomical progression prediction and trial fast-progressor enrichment |
| Dataset | MUV-GA 967 OCT volumes/100 patients; ADNI 2,823 brain MRI volumes/633 patients; TADPOLE holdout |
| Uncertainty | UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §II and evaluation design; §II initial value problem; temporal Dice; TADPOLE evaluation; Đợt 2: arXiv full text methods and evaluation; published DOI |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Explicit continuous-time anatomical future segmentation with domain constraints. Giới hạn: Automated FastSurfer ventricle references may be easier than expert anatomy; no uncertainty calibration or intervention. Liên quan MedicalWorldModel: Directly invalidates broad novelty of continuous anatomical state transition.

<a id="m19"></a>

## M19 — Probabilistic Temporal Prediction of Continuous Disease Trajectories and Treatment Effects Using Neural SDEs

**VERIFIED — hồ sơ nguồn:** Joshua Durso-Finley; Berardino Barile; Jean-Pierre Falet; Douglas L. Arnold; Nick Pawlowski; Tal Arbel. 2024, MICCAI; LNCS15003:400–410; Published. DOI: [10.1007/978-3-031-72384-1_38](https://doi.org/10.1007/978-3-031-72384-1_38); arXiv: [2406.12807v1](https://arxiv.org/abs/2406.12807v1). [Nguồn chính](https://papers.miccai.org/miccai-2024/619-Paper3431.html). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh Crossref DOI metadata matched after retry 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Continuous MS clinical disease/disability trajectory conditioned on MRI, clinical variables and treatment assignment |
| Observation → state | Baseline MRI plus clinical/demographic features and treatment assignment → Joint latent disease trajectory read out as EDSS |
| Loại state / thông tin suy ra | Predictive clinical latent; not lesion-image state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Randomized treatment assignment/condition in RCT data |
| Transition | Treatment-conditioned Neural SDE |
| Thời gian; future quantity | Clinical visits; approximately 12 weeks to week 96; Factual future EDSS and treatment contrasts |
| Horizon / rollout | Approximately 12-week intervals through week 96 in the reported factual evaluation; Sample latent SDE trajectories and EDSS readout |
| Evaluation / downstream | Future EDSS MSE against non-temporal/LSTM baselines; confidence filtering lowers error for high-confidence subgroup; treatment-response/uplift analyses; Continuous clinical progression and treatment-effect subgroup analysis |
| Dataset | Six proprietary MS randomized clinical trials, reported as multi-centre and >3,600 participants in the paper context |
| Uncertainty | Trajectory variance/confidence and confidence-error filtering; calibration coverage UNKNOWN |
| Planning đã xác minh | No policy planning; treatment contrast analysis |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full-text §2–3; §2.2 potential outcomes/RCT independence; §3 trials; Đợt 2: MICCAI official paper page and arXiv §§2–3 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Stochastic continuous clinical trajectory with treatment contrast and uncertainty ranking. Giới hạn: Not a visual lesion-state forecast; counterfactual validity depends on RCT/potential-outcome assumptions and no closed-loop policy is evaluated. Liên quan MedicalWorldModel: Adverse prior art for broad stochastic continuous medical dynamics and treatment analysis.

<a id="m20"></a>

## M20 — Predictive digital twins with quantified uncertainty for patient-specific decision making in oncology

**VERIFIED — hồ sơ nguồn:** Graham Pash; Umberto Villa; David A. Hormuth II; Thomas E. Yankeelov; Karen Willcox. 2026, Journal of Computational Physics 560:114937; Published 2026-09-01. DOI: [10.1016/j.jcp.2026.114937](https://doi.org/10.1016/j.jcp.2026.114937); arXiv: [2505.08927](https://arxiv.org/abs/2505.08927). [Nguồn chính](https://www.sciencedirect.com/science/article/pii/S0021999126002901). arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh Crossref DOI metadata matched after retry 2026-09-12.

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Patient-specific glioma cellularity/anatomy under recorded treatment schedule |
| Observation → state | Longitudinal MRI-derived cellularity/tumor proxy, anatomy and radiotherapy/chemotherapy schedule → Cell-density field and posterior spatial proliferation/diffusion/treatment parameters |
| Loại state / thông tin suy ra | Mechanistic/model-based state inferred from imaging proxies; not direct in-vivo cellularity measurement; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Specified treatment schedule as model input; intervention validity not established |
| Transition | Reaction-diffusion PDE with treatment terms and implicit Euler one-day solver |
| Thời gian; future quantity | Daily numerical steps over clinical treatment/follow-up interval; Tumor volume, spatial cellularity and quantities of interest |
| Horizon / rollout | Historical first-to-last scan window with last image held out; forward simulation; broad prospective multi-step validation UNKNOWN; Numerical PDE forward solve after Bayesian parameter assimilation |
| Evaluation / downstream | Posterior predictive spatial agreement/Dice/cellularity and experimental-design analysis; model inadequacy discussed; Forecasting and virtual experimental-design analysis |
| Dataset | UPENN-GBM and IvyGAP longitudinal MRI/treatment data as described by paper |
| Uncertainty | Bayesian posterior/low-rank Laplace propagation |
| Planning đã xác minh | Experimental-design analysis; no validated closed-loop clinical policy |
| Project/repository | [official](https://github.com/gtpash/dt4co) |
| Mức đọc / vị trí | full-text §3–5; §4.3; §5.1–5.3; AppendixC; Đợt 2: arXiv HTML §§3–5 and Appendix C; published DOI metadata |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Mechanistic data assimilation with posterior uncertainty and held-out last-scan prediction. Giới hạn: Model adequacy and clinical utility are not established; posterior uncertainty is not a cohort-level calibration/coverage guarantee. Liên quan MedicalWorldModel: Strong adverse prior art for mechanistic state, treatment schedule, uncertainty and forward simulation.

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
| Mức đọc / vị trí | full PMC methods/evaluation (round2); https://d-nb.info/1318665426/34; Methods; A audit: linear prediction, crossing/gating error and prediction timing |

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
| Hệ | Spatially conditioned ultrasound image appearance field |
| Observation → state | Calibrated x/y/z physical coordinate grids plus Gaussian noise → No temporal state; query location-conditioned appearance |
| Loại state / thông tin suy ra | Geometric/query-conditioned predictive representation; not validated clinical state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None |
| Transition | None; direct conditional image generation |
| Thời gian; future quantity | Spatial query only; Synthetic ultrasound image at a queried physical location |
| Horizon / rollout | None; same-location held-out query evaluation; None |
| Evaluation / downstream | Held-out-location image/landmark realism; reader discrimination; speed; no multi-step forecast; Freehand ultrasound simulation and spatial query synthesis |
| Dataset | One-hour fetal phantom scan; >10-year sonographer; 26,396 selected frames; Polaris Spectra; 4 sessions |
| Uncertainty | Gaussian input noise; no calibrated predictive uncertainty |
| Planning đã xác minh | No |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | author PDF §2.1–2.3 and §3 methods/evaluation (round2); Trang nguồn/abstract; Round2: PDF §§2.1-2.3, 3-4; UCL record |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Injects physical coordinate grids into generator/discriminator for spatial conditioning. Giới hạn: No temporal transition, action conditioning, future query protocol, or physical patient validation. Liên quan MedicalWorldModel: Close prior against broad pose-conditioned ultrasound novelty; does not test prefix-to-future state forecasting.

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
| Hệ | Patient-specific tumor response during neoadjuvant chemotherapy |
| Observation → state | Pretreatment multiparametric MRI; source ARTEMIS trial also has visit 2 after two cycles and visit 3 after four cycles → Parameters of a calibrated biology-based mathematical model, including tumor cell net proliferation behavior |
| Loại state / thông tin suy ra | Mechanistic model parameter inferred from imaging; not direct cellular measurement; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Neoadjuvant chemotherapy regimen/context |
| Transition | Biology-based tumor response model driven by CNN-predicted parameters |
| Thời gian; future quantity | Neoadjuvant cycles and mid/end treatment visits; Mid/end treatment total tumor cellularity and total tumor volume; pathologic complete response status |
| Horizon / rollout | Pretreatment to mid/end NAC; three trial visits in source description; free multi-step rollout UNKNOWN; Infer model parameters from baseline MRI, then forward biology-based simulation |
| Evaluation / downstream | 118 women; concordance correlation for predicted/measured TTC/TTV and ROC AUC for pCR; MRI-only parameter prediction evaluated against calibrated model outcomes; Pretreatment response forecast and pCR prediction |
| Dataset | ARTEMIS prospective clinical trial, NCT02276443; 118 stage I–III TNBC patients |
| Uncertainty | 95% confidence intervals for reported metrics; predictive state calibration UNKNOWN |
| Planning đã xác minh | none |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | original PDF methods/evaluation pp2–5; Mathematical Model; CNN Inputs and Outputs; Patient Demographics; pCR subset; Đợt 2: RSNA primary HTML abstract, key points and Materials and Methods patient data |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Couples pretreatment MRI CNN with interpretable biology-based response model. Giới hạn: Treatment response remains cohort/model conditional; not a validated counterfactual policy or public multi-visit benchmark; no broad calibration/coverage report. Liên quan MedicalWorldModel: Strong adverse prior art for treatment-response state/transition claims, especially Q8.

<a id="g27"></a>

## G27 — Predictive Representations of State

**VERIFIED — hồ sơ nguồn:** Michael L. Littman; Richard S. Sutton; Satinder Singh. 2001, NeurIPS 14; Published. DOI: UNKNOWN; arXiv: UNKNOWN. [Nguồn chính](https://proceedings.neurips.cc/paper/2001/hash/1e4d36177d71bbb3558e43af9577d70e-Abstract.html). conference year 2001; proceedings volume 14; no invented DOI

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Foundational predictive state theory |
| Observation → state | action-observation history → probabilities of core future tests |
| Loại state / thông tin suy ra | predictive sufficient statistic, not hidden biological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | discrete actions |
| Transition | recursive predictive-state update; projections to other tests |
| Thời gian; future quantity | discrete steps; no physical duration; probability of future observation sequences |
| Horizon / rollout | arbitrary tests under finite-POMDP representability; recursive test-probability updates |
| Evaluation / downstream | representation theorem; illustrative float/reset system; state sufficient for prediction |
| Dataset | theoretical finite systems |
| Uncertainty | stochastic observation probabilities |
| Planning đã xác minh | not performed; prediction theory |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full original PDF §1–3, Theorem 1; §1 Eq1–3; Theorem1; conclusion |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: state grounded in future tests. Giới hạn: existence result does not establish learnability from medical images. Liên quan MedicalWorldModel: sufficiency must be scoped to target/query, not anatomical naming.

<a id="g28"></a>

## G28 — WorldSimBench: Towards Video Generation Models as World Simulators

**VERIFIED — hồ sơ nguồn:** Yiran Qin; Zhelun Shi; Jiwen Yu; Xijun Wang; Enshen Zhou; Lijun Li; Zhenfei Yin; Xihui Liu; Lu Sheng; Jing Shao; Lei Bai; Ruimao Zhang. 2025, ICML; PMLR 267:50338–50362; Published. DOI: UNKNOWN; arXiv: [2410.18072](https://arxiv.org/abs/2410.18072). [Nguồn chính](https://proceedings.mlr.press/v267/qin25f.html). arXiv first posted 2024; proceedings canonical 2025; author list differs (arXiv includes Wanli Ouyang)

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | CV/embodied evaluation benchmark |
| Observation → state | current RGB + text instructions → evaluated video-model state; not a common physical state |
| Loại state / thông tin suy ra | benchmark; model-dependent latent/history; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | text subtask; video-to-action/goal policy produces executed actions |
| Transition | future video prediction, adapter, execution and observation refresh |
| Thời gian; future quantity | task/environment dependent; generated future and executed task outcome |
| Horizon / rollout | receding-horizon episodes; single common duration UNKNOWN; generate video → execute decoded controls → refreshed real simulator observation |
| Evaluation / downstream | human preference; MineRL counters; CARLA infractions; CALVIN success; test actionable video utility |
| Dataset | HF-Embodied; MineRL; CARLA/LangAuto; CALVIN |
| Uncertainty | no verified calibrated trajectory uncertainty protocol |
| Planning đã xác minh | yes, high-level task breakdown and closed-loop video-to-action pipeline |
| Project/repository | [official](https://iranqin.github.io/WorldSimBench.github.io) |
| Mức đọc / vị trí | canonical proceedings PDF methods/evaluation, rendered page; §3.2; Fig3; §4.1; pp6–7 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: pairs perceptual and manipulative evaluation. Giới hạn: pipeline utility cannot isolate video dynamics from controller/adapters. Liên quan MedicalWorldModel: utility evaluation transferable; modality hierarchy not adopted.

<a id="g29"></a>

## G29 — WorldModelBench: Judging Video Generation Models As World Models

**VERIFIED — hồ sơ nguồn:** Dacheng Li; Yunhao Fang; Yukang Chen; Shuo Yang; Shiyi Cao; Justin Wong; Michael Luo; Xiaolong Wang; Hongxu Yin; Joseph E. Gonzalez; Ion Stoica; Song Han; Yao Lu. 2025, NeurIPS 38, Datasets and Benchmarks Track; Published. DOI: [10.52202/085713-1834](https://doi.org/10.52202/085713-1834); arXiv: [2502.20694](https://arxiv.org/abs/2502.20694). [Nguồn chính](https://proceedings.neurips.cc/paper_files/paper/2025/hash/4ec03ed08a3fcb59e1c815b5598beff1-Abstract-Datasets_and_Benchmarks_Track.html). canonical published abstract differs from initial arXiv performance wording; no numbers mixed

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | world-model video evaluation benchmark |
| Observation → state | text and optional first image → model-specific generated-video representation |
| Loại state / thông tin suy ra | benchmark; no unified latent physical state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | language action description, no executed action experiment |
| Transition | video generation → human/learned judgment |
| Thời gian; future quantity | video clip; instruction fulfillment and annotated physical violations |
| Horizon / rollout | clip-level; common physical horizon UNKNOWN; model generates a conditioned clip; no verified environmental closed loop |
| Evaluation / downstream | human labels, learned-judge agreement, alignment experiment; detect violations missed by appearance-only evaluation |
| Dataset | WorldModelBench prompts/videos/human labels |
| Uncertainty | human disagreement; not predictive uncertainty calibration |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://github.com/WorldModelBench-Team/WorldModelBench) |
| Mức đọc / vị trí | canonical NeurIPS PDF §3–4 plus arXiv full HTML; §3.1 grading; §3.2 curation; §3.3 judge; §4 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: fine-grained evaluation of physical plausibility. Giới hạn: physical-law labels are proxies, not measurement of physical-state trajectories. Liên quan MedicalWorldModel: medical judge requires independent target-domain validation.

<a id="g30"></a>

## G30 — WorldArena: A Unified Benchmark for Evaluating Perception and Functional Utility of Embodied World Models

**VERIFIED — hồ sơ nguồn:** Yu Shang; Zhuohang Li; Yiding Ma; Weikang Su; Xin Jin; Ziyou Wang; Lei Jin; Xin Zhang; Yinzhou Tang; Haisheng Su; Chen Gao; Wei Wu; Xihui Liu; Dhruv Shah; Zhaoxiang Zhang; Zhibo Chen; Jun Zhu; Yonghong Tian; Tat-Seng Chua; Wenwu Zhu; Yong Li. 2026, arXiv; peer-reviewed venue UNKNOWN; Preprint verified. DOI: UNKNOWN; arXiv: [2602.08971v2](https://arxiv.org/abs/2602.08971v2). [Nguồn chính](https://arxiv.org/abs/2602.08971v2). v2 adds authors relative to indexed v1; challenge affiliation is not main-conference publication

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | embodied benchmark |
| Observation → state | image + instruction or action depending on track → model-dependent video/latent history |
| Loại state / thông tin suy ra | benchmark; no common mechanistic state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | robot actions or instructions; IDM for action planner |
| Transition | video rollouts and separate functional pipelines |
| Thời gian; future quantity | frames/episodes; physical horizon depends on task; future video; policy success/ranking/data value |
| Horizon / rollout | policy-evaluation rollout until >120% reference-video length; other tracks variable; track-specific open-loop video or policy-world-model rollout |
| Evaluation / downstream | 16 video metrics; simulator policy utility; VLM success judgment; evaluate data engine, policy evaluator and action planner |
| Dataset | RoboTwin 2.0 |
| Uncertainty | no calibrated predictive distribution assessment verified |
| Planning đã xác minh | action-planner track pairs video model with IDM and executes in RoboTwin |
| Project/repository | [official](https://github.com/tsinghua-fib-lab/WorldArena) |
| Mức đọc / vị trí | full HTML §3–4 and Appendix A/B; §3.2–3.4; Appendix A.11–A.17/B |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: separates perceptual and functional outcomes. Giới hạn: EWMScore averages video metrics only; proxy geometry/judges; simulator-based functional comparison. Liên quan MedicalWorldModel: do not substitute composite score for medical endpoint.

<a id="g31"></a>

## G31 — WorldArena 2.0: Extending Embodied World Model Benchmarking on Modality, Functionality and Platform

**VERIFIED — hồ sơ nguồn:** Yu Shang; Yinzhou Tang; Yiding Ma; Zhuohang Li; Lei Jin; Weikang Su; Xin Jin; Zhaolu Wang; Ziyou Wang; Xin Zhang; Haisheng Su; Weizhen He; Wei Wu; Haoyi Duan; Gordon Wetzstein; Xihui Liu; Dhruv Shah; Zhaoxiang Zhang; Zhibo Chen; Jun Zhu; Yonghong Tian; Tat-Seng Chua; Wenwu Zhu; Chen Gao; Yong Li. 2026, arXiv; peer-reviewed venue UNKNOWN; Preprint verified. DOI: UNKNOWN; arXiv: [2605.17912v1](https://arxiv.org/abs/2605.17912v1). [Nguồn chính](https://arxiv.org/abs/2605.17912v1). v1 May 2026; live leaderboard has later scoring updates; paper audit is version-specific

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | multimodal embodied benchmark |
| Observation → state | visual observations, actions, tactile deformation-map sequences for tactile track → model-dependent visual/tactile latent |
| Loại state / thông tin suy ra | benchmark; modality-specific learned latents, not measured force state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | robot actions; instructions; learned action head |
| Transition | predict visual/tactile observations; policy interactions with learned environment |
| Thời gian; future quantity | task dependent; tactile/video predictions and task outcomes |
| Horizon / rollout | track-specific multi-step rollouts; no common duration verified; synchronized multimodal predictions or policy-environment loop per track |
| Evaluation / downstream | tactile PSNR/SSIM and UniVTAC task success; RL-trained policy success; real-robot task success; evaluate contact information, RL-environment utility and platform transfer |
| Dataset | UniVTAC; RoboTwin 2.0; LIBERO; AgileX Split-Type ALOHA |
| Uncertainty | no calibrated future-state uncertainty evaluation verified |
| Planning đã xác minh | yes, action-planner tasks and interactive RL evaluation |
| Project/repository | [official](https://v2.world-arena.ai/) |
| Mức đọc / vị trí | full HTML §3–4 and Tables1–3; §3.2 UniVTAC; §3.3 RL; §4.1–4.3 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: tests more than vision-only generation. Giới hạn: tactile simulation table and real-robot table are different experiments. Liên quan MedicalWorldModel: contact state requires corresponding measurements and separate transfer validation.

<a id="g32"></a>

## G32 — Do Generative Video Models Understand Physical Principles?

**VERIFIED — hồ sơ nguồn:** Saman Motamed; Laura Culp; Kevin Swersky; Priyank Jaini; Robert Geirhos. 2026, WACV:948–958; Published. DOI: UNKNOWN; arXiv: [2501.09038v3](https://arxiv.org/abs/2501.09038v3). [Nguồn chính](https://openaccess.thecvf.com/content/WACV2026/html/Motamed_Do_Generative_Video_Models_Understand_Physical_Principles_WACV_2026_paper.html). arXiv v3 February 2025; WACV 2026 canonical publication

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Physics-IQ real-world video benchmark |
| Observation → state | up to 3 s context or a switch frame, optional text → model-dependent implicit predictive state |
| Loại state / thông tin suy ra | benchmark; physical state not directly recovered; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | no executed model action; recorded physical setup |
| Transition | conditioned future-video generation |
| Thời gian; future quantity | 3 s context maximum → 5 s continuation; 5 s video continuation and motion pattern |
| Horizon / rollout | 5 s; one conditioned continuation per model protocol |
| Evaluation / downstream | spatial/spatiotemporal/weighted motion IoU; MSE; repeated-take variability reference; diagnose physics prediction under controlled scenes |
| Dataset | Physics-IQ, recorded physical events |
| Uncertainty | two real takes characterize variability; not learned calibrated future distribution |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://physics-iq.github.io/) |
| Mức đọc / vị trí | canonical CVF PDF §2.2–2.5, §4; rendered protocol figure; Fig2; §2.5; discussion of metric limitations |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: repeat real scenes and separate motion timing/location. Giới hạn: static cameras and model-dependent context; metrics are proxies for physical understanding. Liên quan MedicalWorldModel: control preprocessing/context and measure timing rather than visual realism.

<a id="k03"></a>

## K03 — Strictly Proper Scoring Rules, Prediction, and Estimation

**VERIFIED — hồ sơ nguồn:** Tilmann Gneiting; Adrian E. Raftery. 2007, Journal of the American Statistical Association 102(477):359–378; Published. DOI: [10.1198/016214506000001437](https://doi.org/10.1198/016214506000001437); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1198/016214506000001437). canonical JASA 2007, author-hosted original PDF

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | N/A: methodological evaluation rather than a world model |
| Observation → state | predictive distribution and realized value → N/A |
| Loại state / thông tin suy ra | N/A: no proposed latent biological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | N/A |
| Transition | N/A: scoring/calibration, not a dynamics model |
| Thời gian; future quantity | N/A; N/A: evaluates predictive distributions |
| Horizon / rollout | N/A; N/A |
| Evaluation / downstream | propriety theory; CRPS/energy/interval scores; evaluate honest probabilistic forecasts |
| Dataset | theoretical examples |
| Uncertainty | core subject: predictive distribution scoring |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | author PDF §4.2–4.3, §6; CRPS §4.2; energy score Eq22 and moment conditions; interval scores §6 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: scoring distributions rather than oracle samples. Giới hạn: proper score alone does not establish clinical usefulness. Liên quan MedicalWorldModel: supports distribution scoring for future anatomical quantities.

<a id="k04"></a>

## K04 — Variogram-Based Proper Scoring Rules for Probabilistic Forecasts of Multivariate Quantities

**VERIFIED — hồ sơ nguồn:** Michael Scheuerer; Thomas M. Hamill. 2015, Monthly Weather Review 143(4):1321–1334; Published. DOI: [10.1175/MWR-D-14-00269.1](https://doi.org/10.1175/MWR-D-14-00269.1); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1175/MWR-D-14-00269.1). title footnote asterisk omitted; DOI confirmed, issue April 2015

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | N/A: methodological evaluation rather than a world model |
| Observation → state | forecast ensembles and multivariate truth → N/A |
| Loại state / thông tin suy ra | N/A: no proposed latent biological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | N/A |
| Transition | N/A: scoring/calibration, not a dynamics model |
| Thời gian; future quantity | N/A: vector components may be locations or lead times; N/A: assesses forecast dependence |
| Horizon / rollout | N/A; N/A |
| Evaluation / downstream | controlled distribution misspecifications and wind-speed forecasts; diagnose dependence errors in probabilistic predictions |
| Dataset | synthetic multivariate processes; Colorado wind observations |
| Uncertainty | multivariate ensemble evaluation |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | original NOAA PDF §2–3, §5; §2 propriety/limitations; §3 correlation experiments; §5 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: variogram score complements energy/marginal scoring. Giới hạn: not strictly proper; shared bias cancels; finite-ensemble noise. Liên quan MedicalWorldModel: test temporal dependence as well as marginal future accuracy.

<a id="k05"></a>

## K05 — Conformalized Adaptive Forecasting of Heterogeneous Trajectories

**VERIFIED — hồ sơ nguồn:** Yanfei Zhou; Lars Lindemann; Matteo Sesia. 2024, ICML; PMLR 235:62002–62056; Published. DOI: UNKNOWN; arXiv: [2402.09623](https://arxiv.org/abs/2402.09623). [Nguồn chính](https://proceedings.mlr.press/v235/zhou24l.html). ICML 2024 canonical; arXiv tracked separately

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | trajectory uncertainty calibration |
| Observation → state | partial trajectory plus sequentially revealed observations → forecaster state + adaptive bands/residual calibration |
| Loại state / thông tin suy ra | predictive forecaster state, no biological interpretation; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | N/A |
| Transition | black-box forecaster; online band update; trajectory-level calibration |
| Thời gian; future quantity | discrete steps; physical seconds dataset-dependent; simultaneous bands for new trajectory |
| Horizon / rollout | main one-step sequential; Appendix A6 H-step forecasts updated at each observed time; observe true current value, issue next/H-step bands, update online |
| Evaluation / downstream | simultaneous marginal/group coverage and band width; reliable trajectory uncertainty with heterogeneous difficulty |
| Dataset | synthetic heterogeneous trajectories; driving simulator trajectories |
| Uncertainty | simultaneous marginal coverage under trajectory exchangeability; empirical conditional coverage |
| Planning đã xác minh | no direct medical planning experiment |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | canonical PDF §2–3, Theorem1, Appendix A6; §2.1 observation timing; §2.2 marginal limitation; Theorem1; A6 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: trajectory-level exchangeability allows within-trajectory dependence. Giới hạn: online protocol is not autonomous fixed-prefix rollout; conditional coverage is not universal guarantee. Liên quan MedicalWorldModel: patient/trajectory unit and observation schedule must match.

<a id="k06"></a>

## K06 — Metrics reloaded: recommendations for image analysis validation

**VERIFIED — hồ sơ nguồn:** Lena Maier-Hein; Annika Reinke; Patrick Godau; Minu D. Tizabi; Florian Buettner; Evangelia Christodoulou; Ben Glocker; Fabian Isensee; Jens Kleesiek; Michal Kozubek; Mauricio Reyes; Michael A. Riegler; Manuel Wiesenfarth; A. Emre Kavur; Carole H. Sudre; Michael Baumgartner; Matthias Eisenmann; Doreen Heckmann-Nötzel; Tim Rädsch; Laura Acion; Michela Antonelli; Tal Arbel; Spyridon Bakas; Arriel Benis; Matthew B. Blaschko; M. Jorge Cardoso; Veronika Cheplygina; Beth A. Cimini; Gary S. Collins; Keyvan Farahani; Luciana Ferrer; Adrian Galdran; Bram van Ginneken; Robert Haase; Daniel A. Hashimoto; Michael M. Hoffman; Merel Huisman; Pierre Jannin; Charles E. Kahn; Dagmar Kainmueller; Bernhard Kainz; Alexandros Karargyris; Alan Karthikesalingam; Florian Kofler; Annette Kopp-Schneider; Anna Kreshuk; Tahsin Kurc; Bennett A. Landman; Geert Litjens; Amin Madani; Klaus Maier-Hein; Anne L. Martel; Peter Mattson; Erik Meijering; Bjoern Menze; Karel G. M. Moons; Henning Müller; Brennan Nichyporuk; Felix Nickel; Jens Petersen; Nasir Rajpoot; Nicola Rieke; Julio Saez-Rodriguez; Clara I. Sánchez; Shravya Shetty; Maarten van Smeden; Ronald M. Summers; Abdel A. Taha; Aleksei Tiulpin; Sotirios A. Tsaftaris; Ben Van Calster; Gaël Varoquaux; Paul F. Jäger. 2024, Nature Methods 21:195–212; Published. DOI: [10.1038/s41592-023-02151-z](https://doi.org/10.1038/s41592-023-02151-z); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1038/s41592-023-02151-z). Perspective, published 12 February 2024

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | N/A: methodological evaluation rather than a world model |
| Observation → state | domain interest, reference labels, dataset and algorithm outputs → N/A |
| Loại state / thông tin suy ra | N/A: no proposed latent biological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | N/A |
| Transition | N/A: scoring/calibration, not a dynamics model |
| Thời gian; future quantity | N/A; N/A: metric selection framework |
| Horizon / rollout | N/A; N/A |
| Evaluation / downstream | problem fingerprint and metric recommendations; match evaluation to scientific target |
| Dataset | illustrative biomedical use cases |
| Uncertainty | metric/validation pitfalls, not calibrated state transition |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://github.com/Project-MONAI/MetricsReloaded/) |
| Mức đọc / vị trí | original author-hosted PDF pp195–197; primary Nature metadata; Fig1–3, problem fingerprint and categorical-target scope |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: problem-aware metric selection. Giới hạn: classification/detection/segmentation scope; not a complete temporal forecasting protocol. Liên quan MedicalWorldModel: principle extends by interpretation, not automatic authority, to MWM contracts.

<a id="m28"></a>

## M28 — Conformal Forecasting for Surgical Instrument Trajectory

**VERIFIED — hồ sơ nguồn:** Sara Sangalli; Gary Sarwin; Ertunc Erdil; Carlo Serra; Alessandro Carretta; Victor Staartjes; Ender Konukoglu. 2025, MICCAI 2025; LNCS 15968:117–127; Published. DOI: [10.1007/978-3-032-05114-1_12](https://doi.org/10.1007/978-3-032-05114-1_12); arXiv: [2503.04191v2](https://arxiv.org/abs/2503.04191v2). [Nguồn chính](https://papers.miccai.org/miccai-2025/0168-Paper0260.html). published author order differs from arXiv; MICCAI page curator Kitty K. Wong is not a paper author

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | medical video; surgical trajectory forecasting |
| Observation → state | 64-frame endoscopic anatomy/instrument detection history → encoded detection history |
| Loại state / thông tin suy ra | latent predictive history and explicit image-plane displacement, not causal surgical state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none; observed surgeon motion, not commanded intervention |
| Transition | history encoder → future displacement; conformal/CQR calibration |
| Thời gian; future quantity | frames; verified FPS UNKNOWN; angle and magnitude of endpoint instrument displacement |
| Horizon / rollout | 8 future frames; seconds UNKNOWN; direct future displacement from fixed observation window |
| Evaluation / downstream | marginal/joint endpoint coverage and interval size; anticipatory surgical guidance uncertainty |
| Dataset | 144 unique-patient surgery videos overall; 10 held out split 6 calibration/4 evaluation |
| Uncertainty | split conformal/CQR; Bonferroni/Sidak/Max-Rank; coverage/width |
| Planning đã xác minh | not performed; guidance potential only |
| Project/repository | [official](https://github.com/salusanga/conformal_instrument_trajectory) |
| Mức đọc / vị trí | canonical MICCAI PDF §2–4/Table1; arXiv compared; §2.1 endpoint target; §2.2 assumptions; §3 split/context; Table1 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: medical forecasting already evaluates calibrated multivariate endpoint uncertainty. Giới hạn: joint endpoint interval is not full-path band; exchangeability assumptions need cohort-level audit; source dataset described as in-house, public image access not verified. Liên quan MedicalWorldModel: invalidates broad first calibrated medical trajectory forecast claim.

<a id="m29"></a>

## M29 — Recalibration of Aleatoric and Epistemic Regression Uncertainty in Medical Imaging

**VERIFIED — hồ sơ nguồn:** Max-Heinrich Laves; Sontje Ihler; Jacob F. Fast; Lüder A. Kahrs; Tobias Ortmaier. 2021, Machine Learning for Biomedical Imaging 1, MIDL 2020 special issue:1–26; Published. DOI: [10.59275/j.melba.2021-a6fd](https://doi.org/10.59275/j.melba.2021-a6fd); arXiv: [2104.12376](https://arxiv.org/abs/2104.12376). [Nguồn chính](https://www.melba-journal.org/papers/2021:008.html). journal 2021; title typography 'EpistemicRegression' normalized with space

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | image regression, not time evolution |
| Observation → state | medical image → regression prediction and estimated variance |
| Loại state / thông tin suy ra | predicted quantity/variance, no world state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | N/A |
| Transition | N/A: scoring/calibration, not a dynamics model |
| Thời gian; future quantity | N/A; current-image regression quantity, not future patient state |
| Horizon / rollout | N/A; N/A |
| Evaluation / downstream | uncertainty calibration; interval coverage; rejection/OOD; calibrate regression uncertainty |
| Dataset | medical regression datasets including BoneAge, BreastPathQ, EndoVis |
| Uncertainty | aleatoric/epistemic estimates recalibrated via sigma scaling |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://github.com/mlaves/well-calibrated-regression-uncertainty) |
| Mức đọc / vị trí | original journal full HTML §2–4; §2 uncertainty/recalibration; §4.1 intervals; §4.2 rejection |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: simple sigma scaling can improve calibration. Giới hạn: not a world model or longitudinal forecast; outcome utility not established. Liên quan MedicalWorldModel: simple calibrated regression baseline is mandatory adversarial prior art.

<a id="m30"></a>

## M30 — Online Learning in Motion Modeling for Intra-interventional Image Sequences

**VERIFIED — hồ sơ nguồn:** Niklas Gunnarsson; Jens Sjölund; Peter Kimstrand; Thomas B. Schön. 2024, MICCAI 2024; Lecture Notes in Computer Science, pp. 706–716; Published. DOI: [10.1007/978-3-031-72069-7_66](https://doi.org/10.1007/978-3-031-72069-7_66); arXiv: [2410.11491](https://arxiv.org/abs/2410.11491). [Nguồn chính](https://papers.miccai.org/miccai-2024/paper/1838_paper.pdf). arXiv:2410.11491; published MICCAI 2024 version canonical; Crossref DOI checked

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | intra-interventional 2D cardiac/organ image motion |
| Observation → state | reference image plus incoming image sequence → 8-D encoder latent x_t and 16-D linear-Gaussian state z_t decoded to a diffeomorphic 2D deformation |
| Loại state / thông tin suy ra | inferred latent dynamical state with geometric DVF decoder; not shown clinically interpretable; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | linear Gaussian state-space transition with Kalman filtering/forecasting; online gradient updates of LG-SSM parameters |
| Thời gian; future quantity | frame/sample steps; physical cadence for EchoNet not verified in paper extraction; future latent samples and decoded deformation/image; EchoNet LV Dice endpoint at 25 steps |
| Horizon / rollout | EchoNet H=50 unseen samples; physical seconds UNKNOWN; ACDC experiment is sparse reconstruction/interpolation, not future forecasting; Kalman predictive rollout in latent LG-SSM; decoder maps state to diffeomorphic transform |
| Evaluation / downstream | EchoNet held-out videos: latent log likelihood, RMSE of 50 forecast samples, LV Dice at 25 steps; ACDC 100 train/50 test patients: DSC/HD95 for sparse reconstruction; motion prediction for image-guided intervention and LV reconstruction/segmentation proxy |
| Dataset | EchoNet-Dynamic (10,023 videos in paper; 9,540 train/483 test) and ACDC (100/50 patients) |
| Uncertainty | Gaussian latent predictive distribution; calibration in image/DVF space UNKNOWN |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://github.com/ngunnar/2D_motion_model) |
| Mức đọc / vị trí | full MICCAI proceedings PDF, methods and evaluation; MICCAI 2024 paper §§2–4; Tables 1–2 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: explicit probabilistic linear-Gaussian latent transition with online adaptation and 50-sample EchoNet forecast. Giới hạn: latent predictive distribution is not mapped to calibrated DVF uncertainty; no policy/planning; ACDC result does not establish forecasting. Liên quan MedicalWorldModel: direct adversarial prior art against claims that medical motion models lack explicit probabilistic transitions, online adaptation, or multi-step forecast.

<a id="m31"></a>

## M31 — Prediction of high-dimensional states subject to respiratory motion: a manifold learning approach

**VERIFIED — hồ sơ nguồn:** Wenyang Liu; Amit Sawant; Dan Ruan. 2016, Physics in Medicine and Biology 61(13):4989–4999; Published. DOI: [10.1088/0031-9155/61/13/4989](https://doi.org/10.1088/0031-9155/61/13/4989); arXiv: UNKNOWN. [Nguồn chính](https://pmc.ncbi.nlm.nih.gov/articles/PMC4975535/). Publisher article and PMC record; no arXiv version identified

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | high-dimensional respiratory surface motion |
| Observation → state | 3D photogrammetry point-cloud surfaces sampled at 15 Hz → kernel-PCA nonlinear feature coordinates for 3D surface geometry |
| Loại state / thông tin suy ra | inferred geometric manifold state; not image or biological latent; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | vector autoregression of order 20 in feature space; fixed-point pre-image reconstructs surface |
| Thời gian; future quantity | 15 Hz; 200/600 ms lookahead; future high-dimensional respiratory surface |
| Horizon / rollout | 200 ms and 600 ms lookahead; long free-running rollout not established; VAR feature-space direct lookahead plus geometric pre-image |
| Evaluation / downstream | pointwise RMSE and variance on 200×150 grid; 100 train/100 test surfaces from one patient; paired Mann–Whitney tests; irregular-breathing warp simulation lacks true future surfaces; latency compensation / future respiratory geometry estimation |
| Dataset | one patient, approximately 200 surface observations |
| Uncertainty | reported surface variance/error; no calibrated future distribution verified |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full PMC/BioC article, methods and evaluation; PMC4975535; methods, experiments and tables |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: nonlinear manifold state outperformed independent-component prediction for high-dimensional respiratory surfaces. Giới hạn: single-patient within-sequence evaluation; no calibrated predictive distribution, action, planning, or cross-patient cine-image test. Liên quan MedicalWorldModel: strong prior art against a broad claim that a learned geometric respiratory state is absent.

<a id="m32"></a>

## M32 — Predicting real-time 3D deformation field maps (DFM) based on volumetric cine MRI (VC-MRI) and artificial neural networks for on-board 4D target tracking: a feasibility study

**VERIFIED — hồ sơ nguồn:** Jonathan Pham; Wendy Harris; Wenzheng Sun; Zi Yang; Fang-Fang Yin; Lei Ren. 2019, Physics in Medicine and Biology 64(16):165016; Published. DOI: [10.1088/1361-6560/ab359a](https://doi.org/10.1088/1361-6560/ab359a); arXiv: UNKNOWN. [Nguồn chính](https://pmc.ncbi.nlm.nih.gov/articles/PMC6734921/). Published journal version; PMC full text canonical for audit

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | 3D respiratory organ/tumor deformation for on-board 4D target tracking |
| Observation → state | 2D on-board cine signal/image plus a prior volumetric 4D-MRI model → three PCA respiratory deformation-field coefficients derived from prior 4D-MRI |
| Loại state / thông tin suy ra | inferred low-dimensional geometric state conditioned on prior anatomy; not directly observed physiology; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | adaptive boosting and multilayer perceptron predictions of PCA coefficients |
| Thời gian; future quantity | milliseconds to seconds; frame rates about 8 fps phantom and 3 fps patient; future 3D deformation field, VC-MRI and tumor position |
| Horizon / rollout | XCAT 120–600 ms; real patient 330 ms and a 15 s tracking curve; free-running recursive semantics not verified; coefficient prediction followed by DFM/VC-MRI reconstruction |
| Evaluation / downstream | XCAT five respiratory signals and one liver-cancer patient; PCA NCC/NRMSE, volume deformation consistency and center-of-mass errors; latency-compensated 3D target tracking in radiotherapy |
| Dataset | XCAT phantom (five RPM curves, about 2 minutes at ~8 fps) plus one real liver-cancer patient (about 1 minute at ~3 fps) |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed; tracking use only |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full PMC article, methods and evaluation; PMC6734921; methods, data and results sections |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: maps 2D cine observations into predicted 3D deformation fields via a prior 4D-MRI/PCA representation. Giới hạn: prior 4D image and XCAT dominate feasibility; real-patient n=1; no uncertainty calibration, patient split, action or closed-loop beam evaluation. Liên quan MedicalWorldModel: directly weakens novelty of PCA/DVF state plus future anatomical motion prediction from cine observations.

<a id="m33"></a>

## M33 — Prediction of in-plane organ deformation during free-breathing radiotherapy via discriminative spatial transformer networks

**VERIFIED — hồ sơ nguồn:** Liset Vázquez Romaguera; Rosalie Plantefève; Francisco Perdigón Romero; François Hébert; Jean-François Carrier; Samuel Kadoury. 2020, Medical Image Analysis 64:101754; Published. DOI: [10.1016/j.media.2020.101754](https://doi.org/10.1016/j.media.2020.101754); arXiv: UNKNOWN. [Nguồn chính](https://pubmed.ncbi.nlm.nih.gov/32580056/). Published Medical Image Analysis version canonical; DOI checked

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | in-plane respiratory organ deformation during free-breathing radiotherapy |
| Observation → state | medical image sequences from MRI, ultrasound and CT → recurrent multi-scale feature representation and dense deformation maps |
| Loại state / thông tin suy ra | inferred image/geometry representation; clinical semantics and calibration UNKNOWN; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | recurrent encoder-decoder extrapolation followed by cascaded spatial transformers |
| Thời gian; future quantity | free-breathing sequence; exact cadence/horizon UNKNOWN; future dense in-plane organ deformation and image sequence |
| Horizon / rollout | multi-frame prediction block; exact physical horizon and teacher-forcing/free-running contract UNKNOWN from accessible source; recurrent image/deformation extrapolation plus spatial-transformer warping |
| Evaluation / downstream | 85 cases across healthy volunteers and patients/modalities; median vessel-position errors reported for MRI, ultrasound and CT; motion compensation and image-guided radiotherapy |
| Dataset | 85 cases, mixed MRI/US/CT; exact patient/sequence allocation UNKNOWN |
| Uncertainty | not verified |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | PubMed abstract and Crossref metadata; methods details bounded; PubMed 32580056 abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: dense deformation forecast evaluated with physical vessel-position endpoint across modalities. Giới hạn: accessible abstract does not establish probabilistic calibration, recursive rollout, patient/scanner split or action planning. Liên quan MedicalWorldModel: adjacent prior art that weakens claims that dense future organ deformation has not been attempted.

<a id="m34"></a>

## M34 — Probabilistic 4D predictive model from in-room surrogates using conditional generative networks for image-guided radiotherapy

**VERIFIED — hồ sơ nguồn:** Liset Vázquez Romaguera; Tal Mezheritsky; Rihab Mansour; Jean-François Carrier; Samuel Kadoury. 2021, Medical Image Analysis 74:102250; Published. DOI: [10.1016/j.media.2021.102250](https://doi.org/10.1016/j.media.2021.102250); arXiv: UNKNOWN. [Nguồn chính](https://pubmed.ncbi.nlm.nih.gov/34601453/). Published Medical Image Analysis version canonical; DOI checked

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | 4D organ motion inferred from in-room surrogate images |
| Observation → state | 2D in-room surrogate images plus a static pre-operative 3D volume → temporal representation and phase-specific motion distribution with sampled latent variables |
| Loại state / thông tin suy ra | inferred geometric/probabilistic state; not proven causal physiology; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | sequence-to-sequence temporal extrapolation with conditional generative latent sampling |
| Thời gian; future quantity | radiotherapy respiratory motion; exact cadence/horizon UNKNOWN; dense organ deformation at multiple future times |
| Horizon / rollout | multiple future times; exact direct-versus-recursive implementation UNKNOWN from abstract-level audit; conditional sequence extrapolation and sampled latent future motion fields |
| Evaluation / downstream | 25 healthy volunteers and 11 cancer patients with cancer data held out; MRI/US deformation errors and personalization results; image-guided radiotherapy motion compensation |
| Dataset | 25 healthy volunteers + 11 cancer patients; modalities MRI and ultrasound |
| Uncertainty | multi-sample latent future distribution; calibration/coverage UNKNOWN |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | PubMed abstract and Crossref metadata; methods detail bounded; PubMed 34601453 abstract |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: multi-time probabilistic future deformation from in-room surrogates with subject personalization. Giới hạn: abstract does not establish calibrated coverage, open-loop recursive stability, action input or planning utility. Liên quan MedicalWorldModel: adversarial prior art against claims that medical motion models lack multi-future latent uncertainty or personalization.

<a id="m35"></a>

## M35 — Predicting 4D liver MRI for MR-guided interventions

**VERIFIED — hồ sơ nguồn:** Gino Gulamhussene; Anneke Meyer; Marko Rak; Oleksii Bashkanov; Jazan Omari; Maciej Pech; Christian Hansen. 2022, Computerized Medical Imaging and Graphics 101:102122; Published. DOI: [10.1016/j.compmedimag.2022.102122](https://doi.org/10.1016/j.compmedimag.2022.102122); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1016/j.compmedimag.2022.102122). Published 2022 volume 101 article 102122; Crossref title/authors checked

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | free-breathing liver 4D-MRI reconstruction for MR-guided intervention |
| Observation → state | 2D liver MRI slices interleaved with navigator frames → image-based temporal representation for 4D liver MRI; exact state parameterization UNKNOWN in this audit |
| Loại state / thông tin suy ra | inferred image/temporal reconstruction state; not established as a sufficient anatomical state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | deep temporal prediction/reconstruction from navigator information; exact transition and future-query contract UNKNOWN |
| Thời gian; future quantity | cine/interleaved MRI; exact cadence UNKNOWN; 4D liver MRI volume/frames from live navigator acquisitions |
| Horizon / rollout | future/interleaved 4D reconstruction; exact physical horizon and recursive semantics UNKNOWN; temporal image prediction/reconstruction; exact mechanism UNKNOWN |
| Evaluation / downstream | published article is a 4D liver MRI prediction/reconstruction study; exact patient split and metric details not extracted here; MR-guided interventions and reduced navigator burden |
| Dataset | 2D MRI liver slices with navigator frames test datasets; exact public subject count UNKNOWN |
| Uncertainty | not verified |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | Crossref/publisher metadata; adjacent-paper scope only; Crossref record and DOI landing metadata |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: adjacent 4D liver-MRI prediction problem using live navigator information. Giới hạn: not verified as prefix-only open-loop forecasting or calibrated simulator; dataset/split details remain bounded. Liên quan MedicalWorldModel: useful negative control: adjacent mathematical problem can be reconstruction/interpolation rather than a world model transition.

<a id="m36"></a>

## M36 — Respiratory motion prediction using deep convolutional long short-term memory network

**VERIFIED — hồ sơ nguồn:** Shahabedin Nabavi; Monireh Abdoos; Mohsen Ebrahimi Moghaddam; Mohammad Mohammadi. 2020, Journal of Medical Signals & Sensors 10(2):69–75; Published. DOI: [10.4103/jmss.JMSS_38_19](https://doi.org/10.4103/jmss.JMSS_38_19); arXiv: UNKNOWN. [Nguồn chính](https://pmc.ncbi.nlm.nih.gov/articles/PMC7359959/). Published 2020; DOI capitalization normalized

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | respiratory motion in CT image sequences |
| Observation → state | short CT image history → ConvLSTM hidden representation of image sequence |
| Loại state / thông tin suy ra | inferred predictive latent; no anatomical sufficiency test verified; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | ConvLSTM sequence prediction |
| Thời gian; future quantity | frame steps; physical timestamps UNKNOWN; next six CT frames/images |
| Horizon / rollout | six future frames; physical cadence UNKNOWN; ConvLSTM future-frame sequence generation; exact recursion contract bounded |
| Evaluation / downstream | six patients and 3,295 CT images; leave-one-patient-out; reported RMSE about 9e-3 and SSIM about 0.943; respiratory motion estimation / image prediction |
| Dataset | six patients, 3,295 CT images |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | PMC full text/metadata; methods and evaluation details bounded; PMC7359959; methods, experiments and results |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: early medical ConvLSTM future-frame baseline with patient-level leave-one-out evaluation. Giới hạn: image metrics dominate; exact direct/recursive teacher-forcing semantics and physical horizon require careful audit; no uncertainty/planning. Liên quan MedicalWorldModel: weakens novelty claims based only on ConvLSTM future image prediction; useful simple image baseline.

<a id="m37"></a>

## M37 — Benchmarking machine learning-based real-time respiratory signal predictors in 4D SBRT

**VERIFIED — hồ sơ nguồn:** Lukas Wimmert; Maximilian Nielsen; Frederic Madesta; Tobias Gauer; Christian Hofmann; Rene Werner. 2024, Medical Physics 51(5):3173–3183; Published. DOI: [10.1002/mp.17038](https://doi.org/10.1002/mp.17038); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1002/mp.17038). Published 2024; official README current count differs from paper after corruption filtering

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | external respiratory surrogate during 4D SBRT |
| Observation → state | noisy 25 Hz Varian RPM marker signal → scalar respiratory signal / denoised target; not an anatomical state |
| Loại state / thông tin suy ra | observed/inferred signal state, predictive but not geometric anatomy; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | Linear, DLinear, XGBoost, LSTM, full-history Transformer and limited-history Transformer predictors |
| Thời gian; future quantity | 25 Hz; 480/680/920 ms; single future respiratory signal point |
| Horizon / rollout | 480, 680 and 920 ms direct targets; no image/geometry rollout; direct single-point regression from history; no recursive image rollout |
| Evaluation / downstream | 2,502 signals from 416 patients; patient split 215/84/117; median/IQR nRMSE per signal; 70 OOD curves; online scaling after first 20 s; real-time respiratory compensation/gating baseline selection |
| Dataset | public respiratory database: 2,510 signals/419 patients current README; study analysis 2,502 signals/416 patients after removing 8 corrupted signals from 3 patients |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://github.com/IPMI-ICNS-UKE/respiratory-motion-prediction; https://github.com/IPMI-ICNS-UKE/respiratory-signal-database) |
| Mức đọc / vị trí | full publisher HTML/methods/evaluation and official database/code README; Medical Physics article methods/results; official GitHub README |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: patient-level split, OOD evaluation and strong simple/deep baseline comparison across clinically relevant latency horizons. Giới hạn: no anatomy images, contour, pose/action, treatment effect or uncertainty calibration. Liên quan MedicalWorldModel: mandatory scalar timing/control baseline and fairness template; cannot establish visual anatomical world state.

<a id="m38"></a>

## M38 — Performance comparison of prediction filters for respiratory motion tracking in radiotherapy

**VERIFIED — hồ sơ nguồn:** Alexander Jöhl; Stefanie Ehrbar; Matthias Guckenberger; Stephan Klöck; Mirko Meboldt; Melanie Zeilinger; Stephanie Tanadini-Lang; Marianne Schmid Daners. 2020, Medical Physics 47(2):643–650; Published. DOI: [10.1002/mp.13929](https://doi.org/10.1002/mp.13929); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1002/mp.13929). Online publication 2019; print issue 2020; canonical citation uses 2020; first online 2019-12-07, issue 2020-02; canonical issue year 2020

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | scalar respiratory motion for radiotherapy tracking |
| Observation → state | 93 standardized respiratory traces → scalar breathing signal |
| Loại state / thông tin suy ra | observed signal state, not anatomy; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | 18 prediction filters including linear, LMS and wavelet filters |
| Thời gian; future quantity | 160/480 ms; future respiratory signal |
| Horizon / rollout | 160 ms and 480 ms benchmark horizons; direct filter prediction |
| Evaluation / downstream | 10 traces for hyperparameter optimization and 83 for evaluation; smooth-signal wavelet LMS/linear nRMSE below 0.05 at relevant horizons; noisy performance converges; prediction-filter selection for radiotherapy tracking |
| Dataset | 93 respiratory traces |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | official repository metadata and published article record; methods detail bounded; DOI/publisher record; ETH repository copy |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: broad simple-filter comparison showing signal smoothness/noise and horizon materially affect ranking. Giới hạn: scalar signal only; no anatomical geometry, patient-level visual split, uncertainty calibration or planning. Liên quan MedicalWorldModel: adversarial baseline against assuming a deep predictor is needed before measuring simple dynamics.

<a id="m39"></a>

## M39 — Real-time prediction and gating of respiratory motion in 3D space using extended Kalman filters and Gaussian process regression network

**VERIFIED — hồ sơ nguồn:** W. Bukhari; S.-M. Hong. 2016, Physics in Medicine and Biology 61(5):1947–1967; Published. DOI: [10.1088/0031-9155/61/5/1947](https://doi.org/10.1088/0031-9155/61/5/1947); arXiv: UNKNOWN. [Nguồn chính](https://pubmed.ncbi.nlm.nih.gov/26878653/). Published 2016; 3D extension of 2015 EKF+GPR work

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | 3D respiratory marker/position motion |
| Observation → state | 3D respiratory coordinates → per-coordinate extended-Kalman-filter state with residual multi-output GPRN |
| Loại state / thông tin suy ra | inferred geometric signal state with predictive covariance; not image anatomy; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | EKF transition plus GPRN residual correction |
| Thời gian; future quantity | 192/384/576 ms; future 3D respiratory position and covariance/gating risk |
| Horizon / rollout | 192, 384 and 576 ms lookahead; EKF/GPRN direct lookahead with covariance-based gating |
| Evaluation / downstream | 304 respiratory traces; RMS error relative to no prediction reported at the three horizons; covariance trace used for gating high-error periods; latency compensation and uncertainty-aware beam gating |
| Dataset | 304 respiratory traces; exact patient/subject split UNKNOWN in this audit |
| Uncertainty | predictive covariance used operationally; calibration in anatomical space UNKNOWN |
| Planning đã xác minh | beam pause/gating thresholding, not model-based planning |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | PubMed record/abstract and primary journal metadata; PubMed 26878653 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: combines 3D motion prediction with predictive covariance used to gate likely high-error periods. Giới hạn: not image-derived anatomy; no calibrated contour/DVF uncertainty, action-conditioned intervention or closed-loop planning. Liên quan MedicalWorldModel: direct prior art invalidating a broad novelty claim for uncertainty-aware 3D motion/gating.

<a id="m40"></a>

## M40 — Prediction of real-time cine-MR images during MRI-guided radiotherapy of liver cancer using a GAN–ConvLSTM network

**VERIFIED — hồ sơ nguồn:** Guodong Jin; Yuxiang Liu; Ran Wei; Bining Yang; Bo Pang; Xinyuan Chen; Hong Quan; Jianrong Dai; Kuo Men. 2025, Medical Physics 52(5):3161–3172; Published. DOI: [10.1002/mp.17609](https://doi.org/10.1002/mp.17609); arXiv: UNKNOWN. [Nguồn chính](https://pmc.ncbi.nlm.nih.gov/articles/PMC12082801/). Published Medical Physics 2025 issue; DOI checked

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | liver cine-MR image sequence during MRI-guided radiotherapy |
| Observation → state | five sagittal cine-MR frames → GAN–ConvLSTM hidden/image representation |
| Loại state / thông tin suy ra | inferred predictive image state; not shown to be sufficient or clinically interpretable; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | ConvLSTM/GAN generator iteratively predicts future image content |
| Thời gian; future quantity | frame steps; physical cadence UNKNOWN; next five cine-MR frames plus landmark displacement endpoint |
| Horizon / rollout | five-frame future block; exact physical cadence and teacher-forcing/free-running semantics UNKNOWN; block future-frame generation with iterative spatial transformation |
| Evaluation / downstream | 15 liver-cancer patients, 300 frames each; PSNR/SSIM/VIF/Pearson and manual landmark errors about 2.42±0.91 and 2.44±0.96 mm at steps 4/5; personalized per-patient models; future cine-MR display/latency compensation during MRI-guided radiotherapy |
| Dataset | 15 liver-cancer patients; each sequence 300 frames |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full PMC article metadata/methods/results bounded; PMC12082801; methods and results |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: future cine-MR image prediction with a physical landmark error endpoint. Giới hạn: personalized per-patient models and no patient-independent split, calibrated uncertainty, action or planning; image quality does not establish simulator utility. Liên quan MedicalWorldModel: negative control against equating future-frame generation with a medical world model.

<a id="m41"></a>

## M41 — Non-stationary transformers-based model for predicting liver motion for interleaved two-dimensional cine magnetic resonance imaging

**VERIFIED — hồ sơ nguồn:** Suzune Shimizu; Masato Tsuneda; Kota Abe; Takashi Uno; Hiroki Suyari; Yasukuni Mori. 2026, Medical Physics 53:e70241; Published; first online 2025-12-29, issue 2026. DOI: [10.1002/mp.70241](https://doi.org/10.1002/mp.70241); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1002/mp.70241). First online 2025-12-29; print/issue 2026 Medical Physics 53:e70241; online 2025-12-29, issue 2026-01; canonical issue year 2026

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | liver motion in interleaved 2D cine-MR during MR-guided radiotherapy |
| Observation → state | interleaved cine-MR images → liver centroid from intensity-based deformable registration |
| Loại state / thông tin suy ra | inferred geometric summary state; not full anatomy or biology; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | NsTransformer compared with iTransformer, biLSTM-attention, LSTM and linear predictors |
| Thời gian; future quantity | 200/400/600 ms; future liver centroid |
| Horizon / rollout | direct 200, 400 and 600 ms targets; direct horizon-specific regression |
| Evaluation / downstream | 17 liver-cancer patients; RMSE and margin-based accuracy Pθ; Friedman/Nemenyi comparisons; about 5 ms prediction time; irregular-breathing degradation reported; latency-compensated liver motion prediction for MR-guided radiotherapy |
| Dataset | 17 liver-cancer patients; exact context window, split and patient weighting UNKNOWN from accessible publisher text |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | publisher metadata/abstract and Crossref record; methods detail bounded; DOI landing page and Crossref record |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: recent direct cine-MR centroid forecast with strong simple and sequence-model baselines and irregular-breathing stress. Giới hạn: centroid endpoint only; no predictive distribution, full-shape state, action or planning; split/context details remain UNKNOWN. Liên quan MedicalWorldModel: invalidates novelty claim that cine-MR centroid prediction itself is new; leaves full-shape/calibration as hypotheses only.

<a id="m42"></a>

## M42 — Real-time respiratory motion forecasting with online learning of recurrent neural networks for accurate targeting in externally guided radiotherapy

**VERIFIED — hồ sơ nguồn:** Michel Pohl; Mitsuru Uesaka; Hiroyuki Takahashi; Kazuyuki Demachi; Ritu Bhusal Chhatkuli. 2025, Computer Methods and Programs in Biomedicine 269:108828; Published. DOI: [10.1016/j.cmpb.2025.108828](https://doi.org/10.1016/j.cmpb.2025.108828); arXiv: [2403.01607](https://arxiv.org/abs/2403.01607). [Nguồn chính](https://doi.org/10.1016/j.cmpb.2025.108828). Published 2025; arXiv:2403.01607 tracked separately

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | 3D external chest-marker respiratory motion |
| Observation → state | three external chest-marker coordinates sampled at 10 Hz and resampled evaluation rates → multivariate marker-position signal |
| Loại state / thông tin suy ra | observed geometric surrogate state, not internal anatomy; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | online UORO, SnAp-1, DNI, RTRL, LMS, SVR and linear predictors |
| Thời gian; future quantity | 3.33/10/30 Hz; ≤2.1 s; future external-marker positions |
| Horizon / rollout | direct horizons up to about 2.1 s at 3.33/10/30 Hz; free-running image rollout absent; online direct horizon prediction; no verified recursive frame rollout |
| Evaluation / downstream | 9 sequences, 73–320 s; first minute used for training/testing protocol; nRMSE by method, regular/irregular breathing comparisons; SnAp-1/UORO and linear baselines reported; latency compensation for externally guided radiotherapy targeting |
| Dataset | 9 respiratory marker sequences; exact subject count UNKNOWN |
| Uncertainty | not reported as calibrated predictive distribution |
| Planning đã xác minh | not performed |
| Project/repository | [official](https://github.com/pohl-michel/2D-MR-image-prediction) |
| Mức đọc / vị trí | published article metadata/abstract and official repository README; methods detail bounded; DOI landing page; official README references and time-series folder |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: online adaptation comparison showing method ranking depends on sampling rate and horizon. Giới hạn: surrogate marker not anatomy; sequence-wise small study; no calibrated uncertainty, patient-independent population split or planning. Liên quan MedicalWorldModel: invalidates broad novelty claim for online RNN motion forecasting and requires strong linear baseline.

<a id="m43"></a>

## M43 — Dynamic Image Prediction Using Principal Component and Multi-Channel Singular Spectral Analysis: A Feasibility Study

**VERIFIED — hồ sơ nguồn:** Ritu Bhusal Chhatkuli; Kazuyuki Demachi; Naoki Miyamoto; Mitsuru Uesaka; Akihiro Haga. 2015, Open Journal of Medical Imaging 5:133–142; Published. DOI: [10.4236/ojmi.2015.53017](https://doi.org/10.4236/ojmi.2015.53017); arXiv: UNKNOWN. [Nguồn chính](https://www.scirp.org/pdf/ojmi_2015090914071968.pdf). Published 2015; DOI checked

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | lung respiratory image dynamics |
| Observation → state | CT and kilovoltage fluoroscopy/image sequence → PCA spatial modes plus multi-channel singular-spectrum-analysis temporal components |
| Loại state / thông tin suy ra | inferred low-dimensional image dynamics; not proven anatomical/physiological state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | MSSA temporal prediction of the next breathing-period image |
| Thời gian; future quantity | breathing-period scale; exact frame cadence UNKNOWN; future dynamic respiratory image |
| Horizon / rollout | next breathing period; exact recursive/direct semantics UNKNOWN; low-rank PCA representation followed by MSSA temporal forecast and image reconstruction |
| Evaluation / downstream | one lung-cancer CT sequence and moving phantom; cross-correlation reported above 0.999 for CT and 0.995 for kV phantom; feasibility of dynamic image prediction for motion compensation |
| Dataset | one lung-cancer CT sequence plus moving phantom |
| Uncertainty | not reported |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full official PDF and metadata; methods/evaluation read; SCIRP official PDF; methods and results |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: early PCA+MSSA image-forecast feasibility baseline. Giới hạn: single sequence/phantom feasibility, no patient split, calibrated uncertainty, state endpoint or planning. Liên quan MedicalWorldModel: negative control against calling PCA temporal image synthesis a novel world model state-transition contribution.

<a id="m44"></a>

## M44 — Signal-aware deep learning–based respiratory motion prediction for lung tumor management

**VERIFIED — hồ sơ nguồn:** Kaushik Pratim Das; Chandra J.; Partha Pratim Medhi. 2026, Frontiers in Oncology 16:1735140; Published. DOI: [10.3389/fonc.2026.1735140](https://doi.org/10.3389/fonc.2026.1735140); arXiv: UNKNOWN. [Nguồn chính](https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2026.1735140/full). Published 2026-02-13; DOI and article number canonical

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | lung-tumor respiratory motion surrogate derived from PET/CT |
| Observation → state | PET/CT-derived HU/time-intensity surrogate signals and amplitude classes → low-dimensional surrogate signal plus amplitude-class representation |
| Loại state / thông tin suy ra | inferred predictive signal state; physical anatomy and tumor displacement not directly established; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | none / autonomous physiological process; no commanded action input verified |
| Transition | dilated CNN plus bidirectional LSTM and autoencoder components |
| Thời gian; future quantity | 50–500 ms reported horizons; future respiratory surrogate and signal-derived classification outputs |
| Horizon / rollout | authors report 50–500 ms prediction; exact direct/recursive contract UNKNOWN; hybrid signal prediction/classification; exact autoregressive rollout UNKNOWN |
| Evaluation / downstream | authors report 1,777 patients and approximately 400,000 signal segments with an 80/20 patient split; RMSE/MAE/AUC/F1; no confidence intervals or hypothesis tests verified; respiratory motion management / lung tumor targeting proxy |
| Dataset | private/confidential PET/CT-derived signals; article says data cannot be shared |
| Uncertainty | no calibrated predictive distribution or statistical uncertainty intervals verified |
| Planning đã xác minh | not performed |
| Project/repository | UNKNOWN |
| Mức đọc / vị trí | full official Frontiers HTML methods/results/discussion; Frontiers in Oncology article §§Methods, Results, Data availability and Discussion |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: recent large reported cohort and signal-aware hybrid predictor with patient-level split. Giới hạn: no physical-space calibration to tumor/marker displacement, dosimetry, closed-loop treatment evaluation or public reproducibility; authors defer these validations. Liên quan MedicalWorldModel: latest adversarial caution: high algorithmic signal metrics on private surrogates do not establish anatomical state, simulator utility or clinical benefit.

<a id="m45"></a>

## M45 — Trackerless Freehand Ultrasound with Sequence Modelling and Auxiliary Transformation Over Past and Future Frames

**VERIFIED — hồ sơ nguồn:** Qi Li; Ziyi Shen; Qian Li; Dean C. Barratt; Thomas Dowrick; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. 2023, IEEE ISBI 2023, pp. 1-5; Peer-reviewed conference paper; arXiv 2211.04867v2. DOI: [10.1109/ISBI53787.2023.10230773](https://doi.org/10.1109/ISBI53787.2023.10230773); arXiv: [2211.04867v2](https://arxiv.org/abs/2211.04867v2). [Nguồn chính](https://doi.org/10.1109/ISBI53787.2023.10230773). Published ISBI version canonical; arXiv 2211.04867v2 recorded

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Rigid probe-motion estimation from ultrasound image sequences |
| Observation → state | Past/future ultrasound frames; optical-tracker labels for training/evaluation → Pairwise rigid transformation history |
| Loại state / thông tin suy ra | Geometric motion estimate; not anatomy state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None; measured probe motion labels |
| Transition | CNN/RNN predicts pairwise transform with delayed future-frame setup |
| Thời gian; future quantity | Frame-level; approximately sub-second to one-second intervals; Rigid transform and reconstructed volume |
| Horizon / rollout | Frame intervals up to roughly 1 second; delayed prediction; Delayed transform prediction |
| Evaluation / downstream | Frame error, accumulated tracking, volume Dice and final drift; Trackerless 3D ultrasound reconstruction |
| Dataset | 19 volunteers, 38 forearms, 228 scans, 36-430 frames, 20 fps, optical tracker |
| Uncertainty | Not a calibrated forecast |
| Planning đã xác minh | No |
| Project/repository | [official](https://github.com/ucl-candi/freehand) |
| Mức đọc / vị trí | Full paper PDF, §§2-3; official code metadata; ISBI paper §§2.1, 3.1-3.3, Table 1 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Sequence model with auxiliary transformation over past/future frames. Giới hạn: No target-view anatomy forecasting or causal action intervention; future context is not prefix-only. Liên quan MedicalWorldModel: Adversarial prior against broad sequence-memory novelty.

<a id="m46"></a>

## M46 — Long-Term Dependency for 3D Reconstruction of Freehand Ultrasound Without External Tracker

**VERIFIED — hồ sơ nguồn:** Qi Li; Ziyi Shen; Qian Li; Dean C. Barratt; Thomas Dowrick; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. 2024, IEEE Transactions on Biomedical Engineering 71(3):1033-1042; Peer-reviewed journal article; arXiv 2310.10248. DOI: [10.1109/TBME.2023.3325551](https://doi.org/10.1109/TBME.2023.3325551); arXiv: [2310.10248](https://arxiv.org/abs/2310.10248). [Nguồn chính](https://doi.org/10.1109/TBME.2023.3325551). Published journal version canonical; arXiv 2310.10248 recorded

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Long-history image-to-transform reconstruction |
| Observation → state | Past/future/delayed ultrasound image sequences → History-dependent rigid motion representation |
| Loại state / thông tin suy ra | Geometric/protocol-sensitive predictive feature; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None |
| Transition | Long-history transform prediction |
| Thời gian; future quantity | Frame to accumulated scan; Pairwise transforms and reconstructed volume |
| Horizon / rollout | Frame and accumulated reconstruction horizon; History window transform estimation |
| Evaluation / downstream | Frame/accumulated tracking, volume Dice and drift; history-length and protocol analyses; Improve trackerless 3D reconstruction |
| Dataset | Same UCL freehand ultrasound family; 19 volunteers, 38 forearms, 228 scans |
| Uncertainty | Not reported as calibrated predictive uncertainty |
| Planning đã xác minh | No |
| Project/repository | [official](https://discovery.ucl.ac.uk/id/eprint/10179008/) |
| Mức đọc / vị trí | Full publisher/HTML paper and UCL record; TBME methods/results; UCL record |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Explicit long-term dependency/history-length study. Giới hạn: No target observation forecasting; history gains confounded by acquisition protocol. Liên quan MedicalWorldModel: Requires protocol/coverage-matched memory ablations.

<a id="m47"></a>

## M47 — Privileged Anatomical and Protocol Discrimination in Trackerless 3D Ultrasound Reconstruction

**VERIFIED — hồ sơ nguồn:** Qi Li; Ziyi Shen; Qian Li; Dean C. Barratt; Thomas Dowrick; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. 2023, ASMUS 2023 / MICCAI LNCS 14337:142-151; Peer-reviewed workshop/proceedings paper; arXiv 2308.10293. DOI: [10.1007/978-3-031-44521-7_14](https://doi.org/10.1007/978-3-031-44521-7_14); arXiv: [2308.10293](https://arxiv.org/abs/2308.10293). [Nguồn chính](https://doi.org/10.1007/978-3-031-44521-7_14). Published LNCS version canonical; arXiv 2308.10293 recorded

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Image sequence reconstruction with privileged anatomy/protocol discrimination |
| Observation → state | Ultrasound sequence plus training-time anatomy/protocol labels → Predictive feature constrained to discriminate anatomy and protocol |
| Loại state / thông tin suy ra | Representation with auxiliary semantic/protocol supervision; not clinical state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None |
| Transition | Trackerless transform/reconstruction with auxiliary discriminators |
| Thời gian; future quantity | Scan-level accumulation; Frame/volume reconstruction and transform quality |
| Horizon / rollout | Accumulated scan reconstruction; Sequence reconstruction |
| Evaluation / downstream | Frame/volume reconstruction and error metrics; anatomy/protocol ablations; Improve trackerless 3D reconstruction |
| Dataset | Same 19-volunteer, six-protocol freehand ultrasound setting |
| Uncertainty | Not reported |
| Planning đã xác minh | No |
| Project/repository | [official](https://discovery.ucl.ac.uk/id/eprint/10178259/) |
| Mức đọc / vị trí | Accepted/full PDF and official UCL record; MICCAI/ASMUS paper methods and experiments |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Tests anatomy and protocol factors explicitly rather than treating latent as anatomy by default. Giới hạn: No future-view query or multi-step predictive anatomy evaluation. Liên quan MedicalWorldModel: Direct adversarial evidence against unverified claims that history latent equals anatomy state.

<a id="m48"></a>

## M48 — Nonrigid Reconstruction of Freehand Ultrasound Without a Tracker

**VERIFIED — hồ sơ nguồn:** Qi Li; Ziyi Shen; Qianye Yang; Dean C. Barratt; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. 2024, MICCAI 2024, LNCS 15004, pp. 689-699; Peer-reviewed conference paper; arXiv 2407.05767. DOI: [10.1007/978-3-031-72083-3_64](https://doi.org/10.1007/978-3-031-72083-3_64); arXiv: [2407.05767](https://arxiv.org/abs/2407.05767). [Nguồn chính](https://papers.miccai.org/miccai-2024/568-Paper2245.html). Published MICCAI version canonical; arXiv 2407.05767 recorded

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Rigid-plus-dense-deformation reconstruction |
| Observation → state | Ultrasound frames and optical rigid labels/landmarks during training/evaluation → Rigid pose plus dense deformation field |
| Loại state / thông tin suy ra | Geometric registration state; dense physical tissue state not independently observed; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None |
| Transition | Image registration and dense deformation estimation |
| Thời gian; future quantity | Within-scan; Nonrigid 3D reconstruction and deformation field |
| Horizon / rollout | Scan reconstruction; no future forecast; Registration-based reconstruction |
| Evaluation / downstream | GPE/GLE/LPE/LLE and reconstruction comparisons; Improve freehand ultrasound reconstruction under tissue deformation |
| Dataset | 60 volunteers, 720 scans, over 357K frames, about 500 frames/scan, subject split |
| Uncertainty | Not reported as calibrated |
| Planning đã xác minh | No |
| Project/repository | [official](https://github.com/QiLi111/NR-Rec-FUS) |
| Mức đọc / vị trí | Full PDF; official MICCAI page and code README; MICCAI paper methods/results and Tables 1-2 |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Introduces nonrigid reconstruction with dense deformation field. Giới hạn: No dense ground-truth deformation; rigid tracker labels/manual landmarks do not prove physical contact dynamics. Liên quan MedicalWorldModel: Weakens broad nonrigid-state novelty while leaving prefix forecast/contact separation open.

<a id="g33"></a>

## G33 — GenNBV: Generalizable Next-Best-View Policy for Active 3D Reconstruction

**VERIFIED — hồ sơ nguồn:** Xiao Chen; Quanyi Li; Tai Wang; Tianfan Xue; Jiangmiao Pang. 2024, CVPR 2024, pp. 16436-16445; Peer-reviewed conference paper; arXiv 2402.16174. DOI: UNKNOWN; arXiv: [2402.16174v3](https://arxiv.org/abs/2402.16174v3). [Nguồn chính](https://openaccess.thecvf.com/content/CVPR2024/html/Chen_GenNBV_Generalizable_Next-Best-View_Policy_for_Active_3D_Reconstruction_CVPR_2024_paper.html). Published CVPR version canonical; arXiv 2402.16174 recorded; DOI UNKNOWN

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Active RGB-D camera reconstruction environment |
| Observation → state | RGB-D, camera pose, history actions and scene occupancy/unknown state → Probabilistic occupied/free/unknown occupancy plus semantic/action embeddings |
| Loại state / thông tin suy ra | Geometric/uncertainty-aware scene state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | 5D free-space camera action in Isaac Gym |
| Transition | Environment transition provided by Isaac Gym; occupancy map updated with new observed depth; no learned forward world transition |
| Thời gian; future quantity | Discrete view/action steps; Next-best camera viewpoint from policy, not a predicted future scene |
| Horizon / rollout | Multi-step view budgets; Execute PPO policy in simulator, receive true simulated observation, update map each step |
| Evaluation / downstream | Coverage, AUC and Chamfer on Houses3K/OmniObject3D under budgets; Active next-best-view planning for 3D reconstruction |
| Dataset | Houses3K and OmniObject3D plus Isaac Gym simulator |
| Uncertainty | Probabilistic occupancy with occupied/free/unknown categories; no calibrated future-state uncertainty evaluation |
| Planning đã xác minh | Learned NBV view-selection policy; no search through learned imagined dynamics |
| Project/repository | [official](https://github.com/zjwzcx/GenNBV) |
| Mức đọc / vị trí | full methods/evaluation HTML + official CVF/project metadata; Root: arXiv v3 §§3.1–3.3, §4, Appendix A.1; CVF metadata |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Generalizable policy with uncertainty/unknown-space and budgeted multi-step evaluation. Giới hạn: Provided simulator and geometric ground truth; does not establish learned world simulation or transfer to medical contact/acquisition dynamics. Liên quan MedicalWorldModel: Transfer budgeted coverage/support evaluation; boundary case separating policy-in-simulator from a learned world model.

<a id="m49"></a>

## M49 — Automatic Probe Movement Guidance for Freehand Obstetric Ultrasound

**VERIFIED — hồ sơ nguồn:** Richard Droste; Lior Drukker; Aris T. Papageorghiou; J. Alison Noble. 2020, MICCAI 2020, LNCS 12263, pp. 583-592; Peer-reviewed conference paper; arXiv 2007.04480. DOI: [10.1007/978-3-030-59716-0_56](https://doi.org/10.1007/978-3-030-59716-0_56); arXiv: [2007.04480](https://arxiv.org/abs/2007.04480). [Nguồn chính](https://pmc.ncbi.nlm.nih.gov/articles/PMC7116254/). Published MICCAI version canonical; arXiv 2007.04480 recorded

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Freehand probe movement guidance |
| Observation → state | Ultrasound video and probe IMU → Probe/view guidance representation |
| Loại state / thông tin suy ra | Predictive guidance feature; not world state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | Probe movement guidance |
| Transition | Guidance prediction; no explicit learned world transition |
| Thời gian; future quantity | Video/acquisition episode; Probe movement/target view |
| Horizon / rollout | Guidance episodes; no named world-model rollout; Direct guidance prediction |
| Evaluation / downstream | Guidance accuracy on routine scans; Assist acquisition of standard obstetric views |
| Dataset | 464 examinations and 17 accredited sonographers, as reported by source |
| Uncertainty | Not reported |
| Planning đã xác minh | No explicit planning |
| Project/repository | [official](https://pmc.ncbi.nlm.nih.gov/articles/PMC7116254/) |
| Mức đọc / vị trí | Primary PMC full text and arXiv metadata; MICCAI paper methods/results; PMC full text |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Early clinical acquisition guidance prior to named medical WMs. Giới hạn: No explicit state-transition simulator or active planning evidence. Liên quan MedicalWorldModel: Adversarial prior against treating probe guidance alone as a new WM contribution.

<a id="m50"></a>

## M50 — RecON: Online learning for sensorless freehand 3D ultrasound reconstruction

**VERIFIED — hồ sơ nguồn:** Mingyuan Luo; Xin Yang; Hongzhang Wang; Haoran Dou; Xindi Hu; Yuhao Huang; Nishant Ravikumar; Songcheng Xu; Yuanji Zhang; Yi Xiong; Wufeng Xue; Alejandro F. Frangi; Dong Ni; Litao Sun. 2023, Medical Image Analysis 87, 102810; Peer-reviewed journal article. DOI: [10.1016/j.media.2023.102810](https://doi.org/10.1016/j.media.2023.102810); arXiv: UNKNOWN. [Nguồn chính](https://doi.org/10.1016/j.media.2023.102810). Published journal version; no arXiv record verified

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Online-adapted sensorless 3D reconstruction |
| Observation → state | Freehand ultrasound image sequences → Reconstruction feature/shape prior |
| Loại state / thông tin suy ra | Geometric reconstruction representation; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None |
| Transition | Online test-time adaptation with motion-weighted/pseudo-supervised reconstruction |
| Thời gian; future quantity | Within scan; 3D reconstruction |
| Horizon / rollout | Scan reconstruction; future query forecast not verified; Online adaptation/reconstruction |
| Evaluation / downstream | Reconstruction metrics as described by publisher/official code; Sensorless freehand 3D ultrasound reconstruction |
| Dataset | UNKNOWN from audited metadata |
| Uncertainty | UNKNOWN |
| Planning đã xác minh | No |
| Project/repository | [official](https://github.com/Lmy0217/RecON) |
| Mức đọc / vị trí | Publisher abstract, official code/README and metadata; not full methods; Publisher DOI page and official GitHub README |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Online learning with motion-weighted loss, pseudo-supervision and shape prior. Giới hạn: Not evidence of prefix-only target-view forecast; methods not used for stronger claim in this audit. Liên quan MedicalWorldModel: Adjacent reconstruction baseline and leakage risk via online adaptation.

<a id="m51"></a>

## M51 — TUS-REC2024: A Challenge to Reconstruct 3D Freehand Ultrasound Without External Tracker

**VERIFIED — hồ sơ nguồn:** Qi Li; Shaheer U. Saeed; Yuliang Huang; Mingyuan Luo; Zhongnuo Yan; Jiongquan Chen; Xin Yang; Dong Ni; Nektarios Winter; Phuc Nguyen; Lucas Steinberger; Caelan Haney; Yuan Zhao; Mingjie Jiang; Bowen Ren; SiYeoul Lee; Seonho Kim; MinKyung Seo; MinWoo Kim; Yimeng Dou; Zhiwei Zhang; Yin Li; Tomy Varghese; Dean C. Barratt; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. 2025, UNKNOWN; arXiv 2506.21765v2; arXiv challenge paper v2; venue UNKNOWN. DOI: UNKNOWN; arXiv: [2506.21765v2](https://arxiv.org/abs/2506.21765v2). [Nguồn chính](https://arxiv.org/html/2506.21765). v2 dated 2025-11-13; venue/DOI UNKNOWN; policy says CC BY NC SA/research-only

| Trường | Trích xuất có giới hạn từ nguồn |
| --- | --- |
| Hệ | Full-scan ultrasound-to-3D reconstruction with optical tracking |
| Observation → state | Temporally ordered ultrasound frames, tracked transforms and calibration → 3D reconstructed volume/displacement field |
| Loại state / thông tin suy ra | Geometric reconstruction state; not future predictive state; input như trên; không suy clinical meaning từ latent |
| Action / tác động làm state đổi | None in public benchmark schema; trajectory is measured |
| Transition | Reconstruction from scan sequence; no forecast transition |
| Thời gian; future quantity | 20 fps nominal; exact valid-frame horizon UNKNOWN; Global/local displacement and reconstructed volume |
| Horizon / rollout | Full scan; no prefix/query horizon in official task; Full-scan reconstruction |
| Evaluation / downstream | SIFT landmark/pixel GPE/GLE/LPE/LLE and runtime; subject split; Benchmark tracked freehand 3D ultrasound reconstruction |
| Dataset | 85 healthy volunteers, 2,040 scans, 24 scans/person; 20 fps, 480x640, optical tracker; 50/3/32 subject split |
| Uncertainty | Tracker RMS/repeatability reported; predictive uncertainty not evaluated |
| Planning đã xác minh | No |
| Project/repository | [official](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/) |
| Mức đọc / vị trí | Official data/task/assessment/policy pages, arXiv HTML §§2-4, Zenodo metadata; arXiv §§2-4; official data/task/assessment/policy; Zenodo Parts 1-2/validation |

**INTERPRETATION / HYPOTHESIS:** đóng góp nổi bật: Public acquisition/configuration/calibration and reconstruction benchmark metadata. Giới hạn: Exact per-scan duration/gaps, command/force logs and prefix future-query protocol are UNKNOWN. Liên quan MedicalWorldModel: Potential measured-pose query source only after metadata/access audit; does not support action-conditioned claim.
