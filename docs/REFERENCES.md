# Sổ nguồn tham khảo và xác minh

Cập nhật **2026-09-12** (Asia/Bangkok). **90 paper + 13 hồ sơ data release** trong survey. Mỗi paper có một ID thống nhất với [PAPER_MATRIX](PAPER_MATRIX.md) và [CSV](paper_matrix.csv). Dataset không được cộng thành paper hoặc trajectories nếu không đúng đơn vị.

## Lịch sử và mức bằng chứng

Ngày 2026-09-07, các REF-* là đầu mối từ thảo luận, chưa đối chiếu. Đợt 2026-09-12 đã đọc nguồn sơ cấp để nâng **phần metadata/method/data-card được chỉ rõ**; không nâng các trường UNKNOWN, không biến public description thành actual data access. Lịch sử khởi tạo còn trong [CHANGELOG](CHANGELOG.md) và commit trước.

**VERIFIED**: nguồn thật và claim trong phạm vi đọc; **INTERPRETATION / HYPOTHESIS**: tổng hợp/critique/gap. “Published” không có nghĩa nhóm tái lập hay claim causal đúng. Trường `read_depth` và source locator trong matrix giới hạn mức xác minh. Canonical dùng proceedings/journal khi xác minh được; arXiv giữ riêng, methods ở extended preprint không được gán toàn bộ vào short proceedings version. Trang publisher bị chặn dùng original arXiv + official institutional/proceedings metadata, ghi rõ trong version notes.

## Crosswalk từ sổ đầu mối 2026-09-07

