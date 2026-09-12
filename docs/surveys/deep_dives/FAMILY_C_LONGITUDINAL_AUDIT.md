# Audit Family C — longitudinal disease/lesion dynamics

**Cập nhật:** 2026-09-12, Asia/Bangkok
**Phạm vi:** temporal-protocol audit cho Family C và feasibility audit ở mức metadata công khai.
**Không phải:** quyết định chọn A/B/C, quyết định modality, lựa chọn backbone, hay bằng chứng về clinical utility.

## 0. Cách đọc bằng chứng

Tài liệu này tách hai lớp:

- **VERIFIED:** điều được đọc trực tiếp từ bài gốc, proceedings/publisher, trang dữ liệu chính thức, README hoặc manifest công khai. URL và vị trí đọc được ghi ngay cạnh phát biểu. Các con số đếm từ manifest được đánh dấu là *derived audit*; chúng không thay thế phát biểu của dataset paper.
- **INTERPRETATION / HYPOTHESIS:** phép phân loại theo khung observation → state → transition → future → purpose, nhận xét về leakage, novelty, rủi ro và falsifier. Đây là tổng hợp nghiên cứu, không phải kết quả của nguồn.

Đợt audit này không tải ảnh bệnh nhân, không giải nén ảnh, không xin hoặc chấp nhận DUA. Đối với LUMIERE, chỉ đọc metadata API/README và ZIP central directory bằng HTTP range; không đọc các member chứa pixel. Những thuộc tính không có ở mức patient/visit vẫn giữ **UNKNOWN**.

## 1. Hợp đồng thời gian cần kiểm tra

Với Family C, một mô hình chỉ được gọi là có giá trị world-model theo nghĩa vận hành của dự án khi có thể trả lời rõ năm ô sau:

| Ô | Câu hỏi phải trả lời | Cảnh báo |
|---|---|---|
| Observation | Tại cutoff, ảnh, mask, timestamp, care metadata nào thực sự đã biết? | Ảnh ở visit tương lai, template, crop, registration hoặc label được tạo từ toàn bộ trajectory có thể làm đổi bài toán. |
| State | State mô tả gánh nặng/tổn thương, giải phẫu, tốc độ thay đổi, hay chỉ một latent phục vụ tái tạo? | Latent dự đoán tốt không chứng minh là biology, viable tumor, hay state lâm sàng. |
| Transition | Cái gì làm state thay đổi; có điều kiện theo action/treatment hay chỉ theo thời gian? | `treatment-conditioned` trên dữ liệu quan sát không đồng nghĩa với `do(treatment)`. |
| Future | Dự báo observation, mask, volume, change map, clinical endpoint hay phân phối nhiều tương lai? | Một target sau một context, interpolation, reconstruction và free multi-step rollout là các protocol khác nhau. |
| Purpose | Dự báo để làm gì: mô tả trajectory, cảnh báo, chọn nhóm nghiên cứu, mô phỏng hay planning? | Image similarity, correlation hoặc sample diversity không tự chứng minh simulation/planning/decision support. |

Hai kiểm tra tối thiểu là: (i) chỉ dùng prefix được phép trước mỗi target; (ii) báo cáo sai số theo từng horizon và từng visit tương lai. Với C, cần thêm current-only, last-observation/persistence, trend đơn giản và endpoint-level evaluation. Causal treatment claim chỉ được mở khi thiết kế dữ liệu và giả định nhận dạng hỗ trợ nó.

## 2. Những bài trực tiếp có temporal evaluation cần đối chiếu

### 2.1 Petersen et al. — `Continuous-Time Deep Glioma Growth Models` (MICCAI 2021)

