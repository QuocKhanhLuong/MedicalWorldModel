# Research log — visual → medical world models

Ngày nghiên cứu/đối chiếu **2026-09-12**, Asia/Bangkok. Công việc tài liệu theo yêu cầu chủ dự án; **không thực nghiệm mô hình, không chọn topic/architecture, không xác nhận clinical utility**. Đợt 1 dưới đây là snapshot lịch sử 55 papers; trạng thái mới nhất ở đợt 2 (90 papers, metadata audit giới hạn).

## Đợt 1 — survey lineage và feasibility theo nguồn mô tả

### Phạm vi và cách làm thực tế

Đã đọc README, AGENTS, SOURCE_OF_TRUTH, KNOWLEDGE_BASE, RESEARCH_SETUPS, REFERENCES và CHANGELOG hiện tại trước sửa. Baseline HEAD của đợt làm việc là `1d3fcab3afc1f2fbc97181ba60f2d7e518060dfe`; A/B/C và lịch sử đề xuất A1/C1 được bảo toàn, không nâng thành researcher decisions.

Dùng discovery → primary-source verification → method/evaluation extraction → adversarial prior-art search → synthesis → integrity review. Không gọi đây là systematic review toàn bộ lĩnh vực; không có PRISMA flow/counts hoặc citation-graph coverage giả định. Tập chọn **55 papers (26 general-CV/RL, 27 medical/adjacent, 2 methodological)** và **13 dataset profiles**. Mỗi paper có một hàng trong CSV; một source xuất hiện nhiều tài liệu vẫn chỉ là một paper.

Paper được ưu tiên vì trực tiếp trả lời system/state/transition/horizon/purpose hoặc có thể bác bỏ novelty, không vì citation count. Dùng proceedings/publisher/arXiv/official projects; search indexes chỉ discovery/corroboration. Các findings trong docs phân biệt VERIFIED và INTERPRETATION / HYPOTHESIS. “UNKNOWN” giữ nguyên khi không có xác minh, kể cả dataset licenses, số complete trajectories và current venue.

### Skills được dùng có ý nghĩa

| Skill / workflow | Sử dụng cụ thể | Điều chỉnh có chủ đích |
| --- | --- | --- |
| **academic-research-suite → ars/deep-research/WORKFLOW.md** | Khung chính: evidence extraction, verification, synthesis, gap analysis; vận dụng source-verification và devil’s-advocate checklists trong cùng mạch nghiên cứu | Không khởi tạo nested teams hoặc giả lập independent reviewers. Yêu cầu user đã xác định scope nên không lặp intake/clarification |
| **literature-review** | Search nhiều formulations, selection theo relevance, backward/forward manual chaining, synthesis theo capability | Không tự báo systematic completeness hoặc chạy mọi CLI/workflow |
| **citation-management** | Canonical-vs-preprint metadata, DOI/title/author/year checks; Crossref và primary-record corroboration | Dùng CSV/Markdown đúng output yêu cầu; không tạo BibTeX/manuscript/PDF chỉ để chạy script |
| **pdf:pdf** | Đọc actual papers bằng PDF text và rendered page inspection | EchoWorld và PCA cine-MRI có PDF tải tạm, render/xem page; các paper khác dùng full HTML hoặc official PDF khi có. Không commit paper PDFs |
| **deep-research-work:deep-research** | Đọc hướng dẫn evidence-first/primary-source research ban đầu | Không chạy một pipeline discovery trùng với ARS; ARS giữ vai trò phương pháp chính |

Git thao tác trực tiếp theo AGENTS/RTK; không cần worktree skill vì không có code implementation hoặc branch isolation conflict. Không dùng skill output làm nguồn khoa học.

**Giải quyết khác biệt với skill:** source-verification template gợi ý hierarchy ưu tiên review/RCT và API title-similarity checks. Với claim về thuật toán, paper gốc/methods là nguồn thích hợp hơn review/RCT; với causal treatment claim, trial design lại quan trọng. Không coi Semantic Scholar “not found” hoặc HTTP lỗi là chứng cứ paper giả; không coi API match là chứng minh scientific validity. Đây là điều chỉnh theo primary evidence và yêu cầu user, không phải làm theo skill máy móc.

### Search và citation tracing

Các nhóm query đã dùng bao gồm:

