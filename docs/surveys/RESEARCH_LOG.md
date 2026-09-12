# Research log — visual → medical world models

Ngày nghiên cứu/đối chiếu **2026-09-12**, Asia/Bangkok. Công việc tài liệu theo yêu cầu chủ dự án; **không thực nghiệm, không chọn topic/architecture, không xác nhận clinical utility**.

## Phạm vi và cách làm thực tế

Đã đọc README, AGENTS, SOURCE_OF_TRUTH, KNOWLEDGE_BASE, RESEARCH_SETUPS, REFERENCES và CHANGELOG hiện tại trước sửa. Baseline HEAD của đợt làm việc là `1d3fcab3afc1f2fbc97181ba60f2d7e518060dfe`; A/B/C và lịch sử đề xuất A1/C1 được bảo toàn, không nâng thành researcher decisions.

Dùng discovery → primary-source verification → method/evaluation extraction → adversarial prior-art search → synthesis → integrity review. Không gọi đây là systematic review toàn bộ lĩnh vực; không có PRISMA flow/counts hoặc citation-graph coverage giả định. Tập chọn **55 papers (26 general-CV/RL, 27 medical/adjacent, 2 methodological)** và **13 dataset profiles**. Mỗi paper có một hàng trong CSV; một source xuất hiện nhiều tài liệu vẫn chỉ là một paper.

Paper được ưu tiên vì trực tiếp trả lời system/state/transition/horizon/purpose hoặc có thể bác bỏ novelty, không vì citation count. Dùng proceedings/publisher/arXiv/official projects; search indexes chỉ discovery/corroboration. Các findings trong docs phân biệt VERIFIED và INTERPRETATION / HYPOTHESIS. “UNKNOWN” giữ nguyên khi không có xác minh, kể cả dataset licenses, số complete trajectories và current venue.

## Skills được dùng có ý nghĩa

| Skill / workflow | Sử dụng cụ thể | Điều chỉnh có chủ đích |
| --- | --- | --- |
| **academic-research-suite → ars/deep-research/WORKFLOW.md** | Khung chính: evidence extraction, verification, synthesis, gap analysis; vận dụng source-verification và devil’s-advocate checklists trong cùng mạch nghiên cứu | Không khởi tạo nested teams hoặc giả lập independent reviewers. Yêu cầu user đã xác định scope nên không lặp intake/clarification |
| **literature-review** | Search nhiều formulations, selection theo relevance, backward/forward manual chaining, synthesis theo capability | Không tự báo systematic completeness hoặc chạy mọi CLI/workflow |
| **citation-management** | Canonical-vs-preprint metadata, DOI/title/author/year checks; Crossref và primary-record corroboration | Dùng CSV/Markdown đúng output yêu cầu; không tạo BibTeX/manuscript/PDF chỉ để chạy script |
| **pdf:pdf** | Đọc actual papers bằng PDF text và rendered page inspection | EchoWorld và PCA cine-MRI có PDF tải tạm, render/xem page; các paper khác dùng full HTML hoặc official PDF khi có. Không commit paper PDFs |
| **deep-research-work:deep-research** | Đọc hướng dẫn evidence-first/primary-source research ban đầu | Không chạy một pipeline discovery trùng với ARS; ARS giữ vai trò phương pháp chính |

Git thao tác trực tiếp theo AGENTS/RTK; không cần worktree skill vì không có code implementation hoặc branch isolation conflict. Không dùng skill output làm nguồn khoa học.

**Giải quyết khác biệt với skill:** source-verification template gợi ý hierarchy ưu tiên review/RCT và API title-similarity checks. Với claim về thuật toán, paper gốc/methods là nguồn thích hợp hơn review/RCT; với causal treatment claim, trial design lại quan trọng. Không coi Semantic Scholar “not found” hoặc HTTP lỗi là chứng cứ paper giả; không coi API match là chứng minh scientific validity. Đây là điều chỉnh theo primary evidence và yêu cầu user, không phải làm theo skill máy móc.

## Search và citation tracing

Các nhóm query đã dùng bao gồm:

- “world model”, “visual predictive model”, video prediction, action-conditioned video, embodied/navigation, robot world model, driving world model, 3D/4D scene, generative simulator, representation world model.
- “medical world model”, “visual world model medical”, “medical imaging world model”, “ultrasound world model”, “echocardiography world model”, “robotic ultrasound world model”, “medical video world model”.
- “anatomical dynamics model”, “physiological dynamics”, “longitudinal imaging prediction”, “disease trajectory imaging”, “latent dynamics medical imaging”, với tumor/MS/neurodegeneration/respiratory/pose variants.
- Exact-title/DOI queries cho metadata, kết hợp “published”, conference/journal và official sites.
- Counter-search cho memory/state sufficiency, continuous time, uncertainty/calibration, multi-hypothesis, pose versus command, physical/biological state và policy evaluation.

Các chuỗi backward/forward có ích: EchoWorld → Cardiac Copilot; ImageFlowNet/Lachinov → Petersen; DreamDojo → Cosmos-Surg-dVRK; BrLP → SPIE technical assessment; TUS-REC references → spatial synthesis/trackerless reconstruction. Đây là manual tracing, không duyệt toàn bộ citing papers. Queries chống novelty và quyết định hạ claim có bảng riêng ở [TRANSFER_GAPS](TRANSFER_GAPS.md).

## Methods/evaluation thực sự đã đọc