| ID cũ | Hồ sơ hiện tại | Đã làm rõ; điều còn mở |
| --- | --- | --- |
| REF-A01 | [D01 TrackRAD](DATASET_FEASIBILITY.md#d01) | Data/paper metadata và release card; manifest/continuity/available labels UNKNOWN |
| REF-A02 | [M09](PAPER_MATRIX.md#m09) | Canonical CMIG 2026, direct horizon-specific forecast, prefix PCA; không tự AR rollout |
| REF-A03 | [M10](PAPER_MATRIX.md#m10) | Preprint có thật; full-cycle encoding khác prefix forecast |
| REF-B01 | [D05 TUS-REC2024](DATASET_FEASIBILITY.md#d05) | Data-page cohort/poses/terms; command/force/current test access UNKNOWN |
| REF-B02 | [M02](PAPER_MATRIX.md#m02) | CVPR 2025, measured pose feature prediction/guidance; public release UNKNOWN |
| REF-B03 | [M03](PAPER_MATRIX.md#m03) | arXiv v2 2026, real robot results nhưng force input không nằm trong WM; venue UNKNOWN |
| REF-C01 | [D06 LUMIERE](DATASET_FEASIBILITY.md#d06) | 638 study dates khác 2,487 MRI images; automated labels; full usable depth UNKNOWN |
| REF-C02 | [M05](PAPER_MATRIX.md#m05) | ICASSP 2025 canonical, extended arXiv methods; prefix preprocessing cần audit |
| REF-C03 | [M07](PAPER_MATRIX.md#m07) | ICLR 2026 camera-ready; patient trajectory không tự clinical state |
| REF-C04 | [M06](PAPER_MATRIX.md#m06) | TMI 2025; observational treatment prediction; external automask limitation |
| REF-K01 | [G03](PAPER_MATRIX.md#g03) | Nature 2025 canonical; arXiv 2023 title khác; model và actor khác nhau |
| REF-K02 | [K01](PAPER_MATRIX.md#k01) | ICML 2019; không suy clinical disentanglement chỉ từ latent |
| REF-K03 | [K02](PAPER_MATRIX.md#k02) | NeurIPS 2018, Bryan Lim; time-varying treatment-response methodology với simulation evidence |

## Nguồn paper đã đối chiếu

Các phần “hỗ trợ” dưới đây mô tả task/method được nguồn nghiên cứu; không mặc nhiên khẳng định hiệu quả lâm sàng. Contribution/limitation là phân tích trong matrix, không phải phát biểu đã được nguồn chứng minh.

### G01 — Recurrent World Models Facilitate Policy Evolution

David Ha; Jürgen Schmidhuber. **2018; NeurIPS 31; Published.** [Nguồn canonical/primary](https://proceedings.neurips.cc/paper/2018/hash/2de5d16682c3c35007e4e92982f1a2ba-Abstract.html); DOI UNKNOWN; [arXiv 1809.01999](https://arxiv.org/abs/1809.01999). Đối chiếu 2026-09-12. World Models (1803.10122) là bản sớm; NeurIPS dùng tên và ID 1809.01999

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu học policy trong mô hình. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G01](PAPER_MATRIX.md#g01).

### G02 — Learning Latent Dynamics for Planning from Pixels

Danijar Hafner; Timothy Lillicrap; Ian Fischer; Ruben Villegas; David Ha; Honglak Lee; James Davidson. **2019; ICML; PMLR 97; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v97/hafner19a.html); DOI UNKNOWN; [arXiv 1811.04551](https://arxiv.org/abs/1811.04551). Đối chiếu 2026-09-12. Không coi overshooting bắt buộc: supplement ghi không cần trong cấu hình cuối

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation và supplement; §2–4; supplement latent overshooting. Hỗ trợ nghiên cứu planning từ pixels. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G02](PAPER_MATRIX.md#g02).

### G03 — Mastering diverse control tasks through world models

Danijar Hafner; Jurgis Pasukonis; Jimmy Ba; Timothy Lillicrap. **2025; Nature 640:647–653; Published.** [Nguồn canonical/primary](https://www.nature.com/articles/s41586-025-08744-2); [DOI 10.1038/s41586-025-08744-2](https://doi.org/10.1038/s41586-025-08744-2); [arXiv 2301.04104](https://arxiv.org/abs/2301.04104). Đối chiếu 2026-09-12. arXiv tên Mastering Diverse Domains through World Models; published title canonical

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation; Methods: world model; actor–critic; benchmarks. Hỗ trợ nghiên cứu học actor–critic bằng imagined futures. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G03](PAPER_MATRIX.md#g03).

### G04 — Mastering Atari, Go, chess and shogi by planning with a learned model

Julian Schrittwieser; Ioannis Antonoglou; Thomas Hubert; Karen Simonyan; Laurent Sifre; Simon Schmitt; Arthur Guez; Edward Lockhart; Demis Hassabis; Thore Graepel; Timothy Lillicrap; David Silver. **2020; Nature 588:604–609; Published.** [Nguồn canonical/primary](https://www.nature.com/articles/s41586-020-03051-4); [DOI 10.1038/s41586-020-03051-4](https://doi.org/10.1038/s41586-020-03051-4); [arXiv 1911.08265](https://arxiv.org/abs/1911.08265). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu search without supplied simulator. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G04](PAPER_MATRIX.md#g04).

### G05 — Unsupervised Learning for Physical Interaction through Video Prediction

Chelsea Finn; Ian Goodfellow; Sergey Levine. **2016; NeurIPS 29; Published.** [Nguồn canonical/primary](https://papers.nips.cc/paper/6161-unsupervised-learning-for-physical-interaction-through-video-prediction); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu learn visual physical interaction. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G05](PAPER_MATRIX.md#g05).

### G06 — Stochastic Video Generation with a Learned Prior

Emily Denton; Rob Fergus. **2018; ICML; PMLR 80:1174–1183; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v80/denton18a.html); DOI UNKNOWN; [arXiv 1802.07687](https://arxiv.org/abs/1802.07687). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu plausible diverse future video. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G06](PAPER_MATRIX.md#g06).

### G07 — Transformers are Sample-Efficient World Models

Vincent Micheli; Eloi Alonso; François Fleuret. **2023; ICLR; Published.** [Nguồn canonical/primary](https://openreview.net/pdf?id=vhFu1Acb0xb); DOI UNKNOWN; [arXiv 2209.00588](https://arxiv.org/abs/2209.00588). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** PDF methods/evaluation; §2–4. Hỗ trợ nghiên cứu sample-efficient policy learning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G07](PAPER_MATRIX.md#g07).

### G08 — Diffusion for World Modeling: Visual Details Matter in Atari

Eloi Alonso; Adam Jelley; Vincent Micheli; Anssi Kanervisto; Amos Storkey; Tim Pearce; François Fleuret. **2024; NeurIPS 37; Published.** [Nguồn canonical/primary](https://proceedings.neurips.cc/paper_files/paper/2024/hash/6bdde0373d53d4a501249547084bed43-Abstract-Conference.html); [DOI 10.52202/079017-1873](https://doi.org/10.52202/079017-1873); [arXiv 2405.12399](https://arxiv.org/abs/2405.12399). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** PDF methods/evaluation; World model and Atari evaluation. Hỗ trợ nghiên cứu policy training. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G08](PAPER_MATRIX.md#g08).

### G09 — TD-MPC2: Scalable, Robust World Models for Continuous Control

Nicklas Hansen; Hao Su; Xiaolong Wang. **2024; ICLR; Published.** [Nguồn canonical/primary](https://openreview.net/pdf?id=Oxh5CstDJU); DOI UNKNOWN; [arXiv 2310.16828](https://arxiv.org/abs/2310.16828). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** PDF methods/evaluation; §3–4. Hỗ trợ nghiên cứu online MPC. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G09](PAPER_MATRIX.md#g09).

### G10 — SlotFormer: Unsupervised Visual Dynamics Simulation with Object-Centric Models

Ziyi Wu; Nikita Dvornik; Klaus Greff; Thomas Kipf; Animesh Garg. **2023; ICLR; Published.** [Nguồn canonical/primary](https://openreview.net/pdf?id=TFbwV6I0VLg); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** PDF methods; evaluation overview; §3 and downstream tasks. Hỗ trợ nghiên cứu reasoning and planning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G10](PAPER_MATRIX.md#g10).

### G11 — DINO-WM: World Models on Pre-trained Visual Features enable Zero-shot Planning

Gaoyue Zhou; Hengkai Pan; Yann LeCun; Lerrel Pinto. **2025; ICML; PMLR 267:79115–79135; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v267/zhou25t.html); DOI UNKNOWN; [arXiv 2411.04983](https://arxiv.org/abs/2411.04983). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation/appendix; §3–4; Appendix A.5.3. Hỗ trợ nghiên cứu image-goal planning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G11](PAPER_MATRIX.md#g11).

### G12 — V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Planning

Mido Assran (Mahmoud Assran trong PDF); Adrien Bardes; David Fan; Quentin Garrido; Russell Howes; Mojtaba Komeili; Matthew Muckley; Ammar Rizvi; Claire Roberts; Koustuv Sinha; Artem Zholus; Sergio Arnaud; Abha Gejji; Ada Martin; Francois Robert Hogan; Daniel Dugas; Piotr Bojanowski; Vasil Khalidov; Patrick Labatut; Francisco Massa; Marc Szafraniec; Kapil Krishnakumar; Yong Li; Xiaodong Ma; Sarath Chandar; Franziska Meier; Yann LeCun; Michael Rabbat; Nicolas Ballas. **2025; arXiv; venue peer-reviewed UNKNOWN; Preprint verified.** [Nguồn canonical/primary](https://arxiv.org/abs/2506.09985); DOI UNKNOWN; [arXiv 2506.09985v1](https://arxiv.org/abs/2506.09985v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3 and §4.3; §3 action-conditioned model; §4.3 limitations. Hỗ trợ nghiên cứu representation reuse and image-goal MPC. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G12](PAPER_MATRIX.md#g12).

### G13 — Genie: Generative Interactive Environments

Jake Bruce; Michael D Dennis; Ashley Edwards; Jack Parker-Holder; Yuge Shi; Edward Hughes; Matthew Lai; Aditi Mavalankar; Richie Steigerwald; Chris Apps; Yusuf Aytar; Sarah Maria Elisabeth Bechtle; Feryal Behbahani; Stephanie C.Y. Chan; Nicolas Heess; Lucy Gonzalez; Simon Osindero; Sherjil Ozair; Scott Reed; Jingwei Zhang; Konrad Zolna; Jeff Clune; Nando De Freitas; Satinder Singh; Tim Rocktäschel. **2024; ICML; PMLR 235:4603–4623; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v235/bruce24a.html); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** proceedings metadata/abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu interactive learned environments. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G13](PAPER_MATRIX.md#g13).

### G14 — Learning Interactive Real-World Simulators

Sherry Yang; Yilun Du; Kamyar Ghasemipour; Jonathan Tompson; Leslie Kaelbling; Dale Schuurmans; Pieter Abbeel. **2024; ICLR; Published.** [Nguồn canonical/primary](https://openreview.net/pdf/ebbd0d77e65c2e2ffb1eef300c8c55e4f2f27c86.pdf); DOI UNKNOWN; [arXiv 2310.06114](https://arxiv.org/abs/2310.06114). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; ICLR published PDF; abstract. Hỗ trợ nghiên cứu simulation for RL/planning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G14](PAPER_MATRIX.md#g14).

### G15 — Navigation World Models

Amir Bar; Gaoyue Zhou; Danny Tran; Trevor Darrell; Yann LeCun. **2025; CVPR:15791–15801; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2025/html/Bar_Navigation_World_Models_CVPR_2025_paper.html); DOI UNKNOWN; [arXiv 2412.03572](https://arxiv.org/abs/2412.03572). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation; Planning implementation; navigation evaluation. Hỗ trợ nghiên cứu image-goal navigation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G15](PAPER_MATRIX.md#g15).

### G16 — DriveDreamer: Towards Real-world-driven World Models for Autonomous Driving

Xiaofeng Wang; Zheng Zhu; Guan Huang; Xinze Chen; Jiagang Zhu; Jiwen Lu. **2024; ECCV; Published.** [Nguồn canonical/primary](https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/6416_ECCV_2024_paper.php); DOI UNKNOWN; [arXiv 2309.09777](https://arxiv.org/abs/2309.09777). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu driving simulation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G16](PAPER_MATRIX.md#g16).

### G17 — Vista: A Generalizable Driving World Model with High Fidelity and Versatile Controllability

Shenyuan Gao; Jiazhi Yang; Li Chen; Kashyap Chitta; Yihang Qiu; Andreas Geiger; Jun Zhang; Hongyang Li. **2024; NeurIPS; Published.** [Nguồn canonical/primary](https://proceedings.neurips.cc/paper_files/paper/2024/hash/a6a066fb44f2fe0d36cf740c873b8890-Abstract-Conference.html); [DOI 10.52202/079017-2906](https://doi.org/10.52202/079017-2906); [arXiv 2405.17398](https://arxiv.org/abs/2405.17398). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation/appendix; §3.3; §4.3; Appendix A/C/D. Hỗ trợ nghiên cứu simulation/action assessment. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G17](PAPER_MATRIX.md#g17).

### G18 — Learning to Simulate Complex Physics with Graph Networks

Alvaro Sanchez-Gonzalez; Jonathan Godwin; Tobias Pfaff; Rex Ying; Jure Leskovec; Peter Battaglia. **2020; ICML; PMLR119:8459–8468; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v119/sanchez-gonzalez20a.html); DOI UNKNOWN; [arXiv 2002.09405](https://arxiv.org/abs/2002.09405). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Paper simulation framework and rollout results. Hỗ trợ nghiên cứu physical simulation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G18](PAPER_MATRIX.md#g18).

### G19 — PhysGaussian: Physics-Integrated 3D Gaussians for Generative Dynamics

Tianyi Xie; Zeshun Zong; Yuxing Qiu; Xuan Li; Yutao Feng; Yin Yang; Chenfanfu Jiang. **2024; CVPR:4389–4398; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2024/html/Xie_PhysGaussian_Physics-Integrated_3D_Gaussians_for_Generative_Dynamics_CVPR_2024_paper.html); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu render physical simulation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G19](PAPER_MATRIX.md#g19).

### G20 — 4D Gaussian Splatting for Real-Time Dynamic Scene Rendering

Guanjun Wu; Taoran Yi; Jiemin Fang; Lingxi Xie; Xiaopeng Zhang; Wei Wei; Wenyu Liu; Qi Tian; Xinggang Wang. **2024; CVPR:20310–20320; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2024/html/Wu_4D_Gaussian_Splatting_for_Real-Time_Dynamic_Scene_Rendering_CVPR_2024_paper.html); DOI UNKNOWN; [arXiv 2310.08528](https://arxiv.org/abs/2310.08528). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu reconstruction/rendering. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G20](PAPER_MATRIX.md#g20).

### G21 — GeoWorld: Geometric World Models

Zeyu Zhang; Danning Li; Ian Reid; Richard Hartley. **2026; CVPR:30952–30963; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_GeoWorld_Geometric_World_Models_CVPR_2026_paper.html); DOI UNKNOWN; [arXiv 2602.23058](https://arxiv.org/abs/2602.23058). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu procedure planning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G21](PAPER_MATRIX.md#g21).

### G22 — Cosmos World Foundation Model Platform for Physical AI

NVIDIA: Niket Agarwal et al. (danh sách rút gọn; toàn bộ contributors tại arXiv). **2025; Technical report; Technical report / preprint.** [Nguồn canonical/primary](https://research.nvidia.com/publication/2025-01_cosmos-world-foundation-model-platform-physical-ai); DOI UNKNOWN; [arXiv 2501.03575](https://arxiv.org/abs/2501.03575). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu pretrain then adapt. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G22](PAPER_MATRIX.md#g22).

### G23 — DreamDojo: A Generalist Robot World Model from Large-Scale Human Videos

Shenyuan Gao; William Liang; Kaiyuan Zheng; Ayaan Malik; Seonghyeon Ye; Sihyun Yu; Wei-Cheng Tseng; Yuzhu Dong; Kaichun Mo; Chen-Hsuan Lin; Qianli Ma; Seungjun Nah; Loic Magne; Jiannan Xiang; Yuqi Xie; Ruijie Zheng; Dantong Niu; You Liang Tan; K. R. Zentner; George Kurian; Suneel Indupuru; Pooya Jannaty; Jinwei Gu; Jun Zhang; Jitendra Malik; Pieter Abbeel; Ming-Yu Liu; Yuke Zhu; Joel Jang; Linxi Jim Fan. **2026; ICML 2026 theo official repository; proceedings record UNKNOWN; Accepted/venue reported by authors; version read is preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2602.06949); DOI UNKNOWN; [arXiv 2602.06949v1](https://arxiv.org/abs/2602.06949v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3–4.7 and limitations; §4.7; §5; Table6. Hỗ trợ nghiên cứu policy evaluation and action proposal selection. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G23](PAPER_MATRIX.md#g23).

### G24 — Dyna-style planning with linear function approximation and prioritized sweeping

Richard S. Sutton; Csaba Szepesvári; Alborz Geramifard; Michael Bowling. **2008; UAI; PMLR R6:528–536; Published; PMLR reissue 2024.** [Nguồn canonical/primary](https://proceedings.mlr.press/r6/sutton08a.html); DOI UNKNOWN; [arXiv 1206.3285](https://arxiv.org/abs/1206.3285). Đối chiếu 2026-09-12. Original UAI 2008; arXiv upload 2012; PMLR reissue 2024 không đổi canonical year

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu online value/control learning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G24](PAPER_MATRIX.md#g24).

### G25 — Deep Predictive Coding Networks for Video Prediction and Unsupervised Learning

William Lotter; Gabriel Kreiman; David Cox. **2017; ICLR; Published; author lab confirms ICLR 2017.** [Nguồn canonical/primary](https://arxiv.org/abs/1605.08104v5); DOI UNKNOWN; [arXiv 1605.08104v5](https://arxiv.org/abs/1605.08104v5). Đối chiếu 2026-09-12. ICLR status: https://klab.tch.harvard.edu/resources/lotteretal_prednet.html ; original arXiv 2016, v5 2017

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu unsupervised visual representation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G25](PAPER_MATRIX.md#g25).

### G26 — Revisiting Feature Prediction for Learning Visual Representations from Video

Adrien Bardes; Quentin Garrido; Jean Ponce; Xinlei Chen; Michael Rabbat; Yann LeCun; Mahmoud Assran; Nicolas Ballas. **2024; arXiv; peer-reviewed venue UNKNOWN; Preprint verified.** [Nguồn canonical/primary](https://arxiv.org/abs/2404.08471v1); DOI UNKNOWN; [arXiv 2404.08471v1](https://arxiv.org/abs/2404.08471v1). Đối chiếu 2026-09-12. V-JEPA 2024; không gán ECCV khi proceedings chưa xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu learn reusable visual representation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ G26](PAPER_MATRIX.md#g26).

### K01 — Challenging Common Assumptions in the Unsupervised Learning of Disentangled Representations

Francesco Locatello; Stefan Bauer; Mario Lucic; Gunnar Raetsch; Sylvain Gelly; Bernhard Schölkopf; Olivier Bachem. **2019; ICML; PMLR97:4114–4124; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v97/locatello19a.html); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu test disentanglement assumptions. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ K01](PAPER_MATRIX.md#k01).

### K02 — Forecasting Treatment Responses Over Time Using Recurrent Marginal Structural Networks

Bryan Lim. **2018; NeurIPS31; Published.** [Nguồn canonical/primary](https://papers.nips.cc/paper_files/paper/2018/hash/56e6a93212e4482d99c84a639d254b67-Abstract.html); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** official abstract + original PDF; time-dependent confounding; causal assumptions and simulation. Hỗ trợ nghiên cứu adjust time-dependent confounding. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ K02](PAPER_MATRIX.md#k02).

### M01 — Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model

Haojun Jiang; Zhenguo Sun; Ning Jia; Meng Li; Yu Sun; Shaqi Luo; Shiji Song; Gao Huang. **2024; MICCAI; LNCS15001:190–199; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2024/118-Paper0053.html); [DOI 10.1007/978-3-031-72378-0_18](https://doi.org/10.1007/978-3-031-72378-0_18); [arXiv 2406.13165](https://arxiv.org/abs/2406.13165). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** canonical MICCAI PDF §2–3 methods/evaluation (round2); Abstract; author response items1,2,7; code/data N/A; Round2: PDF §§2.1-2.2, 3.1-3.4, Table 1; MICCAI page. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M01](PAPER_MATRIX.md#m01). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M02 — EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance

Yang Yue; Yulin Wang; Haojun Jiang; Pan Liu; Shiji Song; Gao Huang. **2025; CVPR; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2025/html/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.html); [DOI 10.1109/CVPR52734.2025.02421](https://doi.org/10.1109/CVPR52734.2025.02421); [arXiv 2504.13065v1](https://arxiv.org/abs/2504.13065v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3–5 and appendix; PDF visual inspection p4; §4.1–4.2; sequential protocol; Appendix dataset; Round2: arXiv §§4.1-5.1, Appendix A-B; CVPR PDF Tables 1-2. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M02](PAPER_MATRIX.md#m02). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M03 — Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound

Siqi Fan; Mingcong Chen; Ran Liu; Zixuan Yang; Xiaoyu Fu; Xiaoqing Gao; Yunhui Liu; Hongbin Liu. **2026; arXiv; peer-reviewed venue UNKNOWN; Preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2607.21918v2); DOI UNKNOWN; [arXiv 2607.21918v2](https://arxiv.org/abs/2607.21918v2). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §II–IV; Fig4; TableI; TableIV; Discussion; Round2: arXiv v2 §§II-A to II-C, III-A to III-D, IV, Tables I-III. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M03](PAPER_MATRIX.md#m03). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M04 — Medical World Model

Yijun Yang; Zhao-Yang Wang; Qiuping Liu; Shuwen Sun; Kang Wang; Rama Chellappa; Zongwei Zhou; Alan Yuille; Lei Zhu; Yu-Dong Zhang; Jieneng Chen. **2025; ICCV:8319–8329; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html); DOI UNKNOWN; [arXiv 2506.02327](https://arxiv.org/abs/2506.02327). Đối chiếu 2026-09-12. arXiv title adds Generative Simulation of Tumor Evolution for Treatment Planning; ICCV title canonical

**VERIFIED trong phạm vi đọc:** full-text §3 and evaluation/appendix; §3 forward/inverse dynamics; retrospective evaluation. Hỗ trợ nghiên cứu treatment candidate search. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M04](PAPER_MATRIX.md#m04).

### M05 — ImageFlowNet: Forecasting Multiscale Image-Level Trajectories of Disease Progression with Irregularly-Sampled Longitudinal Medical Images

Chen Liu; Ke Xu; Liangbo L. Shen; Guillaume Huguet; Zilong Wang; Alexander Tong; Danilo Bzdok; Jay Stewart; Jay C. Wang; Lucian V. Del Priore; Smita Krishnaswamy. **2025; ICASSP; Published.** [Nguồn canonical/primary](https://doi.org/10.1109/ICASSP49660.2025.10890535); [DOI 10.1109/ICASSP49660.2025.10890535](https://doi.org/10.1109/ICASSP49660.2025.10890535); [arXiv 2406.14794v6](https://arxiv.org/abs/2406.14794v6). Đối chiếu 2026-09-12. Canonical ICASSP 2025 short version; methods dùng extended arXiv v6. DOI/title/authors corroborated by Duke institutional record and official repository; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation/Appendix D,F; §5.5–5.6; AppendixD.1/D.3; Đợt 2: arXiv HTML preprocessing, datasets, evaluation and test-time optimization sections. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M05](PAPER_MATRIX.md#m05). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M06 — Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction

Qinghui Liu; Elies Fuster-Garcia; Ivar Thokle Hovden; Bradley J. MacIntosh; Edvard O. S. Grødem; Petter Brandal; Carles Lopez-Mateu; Donatas Sederevičius; Karoline Skogen; Till Schellhorn; Atle Bjørnerud; Kyrre Eeg Emblem. **2025; IEEE Transactions on Medical Imaging 44(6):2449–2462; Published.** [Nguồn canonical/primary](https://doi.org/10.1109/TMI.2025.3533038); [DOI 10.1109/TMI.2025.3533038](https://doi.org/10.1109/TMI.2025.3533038); [arXiv 2309.05406v5](https://arxiv.org/abs/2309.05406v5). Đối chiếu 2026-09-12. Canonical TMI 2025; arXiv v5 dùng cho methods. DOI metadata corroborated by UPV institutional record and PubMed 40031286; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

**VERIFIED trong phạm vi đọc:** full-text methods; §IV-A/B evaluation; §IV-A 18/5 patient split; external labels; training sampling; Đợt 2: arXiv HTML methods, local/external evaluation and treatment-day analysis; root re-read arXiv v5 §IV-A and §IV-C2. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M06](PAPER_MATRIX.md#m06). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M07 — Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation

Hao Chen; Rui Yin; Yifan Chen; Qi Chen; Chao Li. **2026; ICLR; Published.** [Nguồn canonical/primary](https://openreview.net/pdf/a1558b2e7d9494789fdd3057059dfbe2add8737e.pdf); DOI UNKNOWN; [arXiv 2512.09185v4](https://arxiv.org/abs/2512.09185v4). Đối chiếu 2026-09-12. v4 2026-06-17; ICLR publication verified in camera-ready header

**VERIFIED trong phạm vi đọc:** camera-ready metadata; full arXiv methods/evaluation; §3; §4.1; regional-change experiments; Đợt 2: arXiv HTML methods/evaluation; OpenReview camera-ready metadata. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M07](PAPER_MATRIX.md#m07). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M08 — Brain Latent Progression: Individual-based spatiotemporal disease progression on 3D Brain MRIs via latent diffusion

Lemuel Puglisi; Daniel C. Alexander; Daniele Ravì. **2025; Medical Image Analysis 106:103734; Published.** [Nguồn canonical/primary](https://doi.org/10.1016/j.media.2025.103734); [DOI 10.1016/j.media.2025.103734](https://doi.org/10.1016/j.media.2025.103734); [arXiv 2502.08560v2](https://arxiv.org/abs/2502.08560v2). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Canonical author metadata lists Puglisi, Alexander, Ravì; ADNI/AIBL study-group acknowledgement is not expanded as additional named authors.

**VERIFIED trong phạm vi đọc:** full-text methods §4; evaluation §5.6; §4.3–4.6; §5.5–5.7; Đợt 2: arXiv HTML methods, uncertainty evaluation and fast-progressor analysis. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M08](PAPER_MATRIX.md#m08). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M09 — Frame forecasting in cine MRI using the PCA respiratory motion model: comparing recurrent neural networks trained online and transformers

Michel Pohl; Mitsuru Uesaka; Hiroyuki Takahashi; Kazuyuki Demachi; Ritu Bhusal Chhatkuli. **2026; Computerized Medical Imaging and Graphics 131:102755; Published.** [Nguồn canonical/primary](https://www.sciencedirect.com/science/article/abs/pii/S0895611126000583); [DOI 10.1016/j.compmedimag.2026.102755](https://doi.org/10.1016/j.compmedimag.2026.102755); [arXiv 2410.05882v3](https://arxiv.org/abs/2410.05882v3). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** PDF methods/evaluation; visually inspected Table2; §2.2–2.4; Table2; §2.3.3; Round2 A audit §§2.2–2.3.3/Table2: prefix PCA/direct horizons. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M09](PAPER_MATRIX.md#m09). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M10 — A Latent ODE Approach to Spatiotemporal Modeling of Cine Cardiac MRI

David Brüggemann; Ekaterina Krymova; Firat Özdemir; Jochen von Spiczak; Sebastian Kozerke; Samia Mora; Robert Manka; Mathieu Salzmann; Olga V. Demler. **2026; arXiv; venue UNKNOWN; Preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2606.26718); DOI UNKNOWN; [arXiv 2606.26718v1](https://arxiv.org/abs/2606.26718v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3.5, evaluation and AppendixB; §3.5 encoder; downstream Cox analysis. Hỗ trợ nghiên cứu spatiotemporal representation and risk association. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M10](PAPER_MATRIX.md#m10).

### M11 — 4D CardioSynth: Synthesising Dynamic Virtual Heart Populations Through Spatiotemporal Disentanglement

Haoran Dou; Jinghan Huang; Arezoo Zakeri; Zherui Zhou; Tingting Mu; Jinming Duan; Alejandro F. Frangi. **2025; MICCAI 2025:3–12; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2025/0004-Paper2701.html); [DOI 10.1007/978-3-032-04947-6_1](https://doi.org/10.1007/978-3-032-04947-6_1); arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Crossref: online 2025-09-21, print 2026; canonical conference year giữ 2025.

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu virtual cohorts. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M11](PAPER_MATRIX.md#m11).

### M12 — MRI Contrast Enhancement Kinetics World Model

Jindi Kong; Yuting He; Cong Xia; Rongjun Ge; Shuo Li. **2026; CVPR:1288–1299; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2026/html/Kong_MRI_Contrast_Enhancement_Kinetics_World_Model_CVPR_2026_paper.html); DOI UNKNOWN; [arXiv 2602.19285](https://arxiv.org/abs/2602.19285). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3–4; §3.1; Eq3–4; §4.1.1 cSSIM; Fig6. Hỗ trợ nghiên cứu virtual contrast phases. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M12](PAPER_MATRIX.md#m12).

### M13 — X-WIN: Building Chest Radiograph World Model via Predictive Sensing

Zefan Yang; Ge Wang; James Hendler; Mannudeep K. Kalra; Pingkun Yan. **2026; CVPR:6920–6930; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2026/html/Yang_X-WIN_Building_Chest_Radiograph_World_Model_via_Predictive_Sensing_CVPR_2026_paper.html); DOI UNKNOWN; [arXiv 2511.14918](https://arxiv.org/abs/2511.14918). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu representation learning. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M13](PAPER_MATRIX.md#m13).

### M14 — Surgical Vision World Model

Saurabh Koju; Saurav Bastola; Prashant Shrestha; Sanskar Amgain; Yash Raj Shrestha; Rudra P. K. Poudel; Binod Bhattarai. **2025; DEMI workshop at MICCAI:1–10; Published workshop chapter.** [Nguồn canonical/primary](https://doi.org/10.1007/978-3-032-08009-7_1); [DOI 10.1007/978-3-032-08009-7_1](https://doi.org/10.1007/978-3-032-08009-7_1); [arXiv 2503.02904](https://arxiv.org/abs/2503.02904). Đối chiếu 2026-09-12. DEMI workshop chapter verified author page https://saurabhkoju.com.np/publications/ + Springer book; chapter resolver error; methods scope from arXiv. Not MICCAI main.

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu controllable surgery video simulation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M14](PAPER_MATRIX.md#m14).

### M15 — SAW: Toward a Surgical Action World Model via Controllable and Scalable Video Generation

Sampath Rapuri; Lalithkumar Seenivasan; Dominik Schneider; Roger Soberanis-Mukul; Yufan He; Hao Ding; Jiru Xu; Chenhao Yu; Chenyan Jing; Pengfei Guo; Daguang Xu; Mathias Unberath. **2026; arXiv; venue UNKNOWN; Preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2603.13024); DOI UNKNOWN; [arXiv 2603.13024](https://arxiv.org/abs/2603.13024). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu data augmentation/recognition. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M15](PAPER_MATRIX.md#m15).

### M16 — Cosmos-Surg-dVRK: World Foundation Model-based Automated Online Evaluation of Surgical Robot Policy Learning

Lukas Zbinden; Nigel Nelson; Juo-Tung Chen; Xinhao Chen; Ji Woong Kim; Mahdi Azizian; Axel Krieger; Sean Huver. **2025; arXiv; venue UNKNOWN; Preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2510.16240v2); DOI UNKNOWN; [arXiv 2510.16240v2](https://arxiv.org/abs/2510.16240v2). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text system/evaluation; §5.2–5.3; Table1–3; §5.2.3 hallucinations; §5.3 ex-vivo. Hỗ trợ nghiên cứu evaluate policies without physical reruns. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M16](PAPER_MATRIX.md#m16).

### M17 — Continuous-Time Deep Glioma Growth Models

Jens Petersen; Fabian Isensee; Gregor Köhler; Paul F. Jäger; David Zimmerer; Ulf Neuberger; Wolfgang Wick; Jürgen Debus; Sabine Heiland; Martin Bendszus; Philipp Vollmuth; Klaus H. Maier-Hein. **2021; MICCAI; LNCS12903:83–92; Published.** [Nguồn canonical/primary](https://doi.org/10.1007/978-3-030-87199-4_8); [DOI 10.1007/978-3-030-87199-4_8](https://doi.org/10.1007/978-3-030-87199-4_8); [arXiv 2106.12917v2](https://arxiv.org/abs/2106.12917v2). Đối chiếu 2026-09-12. Canonical MICCAI 2021; full methods read in arXiv 2106.12917v2; publisher book metadata corroborated by DKFZ institutional repository.

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation; §2.1–2.2; Query Volume Dice; Đợt 2: arXiv HTML abstract, methods and evaluation; Query Volume Dice. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M17](PAPER_MATRIX.md#m17). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M18 — Learning Spatio-Temporal Model of Disease Progression With NeuralODEs From Longitudinal Volumetric Data

Dmitrii Lachinov; Arunava Chakravarty; Christoph Grechenig; Ursula Schmidt-Erfurth; Hrvoje Bogunović. **2024; IEEE TMI 43(3):1165–1179; Published; online 2023, issue 2024.** [Nguồn canonical/primary](https://doi.org/10.1109/TMI.2023.3330576); [DOI 10.1109/TMI.2023.3330576](https://doi.org/10.1109/TMI.2023.3330576); [arXiv 2211.04234](https://arxiv.org/abs/2211.04234). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §II and evaluation design; §II initial value problem; temporal Dice; TADPOLE evaluation; Đợt 2: arXiv full text methods and evaluation; published DOI. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M18](PAPER_MATRIX.md#m18). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M19 — Probabilistic Temporal Prediction of Continuous Disease Trajectories and Treatment Effects Using Neural SDEs

Joshua Durso-Finley; Berardino Barile; Jean-Pierre Falet; Douglas L. Arnold; Nick Pawlowski; Tal Arbel. **2024; MICCAI; LNCS15003:400–410; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2024/619-Paper3431.html); [DOI 10.1007/978-3-031-72384-1_38](https://doi.org/10.1007/978-3-031-72384-1_38); [arXiv 2406.12807v1](https://arxiv.org/abs/2406.12807v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §2–3; §2.2 potential outcomes/RCT independence; §3 trials; Đợt 2: MICCAI official paper page and arXiv §§2–3. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M19](PAPER_MATRIX.md#m19). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M20 — Predictive digital twins with quantified uncertainty for patient-specific decision making in oncology

Graham Pash; Umberto Villa; David A. Hormuth II; Thomas E. Yankeelov; Karen Willcox. **2026; Journal of Computational Physics 560:114937; Published 2026-09-01.** [Nguồn canonical/primary](https://www.sciencedirect.com/science/article/pii/S0021999126002901); [DOI 10.1016/j.jcp.2026.114937](https://doi.org/10.1016/j.jcp.2026.114937); [arXiv 2505.08927](https://arxiv.org/abs/2505.08927). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3–5; §4.3; §5.1–5.3; AppendixC; Đợt 2: arXiv HTML §§3–5 and Appendix C; published DOI metadata. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M20](PAPER_MATRIX.md#m20). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M21 — Online prediction for respiratory movement compensation: a patient-specific gating control for MRI-guided radiotherapy

Yang Li; Zhenjiang Li; Jian Zhu; Baosheng Li; Huazhong Shu; Di Ge. **2023; Radiation Oncology 18:149; Published.** [Nguồn canonical/primary](https://doi.org/10.1186/s13014-023-02341-1); [DOI 10.1186/s13014-023-02341-1](https://doi.org/10.1186/s13014-023-02341-1); arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full PMC methods/evaluation (round2); https://d-nb.info/1318665426/34; Methods; A audit: linear prediction, crossing/gating error and prediction timing. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M21](PAPER_MATRIX.md#m21). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M22 — Real-time prediction and gating of respiratory motion using an extended Kalman filter and Gaussian process regression

W. Bukhari; S.-M. Hong. **2015; Physics in Medicine & Biology 60(1):233–252; Published; epub 2014.** [Nguồn canonical/primary](https://pubmed.ncbi.nlm.nih.gov/25489980/); [DOI 10.1088/0031-9155/60/1/233](https://doi.org/10.1088/0031-9155/60/1/233); arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** indexed original abstract/metadata; Trang nguồn/abstract. Hỗ trợ nghiên cứu gate high-risk prediction periods. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M22](PAPER_MATRIX.md#m22).

### M23 — Freehand Ultrasound Image Simulation with Spatially-Conditioned Generative Adversarial Networks

Yipeng Hu; Eli Gibson; Li-Lin Lee; Weidi Xie; Dean C. Barratt; Tom Vercauteren; J. Alison Noble. **2017; RAMBO at MICCAI; Accepted/published chapter DOI recorded.** [Nguồn canonical/primary](https://arxiv.org/abs/1707.05392); [DOI 10.1007/978-3-319-67564-0_11](https://doi.org/10.1007/978-3-319-67564-0_11); [arXiv 1707.05392v1](https://arxiv.org/abs/1707.05392v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** author PDF §2.1–2.3 and §3 methods/evaluation (round2); Trang nguồn/abstract; Round2: PDF §§2.1-2.3, 3-4; UCL record. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M23](PAPER_MATRIX.md#m23). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

### M24 — A technical assessment of latent diffusion for Alzheimer's disease progression

Elyssa M. McMaster; Lemuel Puglisi; Chenyu Gao; Aravind R. Krishnan; Adam M. Saunders; Daniele Ravi; Lori L. Beason-Held; Susan M. Resnick; Lianrui Zuo; Daniel Moyer; Bennett A. Landman. **2025; SPIE Medical Imaging; Proc SPIE13406:1340621; Published proceedings.** [Nguồn canonical/primary](https://pmc.ncbi.nlm.nih.gov/articles/PMC12726967/); [DOI 10.1117/12.3047135](https://doi.org/10.1117/12.3047135); arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** original full-text search extraction methods/abstract; Abstract; §2 methodology; diagnostic-condition comparison. Hỗ trợ nghiên cứu external validity assessment. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M24](PAPER_MATRIX.md#m24).

### M25 — A radiographic world model for clinical reasoning and evidence generation

Suyang Xi; Songtao Hu; Shansong Wang; Mojtaba Safari; Luke del Balzo; Ehsan Ul Karim; Mingzhe Hu; Kuo Zhang; Tonghe Wang; Ralph R. Weichselbaum; Xiaofeng Yang. **2026; arXiv; venue UNKNOWN; Preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2609.07719); DOI UNKNOWN; [arXiv 2609.07719](https://arxiv.org/abs/2609.07719). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu clinical reasoning representation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M25](PAPER_MATRIX.md#m25).

### M26 — World Model for AI Autonomous Navigation in Mechanical Thrombectomy

Harry Robertshaw; Han-Ru Wu; Alejandro Granados; Thomas C. Booth. **2025; MICCAI; LNCS15968:680–690; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2025/1021-Paper3014.html); [DOI 10.1007/978-3-032-05114-1_65](https://doi.org/10.1007/978-3-032-05114-1_65); [arXiv 2509.25518](https://arxiv.org/abs/2509.25518). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Crossref: online 2025-09-21, print 2026; canonical conference year giữ 2025.

**VERIFIED trong phạm vi đọc:** official metadata/abstract; methods details not used; Trang nguồn/abstract. Hỗ trợ nghiên cứu thrombectomy navigation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M26](PAPER_MATRIX.md#m26).

### M27 — Combining Biology-based and MRI Data-driven Modeling to Predict Response to Neoadjuvant Chemotherapy in Patients with Triple-Negative Breast Cancer

Casey E. Stowers; Chengyue Wu; Zhan Xu; Sidharth Kumar; Clinton Yam; Jong Bum Son; Jingfei Ma; Jonathan I. Tamir; Gaiane M. Rauch; Thomas E. Yankeelov. **2025; Radiology: Artificial Intelligence 7(1):e240124; Published; online 2024, issue 2025.** [Nguồn canonical/primary](https://pubs.rsna.org/doi/10.1148/ryai.240124); [DOI 10.1148/ryai.240124](https://doi.org/10.1148/ryai.240124); arXiv UNKNOWN. Đối chiếu 2026-09-12. RSNA PDF ghi issue 2025, copyright/online 2024

**VERIFIED trong phạm vi đọc:** original PDF methods/evaluation pp2–5; Mathematical Model; CNN Inputs and Outputs; Patient Demographics; pCR subset; Đợt 2: RSNA primary HTML abstract, key points and Materials and Methods patient data. Hỗ trợ mô tả observation/state/transition/evaluation trong [hồ sơ M27](PAPER_MATRIX.md#m27). Các limitation/relevance là INTERPRETATION / HYPOTHESIS, không mở causal/clinical claim.

## Nguồn dữ liệu và tài liệu gốc

Mọi license/count/time/label dưới đây chỉ sử dụng ở phạm vi ghi trong [DATASET_FEASIBILITY](DATASET_FEASIBILITY.md); fields còn thiếu giữ UNKNOWN. Ngày đọc: 2026-09-12.

| ID | Nguồn primary / định danh | Phiên bản và phạm vi đã đọc |
| --- | --- | --- |
| D01 | [TrackRAD data card](https://huggingface.co/datasets/LMUK-RADONC-PHYS-RES/TrackRAD2025); data DOI 10.57967/hf/4539; [Yiling Wang et al., TrackRAD2025 challenge dataset: Real-time tumor tracking for MRI-guided radiotherapy](https://arxiv.org/abs/2503.19119v2); Medical Physics DOI 10.1002/mp.17964 | Card có update January 2026; paper v2; counts/splits/cadence sidecar, không manifest audit |
| D02 | [EchoNet-Dynamic](https://echonet.github.io/dynamic/); [David Ouyang et al., Video-based AI for beat-to-beat assessment of cardiac function, Nature 2020](https://doi.org/10.1038/s41586-020-2145-8) | Dataset site, terms/instructions, label description; paper không phải forecasting study |
| D03 | [ACDC database](https://www.creatis.insa-lyon.fr/Challenge/acdc/databases.html); [Olivier Bernard et al., original TMI paper](https://www.creatis.insa-lyon.fr/Challenge/acdc/files/tmi_2018_bernard.pdf) | 150-exam release description; cycle/ED/ES labels; license/headers UNKNOWN |
| D04 | [4D-LUNG TCIA](https://www.cancerimagingarchive.net/collection/4d-lung/); DOI 10.7937/K9/TCIA.2016.ELN8YGLE | Collection v2 2016-10-19; collection counts/license, không true-time audit |
| D05 | [TUS-REC2024 data](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/data.html), [policies](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/policies.html); [Qi Li et al., TUS-REC2024: A Challenge to Reconstruct 3D Freehand Ultrasound Without External Tracker](https://arxiv.org/abs/2506.21765v2) | 2025 preprint v2, venue UNKNOWN; 2024 challenge data ≠ 2024 paper publication. [Zenodo item](https://zenodo.org/records/11178509) |
| D06 | [Yannick Suter et al., The LUMIERE dataset: Longitudinal Glioblastoma MRI with expert RANO evaluation, Scientific Data 9:768, 2022](https://www.nature.com/articles/s41597-022-01881-7); [MRI data item](https://springernature.figshare.com/articles/dataset/LUMIERE_dataset_-_MRI_data_and_automated_segmentations/21249516) | Paper DOI 10.1038/s41597-022-01881-7; collection 10.6084/m9.figshare.c.5904905; original study/counts/label provenance; data CC0 |
| D07 | [ISBI MS challenge data](https://iacl.ece.jhu.edu/index.php/MSChallenge/data) | Official training/test subject/visit/label/preprocessing description; current account/license UNKNOWN |
| D08 | [OASIS imaging dictionary v2.3](https://sites.wustl.edu/oasisbrains/files/2024/04/OASIS-3_Imaging_Data_Dictionary_v2.3-a93c947a586e7367.pdf) | Table3, release 2.0 July 2022; discrepancy với homepage giữ trong D08 |
| D09 | [ADNI access](https://adni.loni.usc.edu/data-samples/adni-data/), [FAQ](https://adni.loni.usc.edu/help-faqs/faqs/) | Access/DUA và actual date guidance; chưa xác định analysis cohort |
| D10 | [HCC-TACE-Seg TCIA](https://www.cancerimagingarchive.net/collection/hcc-tace-seg/); [Multimodality annotated hepatocellular carcinoma data set including pre- and post-TACE with imaging segmentation](https://doi.org/10.1038/s41597-023-01928-3), Scientific Data 2023 | Data DOI 10.7937/TCIA.5FNA-0924; release v1; collection/paper counts có đơn vị khác nhau |
| D11 | [I-SPY2 TCIA](https://www.cancerimagingarchive.net/collection/ispy2/); [DCE/DWI description](https://www.cancerimagingarchive.net/wp-content/uploads/ACRIN-6698-ISPY2-DWI-and-DCE-MRI-Data-Descriptions_20210520.pdf) | Collection v1 2022-05-02; cohort composition/labels/access; individual timeline UNKNOWN |
| D12 | [CFB-GBM TCIA](https://www.cancerimagingarchive.net/collection/cfb-gbm/); [Alexandre G. Leclercq et al., CFB-GBM v2.0: An Augmented Longitudinal Dataset for Multi-Modal Glioblastoma Segmentation, Radiomics, and RANO Progression Tracking](https://arxiv.org/abs/2608.17884v1) | Collection v3 2026-06-26; paper v1 2026 preprint, peer-reviewed venue UNKNOWN; Table3 không cho patient intersection |
| D13 | [Duke Breast Cancer MRI TCIA](https://www.cancerimagingarchive.net/collection/duke-breast-cancer-mri/); DOI 10.7937/TCIA.e3sv-re93 | Collection subjects/intravisit DCE; license/phases/timestamps chưa đủ xác minh |

## Kiểm tra integrity và giới hạn

Xem [RESEARCH_LOG](surveys/RESEARCH_LOG.md) cho DOI checks, corrected metadata, access errors, phương pháp skill và adversarial prior-art results. Không sử dụng survey thứ cấp làm bằng chứng duy nhất cho claim quan trọng; secondary indexes dùng discovery/corroboration, còn methods từ paper gốc. Nguồn chưa đọc methods không được dùng để khẳng định chi tiết methods ngoài abstract đã thấy. Đợt 2 đã có aggregate metadata audit cho LUMIERE/BreastDCEDL; chưa đọc ảnh, chưa code/model replication hoặc clinical validation.

## Bổ sung đợt 2 — state, benchmark và uncertainty

Đối chiếu 2026-09-12; methods audit tại [STATE_AND_EVALUATION_AUDIT](surveys/deep_dives/STATE_AND_EVALUATION_AUDIT.md). Benchmark/methodology papers không được coi là mô hình sinh học; các trường không áp dụng ghi N/A.

### G27 — Predictive Representations of State

Michael L. Littman; Richard S. Sutton; Satinder Singh. **2001; NeurIPS 14; Published.** [Nguồn canonical/primary](https://proceedings.neurips.cc/paper/2001/hash/1e4d36177d71bbb3558e43af9577d70e-Abstract.html); DOI UNKNOWN; arXiv UNKNOWN. Đối chiếu 2026-09-12. conference year 2001; proceedings volume 14; no invented DOI

**VERIFIED trong phạm vi đọc:** full original PDF §1–3, Theorem 1; §1 Eq1–3; Theorem1; conclusion. Phạm vi prediction/evaluation tại [hồ sơ G27](PAPER_MATRIX.md#g27); không suy clinical utility/causality ngoài bằng chứng đó.

### G28 — WorldSimBench: Towards Video Generation Models as World Simulators

Yiran Qin; Zhelun Shi; Jiwen Yu; Xijun Wang; Enshen Zhou; Lijun Li; Zhenfei Yin; Xihui Liu; Lu Sheng; Jing Shao; Lei Bai; Ruimao Zhang. **2025; ICML; PMLR 267:50338–50362; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v267/qin25f.html); DOI UNKNOWN; [arXiv 2410.18072](https://arxiv.org/abs/2410.18072). Đối chiếu 2026-09-12. arXiv first posted 2024; proceedings canonical 2025; author list differs (arXiv includes Wanli Ouyang)

**VERIFIED trong phạm vi đọc:** canonical proceedings PDF methods/evaluation, rendered page; §3.2; Fig3; §4.1; pp6–7. Phạm vi prediction/evaluation tại [hồ sơ G28](PAPER_MATRIX.md#g28); không suy clinical utility/causality ngoài bằng chứng đó.

### G29 — WorldModelBench: Judging Video Generation Models As World Models

Dacheng Li; Yunhao Fang; Yukang Chen; Shuo Yang; Shiyi Cao; Justin Wong; Michael Luo; Xiaolong Wang; Hongxu Yin; Joseph E. Gonzalez; Ion Stoica; Song Han; Yao Lu. **2025; NeurIPS 38, Datasets and Benchmarks Track; Published.** [Nguồn canonical/primary](https://proceedings.neurips.cc/paper_files/paper/2025/hash/4ec03ed08a3fcb59e1c815b5598beff1-Abstract-Datasets_and_Benchmarks_Track.html); [DOI 10.52202/085713-1834](https://doi.org/10.52202/085713-1834); [arXiv 2502.20694](https://arxiv.org/abs/2502.20694). Đối chiếu 2026-09-12. canonical published abstract differs from initial arXiv performance wording; no numbers mixed

**VERIFIED trong phạm vi đọc:** canonical NeurIPS PDF §3–4 plus arXiv full HTML; §3.1 grading; §3.2 curation; §3.3 judge; §4. Phạm vi prediction/evaluation tại [hồ sơ G29](PAPER_MATRIX.md#g29); không suy clinical utility/causality ngoài bằng chứng đó.

### G30 — WorldArena: A Unified Benchmark for Evaluating Perception and Functional Utility of Embodied World Models

Yu Shang; Zhuohang Li; Yiding Ma; Weikang Su; Xin Jin; Ziyou Wang; Lei Jin; Xin Zhang; Yinzhou Tang; Haisheng Su; Chen Gao; Wei Wu; Xihui Liu; Dhruv Shah; Zhaoxiang Zhang; Zhibo Chen; Jun Zhu; Yonghong Tian; Tat-Seng Chua; Wenwu Zhu; Yong Li. **2026; arXiv; peer-reviewed venue UNKNOWN; Preprint verified.** [Nguồn canonical/primary](https://arxiv.org/abs/2602.08971v2); DOI UNKNOWN; [arXiv 2602.08971v2](https://arxiv.org/abs/2602.08971v2). Đối chiếu 2026-09-12. v2 adds authors relative to indexed v1; challenge affiliation is not main-conference publication

**VERIFIED trong phạm vi đọc:** full HTML §3–4 and Appendix A/B; §3.2–3.4; Appendix A.11–A.17/B. Phạm vi prediction/evaluation tại [hồ sơ G30](PAPER_MATRIX.md#g30); không suy clinical utility/causality ngoài bằng chứng đó.

### G31 — WorldArena 2.0: Extending Embodied World Model Benchmarking on Modality, Functionality and Platform

Yu Shang; Yinzhou Tang; Yiding Ma; Zhuohang Li; Lei Jin; Weikang Su; Xin Jin; Zhaolu Wang; Ziyou Wang; Xin Zhang; Haisheng Su; Weizhen He; Wei Wu; Haoyi Duan; Gordon Wetzstein; Xihui Liu; Dhruv Shah; Zhaoxiang Zhang; Zhibo Chen; Jun Zhu; Yonghong Tian; Tat-Seng Chua; Wenwu Zhu; Chen Gao; Yong Li. **2026; arXiv; peer-reviewed venue UNKNOWN; Preprint verified.** [Nguồn canonical/primary](https://arxiv.org/abs/2605.17912v1); DOI UNKNOWN; [arXiv 2605.17912v1](https://arxiv.org/abs/2605.17912v1). Đối chiếu 2026-09-12. v1 May 2026; live leaderboard has later scoring updates; paper audit is version-specific

**VERIFIED trong phạm vi đọc:** full HTML §3–4 and Tables1–3; §3.2 UniVTAC; §3.3 RL; §4.1–4.3. Phạm vi prediction/evaluation tại [hồ sơ G31](PAPER_MATRIX.md#g31); không suy clinical utility/causality ngoài bằng chứng đó.

### G32 — Do Generative Video Models Understand Physical Principles?

Saman Motamed; Laura Culp; Kevin Swersky; Priyank Jaini; Robert Geirhos. **2026; WACV:948–958; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/WACV2026/html/Motamed_Do_Generative_Video_Models_Understand_Physical_Principles_WACV_2026_paper.html); DOI UNKNOWN; [arXiv 2501.09038v3](https://arxiv.org/abs/2501.09038v3). Đối chiếu 2026-09-12. arXiv v3 February 2025; WACV 2026 canonical publication

**VERIFIED trong phạm vi đọc:** canonical CVF PDF §2.2–2.5, §4; rendered protocol figure; Fig2; §2.5; discussion of metric limitations. Phạm vi prediction/evaluation tại [hồ sơ G32](PAPER_MATRIX.md#g32); không suy clinical utility/causality ngoài bằng chứng đó.

### K03 — Strictly Proper Scoring Rules, Prediction, and Estimation

Tilmann Gneiting; Adrian E. Raftery. **2007; Journal of the American Statistical Association 102(477):359–378; Published.** [Nguồn canonical/primary](https://doi.org/10.1198/016214506000001437); [DOI 10.1198/016214506000001437](https://doi.org/10.1198/016214506000001437); arXiv UNKNOWN. Đối chiếu 2026-09-12. canonical JASA 2007, author-hosted original PDF

**VERIFIED trong phạm vi đọc:** author PDF §4.2–4.3, §6; CRPS §4.2; energy score Eq22 and moment conditions; interval scores §6. Phạm vi prediction/evaluation tại [hồ sơ K03](PAPER_MATRIX.md#k03); không suy clinical utility/causality ngoài bằng chứng đó.

### K04 — Variogram-Based Proper Scoring Rules for Probabilistic Forecasts of Multivariate Quantities

Michael Scheuerer; Thomas M. Hamill. **2015; Monthly Weather Review 143(4):1321–1334; Published.** [Nguồn canonical/primary](https://doi.org/10.1175/MWR-D-14-00269.1); [DOI 10.1175/MWR-D-14-00269.1](https://doi.org/10.1175/MWR-D-14-00269.1); arXiv UNKNOWN. Đối chiếu 2026-09-12. title footnote asterisk omitted; DOI confirmed, issue April 2015

**VERIFIED trong phạm vi đọc:** original NOAA PDF §2–3, §5; §2 propriety/limitations; §3 correlation experiments; §5. Phạm vi prediction/evaluation tại [hồ sơ K04](PAPER_MATRIX.md#k04); không suy clinical utility/causality ngoài bằng chứng đó.

### K05 — Conformalized Adaptive Forecasting of Heterogeneous Trajectories

Yanfei Zhou; Lars Lindemann; Matteo Sesia. **2024; ICML; PMLR 235:62002–62056; Published.** [Nguồn canonical/primary](https://proceedings.mlr.press/v235/zhou24l.html); DOI UNKNOWN; [arXiv 2402.09623](https://arxiv.org/abs/2402.09623). Đối chiếu 2026-09-12. ICML 2024 canonical; arXiv tracked separately

**VERIFIED trong phạm vi đọc:** canonical PDF §2–3, Theorem1, Appendix A6; §2.1 observation timing; §2.2 marginal limitation; Theorem1; A6. Phạm vi prediction/evaluation tại [hồ sơ K05](PAPER_MATRIX.md#k05); không suy clinical utility/causality ngoài bằng chứng đó.

### K06 — Metrics reloaded: recommendations for image analysis validation

Lena Maier-Hein; Annika Reinke; Patrick Godau; Minu D. Tizabi; Florian Buettner; Evangelia Christodoulou; Ben Glocker; Fabian Isensee; Jens Kleesiek; Michal Kozubek; Mauricio Reyes; Michael A. Riegler; Manuel Wiesenfarth; A. Emre Kavur; Carole H. Sudre; Michael Baumgartner; Matthias Eisenmann; Doreen Heckmann-Nötzel; Tim Rädsch; Laura Acion; Michela Antonelli; Tal Arbel; Spyridon Bakas; Arriel Benis; Matthew B. Blaschko; M. Jorge Cardoso; Veronika Cheplygina; Beth A. Cimini; Gary S. Collins; Keyvan Farahani; Luciana Ferrer; Adrian Galdran; Bram van Ginneken; Robert Haase; Daniel A. Hashimoto; Michael M. Hoffman; Merel Huisman; Pierre Jannin; Charles E. Kahn; Dagmar Kainmueller; Bernhard Kainz; Alexandros Karargyris; Alan Karthikesalingam; Florian Kofler; Annette Kopp-Schneider; Anna Kreshuk; Tahsin Kurc; Bennett A. Landman; Geert Litjens; Amin Madani; Klaus Maier-Hein; Anne L. Martel; Peter Mattson; Erik Meijering; Bjoern Menze; Karel G. M. Moons; Henning Müller; Brennan Nichyporuk; Felix Nickel; Jens Petersen; Nasir Rajpoot; Nicola Rieke; Julio Saez-Rodriguez; Clara I. Sánchez; Shravya Shetty; Maarten van Smeden; Ronald M. Summers; Abdel A. Taha; Aleksei Tiulpin; Sotirios A. Tsaftaris; Ben Van Calster; Gaël Varoquaux; Paul F. Jäger. **2024; Nature Methods 21:195–212; Published.** [Nguồn canonical/primary](https://doi.org/10.1038/s41592-023-02151-z); [DOI 10.1038/s41592-023-02151-z](https://doi.org/10.1038/s41592-023-02151-z); arXiv UNKNOWN. Đối chiếu 2026-09-12. Perspective, published 12 February 2024

**VERIFIED trong phạm vi đọc:** original author-hosted PDF pp195–197; primary Nature metadata; Fig1–3, problem fingerprint and categorical-target scope. Phạm vi prediction/evaluation tại [hồ sơ K06](PAPER_MATRIX.md#k06); không suy clinical utility/causality ngoài bằng chứng đó.

### M28 — Conformal Forecasting for Surgical Instrument Trajectory

Sara Sangalli; Gary Sarwin; Ertunc Erdil; Carlo Serra; Alessandro Carretta; Victor Staartjes; Ender Konukoglu. **2025; MICCAI 2025; LNCS 15968:117–127; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2025/0168-Paper0260.html); [DOI 10.1007/978-3-032-05114-1_12](https://doi.org/10.1007/978-3-032-05114-1_12); [arXiv 2503.04191v2](https://arxiv.org/abs/2503.04191v2). Đối chiếu 2026-09-12. published author order differs from arXiv; MICCAI page curator Kitty K. Wong is not a paper author

**VERIFIED trong phạm vi đọc:** canonical MICCAI PDF §2–4/Table1; arXiv compared; §2.1 endpoint target; §2.2 assumptions; §3 split/context; Table1. Phạm vi prediction/evaluation tại [hồ sơ M28](PAPER_MATRIX.md#m28); không suy clinical utility/causality ngoài bằng chứng đó.

### M29 — Recalibration of Aleatoric and Epistemic Regression Uncertainty in Medical Imaging

Max-Heinrich Laves; Sontje Ihler; Jacob F. Fast; Lüder A. Kahrs; Tobias Ortmaier. **2021; Machine Learning for Biomedical Imaging 1, MIDL 2020 special issue:1–26; Published.** [Nguồn canonical/primary](https://www.melba-journal.org/papers/2021:008.html); [DOI 10.59275/j.melba.2021-a6fd](https://doi.org/10.59275/j.melba.2021-a6fd); [arXiv 2104.12376](https://arxiv.org/abs/2104.12376). Đối chiếu 2026-09-12. journal 2021; title typography 'EpistemicRegression' normalized with space

**VERIFIED trong phạm vi đọc:** original journal full HTML §2–4; §2 uncertainty/recalibration; §4.1 intervals; §4.2 rejection. Phạm vi prediction/evaluation tại [hồ sơ M29](PAPER_MATRIX.md#m29); không suy clinical utility/causality ngoài bằng chứng đó.

## Bổ sung đợt 2 — prior art A/B và active-acquisition boundary

### M30 — Online Learning in Motion Modeling for Intra-interventional Image Sequences

Niklas Gunnarsson; Jens Sjölund; Peter Kimstrand; Thomas B. Schön. **2024; MICCAI 2024; Lecture Notes in Computer Science, pp. 706–716; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2024/paper/1838_paper.pdf); [DOI 10.1007/978-3-031-72069-7_66](https://doi.org/10.1007/978-3-031-72069-7_66); [arXiv 2410.11491](https://arxiv.org/abs/2410.11491). Đối chiếu 2026-09-12. arXiv:2410.11491; published MICCAI 2024 version canonical; Crossref DOI checked

**VERIFIED trong phạm vi đọc:** full MICCAI proceedings PDF, methods and evaluation; MICCAI 2024 paper §§2–4; Tables 1–2. Crossref metadata + official MICCAI proceedings PDF; author order/title/pages checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M30](PAPER_MATRIX.md#m30); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M31 — Prediction of high-dimensional states subject to respiratory motion: a manifold learning approach

Wenyang Liu; Amit Sawant; Dan Ruan. **2016; Physics in Medicine and Biology 61(13):4989–4999; Published.** [Nguồn canonical/primary](https://pmc.ncbi.nlm.nih.gov/articles/PMC4975535/); [DOI 10.1088/0031-9155/61/13/4989](https://doi.org/10.1088/0031-9155/61/13/4989); arXiv UNKNOWN. Đối chiếu 2026-09-12. Publisher article and PMC record; no arXiv version identified

**VERIFIED trong phạm vi đọc:** full PMC/BioC article, methods and evaluation; PMC4975535; methods, experiments and tables. Crossref DOI + PMC full text; title/authors/year/volume/pages checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M31](PAPER_MATRIX.md#m31); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M32 — Predicting real-time 3D deformation field maps (DFM) based on volumetric cine MRI (VC-MRI) and artificial neural networks for on-board 4D target tracking: a feasibility study

Jonathan Pham; Wendy Harris; Wenzheng Sun; Zi Yang; Fang-Fang Yin; Lei Ren. **2019; Physics in Medicine and Biology 64(16):165016; Published.** [Nguồn canonical/primary](https://pmc.ncbi.nlm.nih.gov/articles/PMC6734921/); [DOI 10.1088/1361-6560/ab359a](https://doi.org/10.1088/1361-6560/ab359a); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published journal version; PMC full text canonical for audit

**VERIFIED trong phạm vi đọc:** full PMC article, methods and evaluation; PMC6734921; methods, data and results sections. Crossref DOI + PMC full text; title/authors/year/volume/article number checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M32](PAPER_MATRIX.md#m32); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M33 — Prediction of in-plane organ deformation during free-breathing radiotherapy via discriminative spatial transformer networks

Liset Vázquez Romaguera; Rosalie Plantefève; Francisco Perdigón Romero; François Hébert; Jean-François Carrier; Samuel Kadoury. **2020; Medical Image Analysis 64:101754; Published.** [Nguồn canonical/primary](https://pubmed.ncbi.nlm.nih.gov/32580056/); [DOI 10.1016/j.media.2020.101754](https://doi.org/10.1016/j.media.2020.101754); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published Medical Image Analysis version canonical; DOI checked

**VERIFIED trong phạm vi đọc:** PubMed abstract and Crossref metadata; methods details bounded; PubMed 32580056 abstract. Crossref DOI + PubMed record; title/authors/year/article number checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M33](PAPER_MATRIX.md#m33); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M34 — Probabilistic 4D predictive model from in-room surrogates using conditional generative networks for image-guided radiotherapy

Liset Vázquez Romaguera; Tal Mezheritsky; Rihab Mansour; Jean-François Carrier; Samuel Kadoury. **2021; Medical Image Analysis 74:102250; Published.** [Nguồn canonical/primary](https://pubmed.ncbi.nlm.nih.gov/34601453/); [DOI 10.1016/j.media.2021.102250](https://doi.org/10.1016/j.media.2021.102250); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published Medical Image Analysis version canonical; DOI checked

**VERIFIED trong phạm vi đọc:** PubMed abstract and Crossref metadata; methods detail bounded; PubMed 34601453 abstract. Crossref DOI + PubMed record; title/authors/year/article number checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M34](PAPER_MATRIX.md#m34); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M35 — Predicting 4D liver MRI for MR-guided interventions

Gino Gulamhussene; Anneke Meyer; Marko Rak; Oleksii Bashkanov; Jazan Omari; Maciej Pech; Christian Hansen. **2022; Computerized Medical Imaging and Graphics 101:102122; Published.** [Nguồn canonical/primary](https://doi.org/10.1016/j.compmedimag.2022.102122); [DOI 10.1016/j.compmedimag.2022.102122](https://doi.org/10.1016/j.compmedimag.2022.102122); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published 2022 volume 101 article 102122; Crossref title/authors checked

**VERIFIED trong phạm vi đọc:** Crossref/publisher metadata; adjacent-paper scope only; Crossref record and DOI landing metadata. Crossref DOI record checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M35](PAPER_MATRIX.md#m35); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M36 — Respiratory motion prediction using deep convolutional long short-term memory network

Shahabedin Nabavi; Monireh Abdoos; Mohsen Ebrahimi Moghaddam; Mohammad Mohammadi. **2020; Journal of Medical Signals & Sensors 10(2):69–75; Published.** [Nguồn canonical/primary](https://pmc.ncbi.nlm.nih.gov/articles/PMC7359959/); [DOI 10.4103/jmss.JMSS_38_19](https://doi.org/10.4103/jmss.JMSS_38_19); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published 2020; DOI capitalization normalized

**VERIFIED trong phạm vi đọc:** PMC full text/metadata; methods and evaluation details bounded; PMC7359959; methods, experiments and results. Crossref DOI + PMC record; title/authors/year/volume/pages checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M36](PAPER_MATRIX.md#m36); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M37 — Benchmarking machine learning-based real-time respiratory signal predictors in 4D SBRT

Lukas Wimmert; Maximilian Nielsen; Frederic Madesta; Tobias Gauer; Christian Hofmann; Rene Werner. **2024; Medical Physics 51(5):3173–3183; Published.** [Nguồn canonical/primary](https://doi.org/10.1002/mp.17038); [DOI 10.1002/mp.17038](https://doi.org/10.1002/mp.17038); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published 2024; official README current count differs from paper after corruption filtering

**VERIFIED trong phạm vi đọc:** full publisher HTML/methods/evaluation and official database/code README; Medical Physics article methods/results; official GitHub README. Crossref DOI + official publisher article + official GitHub repositories checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M37](PAPER_MATRIX.md#m37); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M38 — Performance comparison of prediction filters for respiratory motion tracking in radiotherapy

Alexander Jöhl; Stefanie Ehrbar; Matthias Guckenberger; Stephan Klöck; Mirko Meboldt; Melanie Zeilinger; Stephanie Tanadini-Lang; Marianne Schmid Daners. **2020; Medical Physics 47(2):643–650; Published.** [Nguồn canonical/primary](https://doi.org/10.1002/mp.13929); [DOI 10.1002/mp.13929](https://doi.org/10.1002/mp.13929); arXiv UNKNOWN. Đối chiếu 2026-09-12. Online publication 2019; print issue 2020; canonical citation uses 2020; first online 2019-12-07, issue 2020-02; canonical issue year 2020

**VERIFIED trong phạm vi đọc:** official repository metadata and published article record; methods detail bounded; DOI/publisher record; ETH repository copy. Crossref DOI + ETH repository record checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M38](PAPER_MATRIX.md#m38); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M39 — Real-time prediction and gating of respiratory motion in 3D space using extended Kalman filters and Gaussian process regression network

W. Bukhari; S.-M. Hong. **2016; Physics in Medicine and Biology 61(5):1947–1967; Published.** [Nguồn canonical/primary](https://pubmed.ncbi.nlm.nih.gov/26878653/); [DOI 10.1088/0031-9155/61/5/1947](https://doi.org/10.1088/0031-9155/61/5/1947); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published 2016; 3D extension of 2015 EKF+GPR work

**VERIFIED trong phạm vi đọc:** PubMed record/abstract and primary journal metadata; PubMed 26878653. Crossref/DOI + PubMed record; title/authors/year/volume/pages checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M39](PAPER_MATRIX.md#m39); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M40 — Prediction of real-time cine-MR images during MRI-guided radiotherapy of liver cancer using a GAN–ConvLSTM network

Guodong Jin; Yuxiang Liu; Ran Wei; Bining Yang; Bo Pang; Xinyuan Chen; Hong Quan; Jianrong Dai; Kuo Men. **2025; Medical Physics 52(5):3161–3172; Published.** [Nguồn canonical/primary](https://pmc.ncbi.nlm.nih.gov/articles/PMC12082801/); [DOI 10.1002/mp.17609](https://doi.org/10.1002/mp.17609); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published Medical Physics 2025 issue; DOI checked

**VERIFIED trong phạm vi đọc:** full PMC article metadata/methods/results bounded; PMC12082801; methods and results. Crossref DOI + PMC record; title/authors/year/volume/pages checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M40](PAPER_MATRIX.md#m40); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M41 — Non-stationary transformers-based model for predicting liver motion for interleaved two-dimensional cine magnetic resonance imaging

Suzune Shimizu; Masato Tsuneda; Kota Abe; Takashi Uno; Hiroki Suyari; Yasukuni Mori. **2026; Medical Physics 53:e70241; Published; first online 2025-12-29, issue 2026.** [Nguồn canonical/primary](https://doi.org/10.1002/mp.70241); [DOI 10.1002/mp.70241](https://doi.org/10.1002/mp.70241); arXiv UNKNOWN. Đối chiếu 2026-09-12. First online 2025-12-29; print/issue 2026 Medical Physics 53:e70241; online 2025-12-29, issue 2026-01; canonical issue year 2026

**VERIFIED trong phạm vi đọc:** publisher metadata/abstract and Crossref record; methods detail bounded; DOI landing page and Crossref record. Crossref DOI + Wiley publisher record checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M41](PAPER_MATRIX.md#m41); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M42 — Real-time respiratory motion forecasting with online learning of recurrent neural networks for accurate targeting in externally guided radiotherapy

Michel Pohl; Mitsuru Uesaka; Hiroyuki Takahashi; Kazuyuki Demachi; Ritu Bhusal Chhatkuli. **2025; Computer Methods and Programs in Biomedicine 269:108828; Published.** [Nguồn canonical/primary](https://doi.org/10.1016/j.cmpb.2025.108828); [DOI 10.1016/j.cmpb.2025.108828](https://doi.org/10.1016/j.cmpb.2025.108828); [arXiv 2403.01607](https://arxiv.org/abs/2403.01607). Đối chiếu 2026-09-12. Published 2025; arXiv:2403.01607 tracked separately

**VERIFIED trong phạm vi đọc:** published article metadata/abstract and official repository README; methods detail bounded; DOI landing page; official README references and time-series folder. Crossref/DOI + official repository README checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M42](PAPER_MATRIX.md#m42); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M43 — Dynamic Image Prediction Using Principal Component and Multi-Channel Singular Spectral Analysis: A Feasibility Study

Ritu Bhusal Chhatkuli; Kazuyuki Demachi; Naoki Miyamoto; Mitsuru Uesaka; Akihiro Haga. **2015; Open Journal of Medical Imaging 5:133–142; Published.** [Nguồn canonical/primary](https://www.scirp.org/pdf/ojmi_2015090914071968.pdf); [DOI 10.4236/ojmi.2015.53017](https://doi.org/10.4236/ojmi.2015.53017); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published 2015; DOI checked

**VERIFIED trong phạm vi đọc:** full official PDF and metadata; methods/evaluation read; SCIRP official PDF; methods and results. DOI/publisher PDF metadata checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M43](PAPER_MATRIX.md#m43); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M44 — Signal-aware deep learning–based respiratory motion prediction for lung tumor management

Kaushik Pratim Das; Chandra J.; Partha Pratim Medhi. **2026; Frontiers in Oncology 16:1735140; Published.** [Nguồn canonical/primary](https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2026.1735140/full); [DOI 10.3389/fonc.2026.1735140](https://doi.org/10.3389/fonc.2026.1735140); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published 2026-02-13; DOI and article number canonical

**VERIFIED trong phạm vi đọc:** full official Frontiers HTML methods/results/discussion; Frontiers in Oncology article §§Methods, Results, Data availability and Discussion. Official Frontiers article and DOI record checked 2026-09-12; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M44](PAPER_MATRIX.md#m44); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M45 — Trackerless Freehand Ultrasound with Sequence Modelling and Auxiliary Transformation Over Past and Future Frames

Qi Li; Ziyi Shen; Qian Li; Dean C. Barratt; Thomas Dowrick; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. **2023; IEEE ISBI 2023, pp. 1-5; Peer-reviewed conference paper; arXiv 2211.04867v2.** [Nguồn canonical/primary](https://doi.org/10.1109/ISBI53787.2023.10230773); [DOI 10.1109/ISBI53787.2023.10230773](https://doi.org/10.1109/ISBI53787.2023.10230773); [arXiv 2211.04867v2](https://arxiv.org/abs/2211.04867v2). Đối chiếu 2026-09-12. Published ISBI version canonical; arXiv 2211.04867v2 recorded

**VERIFIED trong phạm vi đọc:** Full paper PDF, §§2-3; official code metadata; ISBI paper §§2.1, 3.1-3.3, Table 1. Title/venue/DOI verified through IEEE DOI; authors checked against PDF; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M45](PAPER_MATRIX.md#m45); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M46 — Long-Term Dependency for 3D Reconstruction of Freehand Ultrasound Without External Tracker

Qi Li; Ziyi Shen; Qian Li; Dean C. Barratt; Thomas Dowrick; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. **2024; IEEE Transactions on Biomedical Engineering 71(3):1033-1042; Peer-reviewed journal article; arXiv 2310.10248.** [Nguồn canonical/primary](https://doi.org/10.1109/TBME.2023.3325551); [DOI 10.1109/TBME.2023.3325551](https://doi.org/10.1109/TBME.2023.3325551); [arXiv 2310.10248](https://arxiv.org/abs/2310.10248). Đối chiếu 2026-09-12. Published journal version canonical; arXiv 2310.10248 recorded

**VERIFIED trong phạm vi đọc:** Full publisher/HTML paper and UCL record; TBME methods/results; UCL record. Title/authors/year/venue/DOI verified via IEEE DOI and UCL record; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M46](PAPER_MATRIX.md#m46); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M47 — Privileged Anatomical and Protocol Discrimination in Trackerless 3D Ultrasound Reconstruction

Qi Li; Ziyi Shen; Qian Li; Dean C. Barratt; Thomas Dowrick; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. **2023; ASMUS 2023 / MICCAI LNCS 14337:142-151; Peer-reviewed workshop/proceedings paper; arXiv 2308.10293.** [Nguồn canonical/primary](https://doi.org/10.1007/978-3-031-44521-7_14); [DOI 10.1007/978-3-031-44521-7_14](https://doi.org/10.1007/978-3-031-44521-7_14); [arXiv 2308.10293](https://arxiv.org/abs/2308.10293). Đối chiếu 2026-09-12. Published LNCS version canonical; arXiv 2308.10293 recorded

**VERIFIED trong phạm vi đọc:** Accepted/full PDF and official UCL record; MICCAI/ASMUS paper methods and experiments. Title/venue/DOI verified at Springer DOI; authors checked against PDF; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M47](PAPER_MATRIX.md#m47); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M48 — Nonrigid Reconstruction of Freehand Ultrasound Without a Tracker

Qi Li; Ziyi Shen; Qianye Yang; Dean C. Barratt; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. **2024; MICCAI 2024, LNCS 15004, pp. 689-699; Peer-reviewed conference paper; arXiv 2407.05767.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2024/568-Paper2245.html); [DOI 10.1007/978-3-031-72083-3_64](https://doi.org/10.1007/978-3-031-72083-3_64); [arXiv 2407.05767](https://arxiv.org/abs/2407.05767). Đối chiếu 2026-09-12. Published MICCAI version canonical; arXiv 2407.05767 recorded

**VERIFIED trong phạm vi đọc:** Full PDF; official MICCAI page and code README; MICCAI paper methods/results and Tables 1-2. Title/venue/DOI verified through MICCAI/Springer; author list requires full proceedings check; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M48](PAPER_MATRIX.md#m48); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### G33 — GenNBV: Generalizable Next-Best-View Policy for Active 3D Reconstruction

Xiao Chen; Quanyi Li; Tai Wang; Tianfan Xue; Jiangmiao Pang. **2024; CVPR 2024, pp. 16436-16445; Peer-reviewed conference paper; arXiv 2402.16174.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2024/html/Chen_GenNBV_Generalizable_Next-Best-View_Policy_for_Active_3D_Reconstruction_CVPR_2024_paper.html); DOI UNKNOWN; [arXiv 2402.16174v3](https://arxiv.org/abs/2402.16174v3). Đối chiếu 2026-09-12. Published CVPR version canonical; arXiv 2402.16174 recorded; DOI UNKNOWN

**VERIFIED trong phạm vi đọc:** full methods/evaluation HTML + official CVF/project metadata; Root: arXiv v3 §§3.1–3.3, §4, Appendix A.1; CVF metadata. Title/year/venue verified against CVF; complete authors/DOI not independently recorded. Methods/evaluation ở [hồ sơ G33](PAPER_MATRIX.md#g33); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M49 — Automatic Probe Movement Guidance for Freehand Obstetric Ultrasound

Richard Droste; Lior Drukker; Aris T. Papageorghiou; J. Alison Noble. **2020; MICCAI 2020, LNCS 12263, pp. 583-592; Peer-reviewed conference paper; arXiv 2007.04480.** [Nguồn canonical/primary](https://pmc.ncbi.nlm.nih.gov/articles/PMC7116254/); [DOI 10.1007/978-3-030-59716-0_56](https://doi.org/10.1007/978-3-030-59716-0_56); [arXiv 2007.04480](https://arxiv.org/abs/2007.04480). Đối chiếu 2026-09-12. Published MICCAI version canonical; arXiv 2007.04480 recorded

**VERIFIED trong phạm vi đọc:** Primary PMC full text and arXiv metadata; MICCAI paper methods/results; PMC full text. DOI/venue/year verified; author list not duplicated here because source is canonical; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M49](PAPER_MATRIX.md#m49); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M50 — RecON: Online learning for sensorless freehand 3D ultrasound reconstruction

Mingyuan Luo; Xin Yang; Hongzhang Wang; Haoran Dou; Xindi Hu; Yuhao Huang; Nishant Ravikumar; Songcheng Xu; Yuanji Zhang; Yi Xiong; Wufeng Xue; Alejandro F. Frangi; Dong Ni; Litao Sun. **2023; Medical Image Analysis 87, 102810; Peer-reviewed journal article.** [Nguồn canonical/primary](https://doi.org/10.1016/j.media.2023.102810); [DOI 10.1016/j.media.2023.102810](https://doi.org/10.1016/j.media.2023.102810); arXiv UNKNOWN. Đối chiếu 2026-09-12. Published journal version; no arXiv record verified

**VERIFIED trong phạm vi đọc:** Publisher abstract, official code/README and metadata; not full methods; Publisher DOI page and official GitHub README. Title/year/venue/DOI verified via publisher DOI; root Crossref DOI/title/authors/year/type cross-check 2026-09-12; typographic spaces/hyphens normalized, primary names retained. Methods/evaluation ở [hồ sơ M50](PAPER_MATRIX.md#m50); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

### M51 — TUS-REC2024: A Challenge to Reconstruct 3D Freehand Ultrasound Without External Tracker

Qi Li; Shaheer U. Saeed; Yuliang Huang; Mingyuan Luo; Zhongnuo Yan; Jiongquan Chen; Xin Yang; Dong Ni; Nektarios Winter; Phuc Nguyen; Lucas Steinberger; Caelan Haney; Yuan Zhao; Mingjie Jiang; Bowen Ren; SiYeoul Lee; Seonho Kim; MinKyung Seo; MinWoo Kim; Yimeng Dou; Zhiwei Zhang; Yin Li; Tomy Varghese; Dean C. Barratt; Matthew J. Clarkson; Tom Vercauteren; Yipeng Hu. **2025; UNKNOWN; arXiv 2506.21765v2; arXiv challenge paper v2; venue UNKNOWN.** [Nguồn canonical/primary](https://arxiv.org/html/2506.21765); DOI UNKNOWN; [arXiv 2506.21765v2](https://arxiv.org/abs/2506.21765v2). Đối chiếu 2026-09-12. v2 dated 2025-11-13; venue/DOI UNKNOWN; policy says CC BY NC SA/research-only

**VERIFIED trong phạm vi đọc:** Official data/task/assessment/policy pages, arXiv HTML §§2-4, Zenodo metadata; arXiv §§2-4; official data/task/assessment/policy; Zenodo Parts 1-2/validation. Counts/config/split/license policy cross-checked across official pages and challenge paper; per-scan details UNKNOWN. Methods/evaluation ở [hồ sơ M51](PAPER_MATRIX.md#m51); contribution/limitation/relevance là INTERPRETATION / HYPOTHESIS.

## Metadata nguồn bổ sung đợt 2

- **LUMIERE** [MRI release API v1](https://api.figshare.com/v2/articles/21249516), DOI 10.6084/m9.figshare.21249516.v1; [README v1](https://api.figshare.com/v2/articles/21266241), DOI 10.6084/m9.figshare.21266241.v1; [PDF README](https://ndownloader.figshare.com/files/37983597). Đã đọc API/README và ZIP central directory. CC0 API và non-commercial README là conflict chưa giải quyết. Không đọc image members. Count 62 là derived audit, không claim của paper; [aggregate provenance](research_artifacts/2026-09-12_metadata_audit.json).
- **BreastDCEDL** [official repository](https://github.com/naomifridman/BreastDCEDL), [CSV pinned commit](https://raw.githubusercontent.com/naomifridman/BreastDCEDL/ed4bfe7a3407b722bc32c01ba38aa3619cb73ab5/BreastDCEDL_metadata.csv). CSV/README/code semantics đã đọc: intravisit contrast phases, không treatment-visit depth; derived 2,070 rows. Không cộng thành một public longitudinal cohort mới.
- **TUS-REC2024** [data](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/data.html), [policy](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/policies.html), [Zenodo Part 1](https://zenodo.org/records/11178509), [Part 2](https://zenodo.org/records/11180795), [validation](https://zenodo.org/records/12979481). Policy link xác nhận CC BY-NC-SA 4.0/research limits. Part descriptions không được cộng thành disjoint subjects; chưa audit archives. Challenge paper được ghi một hàng riêng trong matrix.
- **I-SPY2/ACRIN 6698** [source descriptor](https://wiki.cancerimagingarchive.net/plugins/viewsource/viewpagesrc.action?pageId=70230072), [data dictionary](https://wiki.cancerimagingarchive.net/download/attachments/50135447/ACRIN%206698%20ISPY2%20DWI%20and%20DCE%20MRI%20Data%20Descriptions_20210520.pdf?api=v2). Đã xác minh protocol bốn mốc, missing/unanalyzable objects và timing best-effort; chưa patient-level all-four intersection.
- **Wimmert scalar respiratory signal benchmark** [database](https://github.com/IPMI-ICNS-UKE/respiratory-signal-database), [prediction code](https://github.com/IPMI-ICNS-UKE/respiratory-motion-prediction). README/full paper đọc để phân biệt 2,510/419 raw với 2,502/416 sau loại corrupted records; không phải visual anatomy cohort. Data-object terms ngoài repository license vẫn cần kiểm tra trước use.