- “world model”, “visual predictive model”, video prediction, action-conditioned video, embodied/navigation, robot world model, driving world model, 3D/4D scene, generative simulator, representation world model.
- “medical world model”, “visual world model medical”, “medical imaging world model”, “ultrasound world model”, “echocardiography world model”, “robotic ultrasound world model”, “medical video world model”.
- “anatomical dynamics model”, “physiological dynamics”, “longitudinal imaging prediction”, “disease trajectory imaging”, “latent dynamics medical imaging”, với tumor/MS/neurodegeneration/respiratory/pose variants.
- Exact-title/DOI queries cho metadata, kết hợp “published”, conference/journal và official sites.
- Counter-search cho memory/state sufficiency, continuous time, uncertainty/calibration, multi-hypothesis, pose versus command, physical/biological state và policy evaluation.

Các chuỗi backward/forward có ích: EchoWorld → Cardiac Copilot; ImageFlowNet/Lachinov → Petersen; DreamDojo → Cosmos-Surg-dVRK; BrLP → SPIE technical assessment; TUS-REC references → spatial synthesis/trackerless reconstruction. Đây là manual tracing, không duyệt toàn bộ citing papers. Queries chống novelty và quyết định hạ claim có bảng riêng ở [TRANSFER_GAPS](TRANSFER_GAPS.md).

### Methods/evaluation thực sự đã đọc

28 hồ sơ có đọc full-text methods/evaluation hoặc PDF methods theo `read_depth`; không có nghĩa đã đọc từng trang/supplement của cả 55 papers. Các nguồn trung tâm gồm PlaNet, Dreamer, IRIS, DIAMOND, TD-MPC2, SlotFormer, DINO-WM, V-JEPA 2, NWM, Vista, DreamDojo; EchoWorld, Fan robot US, MeWM, ImageFlowNet, TaDiff, Δ-LFM, BrLP, PCA respiratory, cardiac ODE, MRI-CEK, Cosmos-Surg-dVRK, Petersen, Lachinov, neural SDE, Pash và Stowers. Các hồ sơ abstract-only không được trình bày như full-method audit.

PDF inspection cụ thể: EchoWorld page 4 cho method/guidance distinction; PCA paper page chứa Table 2 cùng §2.2–2.3.3 cho prefix basis, online/offline setup và direct horizon prediction. Official RSNA PDF Stowers pp2–5 đọc parameter calibration, pretreatment input, future visits và endpoint subset. Hình minh họa không thay thế đọc equations/evaluation protocol.

### Citation-integrity pass — VERIFIED về kiểm tra đã làm

- **55/55** paper records có primary URL, title/authors/year/status, DOI hoặc arXiv khi xác minh được; các ô còn thiếu ghi UNKNOWN.
- **21/21 DOI được ghi trong paper CSV** đã lấy được Crossref record và đối chiếu title, authors, venue/date với bibliography. Vòng đầu 16 thành công; 4 rate-limit 429 và 1 output truncation; retry qua file tạm giải quyết cả 5. Đây là **metadata verification**, không kiểm chứng claim phương pháp.
- Canonical dùng published version khi xác minh được. Dreamer preprint 2023 khác title Nature 2025; ImageFlowNet ICASSP short version khác extended arXiv; TaDiff TMI 2025; Δ-LFM có ICLR 2026 camera-ready; PCA cine đã có CMIG 2026; Pash đã có JCP September 2026.
- Year được tách theo source: Dyna UAI 2008/arXiv 2012/PMLR reissue 2024; cardiac synthesis/thrombectomy conference 2025 nhưng Crossref print 2026; Surgical Vision WM là **DEMI workshop**, không MICCAI main; Bukhari–Hong online 2014/issue 2015.
- Chỉnh author initials/diacritics theo canonical metadata ở TaDiff, Lachinov và McMaster; không lấy uploader của conference page làm author. Mido/Mahmoud Assran variant ghi ở V-JEPA 2; corporate Cosmos author list rút gọn minh bạch.
- Dataset DOI/license đối chiếu tại official data cards, không gộp vào mẫu số 21 paper-DOI checks. Data card access không phải sample-level verification.
- Vòng cuối bổ sung Stanford AIMI xác nhận unique-patient provenance của EchoNet, OASIS-3 relative days và LUMIERE week-rounded dates; phân biệt ACDC author-hosted draft với canonical TMI 2018 DOI.
- Kiểm tra trên cây tài liệu kết hợp: **13 Markdown files, 215 internal links/anchors, 55 CSV rows × 36 columns, 13 dataset profiles, 8 candidate questions; không có lỗi** thiếu link/anchor, duplicate IDs/DOIs/arXiv, empty fields hoặc title/author mismatch giữa matrix và REFERENCES. `git diff --check` sạch. Không chạy model tests vì chỉ thay docs.

#### Nguồn mâu thuẫn hoặc chưa xác minh hết