28 hồ sơ có đọc full-text methods/evaluation hoặc PDF methods theo `read_depth`; không có nghĩa đã đọc từng trang/supplement của cả 55 papers. Các nguồn trung tâm gồm PlaNet, Dreamer, IRIS, DIAMOND, TD-MPC2, SlotFormer, DINO-WM, V-JEPA 2, NWM, Vista, DreamDojo; EchoWorld, Fan robot US, MeWM, ImageFlowNet, TaDiff, Δ-LFM, BrLP, PCA respiratory, cardiac ODE, MRI-CEK, Cosmos-Surg-dVRK, Petersen, Lachinov, neural SDE, Pash và Stowers. Các hồ sơ abstract-only không được trình bày như full-method audit.

PDF inspection cụ thể: EchoWorld page 4 cho method/guidance distinction; PCA paper page chứa Table 2 cùng §2.2–2.3.3 cho prefix basis, online/offline setup và direct horizon prediction. Official RSNA PDF Stowers pp2–5 đọc parameter calibration, pretreatment input, future visits và endpoint subset. Hình minh họa không thay thế đọc equations/evaluation protocol.

## Citation-integrity pass — VERIFIED về kiểm tra đã làm

- **55/55** paper records có primary URL, title/authors/year/status, DOI hoặc arXiv khi xác minh được; các ô còn thiếu ghi UNKNOWN.
- **21/21 DOI được ghi trong paper CSV** đã lấy được Crossref record và đối chiếu title, authors, venue/date với bibliography. Vòng đầu 16 thành công; 4 rate-limit 429 và 1 output truncation; retry qua file tạm giải quyết cả 5. Đây là **metadata verification**, không kiểm chứng claim phương pháp.
- Canonical dùng published version khi xác minh được. Dreamer preprint 2023 khác title Nature 2025; ImageFlowNet ICASSP short version khác extended arXiv; TaDiff TMI 2025; Δ-LFM có ICLR 2026 camera-ready; PCA cine đã có CMIG 2026; Pash đã có JCP September 2026.
- Year được tách theo source: Dyna UAI 2008/arXiv 2012/PMLR reissue 2024; cardiac synthesis/thrombectomy conference 2025 nhưng Crossref print 2026; Surgical Vision WM là **DEMI workshop**, không MICCAI main; Bukhari–Hong online 2014/issue 2015.
- Chỉnh author initials/diacritics theo canonical metadata ở TaDiff, Lachinov và McMaster; không lấy uploader của conference page làm author. Mido/Mahmoud Assran variant ghi ở V-JEPA 2; corporate Cosmos author list rút gọn minh bạch.
- Dataset DOI/license đối chiếu tại official data cards, không gộp vào mẫu số 21 paper-DOI checks. Data card access không phải sample-level verification.
- Vòng cuối bổ sung Stanford AIMI xác nhận unique-patient provenance của EchoNet, OASIS-3 relative days và LUMIERE week-rounded dates; phân biệt ACDC author-hosted draft với canonical TMI 2018 DOI.
- Kiểm tra trên cây tài liệu kết hợp: **13 Markdown files, 215 internal links/anchors, 55 CSV rows × 36 columns, 13 dataset profiles, 8 candidate questions; không có lỗi** thiếu link/anchor, duplicate IDs/DOIs/arXiv, empty fields hoặc title/author mismatch giữa matrix và REFERENCES. `git diff --check` sạch. Không chạy model tests vì chỉ thay docs.

### Nguồn mâu thuẫn hoặc chưa xác minh hết

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

## Final adversarial review — INTERPRETATION / HYPOTHESIS

**Phản biện mạnh nhất:** “Đây có thể chỉ là temporal prediction được đổi tên; strong simple states đã đủ và prior art đã có mọi thành phần.” Phản biện này chưa bị loại bỏ. Docs giữ state-value tests và falsifiers, không dùng tên world model hoặc độ phức tạp làm contribution.

Các sửa đổi sau kiểm tra:

- Bác bỏ gap rộng về memory, uncertainty, continuous time, anatomy-centric representation và medical planning.
- Không gọi full-cycle cardiac encoding là prefix forecasting; không gọi direct horizon models là recursive rollout.
- Không gọi force-control hardware là force-conditioned world model; không biến measured displacement thành command.
- Không lấy oracle best-future-volume sample, adjacent-frame cSSIM, calibrated-parameter trajectory hoặc image SSIM làm deployable forecast/clinical proof.
- Không suy treatment effect từ MeWM/TaDiff observational conditioning; giữ RCT neural-SDE evidence khác về identification.
- Tách prediction accuracy, uncertainty–error association, coverage calibration, policy ranking và absolute outcome accuracy.

Nếu bỏ một seed paper, kết luận thận trọng vẫn được nhiều nhánh prior art hỗ trợ. Nhưng mọi proposed gap vẫn **chưa chứng minh novelty**; chưa được loại trừ bằng exhaustive prior-art search hoặc replication. Không đánh dấu “independent peer review PASS” vì đây là cùng một tác nhân nghiên cứu.

## Giới hạn và đầu ra tiếp theo

Chưa có patient data/manifest audit, code replication, training, annotation study, power calculation hoặc prospective clinical evidence. Các scores/ranking/MICCAI scope là judgment có điều kiện. Không biết access, đủ temporal depth, treatment/pose completeness hoặc baseline headroom cho dự án.

Đầu ra tiếp theo nên là **feasibility manifest + available-at-cutoff contract + simple-baseline experiment**. Chủ dự án chọn topic sau khi có bằng chứng đó; kiến trúc chưa được đề xuất trong đợt này.
