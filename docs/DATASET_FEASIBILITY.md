# Dataset feasibility — A/B/C

Đối chiếu **2026-09-12**. **Chưa tải/đọc dữ liệu ảnh; đã audit metadata công khai giới hạn cho LUMIERE và BreastDCEDL, chưa xác nhận quyền truy cập của nhóm đối với dataset cần phê duyệt.** “Public” ở đây gồm open download và research access theo điều kiện, không đồng nghĩa unrestricted. Không nhập dữ liệu của dự án ultrasound riêng vào dự án này.

**VERIFIED**: thông tin trực tiếp từ data card, nhà cung cấp hoặc paper dataset được liên kết. **UNKNOWN**: chưa xác minh; không ước lượng hoặc điền từ dataset tương tự. **INTERPRETATION / HYPOTHESIS**: suitability và nguy cơ leakage cần audit. Mọi số đếm giữ đúng đơn vị và phiên bản; “images”, “series”, “studies”, “sessions”, “visits”, “patients” không hoán đổi.

## Sàng lọc feasibility — INTERPRETATION / HYPOTHESIS

| ID / nguồn | Họ có thể hỗ trợ | Thiết kế hợp lý để kiểm tra tiếp | Điều kiện chưa đạt |
| --- | --- | --- | --- |
| [D01 TrackRAD2025](#d01) | A | Future target geometry từ cine prefix | Dense future labels, continuity, số ca thực tải được |
| [D02 EchoNet-Dynamic](#d02) | A | Intraclip cardiac dynamics | Dense temporal contours; cadence thực; không có pose |
| [D03 ACDC](#d03) | A, negative control | Phase/shape modeling | Không mặc định cycle tái dựng là natural multi-beat forecast |
| [D04 4D-LUNG](#d04) | A, adjacent | Respiratory phase/deformation | Phase-binned CT không phải cine time series liên tục |
| [D05 TUS-REC2024](#d05) | B | Pose-conditioned view prediction | Không có căn cứ command/force; data access conditions |
| [D06 LUMIERE](#d06) | C | Glioma observed-care future imaging | Đếm complete trajectories, actual intervals, mask reliability |
| [D07 ISBI2015 MS](#d07) | C, pilot | Kiểm tra temporal protocol | Chỉ 5 subjects có training labels; không đủ tự khẳng định main cohort |
| [D08 OASIS-3](#d08) | C | Regional brain change | Release-specific visits, DUA, segmentation/preprocessing |
| [D09 ADNI](#d09) | C | Individual versus population trajectory | Cohort/access và timestamp/visit completeness |
| [D10 HCC-TACE-Seg](#d10) | C | Pre/post-care imaging | Pair-rich không phải long rollout; treatment granularity |
| [D11 I-SPY2](#d11) | C | Serial treatment-associated response | Landmark dates, usable paired modalities, arm/selection details |
| [D12 CFB-GBM](#d12) | C | Longitudinal lesion change | Intersection các timepoints/labels; version và intervals |
| [D13 Duke Breast Cancer MRI](#d13) | Acquisition/kinetics adjacent | Contrast phase observation | Intravisit sequence không phải longitudinal disease history |

<a id="d01"></a>

## D01 — TrackRAD2025

**VERIFIED.** [Official data card](https://huggingface.co/datasets/LMUK-RADONC-PHYS-RES/TrackRAD2025), [paper](https://arxiv.org/abs/2503.19119v2), [official repository](https://github.com/LMUK-RADONC-PHYS-RES/trackrad2025). Data DOI **10.57967/hf/4539**; paper DOI **10.1002/mp.17964**.

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Hugging Face release; CC BY-NC 4.0. Chưa tải để xác nhận manifest |
| Patients/sequences | Card: 477 unlabeled patients, khoảng 2.8 million frames; 108 labeled patients, khoảng 10,000 annotated frames. “Khoảng” là cách nguồn báo cáo, không phải ước lượng của survey |
| Split/version | 50 labeled training; 58 pretest/test. Update January 2026 nói test đã mở trừ cohort D do privacy; card còn đoạn cũ nói test withheld. Số labeled patients thực tải hiện tại: UNKNOWN |
| Temporal resolution/timestamps | Có per-scan frame-rate.json; cadence toàn bộ cohort và absolute timestamps: UNKNOWN |
| Depth/continuity | Real-time sagittal cine MRI từ MRI-linac. Card mô tả temporal jumps/contrast changes do ghép treatment interruptions ở 1.5 T; labeled frames tránh jumps. Số sequences/subject và valid-run lengths: UNKNOWN |
| Labels | Target masks ở các frame được annotate; thêm multi-observer annotations. Không xác minh dense labels ở mọi horizon |
| Action/pose/treatment | Command/pose/force: UNKNOWN, không có căn cứ coi được cung cấp. RT context có; individual treatment-event timeline: UNKNOWN |

**INTERPRETATION / HYPOTHESIS.** Challenge tracking dùng ảnh hiện tại, còn forecast phải giữ lại ảnh tương lai. Không chia overlapping windows cùng patient sang train/test. Audit random frame sampling, multi-observer label noise, dropped frames, scanner shift và prefix-only registration. Suitability A có điều kiện; chưa chứng minh mọi clip đáp ứng multi-step ground truth.

<a id="d02"></a>

## D02 — EchoNet-Dynamic

**VERIFIED.** [Official dataset site](https://echonet.github.io/dynamic/), [Stanford AIMI data description](https://aimi.stanford.edu/datasets/echonet-dynamic-cardiac-ultrasound), [code/data instructions](https://github.com/echonet/dynamic), [dataset-associated paper](https://doi.org/10.1038/s41586-020-2145-8).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Dataset access qua research/noncommercial agreement; không lấy MIT code license thay data terms |
| Patients/sequences | **10,030 videos** theo paper/site; Stanford AIMI xác nhận videos từ unique patients. Số patient IDs trong manifest thực tải: UNKNOWN, chưa audit |
| Resolution/timestamps | Videos; cadence và timestamp availability từng AVI: UNKNOWN trong đợt đối chiếu này |
| Depth/continuity | Within-exam cardiac clips; repeat longitudinal visits và clip cut/gap metadata: UNKNOWN |
| Labels | EF/volume-related metadata; LV tracings tại ED/ES frames; không phải mask mọi frame |
| Action/pose/treatment | Probe pose, commanded action, contact force, treatment timeline: UNKNOWN; không được giả định có |

**INTERPRETATION / HYPOTHESIS.** Có thể kiểm tra phase/shape prediction nếu thêm/audit dense labels; không chỉ đánh giá EF từ cả video rồi gọi future forecasting. Không dùng future ED/ES hoặc cycle endpoint để căn phase/crop prefix. Cần subject-disjoint split xác nhận từ metadata, không chỉ video-disjoint.

<a id="d03"></a>

## D03 — ACDC

**VERIFIED.** [Official database](https://www.creatis.insa-lyon.fr/Challenge/acdc/databases.html), [author-hosted draft PDF](https://www.creatis.insa-lyon.fr/Challenge/acdc/files/tmi_2018_bernard.pdf). Canonical paper: *Deep Learning Techniques for Automatic MRI Cardiac Multi-Structures Segmentation and Diagnosis: Is the Problem Solved?*, IEEE TMI 37(11):2514–2525 (2018), [DOI 10.1109/TMI.2018.2837502](https://doi.org/10.1109/TMI.2018.2837502), đối chiếu [institutional publication record](https://pure.amsterdamumc.nl/en/publications/deep-learning-techniques-for-automatic-mri-cardiac-multi-structur/).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Official download links cho images/ground truth; exact license/terms: UNKNOWN |
| Patients/sequences | 150 examinations; historical split 100 train/50 test; số distinct longitudinal subjects/visits: UNKNOWN |
| Resolution/timestamps | 3D+t cardiac-cycle sequences; per-case temporal spacing, absolute timestamps: UNKNOWN trước header audit |
| Depth/continuity | Cycle-resolved cine; không có bằng chứng từ release page về uninterrupted repeated-beat trajectories |
| Labels | ED/ES ventricular/myocardial segmentations và diagnosis groups; không dense temporal segmentation |
| Action/pose/treatment | UNKNOWN cho action, device pose và treatment records |

**INTERPRETATION / HYPOTHESIS.** Gated/reconstructed cycle và thông tin phase có thể làm task dễ hơn natural-prefix forecasting. Dùng làm reconstruction/periodic negative control; không ghép cycle vòng lại để tạo “long horizon” mới. Căn chuẩn bằng full-cycle extrema hoặc segmentation tương lai làm sai information contract.

<a id="d04"></a>

## D04 — 4D-LUNG

**VERIFIED.** [TCIA collection/version table](https://www.cancerimagingarchive.net/collection/4d-lung/). DOI **10.7937/K9/TCIA.2016.ELN8YGLE**.

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | TCIA/NBIA download; CC BY 3.0; version 2, 2016-10-19 |
| Patients/studies | 20 subjects; 589 studies, 6,690 series. Studies/series không phải continuous sequences |
| Resolution/timestamps | Respiratory phase-resolved 4D CT; physical frame intervals/true timestamps: UNKNOWN |
| Longitudinal depth/continuity | Có serial imaging, nhưng per-patient repeat depth: UNKNOWN. Phase bins không phải consecutive natural-time frames |
| Labels | CT/RTSTRUCT trong collection; completeness qua mọi phase/date: UNKNOWN |
| Action/pose/treatment | RT-related data hiện diện; actual delivery/treatment timeline, pose, command: UNKNOWN |

**INTERPRETATION / HYPOTHESIS.** Phù hợp audit deformation/phase geometry; không dùng phase 0→10→… như empirical future-time rollout. Sort theo InstanceNumber/series index có thể khác phase/day. Future-informed deformable registration và motion PCA phải được kiểm tra.

<a id="d05"></a>

## D05 — TUS-REC2024

**VERIFIED.** [Official data specification](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/data.html), [policies](https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/policies.html), [paper arXiv 2506.21765v2](https://arxiv.org/abs/2506.21765v2), [Zenodo part 1](https://zenodo.org/records/11178509).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Train/validation trên Zenodo; **CC BY-NC-SA 4.0** và research/noncommercial/citation conditions theo policy 2024 (đã mở license link). Test access hiện tại: UNKNOWN |
| Subjects/sequences | Data page: **85 healthy volunteers, 2,040 scans**, 24 scans/person; split 50/3/32 subjects = 1,200/72/768 scans |
| Conflict / packaging | Home page có mô tả 100 volunteers; data page 85. Zenodo Part 1/2 cùng mô tả total train 50 folders/1,200 scans; không cộng thành disjoint subjects. Per-part unique counts UNKNOWN |
| Temporal resolution | 20 fps, 480×640 frames; synchronized optical tracking |
| Timestamps/depth | Paper mô tả synchronized acquisition và loại invalid transforms; schema public mô tả frames/tforms. Actual timestamp fields sau lọc, jitter/dropouts và scan-duration distribution: UNKNOWN |
| Labels/pose | Forearm sweeps; calibrated 4×4 pose transforms, pixel-to-mm calibration; NDI Polaris Vicra tracked displacement |
| Action/contact/treatment | Command logs, force/contact measurements, treatment records: UNKNOWN; không có căn cứ coi measured trajectory là commanded action |
| Continuity | Recorded sweeps; giữa sweep có reset/reposition, không nối thành một trajectory liên tục |

**INTERPRETATION / HYPOTHESIS.** Dùng cho pose-conditioned observation prediction sau khi audit calibration và prefix-visible anatomy. Reconstruction dùng full sweep hoặc past-and-future pose smoothing là leakage nếu dùng làm prefix state. Không lấy điều kiện challenge TUS-REC2025 thay điều kiện 2024. Đây không tự là dataset cho closed-loop robot planning.

<a id="d06"></a>

## D06 — LUMIERE

**VERIFIED.** [Original Scientific Data paper](https://www.nature.com/articles/s41597-022-01881-7), [MRI data/automated segmentations](https://springernature.figshare.com/articles/dataset/LUMIERE_dataset_-_MRI_data_and_automated_segmentations/21249516), [README item](https://figshare.com/articles/dataset/LUMIERE_dataset_-_Readme_file/21266241/1). Paper DOI **10.1038/s41597-022-01881-7**; collection DOI **10.6084/m9.figshare.c.5904905**.

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Figshare API/MRI item ghi **CC0**, nhưng README ghi **non-commercial use**. Đây là conflict giữa nguồn cùng release chưa phân xử; không kết luận unrestricted. Paper CC BY không thay thế data terms |
| Patients/visits | **91 GBM patients; 638 study dates; 2,487 MRI images**. 599 studies có đủ bốn modalities |
| Modalities/labels | T1 pre/postcontrast, T2, FLAIR; automated DeepBraTumIA/HD-GLIO outputs cho complete studies; expert RANO evaluations không phải expert voxel labels |
| Resolution/timestamps | Paper §Anonymization: relative weeks từ preoperative acquisition; dates được làm mờ theo tuần, same-week studies có suffix giữ thứ tự. Exact days không được cung cấp; đã parse nominal week từ đường dẫn ZIP, chưa audit clinical timestamp/interval |
| Depth/continuity | Derived directory audit: 66 patients có ≥4 study dirs đủ bốn chuỗi; **62** có ≥4 nominal weeks khác nhau sau gộp suffix. Số patients có ≥2 past + ≥2 future **usable** cho horizon/label cụ thể vẫn UNKNOWN. Discrete visits |
| Clinical/treatment | Clinical/outcome và một số molecular data được mô tả; granular dose/start/stop/change history, completeness: UNKNOWN |
| Action/pose | Không xác minh acquisition actions/pose |

**INTERPRETATION / HYPOTHESIS.** Đây là lựa chọn public có thể kiểm tra C, không phải bằng chứng đã có 91 usable multi-step trajectories. Khoảng thời gian theo tuần cần interval/sensitivity analysis; không gán ngày chính xác bằng week × 7 rồi coi là measured date. Audit pseudo-progression, surgery/RT discontinuities qua metadata thực có; không giả định cause của imaging change. Split patient trước registration/normalization; automated masks cần reliability subset độc lập.

<a id="d07"></a>

## D07 — ISBI 2015 Longitudinal MS Lesion Segmentation

**VERIFIED.** [Official data description](https://iacl.ece.jhu.edu/index.php/MSChallenge/data), [access site](https://smart-stats-tools.org/lesion-challenge).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Challenge account/download mechanism; current approval và exact license: UNKNOWN |
| Subjects/visits | 5 training subjects, mean 4 timepoints; 14 test subjects, mean 4.4. Không chuyển mean thành exact total visits |
| Resolution/timestamps | Khoảng cách trung bình khoảng một năm theo source; actual dates/interval distribution: UNKNOWN |
| Labels | T1, T2, PD, FLAIR; manual lesion labels từ hai raters cho train; test labels withheld |
| Preprocessing/continuity | Có original/preprocessed; baseline MPRAGE MNI alignment, các visits khác rigid-to-baseline. Discrete visits; missing visit pattern UNKNOWN |
| Action/pose/treatment | UNKNOWN: không có căn cứ treatment/action logs đủ dùng |

**INTERPRETATION / HYPOTHESIS.** Hữu ích làm protocol pilot và sensitivity to label disagreement; 5 labeled train subjects là data risk lớn cho population forecasting. Không dùng test-label absence để thay bằng future-derived pseudo-GT mà không khai báo. Future segmentation làm target là hợp lệ; cho nó vào registration/state/crop tại cutoff thì phải audit.

<a id="d08"></a>

## D08 — OASIS-3

**VERIFIED.** [Official OASIS-3 description](https://sites.wustl.edu/oasisbrains/home/oasis-3/), [imaging data dictionary v2.3](https://sites.wustl.edu/oasisbrains/files/2024/04/OASIS-3_Imaging_Data_Dictionary_v2.3-a93c947a586e7367.pdf).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Research access qua registration/data-use process; exact current license/approval cho nhóm: UNKNOWN |
| Subjects/sessions | Dictionary Table 3, release 2.0 July 2022: **1,379 subjects, 2,842 MR sessions** |
| Conflict/version | Một homepage hiển thị 1,378. Không gộp số khác release; cohort tải thực tế UNKNOWN |
| Temporal resolution/timestamps | Official site: original dates removed, normalized thành days from study entry; per-subject elapsed intervals và parsing cấp manifest chưa audit |
| Depth/labels | MRI/PET, clinical assessments, derived imaging measures; per-subject usable MRI depth và complete labels UNKNOWN |
| Continuity | Discrete visits, không continuous trajectories; protocol/scanner changes phải audit |
| Action/pose/treatment | UNKNOWN cho pose/actions và treatment timeline đầy đủ |

**INTERPRETATION / HYPOTHESIS.** Hợp lý để audit anatomy trajectories, nhưng không lấy tổng subjects làm số longitudinal pairs. Derived longitudinal templates có thể sử dụng future scans; chỉ dùng prefix-built estimates hoặc tách rõ retrospective measurement khỏi input.

<a id="d09"></a>

## D09 — ADNI

**VERIFIED.** [Official data access](https://adni.loni.usc.edu/data-samples/adni-data/), [FAQ về ngày đo](https://adni.loni.usc.edu/help-faqs/faqs/), [Data Use Agreement](https://adni.loni.usc.edu/wp-content/themes/adni_2023/documents/ADNI_Data_Use_Agreement.pdf).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | Application/DUA và IDA access; nhóm đã được duyệt: UNKNOWN |
| Patients/sessions | Snapshot-specific imaging cohort, usable repeat visits: UNKNOWN; không dùng tổng tuyển ADNI làm số MRI trajectories |
| Time/timestamps | FAQ yêu cầu actual EXAMDATE/VISDATE phù hợp; VISCODE không thay actual elapsed time |
| Depth/labels | Serial imaging/clinical/derived biomarker data; chosen phase, modalities và depth: UNKNOWN |
| Continuity/discontinuities | Discrete visits qua các phases/protocols; patient-level missingness/scanner changes cần audit |
| Action/pose/treatment | Treatment completeness và causal variables cho estimand cụ thể: UNKNOWN; không giả định trial intervention từ tên cohort |

**INTERPRETATION / HYPOTHESIS.** Cần chọn release, manifest, dates và subject split trước khi đặt horizon 12/24 tháng. Không dùng diagnosis cuối follow-up hoặc preprocessing template toàn chuỗi làm baseline covariate. Khả năng truy cập có điều kiện, không phải dữ liệu đang có sẵn trong repo.

<a id="d10"></a>

## D10 — HCC-TACE-Seg

**VERIFIED.** [TCIA collection](https://www.cancerimagingarchive.net/collection/hcc-tace-seg/), [Scientific Data paper](https://doi.org/10.1038/s41597-023-01928-3). Data DOI **10.7937/TCIA.5FNA-0924**.

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | TCIA; CC BY 4.0; release v1 2022-08-17 |
| Subjects/studies | **105 subjects, 211 studies, 677 series** theo collection CT+SEG. 621 CT series trong paper là mẫu số khác |
| Time/depth | Pre/post-TACE imaging; baseline 1–12 weeks trước TACE theo nguồn. Exact patient intervals và ≥3 visits: UNKNOWN |
| Labels | CT/SEG; liver/tumor/vessel annotations ở pretreatment; dense expert post-treatment lesion masks: UNKNOWN |
| Clinical/treatment | Clinical spreadsheet/outcomes và treatment-related fields có; drug/dose/timing completeness: UNKNOWN |
| Continuity/action/pose | Discrete pre/post care; no verified continuous trajectory hoặc device action/pose logs |

**INTERPRETATION / HYPOTHESIS.** Có thể kiểm tra one-transition forecast, không đủ tự chứng minh long rollout. “Treatment-conditioned” chỉ là predictive association nếu không giải quyết assignment/confounding. Audit lesion matching, segmentation provenance, phase mismatch và patient-level leakage.

<a id="d11"></a>

## D11 — I-SPY2 / ACRIN-6698 imaging release

**VERIFIED.** [TCIA collection](https://www.cancerimagingarchive.net/collection/ispy2/), [DWI/DCE data descriptions](https://www.cancerimagingarchive.net/wp-content/uploads/ACRIN-6698-ISPY2-DWI-and-DCE-MRI-Data-Descriptions_20210520.pdf).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | TCIA, CC BY 4.0; collection v1 2022-05-02 |
| Subjects/studies | **985 subjects = 719 I-SPY2 + 266 ACRIN-6698; 3,677 studies**. Không cộng 719 một lần nữa |
| Sequences/depth | Serial breast DCE, DWI trong ACRIN subset; complete per-patient landmark counts: UNKNOWN |
| Time/timestamps | Dictionary đã đọc: protocol tối đa T0/T1/T2/T3; timing từ DICOM là best effort. Actual-day mapping, interval và patient-level intersection: UNKNOWN trước manifest audit |
| Labels | FTV-related segmentation/analysis objects; clinical spreadsheet cho 985 subjects có treatment/molecular/follow-up information |
| Treatment | Có treatment fields; arm, timing, dose, missingness, assignment probabilities cần xác minh cho từng estimand |
| Continuity/action/pose | Discrete treatment visits; DCE phases là intravisit. Device action/pose: UNKNOWN |

**INTERPRETATION / HYPOTHESIS.** Nguồn trial không tự đảm bảo individualized causal identification trong subset imaging. Không trộn phase sau tiêm với visit sau điều trị. Q8 chỉ dự báo under observed care; phải đối chiếu biology-based breast-response prior art trước claim novelty.

<a id="d12"></a>

## D12 — CFB-GBM

**VERIFIED.** [TCIA collection](https://www.cancerimagingarchive.net/collection/cfb-gbm/), [CFB-GBM v2.0 paper, arXiv 2608.17884v1](https://arxiv.org/abs/2608.17884).

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | TCIA/Aspera; CC BY 4.0; collection **version 3, 2026-06-26**. “v2.0” là tên paper, không đổi collection version |
| Subjects/images | **264 subjects; 3,981 NIfTI images**. Không phải 3,981 visits |
| Depth/timestamps | Paper mô tả t0/t1/t2; actual-day intervals và intersection patients đủ cả ba: UNKNOWN |
| Labels | GTV annotations với expert validation, masks và clinical/treatment/availability/RANO/radiomics TSVs |
| Label coverage | Paper Table 3 GTV counts t0/t1/t2: 261/160/122. Không suy số full three-visit subjects từ marginals |
| Treatment | Treatment files có; event-level completeness/causal confounder sufficiency: UNKNOWN |
| Continuity/action/pose | Discrete care milestones; exact discontinuities và action/pose information: UNKNOWN |

**INTERPRETATION / HYPOTHESIS.** Cần audit source files và expert-label provenance. Ba timepoints không đáp ứng thiết kế hai past + hai future; đổi question hoặc tìm nguồn sâu hơn, không nhân tạo visits. Không đồng nhất “có RANO” với dense ground-truth viable tumor state.

<a id="d13"></a>

## D13 — Duke Breast Cancer MRI

**VERIFIED.** [TCIA collection](https://www.cancerimagingarchive.net/collection/duke-breast-cancer-mri/). Data DOI **10.7937/TCIA.e3sv-re93**.

| Thuộc tính | Đối chiếu |
| --- | --- |
| Accessibility/license | TCIA collection công khai; exact license trong đợt đọc này: UNKNOWN |
| Subjects/sequences | **922 subjects**; usable phase/series totals: UNKNOWN |
| Time/timestamps | Preoperative DCE-MRI; exact phase timing/temporal resolution: UNKNOWN trước DICOM audit |
| Depth/labels | Intravisit contrast phases; lesion-location/clinical data. Repeat disease visits và dense segmentation: UNKNOWN |
| Continuity/action/treatment | Sparse sampled contrast phases, không liên tục như natural video; pose/actions và treatment-event completeness UNKNOWN |

**INTERPRETATION / HYPOTHESIS.** Có thể audit contrast kinetics như MRI-CEK; không dùng làm bằng chứng có long-term lesion trajectories. Continuous interpolated output phải chấm ở acquired times và với baseline constant/linear kinetic curve, không chỉ adjacent-frame smoothness.


## Bổ sung metadata đợt 2 — nguồn, phép đếm và giới hạn

**VERIFIED / derived audit.** [LUMIERE archive API](https://api.figshare.com/v2/articles/21249516), [README API](https://api.figshare.com/v2/articles/21266241) và [README PDF](https://ndownloader.figshare.com/files/37983597) được kiểm tra trực tiếp. ZIP central-directory có 91 patient dirs, 638 study dirs, 599 dirs đủ `CT1/T1/T2/FLAIR`; phép đếm độc lập trong bước tích hợp tái lập 66/53 patients có ≥4/≥5 dirs và 62 có ≥4 nominal weeks khác nhau. Chỉ parse directory records; không mở/giải nén image members. HTTP range có thể chứa vài byte nén trước directory, nên không coi đây là full-image download hoặc header/label audit. [Artifact aggregate, URL/version/checksum/quy tắc](research_artifacts/2026-09-12_metadata_audit.json) không chứa patient-level paths/records. Chi tiết và các điều kiện chưa đạt nằm ở [C audit §4](surveys/deep_dives/FAMILY_C_LONGITUDINAL_AUDIT.md#data-audit).

**VERIFIED.** [BreastDCEDL README](https://github.com/naomifridman/BreastDCEDL) mô tả `n_times` là contrast phases trong một exam. CSV tại commit `ed4bfe7a3407b722bc32c01ba38aa3619cb73ab5` có **2,070 rows**, gồm 982 `spy2`, 172 `spy1`, 916 `duke`; root tái lập count và SHA256. README và CSV có total khác nhau; giữ phiên bản riêng. Đây là kiểm tra nguồn derived, không thêm một cohort longitudinal độc lập: `n_times≥4` không chứng minh bốn lần khám điều trị. Access/license của ảnh derived, subject de-duplication, exact phase timestamps, labels/treatment intersection ngoài metadata đã đọc: **UNKNOWN**.

**VERIFIED / nguồn adjacent A.** [Wimmert respiratory-signal database](https://github.com/IPMI-ICNS-UKE/respiratory-signal-database) và [prediction repository](https://github.com/IPMI-ICNS-UKE/respiratory-motion-prediction) cung cấp benchmark scalar breathing: README 2,510 signals/419 patients; phân tích loại 8 corrupted signals/3 patients còn 2,502/416, preprocessing 25 Hz. Đây là nguồn kiểm tra baseline/time protocol, **không phải visual anatomy dataset**; pose/action, image labels và treatment-effect targets không được xác minh. MIT repository license được ghi riêng, không suy quyền của mọi linked data object. [A audit](surveys/deep_dives/FAMILY_A_FORECASTING_AUDIT.md#respiratory-signals) nêu split và giới hạn. Không tăng số 13 hồ sơ chính bằng cách đếm lại nguồn derived/adjacent.

**INTERPRETATION / HYPOTHESIS.** Metadata làm Q5 có căn cứ điều tra rõ hơn, nhưng không nâng thành cohort sẵn huấn luyện. Gate còn lại: label reliability, interval windows, prefix-safe preprocessing và patient-disjoint split. Với A/B, page-level schema cũng không thay header/calibration/dropout audit của release thực tải.


## Những nguồn không được coi là đang có dữ liệu — VERIFIED và giới hạn

EchoWorld/Cardiac Copilot/Fan et al. mô tả collected datasets nhưng public release và quyền truy cập thực tế chưa được xác minh. Neural SDE MS-RCTs và các cohort nội bộ của MeWM/TaDiff không trở thành public vì có paper/code. IvyGAP được dùng trong [Pash et al.](https://arxiv.org/html/2505.08927), nhưng access/version/subject/visit/license của release chưa được xác minh đủ trong đợt này; không xếp là cohort đã feasible. [M01–M06, M19–M20](PAPER_MATRIX.md).

## INTERPRETATION / HYPOTHESIS — audit tối thiểu trước chọn topic

1. Chọn release/terms, xác nhận download quyền nghiên cứu; ghi checksums/manifest, không commit patient data vào repo công khai.
2. Đếm **patient × valid prefix × future horizons** từ timestamps thật; báo số complete trajectories, không chỉ images/frames.
3. Xác minh frame order, gaps, resets, phase bins, intervisit intervals và modality/pose synchronization.
4. Lập “available at cutoff” table cho từng covariate, label, registration/template/crop và normalization statistic.
5. Split theo patient trước windowing; không có future-informed PCA, atlas, smoothing, segmentation-derived input hoặc endpoint diagnosis.
6. Audit annotations: manual/automatic/corrected, rater disagreement, matching lesions qua visits; định lượng error floor.
7. Với B kiểm tra measured pose/command/force là các cột khác nhau; với C kiểm tra treatment events và missingness. Không điền missingness bằng suy đoán.
8. Chỉ sau đó chốt horizon/endpoint và chạy strong simple baselines. Không có dataset nào trong bảng được đánh dấu “đã sẵn sàng huấn luyện” ở thời điểm này.