| Vấn đề | Cách xử lý |
| --- | --- |
| Publisher DOI resolver/TCIA pages có lỗi hoặc bot block | Dùng primary source extraction/official records đã đọc và Crossref metadata; không suy nội dung từ lỗi truy cập |
| DreamDojo venue | Official repo báo ICML 2026; chưa tìm thấy proceedings record. Giữ “accepted/venue reported by authors; version read preprint” |
| V-JEPA/V-JEPA 2, Fan, cardiac ODE, SAW, MedDream và các preprint khác | Không gán venue chưa xác minh; cutoff không bảo đảm survey đã tìm mọi publication mới |
| TUS-REC homepage/data-page count | Ghi 100 versus data-page 85, dùng release-specific description; chưa tải manifest |
| OASIS-3 count | Dictionary release 1,379 versus homepage 1,378; không tự sửa một phía bằng suy đoán |
| TrackRAD release | Update mở test trừ cohort D và legacy closed-test text cùng tồn tại; exact downloadable cohort UNKNOWN |
| CFB-GBM | TCIA collection v3 khác tên paper “v2.0”; marginal visit counts không cho complete-patient intersection |
| LUMIERE | 638 study dates khác 2,487 MRI images; automated masks khác expert voxel GT; MRI item CC0 khác paper license; §Anonymization xác nhận relative weeks làm mờ dates, không exact days. D06/Q5 đã cập nhật |

### Final adversarial review — INTERPRETATION / HYPOTHESIS

**Phản biện mạnh nhất:** “Đây có thể chỉ là temporal prediction được đổi tên; strong simple states đã đủ và prior art đã có mọi thành phần.” Phản biện này chưa bị loại bỏ. Docs giữ state-value tests và falsifiers, không dùng tên world model hoặc độ phức tạp làm contribution.

Các sửa đổi sau kiểm tra:

- Bác bỏ gap rộng về memory, uncertainty, continuous time, anatomy-centric representation và medical planning.
- Không gọi full-cycle cardiac encoding là prefix forecasting; không gọi direct horizon models là recursive rollout.
- Không gọi force-control hardware là force-conditioned world model; không biến measured displacement thành command.
- Không lấy oracle best-future-volume sample, adjacent-frame cSSIM, calibrated-parameter trajectory hoặc image SSIM làm deployable forecast/clinical proof.
- Không suy treatment effect từ MeWM/TaDiff observational conditioning; giữ RCT neural-SDE evidence khác về identification.
- Tách prediction accuracy, uncertainty–error association, coverage calibration, policy ranking và absolute outcome accuracy.

Nếu bỏ một seed paper, kết luận thận trọng vẫn được nhiều nhánh prior art hỗ trợ. Nhưng mọi proposed gap vẫn **chưa chứng minh novelty**; chưa được loại trừ bằng exhaustive prior-art search hoặc replication. Không đánh dấu “independent peer review PASS” vì đây là cùng một tác nhân nghiên cứu.

### Giới hạn và đầu ra tiếp theo

Chưa có patient data/manifest audit, code replication, training, annotation study, power calculation hoặc prospective clinical evidence. Các scores/ranking/MICCAI scope là judgment có điều kiện. Không biết access, đủ temporal depth, treatment/pose completeness hoặc baseline headroom cho dự án.

Đầu ra tiếp theo nên là **feasibility manifest + available-at-cutoff contract + simple-baseline experiment**. Chủ dự án chọn topic sau khi có bằng chứng đó; kiến trúc chưa được đề xuất trong đợt này.

## Đợt 2 — audit methods, temporal contract và metadata

Theo yêu cầu “tiếp tục research sâu hơn nữa”, từ HEAD `9ceaee49a5a1532cd592b62bf1afb8c520e48a95`, đợt này giữ câu hỏi A/B/C chưa chọn và chuyển trọng tâm từ breadth sang **prior-art falsification + exact forecasting contract + source-level data feasibility**. Corpus hiện **90 paper: 33 general/CV/adjacent, 51 medical/adjacent, 6 methodological**, tăng 35; 13 hồ sơ dataset chính và 8 câu hỏi vẫn giữ. Dataset paper TUS-REC được ghi như một publication riêng, không cộng archive parts thành papers/patients.