**Nguồn verified:** Petersen, Isensee, Köhler, Jäger, Zimmerer, Neuberger, Wick, Debus, Heiland, Bendszus, Vollmuth và Maier-Hein; MICCAI 2021, LNCS 12903:83–92, DOI [10.1007/978-3-030-87199-4_8](https://doi.org/10.1007/978-3-030-87199-4_8); bản phương pháp [arXiv:2106.12917v2](https://arxiv.org/html/2106.12917); code [MIC-DKFZ/deep-glioma-growth](https://github.com/MIC-DKFZ/deep-glioma-growth). Canonical bibliographic record là chương MICCAI; chi tiết phương pháp/evaluation dưới đây được đọc ở bản tác giả arXiv HTML, không đồng nhất hai artifact.

| Thành phần | Audit |
|---|---|
| Hệ được mô hình hóa | Diễn tiến không gian của glioma giữa các lần MRI. |
| Observation | MRI đa chuỗi và segmentation tumor ở các thời điểm liên tục; training/test dùng 2–5 context observations rồi query một target time. |
| State | Global stochastic trajectory code và multi-scale context representation. Đây là latent dự báo không gian, không phải đo trực tiếp tốc độ tế bào, viability hay cơ chế sinh học. |
| Transition | Continuous-time conditional neural process; query ở thời gian tùy ý. Không có action. Cohort có hai nhánh điều trị, nhưng tác giả nói không tìm thấy khác biệt OS và **bỏ qua treatment effects, coi biến thiên là stochasticity**. Đây là lựa chọn mô hình, không phải bằng chứng rằng treatment không ảnh hưởng biology. |
| Future | Phân phối segmentation tumor tại target time; nhiều sample có cùng global distribution để tạo trajectory nhất quán. |
| Purpose | Spatial growth forecast và phân tích plausible future masks. Không có policy/planning evaluation. |
| Scale/data | 379 bệnh nhân từ randomized lomustine+bevacizumab versus chemotherapy trial; 3–13 longitudinal scans, mean 4.85; MRI native/pre/post T1, T2, FLAIR và annotation edema/enhancing/necrosis. |
| Evaluation thật sự | Test Loss, KL “Surprise”, predictive Dice và Query Volume Dice. Query Volume Dice lấy 100 sample rồi chọn sample có whole-tumor volume gần **giá trị tương lai thật nhất**. |
| Free rollout? | Không được chứng minh như protocol 2 past → 2 future không nhận observation mới. Mỗi test query dùng context rồi target. “Arbitrary time query” không tự đồng nghĩa autoregressive long-horizon rollout. |
| Bất định | Có sampling nhưng paper không thiết lập calibration/coverage của phân phối segmentation. |

**Adverse finding — oracle selection.** Query Volume Dice là một upper-bound kiểu “best of 100” dùng future tumor volume. Nó hữu ích để hỏi liệu sample set có chứa shape phù hợp hay không, nhưng không phải quy tắc chọn sample triển khai tại cutoff. So sánh novelty bằng metric này mà không có proper score, coverage hoặc quy tắc selection không oracle sẽ làm overstate hiệu năng.

**Allowed claim:** dự báo phân phối spatial mask trong cohort tương tự dưới quy ước treatment bị bỏ qua. **Không allowed:** natural-history forecast không điều trị, treatment effect, hoặc biological growth simulator chỉ từ latent.

### 2.2 ImageFlowNet — `ImageFlowNet: Forecasting Multiscale Image-Level Trajectories of Disease Progression with Irregularly-Sampled Longitudinal Medical Images` (ICASSP 2025)

**Nguồn verified:** Liu, Xu, Shen, Huguet, Wang, Tong, Bzdok, Stewart, Wang, Del Priore và Krishnaswamy; ICASSP 2025, DOI [10.1109/ICASSP49660.2025.10890535](https://doi.org/10.1109/ICASSP49660.2025.10890535); methods mở rộng [arXiv:2406.14794](https://arxiv.org/html/2406.14794); code [KrishnaswamyLab/ImageFlowNet](https://github.com/KrishnaswamyLab/ImageFlowNet).

| Thành phần | Audit |
|---|---|
| Hệ | Ảnh y khoa longitudinal: retinal atrophy, MS và glioma. |
| Observation | Ảnh trước và khoảng thời gian giữa visit; registration/foreground preprocessing; test-time history có thể được dùng để adapt flow field. |
| State | Multi-scale visual latent/flow. Các tác giả mô tả disease progression, nhưng paper không chứng minh latent là biology, lesion viability hoặc clinical state đủ cho mọi endpoint. |
| Transition | ODE/SDE flow theo elapsed time; không action. |
| Future | Ảnh `x_j` hoặc geometry suy ra bằng segmentation, với công thức đánh giá cho các cặp `i<j`. |
| Scale/data | METforMIN: 132 eyes, 2–5 visits, irregular tối đa 24 tháng; LMSLS MS: trung bình 4.4 time points, 79 series, khoảng 5 năm; LUMIERE: 91 bệnh nhân, 795 series, mỗi series 2–18 time points theo paper. Chỉ LUMIERE có relative week-rounded release; không gọi đó là actual days. |
| Evaluation | PSNR/SSIM/MAE/MSE cho ảnh; Dice/HD cho geometry qua segmentation network; stratification major/minor atrophy/growth. Không có calibration/coverage và không có planning/control success. |
| Rollout | Paper cho phép query thời gian, nhưng protocol chính là direct prediction giữa các cặp observed/target. Không có bằng chứng rằng model được free-run qua hai target tương lai liên tiếp mà không nhận ảnh mới. |
| Uncertainty | Có SDE sample nhưng tác giả ghi nhận variation nhỏ vì không có explicit diversity encouragement; sample spread không được chứng minh calibrated. |

**Future-informed preprocessing risk.** Appendix/preprocessing chọn retinal registration anchor từ các pairwise matches thành công trên **toàn bộ longitudinal series**, rồi dùng common foreground crop. Nếu protocol là dự báo từ prefix, anchor/crop này nhìn thấy tương lai. Nguồn không báo cáo một ablation định lượng về inflation; kết luận an toàn là cần audit prefix-only, không khẳng định bias đã đo được. Appendix D.2 nói MS đã được đăng ký sẵn; D.3 dùng affine rồi diffeomorphic registration về scan đầu của glioblastoma series. Phép căn ảnh future về hệ tọa độ prefix có thể hợp lệ để chấm target; cần kiểm tra riêng có dùng target để sửa input/crop hay không. Không kết luận mọi nhánh đều rò rỉ.

**Patient-specific adaptation.** Test-time optimization fine-tunes flow field trên các ảnh trước đó rồi dự đoán ảnh kế tiếp; đây là một hình thức fitting theo bệnh nhân, không giống một state encoder cố định. Nó có thể hợp lệ nếu cutoff và số iteration được đóng băng trước, nhưng phải so với no-adaptation và không được để future-informed preprocessing lọt vào adaptation.

**Allowed claim:** image-level interpolation/forecast dưới irregular time với derived geometry evaluation. **Không allowed:** latent được giải thích như tốc độ bệnh sinh học, uncertainty đã hiệu chuẩn, hay treatment/counterfactual effect.

### 2.3 TaDiff — `Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction` (TMI 2025)

**Nguồn verified:** Liu, Fuster-Garcia, Hovden, MacIntosh, Grødem, Brandal, Lopez-Mateu, Sederevičius, Skogen, Schellhorn, Bjørnerud và Emblem; IEEE TMI 44(6):2449–2462, DOI [10.1109/TMI.2025.3533038](https://doi.org/10.1109/TMI.2025.3533038); [arXiv:2309.05406](https://arxiv.org/html/2309.05406); code [samleoqh/TaDiff-Net](https://github.com/samleoqh/TaDiff-Net).

| Thành phần | Audit |
|---|---|
| Hệ | Diffuse glioma dưới observed treatment context. |
| Observation | MRI/mask lịch sử, elapsed time và treatment information được ghi nhận. |
| State | Joint MRI/tumor latent và segmentation branch. Đây vẫn là predictive imaging state; tumor mask không trực tiếp xác nhận viable tumor hay treatment mechanism. |
| Transition | Treatment/time-conditioned stochastic diffusion. Treatment là biến điều kiện đã quan sát, không phải randomized intervention trong thí nghiệm model. |
| Future | MRI slice/volume và tumor segmentation ở future exam; multiple samples tạo alternative futures. |
| Data/evaluation | Local: 225 MRI exams/23 high-grade glioma patients; external LUMIERE: 37 patients/132 exams theo paper. Test dùng **ba MRI lịch sử gần nhất**; nếu ít hơn thì duplicate exam gần nhất. Future được chọn là frame gần target. Local test 3,352 slices và external test 8,976 slices; bins theo treatment/day range 0–50, 51–220, 221–365. |
| Metrics | SSIM, PSNR, MSE ở local và external; tumor DSC, relative volume difference và Pearson correlation giữa predicted/GT volume chỉ ở local treatment/day bins. Correlation giảm ở 221–365, với outliers gồm second surgery/secondary GBM. |
| Rollout | Không phải protocol 2 past → 2 future visits; latest-three history + một target-nearest frame. Paper không cho thấy recursive free-run với treatment sequence mới. |
| Uncertainty | Diffusion samples, nhưng không có calibration/coverage report cho tumor state. |

**External-label caveat — đã đối chiếu lại §IV-A và §IV-C2.** LUMIERE không có expert/manual tumor masks cho protocol này. Tác giả **chỉ đánh giá MRI generation bằng SSIM/PSNR/MSE ở tập ngoài**, không tính DSC/RVD cho external tumor predictions. Hình minh họa mask/uncertainty không thay thế đánh giá định lượng đó. Không diễn giải external image score thành external tumor-growth validation.

**Treatment claim boundary.** Mô hình có thể dự báo ảnh/segmentation trong phân phối treatment đã thấy. Từ đó không suy ra `do(A=a)` hoặc individual treatment effect; treatment assignment, second surgery, censoring và missing visits vẫn là confounders/selection processes.

### 2.4 BrLP — `Brain Latent Progression: Individual-based spatiotemporal disease progression on 3D Brain MRIs via latent diffusion` (Medical Image Analysis 2025)

**Nguồn verified:** Puglisi, Alexander và Ravì; Medical Image Analysis 106:103734, DOI [10.1016/j.media.2025.103734](https://doi.org/10.1016/j.media.2025.103734); [arXiv:2502.08560](https://arxiv.org/html/2502.08560); code [LemuelPuglisi/BrLP](https://github.com/LemuelPuglisi/BrLP).

| Thành phần | Audit |
|---|---|
| Hệ | Thay đổi não theo tuổi/thoái hóa trong ADNI, OASIS-3 và AIBL; không phải treatment simulator. |
| Observation | Baseline/longitudinal T1 MRI, metadata và các regional volume auxiliaries tùy biến thể. |
| State | Patient-conditioned latent progression với auxiliary regional trajectories; voxel/latent là imaging proxy. Không có bằng chứng state là tốc độ atrophy sinh học đo trực tiếp. |
| Transition | Time/metadata-conditioned generative progression, không action. |
| Future | MRI tương lai, regional volumes và derived regional error; target age/follow-up. |
| Evaluation | MSE/SSIM; MAE cho hippocampus, amygdala, lateral ventricles; uncertainty-error relationship. Fast-progressor analysis dùng internal 154 và external 165 subjects có 2-year MRI, xếp hạng theo observed hippocampal atrophy. |
| Uncertainty | LAS/inference samples; sample variance/global/voxel uncertainty. Mixed-effects cho thấy uncertainty liên hệ prediction error (voxel Spearman khoảng 0.63 ± 0.11 sau loại background; global error association có p<.001). |
| Calibration | Không có coverage, reliability diagram hoặc proper-score calibration. Association giữa spread và error không phải calibration. |
| Rollout/planning | Target-time generation; không có free multi-step control/planning. Fast-progressor ranking là retrospective outcome stratification, không phải prospective clinical utility. |

**Potential hidden endpoint use.** Nếu nhóm fast progressor được chọn bằng observed future atrophy, đó là phân tích hậu nghiệm hữu ích cho stratification nhưng không được tính như một deployable selection trước horizon. Prefix-only time adaptation và template/registration của từng release cần kiểm tra riêng; bài không đủ để tuyên bố đã đóng leakage contract cho Family C.

### 2.5 Δ-LFM — `Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation` (ICLR 2026)

**Nguồn verified:** Chen, Yin, Chen, Chen và Li; ICLR 2026 camera-ready, [OpenReview PDF](https://openreview.net/pdf/a1558b2e7d9494789fdd3057059dfbe2add8737e.pdf); methods [arXiv:2512.09185](https://arxiv.org/html/2512.09185). Benchmarks ADNI, OASIS-3 và AIBL; publication metadata được ghi trong camera-ready.

| Thành phần | Audit |
|---|---|
| Hệ | Longitudinal 3D brain MRI, chủ yếu age/degeneration trajectories. |
| Observation | MRI, visit time và history để align patient-specific latent direction. |
| State | Ordered patient-specific latent trajectory; paper dùng ArcRank/latent constraints. Không có chứng minh latent tương ứng một biomarker hay anatomy state độc lập. |
| Transition | Arbitrary-time flow matching. Paper nói rõ progression coordinate **không phải physical clock**, mô hình hóa latent progression gần đường thẳng/constant velocity và thừa nhận progression có thể uneven. |
| Future | Future MRI và regional change/Δ-RMAE. |
| Evaluation | PSNR/SSIM, structure fidelity, regional MAE và Δ-RMAE; ablations trên image/structure. Không có calibration, multi-step free rollout, state-sufficiency test hoặc planning. |
| Action | None. Treatment/lesion discontinuity chưa được giải quyết bởi monotone patient-specific ordering. |

**Adverse implication.** “Patient-specific latent trajectory + arbitrary time + regional anatomy readout” đã có prior art gần; novelty không thể chỉ dựa vào individualization, continuous query hoặc đổi generator. Cần một endpoint/state contract và baseline patient-specific rõ ràng hơn.

### 2.6 Pash et al. — `Predictive digital twins with quantified uncertainty for patient-specific decision making in oncology` (JCP 2026)

**Nguồn verified:** Pash, Villa, Hormuth, Yankeelov và Willcox; Journal of Computational Physics 560:114937, published 2026-09-01, DOI [10.1016/j.jcp.2026.114937](https://doi.org/10.1016/j.jcp.2026.114937); [arXiv:2505.08927](https://arxiv.org/html/2505.08927); code [gtpash/dt4co](https://github.com/gtpash/dt4co).

| Thành phần | Audit |
|---|---|
| Hệ | Glioma patient-specific mechanistic digital twin. |
| Observation | Longitudinal MRI-derived tumor/cellularity proxy, anatomy và recorded radiotherapy/chemotherapy schedule; UPENN-GBM và IvyGAP theo paper. |
| State | Cell-density field cùng posterior spatial parameters về proliferation/diffusion/treatment response. Đây là state **mechanistic/model-based**, nhưng cellularity vẫn được suy ra từ imaging và giả định mô hình, không phải measurement trực tiếp in vivo. |
| Transition | Reaction–diffusion PDE với treatment terms; numerical implicit Euler 1-day step. Có thể chạy scenario trong phạm vi model, nhưng không có evidence đủ cho mọi protocol/action. |
| Future | Tumor volume, spatial cellularity và quantities of interest; posterior predictive distribution. |
| Evaluation | Calibration historical trajectory; **last image được giữ làm prediction target**; posterior prediction spatial agreement/Dice/cellularity; simulation window từ first scan đến last scan qua calibration. |
| Uncertainty | Bayesian posterior/low-rank Laplace và propagation. Paper định lượng uncertainty, nhưng không biến đây thành calibration/coverage guarantee trên cohort độc lập. |
| Rollout/planning | Forward simulation có thể hỗ trợ experimental-design analysis; không phải validation của closed-loop planning hay observed patient benefit. Model inadequacy được tác giả thừa nhận. |

**Interpretation.** Pash là prior art bất lợi cho claim “medical world model cần đưa uncertainty/state vào simulation” ở mức rộng. Khoảng trống có thể còn lại ở independent prospective calibration, image-derived state error, multi-patient generalization hoặc decision utility; không còn ở việc đầu tiên kết hợp MRI, state, transition, treatment schedule và uncertainty.

## 3. Adversarial prior art: các novelty claim rộng đã bị yếu đi

Bảng này nhằm bác bỏ novelty trước khi đề xuất gap. “Bác bỏ” ở đây là bác bỏ **claim rộng**, không phải nói mọi câu hỏi hẹp đã được giải.

| Claim dễ nêu | Prior art đối nghịch đã đọc | Điều còn chưa được chứng minh |
|---|---|---|
| Continuous-time imaging forecast mới trong y khoa | Petersen: arbitrary target-time spatial glioma distribution; Lachinov: NeuralODE future segmentation; ImageFlowNet: irregular-time image trajectories | Prefix-only two-future evaluation, state sufficiency và calibrated long-horizon forecast trong một release công khai cụ thể. |
| Patient-specific latent disease dynamics mới | ImageFlowNet test-time history adaptation; BrLP regional auxiliaries/uncertainty; Δ-LFM patient-specific latent flow | Latent có ý nghĩa sinh học, vượt trend đơn giản, và tái sử dụng trên endpoint độc lập. |
| Stochastic samples đồng nghĩa uncertainty hữu ích | Petersen 100 samples; TaDiff diffusion samples; BrLP sample variance; Pash posterior | Calibration/coverage, proper scores, miss-risk theo horizon và utility của uncertainty. |
| Treatment-conditioned MRI forecast là counterfactual simulator | TaDiff recorded treatment; Stowers biology+MRI model; Pash treatment schedule | Individual treatment effect, transportability và intervention validation. Durso-Finley dùng RCT/Neural SDE cho factual EDSS và treatment contrasts, nhưng vẫn không phải evidence rằng image-only observational treatment input xác định causal effect. |
| State-level treatment response trên MRI chưa có | Stowers dự báo interpretable CBBM parameters từ pretreatment MRI và mid/end NAC TTC/TTV/pCR; TaDiff future MRI/mask; Pash cellularity | Multi-visit spatial state, actual public-data reproducibility, missingness/confounding audit và calibrated future response. |
| Uncertainty/state model đã là simulator/planner | Pash có mechanistic forward simulation và experimental-design analysis | Closed-loop policy, causal intervention và patient utility chưa được chứng minh. |

### Năm prior art adversarial mạnh nhất cho C

1. **Petersen 2021** — đánh trực tiếp vào spatial glioma growth, continuous-time query, stochastic future masks và multi-context history; oracle Query Volume Dice phải bị hạ cấp khi so sánh triển khai.
2. **Lachinov et al. 2024** — đánh vào continuous anatomical state/transition với NeuralODE, future segmentation, volume và multi-dataset evaluation; labels ADNI ventricle có phần tự động nên reliability cũng là cảnh báo.
3. **Durso-Finley et al. 2024, MICCAI** — [DOI](https://doi.org/10.1007/978-3-031-72384-1_38), [arXiv](https://arxiv.org/html/2406.12807). Neural SDE dùng MRI + clinical/demographic variables để dự báo EDSS factual và treatment contrasts ở khoảng 12 tuần đến week 96, đánh giá uncertainty bằng confidence–error filtering. Đây là prior art mạnh cho stochastic continuous trajectories và treatment analysis, dù target là clinical EDSS và dữ liệu RCT độc quyền, không phải lesion image state.
4. **Stowers et al. 2025, Radiology: Artificial Intelligence** — [DOI](https://doi.org/10.1148/ryai.240124). CNN từ pretreatment MRI dự báo tham số mô hình biology-based; model mô phỏng TTC/TTV qua NAC. Cohort 118 phụ nữ TNBC, visit 1 trước điều trị, visit 2 sau hai cycles và visit 3 sau bốn cycles. Đây là prior art bất lợi cho claim “first treatment-response state simulator”.
5. **Pash et al. 2026** — đánh vào mechanistic state, data assimilation, treatment schedule, posterior uncertainty, held-out last-image prediction và forward simulation. Nó không chứng minh clinical utility, nhưng đủ để bác bỏ novelty rộng quanh “digital twin có uncertainty”.

Các công trình ImageFlowNet, TaDiff, BrLP và Δ-LFM ở §2 là các đối chứng trực tiếp hơn cho image-level longitudinal generation; không nên loại chúng chỉ vì title không dùng từ “world model”.

<a id="data-audit"></a>

## 4. Audit dữ liệu công khai: có đủ hai past + hai future không?

### 4.1 LUMIERE — tín hiệu khả thi mạnh nhất, nhưng chưa phải cohort đã usable

**VERIFIED từ dataset paper:** Suter et al., [LUMIERE, Scientific Data 2022, DOI 10.1038/s41597-022-01881-7](https://www.nature.com/articles/s41597-022-01881-7), mô tả 91 bệnh nhân, 638 study dates và 2,487 MRI images. Follow-up dates được anonymize relative với preoperative date và đổi thành **week counts**; cùng một nominal week có suffix như `week-000-1`, `week-000-2`. Vì vậy dossier này không gọi LUMIERE date là actual days. Bài báo ghi 599/638 study dates có đủ bốn sequence T1, T1Gd, T2 và FLAIR; annotation/RANO và automatic segmentation có provenance khác nhau, outliers được giữ lại.

**VERIFIED từ release metadata:** Figshare [archive API](https://api.figshare.com/v2/articles/21249516) và [README API](https://api.figshare.com/v2/articles/21266241) đều public ở thời điểm audit; API ghi license CC0 và archive/README file list. README mô tả cấu trúc `Patient-XXX/week-XXX`, MRI files, masks, RANO, MRI-info và clinical/pathology records. Public release có điều kiện non-commercial trong README; exact institutional-use interpretation vẫn cần nhóm kiểm tra trước khi dùng.

**Derived central-directory audit (không phải claim mới của paper):** chỉ lấy ZIP tail/central directory qua HTTP range, không download hoặc decompress pixel. Đếm được:

| Điều kiện manifest | Kết quả derived |
|---|---:|
| Patient directories | 91 |
| Study/week directories | 638 |
| Study dirs có đủ bốn basename `CT1.nii.gz`, `T1.nii.gz`, `T2.nii.gz`, `FLAIR.nii.gz` | 599 |
| Bệnh nhân có ≥4 study dirs đủ bốn sequence | 66/91 |
| Bệnh nhân có ≥5 study dirs đủ bốn sequence | 53/91 |
| Bệnh nhân có ≥4 study dirs đủ bốn sequence và ≥4 nominal week numbers khác nhau (gộp suffix cùng week) | **62/91** |

Con số 62 là quy tắc conservative để tránh đếm `week-000-1` và `week-000-2` như hai thời điểm danh nghĩa khác nhau. Nó chỉ cho thấy một **feasibility signal** cho 2-past+2-future. Nó chưa chứng minh:

- bốn visit đó có interval đủ cho horizon 90/180 ngày;
- masks/labels ở cả bốn visit đều expert/reliable;
- treatment/second surgery/dropout có thể được audit;
- prefix-only registration/crop/normalization không nhìn tương lai;
- một cutoff và split theo patient sẽ giữ đủ cohort;
- four sequence completeness đồng nghĩa target lesion mask usable.

Do week rounding, window/horizon phải định nghĩa theo interval uncertainty được công bố; không biến week count thành số ngày chính xác.

### 4.2 CFB-GBM v2.0 — public, nhưng không đạt 2-past+2-future theo thiết kế

**VERIFIED:** [CFB-GBM v2.0 arXiv:2608.17884](https://arxiv.org/html/2608.17884), §2–§3, mô tả 264 bệnh nhân GBM với đúng ba temporal labels `t0`, `t1`, `t2`; t0 khoảng một tuần trước chemoradiotherapy, t1 khoảng bốn tháng và t2 khoảng sáu tháng. GTV completion tăng từ 35% lên 97%; generated GTV được five-radiologist validated. Data source được chỉ tới [TCIA CFB-GBM](https://www.cancerimagingarchive.net/collection/cfb-gbm). NIfTI conversion/rigid registration tới baseline T1-Gd được mô tả, modality availability không đồng nhất.

**Kết luận feasibility:** ba mốc có thể hỗ trợ baseline→future hoặc một/two future pairs tùy target, nhưng không thể tạo hai visit past và hai visit future ở cùng bệnh nhân theo release design. Không được dùng 264 bệnh nhân để suy ra một cohort bốn mốc.

### 4.3 I-SPY2/ACRIN 6698 — protocol bốn mốc, patient-level completeness UNKNOWN

**VERIFIED:** trang [TCIA I-SPY2/ACRIN source](https://wiki.cancerimagingarchive.net/plugins/viewsource/viewpagesrc.action?pageId=70230072) mô tả tối đa bốn MRI clinical timepoints: T0 pre-treatment, T1 sau ba cycles/ba tuần, T2 giữa Paclitaxel và AC, T3 sau bốn AC cycles trước surgery. Trang cũng mô tả derived FTV masks/maps và cảnh báo derived values không nhất thiết giống trial values. [Data-description PDF](https://wiki.cancerimagingarchive.net/download/attachments/50135447/ACRIN%206698%20ISPY2%20DWI%20and%20DCE%20MRI%20Data%20Descriptions_20210520.pdf?api=v2) ghi không phải mọi object có mặt ở mọi case vì có study không phân tích được; timing từ DICOM metadata là best effort và độ chính xác không được bảo đảm.

**UNKNOWN:** nguồn đã đọc không cung cấp patient-level intersection thực sự đủ cả T0–T3 cho collection/merged cohort. Con số collection/cohort tổng không được dùng làm số usable 2-past+2-future. Cần manifest/clinical CSV được phép đọc và đếm theo patient, modality, FTV label, treatment arm, timepoint trước khi Q8 được coi là khả thi.

### 4.4 BreastDCEDL — phát hiện dễ nhầm intra-exam phases với longitudinal visits

**VERIFIED:** [official BreastDCEDL repository](https://github.com/naomifridman/BreastDCEDL) README và [metadata CSV](https://raw.githubusercontent.com/naomifridman/BreastDCEDL/ed4bfe7a3407b722bc32c01ba38aa3619cb73ab5/BreastDCEDL_metadata.csv) mô tả một derived breast DCE resource. Trong README, `n_times`/MinCrop là số contrast phases trong **một lần DCE exam** (precontrast, early, late; full version giữ 3–12 acquired contrast phases), không phải T0–T3 treatment visits.

**Derived metadata audit:** snapshot CSV có 2,070 rows, trong đó 982 `spy2`, 172 `spy1`, 916 `duke`; I-SPY2 `n_times` chủ yếu 6–8 phases. README và snapshot hiển thị tổng release hơi khác nhau; đây là version conflict cần ghi UNKNOWN. Vì `n_times≥4` là intra-exam, nó không cung cấp bằng chứng cho ≥2 past + ≥2 future clinical visits. Đây là falsifier trực tiếp cho suy luận “BreastDCEDL có bốn timepoints nên Q8 đã đủ dữ liệu longitudinal”.

### 4.5 OASIS — có quy ước thời gian, chưa có patient-level count trong audit này

**VERIFIED:** [OASIS official FAQ](https://sites.wustl.edu/oasisbrains/home/oasis-resources-and-faq/) mô tả visit identifier kiểu `MR_d1234`, trong đó thời gian được biểu diễn theo days from entry và người dùng phải đặt matching criterion. **UNKNOWN:** trong đợt này chưa audit release/permission snapshot, số người có ≥4 T1 visits, segmentation intersection, scan protocol continuity hay future-safe preprocessing. OASIS không được dùng như bằng chứng đã có cohort usable.

## 5. Adjudication Q5–Q8

Các câu hỏi vẫn là ứng viên; bảng dưới không chọn topic. “Novelty” là plausibility sau adversarial search, không phải claim đã chứng minh.

| Câu hỏi | Bằng chứng làm tăng khả thi | Prior art làm giảm novelty | Falsifier mạnh nhất | Causal boundary |
|---|---|---|---|---|
| **Q5 glioma 2 past → 2 future** | LUMIERE central-directory audit cho 62/91 conservative patients có ≥4 nominal weeks và đủ bốn sequence ở study-dir; cần mask/interval audit. CFB-GBM bị loại cho protocol bốn visit. | Petersen, ImageFlowNet, TaDiff và Pash đã có glioma/longitudinal spatial or MRI prediction. Novelty chỉ còn có thể ở fixed prefix, reliable lesion endpoint, two-future state evaluation và calibrated uncertainty trên release cụ thể. | Sau khi chỉ dùng prefix-safe preprocessing và masks audited, persistence/linear burden hoặc direct predictor ngang/better; second future không cải thiện; cohort usable <4 visits. | Chỉ forecast dưới observed care; không natural-history hoặc treatment effect. |
| **Q6 brain anatomy 2 past → 12/24 mo** | ADNI/OASIS có prior art và OASIS có actual days-from-entry convention; patient-level ≥4 usable intersection chưa audit. | Lachinov, BrLP, Δ-LFM đã có anatomical/individual trajectory; broad patient-specific latent claim không mới. | Regional mixed-effects/individual linear trend đạt ngang; change signal dưới segmentation error; gains mất khi bỏ future-informed template và giữ state fixed cho endpoint thứ hai. | Không gọi latent là biomarker/diagnostic state; chỉ forecast anatomy proxy. |
| **Q7 MS lesion birth/growth** | Có thể đặt endpoint event/location/volume nếu có đủ labeled depth; nguồn public pilot cần audit trước. | ImageFlowNet MS, Petersen stochastic spatial trajectories và Durso-Finley NSDE đã làm stochastic/uncertainty continuous medical trajectories, dù Durso target EDSS. | Inter-rater/matching noise lớn hơn signal; persistence/simple stochastic baseline ngang; không có hai future labeled visits hoặc đủ annual depth. | Chỉ imaging-event forecast; không DMT efficacy hay causal clinical course. |
| **Q8 treatment-associated breast response** | I-SPY2 xác nhận protocol T0–T3; actual four-visit patient intersection UNKNOWN. | Stowers đã biology+MRI response simulator; TaDiff treatment-conditioned MRI/tumor prediction; derived FTV and treatment confounding remain. | FTV slope/mixed-effects/direct predictor ngang spatial state; apparent gain do arm/visit availability or future mask; no sufficient all-four cohort. | Forecast under observed care/treatment schedule; không individual treatment effect hoặc regimen recommendation. |

### Chi tiết falsification protocol đề xuất

1. **Data gate trước model:** patient-level count theo `(patient, visit, modality, mask, timestamp, treatment-known-before-cutoff)`, rồi loại những prefix/future không đủ. Không suy từ số images, series, DCE phases hay tổng cohort.
2. **Prefix-only preprocessing gate:** mọi registration anchor, crop, atlas/template, normalization và patient-specific adaptation phải được fit bằng information available trước target. Chạy một ablation full-series để đo, nhưng không dùng nó làm kết quả chính.
3. **State-value gate:** so sánh state/history model với current-only, last observation, individual linear trend, mixed-effects và direct target predictor dưới cùng patient split. Dùng một endpoint tương lai độc lập để test state reuse; không chỉ decode latent rồi chấm ảnh.
4. **Two-future gate:** báo cáo first-future và second-future riêng, recursive/free-run so với reconditioned tracking. Đây là gate cho Q5 hai future visits, không phải định nghĩa bắt mọi world model phải autoregressive. Dự báo trực tiếp nhiều thời điểm từ một prefix vẫn hợp lệ; cần chấm các target cùng prefix và tính nhất quán joint trajectory. Horizon dài ở một target cũng không tự chứng minh chất lượng cả trajectory.
5. **Uncertainty gate:** dùng coverage/proper score/calibration và sharpness theo horizon; sample spread hoặc uncertainty–error correlation chỉ là exploratory nếu thiếu coverage.
6. **Causal gate:** treatment variable chỉ là context của observed-care forecast. Counterfactual/intervention claim phải có assignment design, time-varying confounding handling và target data hỗ trợ; nếu không, claim bị giới hạn rõ.

## 6. Thông tin còn thiếu ngăn việc chọn đề tài hôm nay

- **LUMIERE:** danh sách patient/nominal-week giao với expert masks/RANO, interval uncertainty từ week rounding, second surgery/treatment/censoring metadata và prefix-safe registration/crop. 62/91 chưa phải số usable cho Q5.
- **CFB-GBM:** không thiếu count cho câu hỏi bốn visit; release có ba mốc nên không thể là nguồn chính cho 2+2.
- **I-SPY2:** manifest/clinical CSV được phép đọc để đếm T0–T3 intersection, FTV-mask completeness, exact treatment/time fields và missingness. Protocol label không thay thế observed visit.
- **BreastDCEDL:** phải tách rõ intra-exam phase khỏi longitudinal visit; không dùng `n_times` như depth qua điều trị.
- **ADNI/OASIS:** approved access snapshot, patient-level count ≥4 usable visits, actual dates, T1/region segmentation provenance, scanner/protocol shifts và future-safe template construction.
- **MS:** release có đủ repeated expert lesion masks, lesion matching/rater agreement, actual interval và two-future coverage hay không.
- **Cross-cutting:** intended-use horizon/latency, endpoint error floor, baseline headroom, missingness/care timeline và người cộng tác clinical/statistical. Không có các thông tin này, xếp hạng Q5–Q8 chỉ là hypothesis.

## 7. Hành động nghiên cứu tiếp theo

1. Đóng một metadata-only audit script cho từng release được phép, lưu số đếm và rule version; chưa tải patient images.
2. Chốt một cutoff/horizon cho mỗi câu hỏi rồi viết protocol trước khi xem target masks, gồm handling của week rounding, missing visits và treatment-after-cutoff.
3. Chạy simple-baseline headroom trên một pilot nhỏ: last observation, linear/mixed-effects, deformation/persistence và direct predictor; không bắt đầu bằng backbone mới.
4. Đối chiếu backward/forward citations của Petersen, Lachinov, Stowers và Pash theo đúng endpoint/horizon; đặc biệt tìm calibration/proper-score and state-reuse prior art.
5. Chỉ sau khi data gate, endpoint reliability và falsification results qua được mới để chủ dự án chọn câu hỏi C hoặc chuyển sang A/B. Không quyết định architecture trong bước này.

## 8. Kết luận audit

**VERIFIED:** Family C đã có prior art thực hiện continuous-time query, patient-specific image trajectories, stochastic samples, treatment-conditioned MRI, anatomy/volume evaluation và mechanistic Bayesian simulation. Public metadata cho thấy LUMIERE có feasibility signal đủ sâu ở một phần bệnh nhân; CFB-GBM không đủ bốn mốc; I-SPY2 có bốn mốc theo protocol nhưng subject-level completeness chưa xác minh; BreastDCEDL `n_times` không phải visit depth.

**INTERPRETATION / HYPOTHESIS:** gap defensible, nếu còn, phải đặt ở temporal contract và endpoint cụ thể: prefix-safe two-future state forecast, state sufficiency so với baseline đơn giản, calibration/coverage, hoặc observed-care estimand có missingness/confounding được nêu rõ. “Medical world model” chung, “continuous-time”, “patient-specific latent”, “multi-hypothesis” hoặc “treatment-aware” riêng lẻ đều không còn là novelty đủ mạnh.
