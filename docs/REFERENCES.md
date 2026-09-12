# Sổ nguồn tham khảo và xác minh

Cập nhật **2026-09-12** (Asia/Bangkok). **55 paper + 13 hồ sơ data release** trong survey. Mỗi paper có một ID thống nhất với [PAPER_MATRIX](PAPER_MATRIX.md) và [CSV](paper_matrix.csv). Dataset không được cộng thành paper hoặc trajectories nếu không đúng đơn vị.

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

**VERIFIED trong phạm vi đọc:** official abstract, paper information and author response; Abstract; author response items1,2,7; code/data N/A. Hỗ trợ nghiên cứu probe guidance. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M01](PAPER_MATRIX.md#m01).

### M02 — EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance

Yang Yue; Yulin Wang; Haojun Jiang; Pan Liu; Shiji Song; Gao Huang. **2025; CVPR; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/CVPR2025/html/Yue_EchoWorld_Learning_Motion-Aware_World_Models_for_Echocardiography_Probe_Guidance_CVPR_2025_paper.html); DOI UNKNOWN; [arXiv 2504.13065v1](https://arxiv.org/abs/2504.13065v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3–5 and appendix; PDF visual inspection p4; §4.1–4.2; sequential protocol; Appendix dataset. Hỗ trợ nghiên cứu probe guidance. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M02](PAPER_MATRIX.md#m02).

### M03 — Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound

Siqi Fan; Mingcong Chen; Ran Liu; Zixuan Yang; Xiaoyu Fu; Xiaoqing Gao; Yunhui Liu; Hongbin Liu. **2026; arXiv; peer-reviewed venue UNKNOWN; Preprint.** [Nguồn canonical/primary](https://arxiv.org/abs/2607.21918v2); DOI UNKNOWN; [arXiv 2607.21918v2](https://arxiv.org/abs/2607.21918v2). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §II–IV; Fig4; TableI; TableIV; Discussion. Hỗ trợ nghiên cứu train goal-guidance policy. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M03](PAPER_MATRIX.md#m03).

### M04 — Medical World Model

Yijun Yang; Zhao-Yang Wang; Qiuping Liu; Shuwen Sun; Kang Wang; Rama Chellappa; Zongwei Zhou; Alan Yuille; Lei Zhu; Yu-Dong Zhang; Jieneng Chen. **2025; ICCV:8319–8329; Published.** [Nguồn canonical/primary](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html); DOI UNKNOWN; [arXiv 2506.02327](https://arxiv.org/abs/2506.02327). Đối chiếu 2026-09-12. arXiv title adds Generative Simulation of Tumor Evolution for Treatment Planning; ICCV title canonical

**VERIFIED trong phạm vi đọc:** full-text §3 and evaluation/appendix; §3 forward/inverse dynamics; retrospective evaluation. Hỗ trợ nghiên cứu treatment candidate search. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M04](PAPER_MATRIX.md#m04).

### M05 — ImageFlowNet: Forecasting Multiscale Image-Level Trajectories of Disease Progression with Irregularly-Sampled Longitudinal Medical Images

Chen Liu; Ke Xu; Liangbo L. Shen; Guillaume Huguet; Zilong Wang; Alexander Tong; Danilo Bzdok; Jay Stewart; Jay C. Wang; Lucian V. Del Priore; Smita Krishnaswamy. **2025; ICASSP; Published.** [Nguồn canonical/primary](https://doi.org/10.1109/ICASSP49660.2025.10890535); [DOI 10.1109/ICASSP49660.2025.10890535](https://doi.org/10.1109/ICASSP49660.2025.10890535); [arXiv 2406.14794v6](https://arxiv.org/abs/2406.14794v6). Đối chiếu 2026-09-12. Canonical ICASSP 2025 short version; methods dùng extended arXiv v6. DOI/title/authors corroborated by Duke institutional record and official repository; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation/Appendix D,F; §5.5–5.6; AppendixD.1/D.3. Hỗ trợ nghiên cứu image-level forecast. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M05](PAPER_MATRIX.md#m05).

### M06 — Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction

Qinghui Liu; Elies Fuster-Garcia; Ivar Thokle Hovden; Bradley J. MacIntosh; Edvard O. S. Grødem; Petter Brandal; Carles Lopez-Mateu; Donatas Sederevičius; Karoline Skogen; Till Schellhorn; Atle Bjørnerud; Kyrre Eeg Emblem. **2025; IEEE Transactions on Medical Imaging 44(6):2449–2462; Published.** [Nguồn canonical/primary](https://doi.org/10.1109/TMI.2025.3533038); [DOI 10.1109/TMI.2025.3533038](https://doi.org/10.1109/TMI.2025.3533038); [arXiv 2309.05406v5](https://arxiv.org/abs/2309.05406v5). Đối chiếu 2026-09-12. Canonical TMI 2025; arXiv v5 dùng cho methods. DOI metadata corroborated by UPV institutional record and PubMed 40031286; publisher resolver access error. Crossref DOI metadata matched 2026-09-12.

**VERIFIED trong phạm vi đọc:** full-text methods; §IV-A/B evaluation; §IV-A 18/5 patient split; external labels; training sampling. Hỗ trợ nghiên cứu forecast under treatment context. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M06](PAPER_MATRIX.md#m06).

### M07 — Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation

Hao Chen; Rui Yin; Yifan Chen; Qi Chen; Chao Li. **2026; ICLR; Published.** [Nguồn canonical/primary](https://openreview.net/pdf/a1558b2e7d9494789fdd3057059dfbe2add8737e.pdf); DOI UNKNOWN; [arXiv 2512.09185v4](https://arxiv.org/abs/2512.09185v4). Đối chiếu 2026-09-12. v4 2026-06-17; ICLR publication verified in camera-ready header

**VERIFIED trong phạm vi đọc:** camera-ready metadata; full arXiv methods/evaluation; §3; §4.1; regional-change experiments. Hỗ trợ nghiên cứu individual future imaging. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M07](PAPER_MATRIX.md#m07).

### M08 — Brain Latent Progression: Individual-based spatiotemporal disease progression on 3D Brain MRIs via latent diffusion

Lemuel Puglisi; Daniel C. Alexander; Daniele Ravì. **2025; Medical Image Analysis 106:103734; Published.** [Nguồn canonical/primary](https://doi.org/10.1016/j.media.2025.103734); [DOI 10.1016/j.media.2025.103734](https://doi.org/10.1016/j.media.2025.103734); [arXiv 2502.08560v2](https://arxiv.org/abs/2502.08560v2). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh; Canonical author metadata lists Puglisi, Alexander, Ravì; ADNI/AIBL study-group acknowledgement is not expanded as additional named authors.

**VERIFIED trong phạm vi đọc:** full-text methods §4; evaluation §5.6; §4.3–4.6; §5.5–5.7. Hỗ trợ nghiên cứu personalized image forecast. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M08](PAPER_MATRIX.md#m08).

### M09 — Frame forecasting in cine MRI using the PCA respiratory motion model: comparing recurrent neural networks trained online and transformers

Michel Pohl; Mitsuru Uesaka; Hiroyuki Takahashi; Kazuyuki Demachi; Ritu Bhusal Chhatkuli. **2026; Computerized Medical Imaging and Graphics 131:102755; Published.** [Nguồn canonical/primary](https://www.sciencedirect.com/science/article/abs/pii/S0895611126000583); [DOI 10.1016/j.compmedimag.2026.102755](https://doi.org/10.1016/j.compmedimag.2026.102755); [arXiv 2410.05882v3](https://arxiv.org/abs/2410.05882v3). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** PDF methods/evaluation; visually inspected Table2; §2.2–2.4; Table2; §2.3.3. Hỗ trợ nghiên cứu latency compensation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M09](PAPER_MATRIX.md#m09).

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

**VERIFIED trong phạm vi đọc:** full-text methods/evaluation; §2.1–2.2; Query Volume Dice. Hỗ trợ nghiên cứu plausible spatial growth trajectories. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M17](PAPER_MATRIX.md#m17).

### M18 — Learning Spatio-Temporal Model of Disease Progression With NeuralODEs From Longitudinal Volumetric Data

Dmitrii Lachinov; Arunava Chakravarty; Christoph Grechenig; Ursula Schmidt-Erfurth; Hrvoje Bogunović. **2024; IEEE TMI 43(3):1165–1179; Published; online 2023, issue 2024.** [Nguồn canonical/primary](https://doi.org/10.1109/TMI.2023.3330576); [DOI 10.1109/TMI.2023.3330576](https://doi.org/10.1109/TMI.2023.3330576); [arXiv 2211.04234](https://arxiv.org/abs/2211.04234). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §II and evaluation design; §II initial value problem; temporal Dice; TADPOLE evaluation. Hỗ trợ nghiên cứu anatomical progression prediction. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M18](PAPER_MATRIX.md#m18).

### M19 — Probabilistic Temporal Prediction of Continuous Disease Trajectories and Treatment Effects Using Neural SDEs

Joshua Durso-Finley; Berardino Barile; Jean-Pierre Falet; Douglas L. Arnold; Nick Pawlowski; Tal Arbel. **2024; MICCAI; LNCS15003:400–410; Published.** [Nguồn canonical/primary](https://papers.miccai.org/miccai-2024/619-Paper3431.html); [DOI 10.1007/978-3-031-72384-1_38](https://doi.org/10.1007/978-3-031-72384-1_38); [arXiv 2406.12807v1](https://arxiv.org/abs/2406.12807v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §2–3; §2.2 potential outcomes/RCT independence; §3 trials. Hỗ trợ nghiên cứu personalized progression/treatment analysis. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M19](PAPER_MATRIX.md#m19).

### M20 — Predictive digital twins with quantified uncertainty for patient-specific decision making in oncology

Graham Pash; Umberto Villa; David A. Hormuth II; Thomas E. Yankeelov; Karen Willcox. **2026; Journal of Computational Physics 560:114937; Published 2026-09-01.** [Nguồn canonical/primary](https://www.sciencedirect.com/science/article/pii/S0021999126002901); [DOI 10.1016/j.jcp.2026.114937](https://doi.org/10.1016/j.jcp.2026.114937); [arXiv 2505.08927](https://arxiv.org/abs/2505.08927). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** full-text §3–5; §4.3; §5.1–5.3; AppendixC. Hỗ trợ nghiên cứu forecast and experimental-design analysis. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M20](PAPER_MATRIX.md#m20).

### M21 — Online prediction for respiratory movement compensation: a patient-specific gating control for MRI-guided radiotherapy

Yang Li; Zhenjiang Li; Jian Zhu; Baosheng Li; Huazhong Shu; Di Ge. **2023; Radiation Oncology 18:149; Published.** [Nguồn canonical/primary](https://doi.org/10.1186/s13014-023-02341-1); [DOI 10.1186/s13014-023-02341-1](https://doi.org/10.1186/s13014-023-02341-1); arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** original paper PDF abstract/method overview; https://d-nb.info/1318665426/34; Methods. Hỗ trợ nghiên cứu latency-aware gating. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M21](PAPER_MATRIX.md#m21).

### M22 — Real-time prediction and gating of respiratory motion using an extended Kalman filter and Gaussian process regression

W. Bukhari; S.-M. Hong. **2015; Physics in Medicine & Biology 60(1):233–252; Published; epub 2014.** [Nguồn canonical/primary](https://pubmed.ncbi.nlm.nih.gov/25489980/); [DOI 10.1088/0031-9155/60/1/233](https://doi.org/10.1088/0031-9155/60/1/233); arXiv UNKNOWN. Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** indexed original abstract/metadata; Trang nguồn/abstract. Hỗ trợ nghiên cứu gate high-risk prediction periods. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M22](PAPER_MATRIX.md#m22).

### M23 — Freehand Ultrasound Image Simulation with Spatially-Conditioned Generative Adversarial Networks

Yipeng Hu; Eli Gibson; Li-Lin Lee; Weidi Xie; Dean C. Barratt; Tom Vercauteren; J. Alison Noble. **2017; RAMBO at MICCAI; Accepted/published chapter DOI recorded.** [Nguồn canonical/primary](https://arxiv.org/abs/1707.05392); [DOI 10.1007/978-3-319-67564-0_11](https://doi.org/10.1007/978-3-319-67564-0_11); [arXiv 1707.05392v1](https://arxiv.org/abs/1707.05392v1). Đối chiếu 2026-09-12. arXiv version UNKNOWN nếu không ghi vN; canonical là bản công bố khi đã xác minh

**VERIFIED trong phạm vi đọc:** metadata + abstract; Trang nguồn/abstract. Hỗ trợ nghiên cứu procedure simulation. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M23](PAPER_MATRIX.md#m23).

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

**VERIFIED trong phạm vi đọc:** original PDF methods/evaluation pp2–5; Mathematical Model; CNN Inputs and Outputs; Patient Demographics; pCR subset. Hỗ trợ nghiên cứu anticipate observed-regimen response. Không mở rộng ra utility/causality ngoài evaluation ghi ở [hồ sơ M27](PAPER_MATRIX.md#m27).

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

Xem [RESEARCH_LOG](surveys/RESEARCH_LOG.md) cho DOI checks, corrected metadata, access errors, phương pháp skill và adversarial prior-art results. Không sử dụng survey thứ cấp làm bằng chứng duy nhất cho claim quan trọng; secondary indexes dùng discovery/corroboration, còn methods từ paper gốc. Nguồn chưa đọc methods không được dùng để khẳng định chi tiết methods ngoài abstract đã thấy. Dataset manifests, code execution, patient-level replication và clinical validation chưa được thực hiện.