| Dossier | Phạm vi và đầu ra |
| --- | --- |
| [A — forecasting audit](deep_dives/FAMILY_A_FORECASTING_AUDIT.md) | Manifold/PCA/DVF, probabilistic motion, state-space/online adaptation; direct/recursive/assimilation; simple baselines và Q1–Q3 falsifiers |
| [B — acquisition audit](deep_dives/FAMILY_B_ACQUISITION_AUDIT.md) | Hu/Copilot/EchoWorld/Fan; trackerless/nonrigid/memory priors; measured query khác command/contact; TUS-REC timing/terms; Q4 |
| [C — longitudinal audit](deep_dives/FAMILY_C_LONGITUDINAL_AUDIT.md) | Petersen/ImageFlowNet/TaDiff/BrLP/Δ-LFM/Pash; exact context/target và oracle/proxy endpoints; LUMIERE/CFB/I-SPY/OASIS; Q5–Q8 |
| [State and evaluation audit](deep_dives/STATE_AND_EVALUATION_AUDIT.md) | PSR sufficiency/reuse; WorldSimBench/WorldModelBench/WorldArena/2.0/Physics-IQ; proper scores, conformal calibration và metric falsifiers |

### Skills dùng có ý nghĩa ở đợt 2

- **academic-research-suite → deep-research:** phương pháp chính; áp dụng source-verification/devil’s-advocate checklists, observation/state/transition extraction và synthesis. Dùng ba nhánh bounded A/B/C cùng phần tổng hợp CV/metrics, không nested teams. Bản nháp được root đối chiếu primary evidence; đây không phải external independent peer review.
- **literature-review:** high-recall nhiều formulations và backward/forward tracing thủ công từ Pohl/Gunnarsson, EchoWorld/TUS-REC, Petersen/ImageFlowNet/Pash và CV benchmark seeds. Không báo citation-graph completeness, PRISMA hoặc systematic-review coverage.
- **citation-management:** phân biệt canonical proceedings/journal, preprint, author manuscript, publication year/online year; kiểm tra title/full author list/DOI/version bằng primary records và Crossref. Dùng checklist final integrity, không coi lỗi API là paper giả hoặc dùng metadata API để xác nhận methods.
- **PDF:** đọc actual PDFs/text và render các figure/table quan trọng. WorldSimBench, WorldModelBench, Physics-IQ, proper/variogram scoring, CAFHT và surgical conformal có PDF methods/evaluation; PSR, A/Pohl/Gunnarsson/Hu/Copilot có original PDFs hoặc full-text tương ứng. Paper central C dùng full author HTML có version và source locator. RecON, một số motion priors vẫn abstract-depth, ghi rõ trong matrix; không mặc định mọi trang/supplement của 90 papers đã đọc.

### Search đối kháng thực đã làm

Các query được chia theo mục đích, không đếm web hits làm evidence count:

- A: `PCA respiratory motion prediction`, `3D deformation field cine MRI prediction`, `manifold high-dimensional respiratory state`, `probabilistic 4D predictive model`, `online learning motion modeling`, `Gaussian process respiratory gating`, `non-stationary transformer liver motion`.
- B: `trackerless ultrasound sequence memory`, `long-term dependency freehand ultrasound`, `anatomical protocol discrimination`, `nonrigid ultrasound reconstruction`, `online sensorless reconstruction`, `next best view ultrasound planning`, `pose conditioned ultrasound simulation`.
- C: irregular longitudinal image forecasting + `test time adaptation`, `glioma continuous-time stochastic growth`, `patient-specific brain latent progression`, `Bayesian oncology digital twin`, `breast MRI biology treatment response`, `LUMIERE four visits`, `I-SPY2 T0 T3 FTV`, `BreastDCEDL n_times`.
- Cross-cutting độc lập: `medical imaging forecasting state sufficiency`, `predictive state representation medical imaging`, `radiotherapy motion forecasting conformal prediction`, `longitudinal imaging prediction calibration prediction interval`, `disease progression energy score`, `medical trajectory variogram score`.
- CV: `world model functional utility benchmark`, `world simulator action planning evaluation`, `WorldArena 2.0 tactile reinforcement learning`, `Physics-IQ motion consistency`.

Backward chains gồm Pohl→manifold/PCA/deformation/motion benchmarks, TUS-REC→Li reconstruction/history, Petersen→stochastic glioma/biophysical priors; forward manual checks gồm WorldArena→WorldSimBench/WorldModelBench và các bài 2025–2026 dẫn/tiếp nối seeds. Không có forward-citation coverage toàn bộ. Một preprint discovery về latent-state sufficiency (arXiv:2605.01694) chỉ củng cố cần tìm prior art theo thuật ngữ; không dùng abstract đó làm bằng chứng empirical hoặc thêm novelty claim.

### Metadata audit có thể tái kiểm tra

[Aggregate artifact](../research_artifacts/2026-09-12_metadata_audit.json) ghi exact release URLs/versions, hashes và counting rules. LUMIERE: HTTP range lấy ZIP directory, parse filenames, không mở/giải nén image members. Một implementation đếm riêng ở bước tích hợp tái lập **91 patient dirs, 638 study dirs, 599 four-sequence dirs; 66/53 patients ≥4/≥5 complete dirs; 62 ≥4 distinct nominal weeks**. Root recount dùng cùng metadata đã lấy, không phải independent download/cohort verification. BreastDCEDL pinned CSV: **2,070 rows = 982 spy2 + 172 spy1 + 916 duke**, checksum khớp; `n_times` là DCE phases, không treatment visits.

Derived counts được ghi riêng với primary-paper facts và hypotheses. Không public raw patient paths/tables, không tải bulk patient images, không chấp nhận DUA. Chưa mở NIfTI/DICOM/masks để xác nhận usability. A/B chỉ page/schema/terms audit; per-scan timestamps/continuous labeled-run lengths còn UNKNOWN. CFB-GBM ba mốc không thể thỏa Q5 bốn visits; I-SPY/OASIS usable intersections chưa đếm.

### Phản chứng và đính chính sau final source review

| Điểm kiểm tra | Kết quả xử lý từ primary evidence |
| --- | --- |
| TaDiff external mask evaluation | Root đọc lại §IV-A/IV-C2: external chỉ SSIM/PSNR/MSE cho MRI, không DSC/RVD tumor masks. Sửa draft C và matrix; giữ parent survey đúng. Không chép suy luận worker làm VERIFIED. |
| GenNBV planning | Root đọc §3.1–3.3/§4: PPO policy dùng Isaac Gym transition và observed depth map updates; không learned forward world model. Sửa draft/CSV thành active-evaluation boundary prior. |
| Zenodo TUS-REC subjects | Part 1/2 mô tả cùng total training cohort; loại suy luận Part 2 “thêm 40 subjects”. Per-part unique subjects UNKNOWN trước manifest. |
| LUMIERE license | API ghi CC0, README PDF ghi non-commercial. Ghi conflict, không tự phân xử quyền sử dụng. |
| Gunnarsson online learning | Tách assimilation prefix rồi forecast EchoNet suffix, giữ ACDC interpolation riêng; không gán toàn bài là tracking hoặc toàn bộ là forecast. |
| Conformal surgical exchangeability | Nguồn nêu memoryless prediction + sampled timepoints; root đánh dấu lập luận đó chưa tự bảo đảm exchangeability của overlapping/patient-correlated windows. Đây là critique có giới hạn, không kết luận toàn bài invalid. |
| Direct versus recursive | Không bắt mọi WM recursive; direct multiple-time queries từ một prefix vẫn có thể hợp lệ. Joint-path quality và fixed-prefix conditioning phải được kiểm tra nếu claim trajectory consistency. |
| Author/version mismatches | WorldSimBench canonical author list khác arXiv sớm; WorldArena v2 thêm authors; dùng version đã đọc. Jöhl online 2019/issue 2020, Shimizu online 2025/issue 2026, Sangalli canonical author order khác preprint. Không trộn. |

### Citation-integrity pass cuối

Root bổ sung **6 DOI checks** cho benchmark/scoring/calibration sources và **24 DOI checks** cho A/B (có DOI đã nằm trong corpus cũ); đối chiếu primary title/authors/year/status. Ba HTTP429 được retry thành công. 21 DOI của đợt 1 đã có pass riêng, không tuyên bố vừa kiểm tra lại toàn bộ. Physics-IQ/CVF PDF được tải khi web renderer lỗi; NeurIPS canonical PDF thay OpenReview bot block. Không suy paper không tồn tại/không công bố từ access error.

Kiểm tra tự động trên cây kết hợp: CSV 90 rows × 36 fields, duplicate ID/DOI/arXiv, nonempty/UNKNOWN, exact title/author presence giữa CSV/matrix/REFERENCES, internal paths/anchors và `git diff --check`. Kết quả final được lưu ở [integrity aggregate](../research_artifacts/2026-09-12_integrity.json). Đây là kiểm tra consistency/citation structure cộng source review ở trên, không phải proof mọi claim khoa học đúng hoặc bibliographic completeness.

### Điều chưa biết sau đợt 2

Chưa có kết quả baseline/headroom, mask error floor, available-at-cutoff implementation, cohort đủ label/time, data-use approval, clinical endpoints hoặc prospective utility. Ranking đã giảm novelty của Q4/Q5 và điều chỉnh feasibility theo bằng chứng, **không chọn topic**. Việc tiếp theo là đóng từng temporal/data contract, audit nhãn/interval, rồi thí nghiệm bác bỏ bằng strong simple baselines; chưa chọn architecture.
