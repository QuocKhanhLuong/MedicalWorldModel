# Family A — audit sâu về dự báo chuyển động sinh lý / giải phẫu

**Ngày đối chiếu:** 2026-09-12 (Asia/Bangkok)
**Phạm vi:** physiological/anatomical motion forecasting, motion modeling và các baseline gần nhất cho ứng viên A.
**Trạng thái quyết định:** A/B/C vẫn là các họ ứng viên; tài liệu này không chọn topic và không chọn kiến trúc.

Tài liệu này là dossier vòng 2, được đọc sau `README.md`, `AGENTS.md`, các source-of-truth/knowledge-base hiện hành, [medical survey](../MEDICAL_WORLD_MODELS_SURVEY.md), [dataset feasibility](../../DATASET_FEASIBILITY.md), [paper matrix](../../PAPER_MATRIX.md), [OPEN_QUESTIONS](../../OPEN_QUESTIONS.md) và [RESEARCH_LOG](../RESEARCH_LOG.md). Nó đào sâu Q1/Q2/Q3 của family A và ghi lại những prior art có thể bác bỏ claim rộng. Những con số trong hồ sơ là số tác giả báo cáo; nhóm chưa tái lập và không suy ra clinical utility từ chúng.

## Quy tắc evidence

**VERIFIED** là thông tin đọc trực tiếp từ bài gốc, proceedings/publisher/PubMed hoặc repository chính thức của tác giả. **INTERPRETATION / HYPOTHESIS** là tổng hợp, câu hỏi, điều kiện hoặc falsifier do dossier đề xuất. `UNKNOWN` nghĩa là nguồn đã kiểm tra nhưng chưa đủ thông tin; không điền bằng suy đoán. Một latent có năng lực dự báo không được gọi là trạng thái sinh lý có ý nghĩa nếu bài không có phép kiểm tra như vậy.

## Kết luận adversarial ngắn — INTERPRETATION / HYPOTHESIS

1. Claim rộng “medical motion forecasting chưa có predictive state hình học, nhiều horizon, uncertainty, patient adaptation hoặc target-level endpoint” đã bị bác bỏ. Các phản chứng gần gồm Liu 2016, Pham 2019, Romaguera 2020/2021, Gunnarsson 2024, Li 2023, Pohl 2025/2026 và Shimizu 2026.
2. Pohl 2026 là baseline đặc biệt gần với Q1, nhưng là **direct horizon-specific regression** trong PCA-DVF space, không phải free-running rollout. Đóng góp của một bài mới không thể chỉ là “PCA state + dự báo frame cine” hoặc “RNN/Transformer thay nhau”.
3. Strong baseline có hai tầng cần giữ riêng: (i) baseline scalar/centroid đã rất mạnh và có split patient-level, OOD và gating endpoint; (ii) baseline geometry/DVF có state giàu hơn nhưng thường ít bệnh nhân, sequence-specific hoặc có prior 4D image. So sánh vượt tầng là không công bằng nếu không nói rõ state và information contract.
4. Gap có thể còn đáng thử chỉ là giả thuyết hẹp: một state hình học có **incremental predictive value** sau khi đã khống chế history/velocity/phase và preprocessing; multi-step prefix-only evaluation có **calibrated uncertainty** trên held-out patient/scanner; hoặc một endpoint downstream được xác định trước mà simple baselines không đạt. Chưa có bằng chứng để chấp nhận gap nào là novel.
5. Không paper nào dưới đây biến dự báo quan sát thành hiệu ứng can thiệp. Các hệ chuyển động chủ yếu là autonomous physiological transition; treatment/gating chỉ là downstream use hoặc mô phỏng latency, không phải randomized action-conditioned transition.

## Hợp đồng bắt buộc cho Family A

| Thành phần | Hợp đồng phải ghi trước khi làm thí nghiệm | Lỗi cần tránh |
| --- | --- | --- |
| **Observation** | Ảnh cine/MRI/US/CT hoặc surrogate đã có tại thời điểm `t`; ghi cadence, gaps, preprocessing và phần history được phép | Lấy frame tương lai để đăng ký, chọn ROI, scale hoặc xác định phase |
| **State** | Ví dụ: centroid, contour, dense DVF, PCA weights, phase/phase velocity, latent belief; ghi rõ đo được hay suy ra | Gọi latent là physiology/clinical state chỉ vì reconstruction hoặc classification tốt |
| **Transition** | `T(s_t, Δt, u_t nếu có) → s_{t+Δt}`; A hiện tại chủ yếu không có `u` | Gọi measured displacement hoặc beam latency là causal action |
| **Future** | Chọn future state, contour, landmark, DVF, image hoặc risk proxy; tách direct, recursive, filtering/tracking và reconstruction | Dùng image similarity thay cho future-state accuracy |
| **Purpose** | Latency compensation, target tracking, retrospective gating proxy, acquisition timing… phải được định nghĩa bằng endpoint | Từ RMSE/SSIM suy ra giảm toxicity, safe beam hoặc clinical benefit |
| **Scale** | Horizon theo thời gian thực hoặc `% cycle`; báo cadence và context window | Chỉ báo số frame, hoặc ghép phase bins thành thời gian liên tục |
| **Uncertainty** | Nếu có distribution, chấm calibration/coverage/sharpness hoặc proper score theo horizon | “Có Gaussian/latent samples” rồi gọi là calibrated |
| **Planning/simulation** | Chỉ claim simulator/planner khi rollout và utility được kiểm tra ngoài model; không bắt buộc A phải có policy | Gọi predictor một bước là simulator |

## 1. Audit chi tiết Pohl et al. 2026

### 1.1 Metadata và hệ được mô hình hóa — VERIFIED

[Michel Pohl, Mitsuru Uesaka, Hiroyuki Takahashi, Kazuyuki Demachi, Ritu Bhusal Chhatkuli, “Frame forecasting in cine MRI using the PCA respiratory motion model: comparing recurrent neural networks trained online and transformers”](https://doi.org/10.1016/j.compmedimag.2026.102755), *Computerized Medical Imaging and Graphics* 131:102755 (2026), published version; preprint [arXiv:2410.05882v3](https://arxiv.org/abs/2410.05882v3); code và preprocessed examples [official repository](https://github.com/pohl-michel/2D-MR-image-prediction). PDF methods/evaluation đã được đọc trực tiếp.

- **System:** respiratory motion trong 2D sagittal cine-MRI ngắn; không phải disease trajectory, robot hay treatment simulator.
- **Observation:** incoming 2D frames và frame tham chiếu đầu sequence. Paper dùng Lucas–Kanade optical flow giữa initial frame và từng incoming frame.
- **State:** dense 2D deformation vector field (DVF) được nén bằng PCA; `w_j(t)` là PCA weights. Đây là state **inferred geometric/predictive**, không phải nhịp thở đo trực tiếp và không được chứng minh là state sinh lý đầy đủ.
- **Transition:** các bộ dự báo của `w(t)` gồm OLS linear AR, LMS, online RTRL/UORO/SnAp-1/DNI RNN và encoder-only transformer.
- **Future:** predicted PCA weights → predicted DVF → warp reference frame → future cine frame. Mục đích là bù latency, không phải planning hay intervention analysis.
- **Action:** không có action input; transition autonomous theo history và horizon.
- **Scale:** h đến khoảng 2.2 s; ETH ~3.18 Hz, OvGU 6 Hz.

### 1.2 Data và split — VERIFIED

- ETH Zürich gồm **4 sequence 2D** lấy từ 2 volumetric chest-MR sequences, mỗi sequence 200 frames; khoảng 63 s; hai slice trái có cardiac motion và hai slice phải. OvGU gồm **8 sagittal sequence**, mỗi sequence từ một cá nhân, mỗi sequence 498 frames sau khi bỏ 15 frame đầu; khoảng 83 s; resolution in-plane 1.82 mm và through-plane 4.0 mm. Tổng là 12 sequence, không được đổi thành 12 bệnh nhân.
- PCA/DVF basis và optical-flow parameters là sequence-specific. Optical-flow grid search dùng 28.3 s đầu; PCA mean/basis dùng `M_train` của sequence và không cập nhật theo thời gian. Paper giả định breathing pattern ổn định trong sequence ngắn và không có motion out-of-plane đáng kể.
- Sequence-specific split: training + validation chiếm 56.6 s đầu; test là 6.3 s cuối ETH và 26.3 s cuối OvGU. Online methods train 28.3 s; offline methods 50.4 s.
- Population transformer train trên dataset kia và test phần cuối của dataset còn lại để có scanner/subject split; PCA/registration vẫn sequence-specific. PCA-score standardization dùng phần training hoặc prefix của sequence theo protocol riêng của paper.

### 1.3 Forecast contract — VERIFIED

`x_n` chứa `L` PCA-score vectors gần nhất; target là tất cả `n_cp` scores tại `t_{n+L+h-1}`. H được chọn từ 1 đến hmax, trong đó hmax tương ứng khoảng 2.2 s. **Mỗi horizon có model train/validation riêng.** Paper nói rõ lựa chọn này tránh recursive forecasting và error accumulation; encoder-only transformer làm fixed-horizon regression, không dùng decoder để tự sinh chuỗi.

Vì vậy, Pohl là **direct multi-horizon predictor**. Nó cho biết state DVF/PCA có thể hữu ích cho một future query, nhưng không chứng minh rằng model có thể lấy output của chính nó làm input qua nhiều bước, hay chịu được closed-loop/assimilation. Đây là một phản biện trực tiếp với proposal chỉ báo thêm nhiều horizon mà không tách direct và recursive.

### 1.4 Metrics và kết quả — VERIFIED

Metric chính là nRMSE PCA scores trên validation/test và geometric/image prediction error sau khi warp. nRMSE cộng sai số theo thời gian và component rồi đánh giá ở mức sequence; không phải patient-weighted clinical endpoint. Bảng ETH báo cáo persistence khoảng 1.458, linear regression khoảng 0.928, sequence-specific transformer khoảng 0.879; SnAp-1/RTRL/UORO thấp hơn ở horizon dài, còn linear gần cạnh tranh ở horizon ngắn. Abstract báo cáo linear đạt khoảng **1.3 mm geometric error tại 0.32 s** trên ETH; sai số tăng khi h tăng. Confidence intervals được tính theo sequence-level runs; với ETH chỉ có 4 sequence nên không nên diễn giải như patient-level uncertainty.

PCA dimension không tự động càng lớn càng tốt: paper báo component 1–2 thường đủ/được chọn; component cao hơn có thể mang noise, có ích ở h ngắn nhưng kém tin cậy ở h dài. Đây là lý do phải so geometry state với constant velocity/periodic/Kalman dưới cùng basis và cùng prefix.

### 1.5 Pohl làm yếu Q1 ở đâu — VERIFIED và INTERPRETATION / HYPOTHESIS

**VERIFIED:** Pohl đã có explicit inferred geometric state, future frame/geometry endpoint, nhiều horizon đến 2.2 s, patient/scanner-cross-dataset test và strong linear/online baselines. Official code/repository làm cho protocol có thể kiểm tra lại.

**INTERPRETATION / HYPOTHESIS:** Q1 không thể giữ dạng “đầu tiên dự báo anatomy state từ cine-MRI”. Câu hỏi còn có thể kiểm tra là liệu state contour/DVF/phase được định nghĩa chặt có thêm giá trị **sau** history/velocity/periodic/PCA/Kalman, và liệu lợi ích còn tồn tại ở held-out patient/scanner với contour endpoint, recursive rollout và calibrated uncertainty. Nếu bài chỉ dùng sequence-specific PCA rồi so với neural network khác, novelty plausibility thấp.

## 2. Prior art gần để chủ động bác bỏ Q1/Q2/Q3

### 2.1 Bảng evidence contract

| Paper | Observation → state | Transition → future | Horizon / rollout contract | Evaluation / split | Uncertainty, planning, limitation | Claim bị làm yếu |
| --- | --- | --- | --- | --- | --- | --- |
| [Liu, Sawant & Ruan, “Prediction of high-dimensional states subject to respiratory motion: a manifold learning approach,” *Physics in Medicine & Biology* 61:4989–4999 (2016), DOI 10.1088/0031-9155/61/13/4989](https://pmc.ncbi.nlm.nih.gov/articles/PMC4975535/) | 3D photogrammetry point-cloud surfaces → kernel-PCA nonlinear feature state; one patient, 15 Hz | VAR(p=20) trong feature space → future high-dimensional surface qua fixed-point pre-image | Lookahead 200 ms và 600 ms; paper so independent vs multidimensional feature prediction, chưa chứng minh long free-running rollout | 200 surfaces; 100 train/100 test trong cùng một bệnh nhân; pointwise RMSE/variance trên 200×150 grid, Mann–Whitney; irregular-warp simulation không có true future surface | Không có calibrated probability, action hay planning; state là geometric surface, không phải image/clinical state | “Geometry/manifold state chưa có”; Q1 cần patient-independent cine và endpoint mạnh hơn để còn phân biệt |
| [Pham et al., “Predicting real-time 3D deformation field maps … for on-board 4D target tracking,” *Physics in Medicine & Biology* 64:165016 (2019), DOI 10.1088/1361-6560/ab359a](https://pmc.ncbi.nlm.nih.gov/articles/PMC6734921/) | Prior 4D-MRI + on-board 2D cine → 3 PCA respiratory DFM weights; XCAT và một liver-cancer patient | ADMLP-NN dự báo weights → 3D DFM → predicted VC-MRI/tumor | XCAT 120–600 ms; patient 330 ms, dự báo 15 s tracking curve; M-step coefficient prediction, không báo free-running chain | VDC/COMS và PCA NCC/NRMSE; XCAT dùng 5 RPM signals, patient n=1; averaging theo predicted time steps | Không uncertainty calibration, action hay closed-loop beam; prior 4D image có thông tin hình học mạnh | “3D deformation prediction từ 2D cine chưa có”; làm yếu Q1 nếu chỉ thêm PCA-DVF/3D output |
| [Romaguera et al., “Prediction of in-plane organ deformation during free-breathing radiotherapy via discriminative spatial transformer networks,” *Medical Image Analysis* 64:101754 (2020), DOI 10.1016/j.media.2020.101754](https://pubmed.ncbi.nlm.nih.gov/32580056/) | Image sequence → recurrent multi-scale features và dense deformation giữa frame kế tiếp | Extrapolated deformation → cascade spatial transformers → future image sequence | Predict block nhiều frame; exact teacher forcing/free-running semantics và physical horizon không được xác minh từ abstract | 85 cases, healthy + patients, nhiều modality; median vessel-position errors MRI 0.45 (0.55), US 0.45 (0.74), CT 0.28 (0.58) mm trong abstract | Không distribution calibration hay action; unsupervised image/deformation loss | “Future organ deformation/frame prediction là gap”; chỉ còn câu hỏi về state sufficiency, shift và fair prefix contract |
| [Romaguera et al., “Probabilistic 4D predictive model from in-room surrogates …,” *Medical Image Analysis* 74:102250 (2021), DOI 10.1016/j.media.2021.102250](https://pubmed.ncbi.nlm.nih.gov/34601453/) | 2D surrogate images + static pre-operative 3D volume → temporal representation + phase-specific motion distribution | Seq2seq extrapolation + sampled latent → dense organ deformation at multiple future times | Scalable predictive horizon; exact direct/recursive implementation cần đọc full paper, không mặc định open-loop | 25 healthy volunteers + 11 cancer patients; cancer data hold-out; mean error 1.67±1.68 mm MRI, 2.17±0.82 mm US; personalization 1.4±1.1 mm | Samples latent để estimate uncertainty; chưa thấy calibration/coverage endpoint trong abstract; no action/planning | “Medical motion model chưa có multi-future uncertainty” bị bác bỏ |
| [Gunnarsson et al., “Online Learning in Motion Modeling for Intra-interventional Image Sequences,” MICCAI 2024, LNCS pp.706–716, DOI 10.1007/978-3-031-72069-7_66](https://papers.miccai.org/miccai-2024/paper/1838_paper.pdf) | Reference image + sequence → encoder latent `x_t` (8D), LG-SSM state `z_t` (16D), diffeomorphic DVF decoder | Linear Gaussian transition, Kalman forecast/smoothing; online update only LG-SSM parameters | EchoNet giữ H=50 unseen samples; ACDC chỉ sparse reconstruction/interpolation, không phải future forecast | EchoNet 10,023 videos; 9,540 train/483 test; latent log p −10.5→−6.3, RMSE 7.04→5.54, Dice at 25 steps .81→.85 with online adaptation; ACDC 100/50 patients, 35 samples/cycle, ED/ES masks | Gaussian latent gives predictive distribution, nhưng paper ghi mapping latent uncertainty→DVF uncertainty là future work; no policy/planning | “Medical model chưa có probabilistic explicit transition, online adaptation hoặc 50-step forecast” sai. ACDC result không được gọi là forecast |
| [Li et al., “Online prediction for respiratory movement compensation …,” *Radiation Oncology* 18:149 (2023), DOI 10.1186/s13014-023-02341-1](https://pmc.ncbi.nlm.nih.gov/articles/PMC10496354/) | 2D cine-MR tumor/organ trace → patient-specific regression state | Linear/Ridge/L1-L2/RNN → future trace và binary gating crossing time | Direct 0.4/0.6 s; adaptive linear burn-in 30 s, update online | 21 liver + 10 lung patients; MAE/RMSE/R² và crossing/gating error; adaptive linear gating accuracy 98.3% liver/98.0% lung, error 44/45 ms; Wilcoxon | Gating endpoint cụ thể, không predictive distribution; no action causal, no dense anatomy | “Linear/periodic baseline yếu” và “uncertainty/gating mới” đều bị làm yếu |
| [Bukhari & Hong, “Real-time prediction and gating … EKF and GPR,” *Physics in Medicine & Biology* 60:233–252 (2015), DOI 10.1088/0031-9155/60/1/233](https://pubmed.ncbi.nlm.nih.gov/25489980/) | Respiratory trace → local-constant-model EKF state + GP residual | EKF forecast + GPR error correction | Lookahead 192/384/576 ms; sparse GP real time | 304 respiratory traces; patient-wise RMS relative to no prediction 37/39/42% at duty cycle 80% | GPR predictive variance dùng để gate high-error points; reduced duty-cycle trade-off; no anatomy contour | “Uncertainty-aware gating chưa có” sai |
| [Bukhari & Hong, “Real-time prediction and gating … in 3D space … GPR network,” *Physics in Medicine & Biology* 61:1947–1967 (2016), DOI 10.1088/0031-9155/61/5/1947](https://pubmed.ncbi.nlm.nih.gov/26878653/) | 3D respiratory coordinates → EKF theo từng coordinate + GPRN covariance | EKF + multi-output GPRN residual → 3D future position | Lookahead 192/384/576 ms | 304 traces; RMS error 38/40/40% relative no prediction; covariance trace gates high-error periods | Predictive covariance có mục đích gating; no image-derived anatomy, no causal action | “3D probabilistic motion predictor là mới” bị bác bỏ |
| [Jöhl et al., “Performance comparison of prediction filters for respiratory motion tracking in radiotherapy,” *Medical Physics* 47:643–650 (2020), DOI 10.1002/mp.13929](https://www.research-collection.ethz.ch/handle/20.500.11850/441529) | 93 standardized respiratory traces → scalar respiratory state | 18 filters, gồm linear/LMS/wavelet filters | 160 ms và 480 ms trong benchmark; direct signal prediction | 10 traces hyperparameter optimization, 83 evaluation; smooth traces wavelet LMS/linear nRMSE <.05 ở horizon tương ứng; noisy traces làm performance gần nhau | Không anatomy/state semantic; mạnh để kiểm tra baseline và noise robustness | “Deep model tất yếu hơn simple dynamics” không được giả định |
| [Wimmert et al., “Benchmarking machine learning-based real-time respiratory signal predictors in 4D SBRT,” *Medical Physics* 51:3173–3183 (2024), DOI 10.1002/mp.17038](https://doi.org/10.1002/mp.17038) | Noisy external RPM signal → scalar denoised respiratory target | Linear, DLinear, XGBoost, LSTM, full-history Transformer, limited-history Transformer | Direct single-point prediction at 480/680/920 ms; no multi-step pixel rollout | 2,502 signals from 416 patients; patient split 215/84/117; first 20 s online scaling; nRMSE per signal, median/IQR; 70 OOD curves | OOD degradation explicitly measured; no uncertainty/action/anatomy. Official data/code public ([database](https://github.com/IPMI-ICNS-UKE/respiratory-signal-database), [models](https://github.com/IPMI-ICNS-UKE/respiratory-motion-prediction)) | Strong fair baseline for A motion timing; không được dùng để chứng minh anatomy state |
| [Pohl et al., “Real-time respiratory motion forecasting with online learning …,” *Computer Methods and Programs in Biomedicine* 269:108828 (2025), DOI 10.1016/j.cmpb.2025.108828](https://www.sciencedirect.com/science/article/pii/S0169260725002457) | 3 external chest markers, 3D → multivariate marker-position state | Online UORO/SnAp-1/DNI/RTRL/LMS/SVR/linear | Direct horizons h≤2.1 s at 3.33/10/30 Hz; first minute trains and predicts within same sequence | 9 sequences, 73–320 s; SnAp-1 average nRMSE .335 (3.33 Hz), .157 (10 Hz), UORO .086 at 30 Hz; linear .098 at 100 ms 10 Hz; irregular vs regular split | Online adaptation and inference-time comparison; no anatomical shape or calibrated uncertainty; sequence-wise not population generalization | “Online RNN in medical motion chưa có” sai; linear must be included |
| [Shimizu et al., “Non-stationary transformers-based model for predicting liver motion for interleaved two-dimensional cine magnetic resonance imaging,” *Medical Physics* 53:e70241 (2026; first online 2025), DOI 10.1002/mp.70241](https://doi.org/10.1002/mp.70241) | 2D interleaved cine-MR → liver centroid from intensity-based deformable registration | NsTransformer/iTransformer/biLSTM-ATT/LSTM/linear → centroid | Direct 200/400/600 ms | 17 liver cancer patients; RMSE + margin-based accuracy `Pθ`; Friedman/Nemenyi; ~5 ms/prediction; accuracy degrades irregular breathing | No output distribution or planning; exact patient aggregation/context window/split UNKNOWN from accessible publisher text; Elekta-funded chairs disclosed | “Cine-MR centroid prediction chưa có” bị bác bỏ. Full-shape/coverage/shift có thể còn là hypothesis |
| [Jin et al., “Prediction of real-time cine-MR images during MRI-guided radiotherapy of liver cancer using a GAN–ConvLSTM network,” *Medical Physics* 52:3161–3172 (2025), DOI 10.1002/mp.17609](https://doi.org/10.1002/mp.17609) | 5 sagittal cine-MR frames → ConvLSTM/GAN image state | Predict next 5 frames; generator iteratively transforms spatial content | Five-frame block; exact physical cadence and teacher forcing/free-running semantics UNKNOWN | 15 liver-cancer patients, each sequence 300 frames; personalized per-patient models; PSNR/SSIM/VIF/Pearson + manual landmark error 2.42±0.91 and 2.44±0.96 mm at steps 4/5 | Ordinary future-frame generator with a landmark endpoint; no patient-independent split, uncertainty calibration or planning | “Future image generation = world model” cần bác bỏ; hình ảnh + landmark error chưa đủ state/simulator |
| [Chhatkuli et al., “Dynamic Image Prediction Using Principal Component and Multi-Channel Singular Spectral Analysis,” *Open Journal of Medical Imaging* 5:133–142 (2015), DOI 10.4236/ojmi.2015.53017](https://www.scirp.org/pdf/ojmi_2015090914071968.pdf) | CT/fluoroscopy image sequence → PCA/MSSA temporal modes | MSSA predicts next breathing-period image | Exact recursive contract UNKNOWN | One lung-cancer CT sequence + moving phantom; reported cross-correlation >.999 CT, .995 kV phantom | Feasibility only; no uncertainty, patient split or policy | “PCA temporal image forecast is new” bị làm yếu; evidence thấp hơn prior art journal chính |
| [Das, Chandra & Medhi, “Signal-aware deep learning–based respiratory motion prediction for lung tumor management,” *Frontiers in Oncology* 16:1735140 (2026), DOI 10.3389/fonc.2026.1735140](https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2026.1735140/full) | PET/CT-derived HU/time-intensity surrogates → low-dimensional signal + amplitude classes | Dilated CNN + biLSTM + autoencoder → signal reconstruction/classification and 50–500 ms future surrogate | Exact direct/recursive contract UNKNOWN; reports 50–500 ms | Authors report 1,777 patients and ~400k signal segments, 80/20 patient split; article says data cannot be shared; algorithm-level RMSE/MAE/AUC/F1 | **No CI/hypothesis test; no physical marker/fluoroscopy calibration or dosimetry**; authors explicitly defer mm calibration | Strong latest caution: high accuracy on private surrogate data does not establish physical-space or clinical utility |

### 2.2 Điều phải ghi khi đọc các prior art này — VERIFIED

- **Pohl 2026:** direct, horizon-specific; không được báo như recursive rollout.
- **Gunnarsson 2024:** EchoNet có forecast 50 samples; ACDC experiment là sparse reconstruction/interpolation vì sequence quá ngắn. Không gom hai thí nghiệm thành một claim “ACDC long-horizon forecasting”.
- **Liu 2016:** feature-space geometry forecast rất gần ý tưởng “state hình dạng”; nhưng chỉ một bệnh nhân và point-cloud surface, không chứng minh cross-patient cine-MRI.
- **Pham 2019:** 3D DFM rất gần target motion state; prior 4D-MRI và XCAT/liver n=1 làm hạn chế generalization.
- **Romaguera 2021:** latent sampling và multi-time dense deformation đã có; abstract không đủ để suy calibration, recursive rollout hoặc utility ngoài error hình học.
- **Li 2023/Bukhari 2015/2016/Jöhl 2020/Wimmert 2024/Pohl 2025:** simple filters và uncertainty-aware gating là đối chứng bắt buộc; không được đánh giá learned model chỉ với last-value hoặc naive persistence.
- **Jin 2025 và Chhatkuli 2015:** image synthesis/correlation có thể làm output đẹp hoặc sát tín hiệu, nhưng không tự chứng minh predictive state, long-horizon simulator hay action utility.
- **Shimizu 2026:** centroid prediction từ cine-MR đã được báo ở 200/400/600 ms; nếu Q1 giữ centroid làm endpoint chính thì novelty plausibility thấp.
- **Das et al. 2026:** “1,777 patients” và “~400k signals” là số tác giả báo cáo trên dataset riêng không public; bài tự ghi chưa physical-space calibration, CI/hypothesis test và dosimetric validation. Không dùng số này để thay thế benchmark public.

## 3. Baseline fairness và forecast protocol

### 3.1 Baseline ladder — INTERPRETATION / HYPOTHESIS

Một thí nghiệm Family A tối thiểu nên có cùng `H(t)`, cùng target mask/ROI và cùng preprocessing cho các bậc sau:

1. **Persistence / last observation:** `ŝ_{t+Δ}=s_t`; cần để phát hiện gain chỉ do target dễ.
2. **Constant velocity / local polynomial:** fit vị trí, centroid hoặc landmarks trong prefix, query theo `Δt`; báo riêng khi phase/irregularity phá giả định.
3. **Periodic/phase baseline:** phase và period chỉ được suy từ prefix; không dùng future ED/ES, full-cycle extrema hoặc full-clip beat detector tại inference.
4. **Linear AR / adaptive linear / Kalman-EKF:** cùng context window, update schedule và noise model; nếu output distribution thì kiểm tra coverage.
5. **PCA/low-rank + linear/VAR:** basis fit trên prefix/training partition, không fit toàn sequence; target dimension và normalization phải giống learned state.
6. **Geometry/state baseline:** last contour + DVF/velocity, tracked centroid, registration-only; tách performance của tracking khỏi performance của transition.
7. **Learned predictor:** chỉ sau khi các bậc trên được tune trên validation; direct và recursive báo tách.

Thắng một persistence baseline không chứng minh state có ý nghĩa. Thắng linear bằng một model có registration/ROI/normalization nhìn future cũng không chứng minh transition tốt hơn.

### 3.2 Direct, recursive, tracking, reconstruction — VERIFIED distinction

| Protocol | Thông tin tại inference | Ví dụ Family A | Claim được phép |
| --- | --- | --- | --- |
| Direct multi-horizon | Cùng prefix, query từng `Δt` bằng model riêng hoặc head riêng | Pohl 2026, Shimizu abstract, Wimmert | Sai số theo nhiều horizon; chưa chứng minh tự rollout |
| Recursive rollout | Prefix một lần, dùng output/state dự đoán cho bước kế | Cần thiết kế riêng; Pohl 2026 không làm | Drift và stability trong open-loop |
| Filtering/tracking / online adaptation | Có observation thật mới để update hoặc adapt state/transition trong prefix quan sát | Gunnarsson online adaptation trước khi forecast suffix; Li adaptive predictor | Phải tách giai đoạn assimilation khỏi forecast; online update không tự đồng nghĩa với forecast open-loop |
| Reconstruction/interpolation | Encoder/preprocessing hoặc query dùng cả chuỗi | Gunnarsson ACDC sparse reconstruction; ACDC cycle models | Reconstruct/impute trong sequence; không gọi là future forecast |

`H=50 samples` của Gunnarsson EchoNet là forecast; ACDC 5th/10th sample là interpolation/reconstruction. `Pohl h=1…hmax` là direct. `Jin 5→5` tạo một block future nhưng semantics teacher forcing/free-running cần audit code/paper full text. Một “video predictor” chỉ đáng gọi là medical world model khi state/transition/future/purpose được kiểm tra theo contract, không do tên model.

### 3.3 Leakage audit checklist — INTERPRETATION / HYPOTHESIS

- Fit registration, optical-flow parameters, PCA basis, scaler, ROI và phase estimator trên prefix/training only.
- Không đưa future masks, future ED/ES frames, future target contour hoặc future image intensity vào state inference.
- Split theo patient/subject trước windowing; với multi-center data, báo center/scanner-held-out nếu có.
- Nếu mỗi patient có nhiều scan/sequence, không đặt các sequence cùng người ở train và test mà không giải thích.
- Ghi `context window` bằng giây và frame count; không dùng full signal history ở một baseline nhưng chỉ 1 s ở baseline kia nếu mục tiêu là so state.
- Chấm theo patient/sequence trước khi pooling; báo số patient, số sequence và quy tắc weighting. Không để một sequence dài chi phối mean mà không báo median/IQR.
- Với noisy input/denoised target, giữ information contract như Wimmert: target denoised không được đi vào input scaling; đo OOD/irregular breathing riêng.
- Nếu state được cập nhật online, ghi burn-in và update latency; so với offline model không được gọi là cùng một setting.
- Nếu có nhiều samples tương lai, báo cả direct horizon và recursive rollout; SSIM/PSNR chỉ là phụ, target geometry/state là chính.

## 4. Q1 — state giải phẫu có thêm giá trị dự báo không?

### VERIFIED phản chứng

Q1 hiện trong [OPEN_QUESTIONS](../../OPEN_QUESTIONS.md) đã có Pohl, Li và EKF-GP. Audit này bổ sung các phản chứng mạnh hơn:

- Liu đã dự báo **high-dimensional respiratory surfaces** bằng nonlinear manifold state + VAR.
- Pham đã dự báo **3D deformation field maps** và tumor tracking từ 2D cine + prior 4D-MRI.
- Romaguera 2020/2021 đã dự báo dense in-plane/volumetric deformation và multi-time sampled future.
- Shimizu đã dự báo **liver centroid** từ interleaved cine-MR ở 200/400/600 ms.
- Gunnarsson đã học latent LG-SSM cho diffeomorphic 2D motion và forecast 50 EchoNet samples.

Do đó, “predictive anatomical state” hoặc “future frame/centroid” không phải novelty claim an toàn. Pohl 2026 còn cho thấy linear và online RNN cạnh tranh ở các horizon khác nhau trong cùng PCA-DVF representation.

### Hypothesis hẹp có thể còn kiểm tra

**Given** cine prefix với cadence thực, **can** state gồm contour/DVF/phase/velocity có incremental value so với `last geometry + velocity + periodic/linear/Kalman/PCA` **whose transition predicts** centroid **và** boundary/contour displacement ở ít nhất hai physical horizons **for** latency-aware retrospective tracking proxy, với patient/scanner-held-out split?

Điểm phân biệt không phải backbone mà là phép kiểm tra:

1. Fit từng state chỉ trên prefix; giữ transition readout/capacity tương đương.
2. So `history direct` với `state + transition`: nếu state không cải thiện khi history đầy đủ, claim state sufficiency yếu.
3. Chấm centroid, surface distance/HD95, area/volume change và error theo phase; không chỉ frame PSNR.
4. Chấm direct và recursive riêng; report error accumulation.
5. Calibrate interval/quantile theo horizon nếu state có belief.

### Falsifier

Kết quả âm được định trước: state geometry không cải thiện constant-velocity/periodic/Kalman/PCA khi cùng prefix và validation budget; hoặc gain mất khi loại target-informed registration/ROI; hoặc chỉ tồn tại trên within-sequence split mà mất ở held-out patient/scanner. Khi đó nên bỏ claim learned anatomical state cần thiết, không tăng complexity để cứu metric.

### Causal boundary

Cho phép nói “dự báo geometry dưới observed respiratory process” hoặc “proxy cho latency compensation”. Không cho phép nói model nhận diện physiology, thay đổi dose/treatment hay bảo đảm an toàn beam nếu không có action, calibration vật lý và evaluation intervention phù hợp.

## 5. Q2 — uncertainty và endpoint gating

### VERIFIED phản chứng

Bukhari & Hong 2015/2016 đã dùng GPR predictive variance/covariance để dự báo giai đoạn sai số lớn và pause beam; Li 2023 đã đo crossing error, gating error và duty-cycle-relevant gating accuracy; Gunnarsson 2024 có probabilistic LG-SSM nhưng chính bài ghi mapping latent uncertainty sang DVF uncertainty là công việc còn lại. Romaguera 2021 sampling latent để tạo nhiều future motion fields. Vì vậy claim “uncertainty-aware medical motion model đầu tiên” không đứng được.

### Hypothesis hẹp có thể còn kiểm tra

**Given** cine history và target geometry hiện có, **can** state/belief dự báo phân phối boundary error tại 0.5/1/2 s với calibrated coverage/sharpness tốt hơn EKF-GP hoặc residual-quantile baseline **for** retrospective gating-like risk ranking dưới center/irregular-motion shift?

Đây là câu hỏi về **calibration và decision ranking**, không phải thêm một uncertainty head. Cần tách:

- aleatoric image/registration uncertainty;
- epistemic/model uncertainty qua patient/scanner shift;
- label/contour disagreement;
- physical target error và gating error.

Endpoint nên gồm coverage của prediction interval, interval width, weighted interval score/CRPS hoặc proper score phù hợp, calibration-by-horizon và error-vs-duty-cycle curve. Bukhari/Li là baseline lịch sử để tránh claim quá rộng.

### Falsifier và giới hạn

Falsifier là calibrated model không vượt simple EKF-GP/quantile ở cùng empirical coverage/duty-cycle, hoặc coverage thất bại trên irregular/OOD dù RMSE tốt. Không có beam-delivery logs thì chỉ được gọi là retrospective gating proxy; không claim reduced toxicity, dose escalation hay safe clinical gating.

## 6. Q3 — cardiac prefix chứa gì ngoài phase tuần hoàn?

### VERIFIED phản chứng

- Gunnarsson 2024 dùng EchoNet để forecast 50 latent samples ahead và đánh giá LV Dice 25 steps ahead; tuy vậy EchoNet labels chính thức chỉ trace LV tại ED/ES, không phải dense expert masks mọi frame.
- Jin 2025 dùng 5 cine-MR frames để dự báo 5 frame tiếp theo, nhưng train model riêng từng patient trong 15 bệnh nhân; đây là ordinary future image generation kèm landmark endpoint, không phải evidence của patient-independent world state.
- ACDC có 28–40 frames cho một gated cardiac cycle, ED/ES instants và labels sparse; không cung cấp repeated natural multi-beat trajectory trên official page.
- Shimizu 2026 làm liver rather than cardiac, nhưng cho thấy centroid cine-MR prediction đã có strong linear/LSTM/transformer benchmark và irregular-breathing stress test.

Vì vậy “cardiac future-frame predictor” hoặc “phase-aware model” không đủ mới. Q3 chỉ có thể còn rõ nếu information contract dùng prefix thực sự, subject-disjoint, future labels dense/usable và endpoint shape/area thay vì reconstruction của cycle đã biết.

### Hypothesis hẹp có thể còn kiểm tra

**Given** cardiac cine prefix với rate và elapsed time quan sát được, **can** state `shape + phase + phase velocity` predict future contour/area tại `% cycle` được định nghĩa từ prefix tốt hơn last-shape, periodic/Fourier, PCA-phase và Kalman **for** acquisition-latency proxy, while preserving subject-disjoint evaluation?

Không được định phase bằng future ED/ES labels; `% cycle` phải suy từ prefix hoặc dùng physical timestamps. Nếu cadence/beat coverage không đủ, Q3 phải đổi trước khi chọn topic.

### Falsifier

Nếu last-shape + phase/periodic hoặc PCA-phase đạt tương đương, hoặc dense future contour không đáng tin vì labels chỉ ED/ES, Q3 không đủ dữ liệu cho một world-model claim. Một model dự báo frame đẹp nhưng không cải thiện area/contour/phase error là negative result hợp lệ.

## 7. Dataset feasibility — public metadata only

Không tải patient images, không xin DUA thay researcher và không coi repository code license là data license.
Aggregate statements, source snapshot dates và SHA256 ở [metadata provenance](../../research_artifacts/2026-09-12_metadata_audit.json). Đây là page-level transcription, không phải đếm patient files; root đã kiểm tra hash các trang tải về, chưa audit ảnh/nhãn.

### 7.1 TrackRAD2025 — có cine nhưng continuity/future-label contract chưa đóng

**VERIFIED.** [Official HF card](https://huggingface.co/datasets/LMUK-RADONC-PHYS-RES/TrackRAD2025) báo 477 unlabeled patients, hơn 2.8M sagittal cine-MRI frames, 108 labeled patients và hơn 10k labeled frames (+8000 multi-observer); CC BY-NC 4.0. Data structure có `frame-rate.json`, scanner field-strength, scanned-region, `.mha` images và target masks. Card báo 0.35 T/1.5 T, sáu trung tâm, 2D+t sagittal cine; training gồm 477 unlabeled + 50 labeled; update January 2026 nói preliminary/final test đã mở trừ cohort D vì privacy, trong khi đoạn mô tả challenge cũ vẫn nói 58 test không cung cấp. Đây là conflict phải giữ nguyên và re-check khi nhóm thật sự có access.

**VERIFIED:** Card ghi 1.5 T cine có thể có temporal jumps/contrast changes do treatment interruptions được gộp trong một scan; labeled frames được chọn để tránh jumps. 0.35 T data có gantry-related degradation; labeled frames được chọn để tránh vùng đó. Breath-holds và free breathing cùng xuất hiện. Pixel spacing sau preprocessing được resample 1×1 mm², nhưng slice thickness và native frame rate khác center/field strength.

**UNKNOWN:** absolute timestamps, drop-frame/jitter map, complete sequence count per patient, continuous valid-run lengths, dense future target masks tại mọi horizon, treatment event timing, commanded action, probe/scanner pose và force/contact. Vì vậy TrackRAD là ứng viên cần audit cho A, chưa phải bằng chứng rằng public release hỗ trợ multi-step forecast.

**INTERPRETATION / HYPOTHESIS:** challenge tracking có thể đọc frame hiện tại và label sparse; forecasting phải giữ target future ngoài prefix. Trước khi dùng phải lập manifest per patient/scan, kiểm tra jumps, frame-rate, target density và patient/center split; không nối các đoạn bị treatment interruption thành một trajectory.

### 7.2 EchoNet-Dynamic — cardiac clips và sparse tracings, không phải longitudinal trajectory

**VERIFIED.** [Official dataset page](https://echonet.github.io/dynamic/) báo 10,030 apical-4-chamber echocardiogram videos từ unique individuals tại Stanford, downsampled 112×112; có EF/EDV/ESV và LV tracing tại hai time points ED/ES. [Stanford AIMI](https://aimi.stanford.edu/datasets/echonet-dynamic-cardiac-ultrasound) xác nhận over 10k videos từ unique patients và RUA; official page yêu cầu personal, non-commercial research, không được redistribute và cấm dùng cho diagnosis/patient care. Code/repository [EchoNet-Dynamic](https://github.com/echonet/dynamic) là MIT, nhưng điều đó không thay data agreement.

**VERIFIED:** Public page không cung cấp trong phần metadata đã đọc cadence chính xác từng AVI, absolute timestamps, repeated visits hoặc probe pose. Gunnarsson 2024 báo count khác là 10,023 unique videos (9,540 train/483 test) trong experiment của họ. Đây là version/report discrepancy cần giữ lại, không làm tròn thành một số “chắc chắn”.

**UNKNOWN:** dense contour từng frame ở public labels, true frame timestamps, uninterrupted multi-beat length, longitudinal visits, probe motion/force và treatment. Do đó EchoNet phù hợp để audit intraclip cardiac motion hoặc làm control, nhưng không tự hỗ trợ disease progression, action-conditioned acquisition hay patient-level longitudinal state.

### 7.3 ACDC — cycle-resolved cardiac MRI nhưng không phải natural multi-beat

**VERIFIED.** [Official ACDC database](https://www.creatis.insa-lyon.fr/Challenge/acdc/databases.html) có 150 exams từ 150 bệnh nhân khác nhau, publicly downloadable; acquired at 1.5 T/3.0 T, breath-hold retrospective/prospective gating, short-axis SSFP. Mỗi exam có 28–40 images bao phủ hoàn toàn hoặc gần toàn bộ cardiac cycle; official page cung cấp diastolic/systolic phase instants và ED/ES ground truth. Có trường hợp prospective gating bỏ 5–10% cuối cycle.

**UNKNOWN:** exact per-frame timestamps/cadence trước header audit, repeated natural cycles, dense segmentation mỗi frame, action/pose/treatment. **INTERPRETATION / HYPOTHESIS:** dùng ACDC để cycle shape/reconstruction hoặc negative control; không lặp vòng một cycle để tạo long-horizon future giả.

<a id="respiratory-signals"></a>

### 7.4 Public continuous respiratory signals — baseline timing, không phải anatomy

**VERIFIED.** [Wimmert respiratory database](https://github.com/IPMI-ICNS-UKE/respiratory-signal-database) repository mô tả 2,510 univariate signals từ 419 patients, >325,000 s, với 4DCT/CBCT/dose-delivery, Varian RPM và 25 Hz preprocessing; patient split 1,262/514/726 signals tương ứng 215/84/117 patients cho **2,502 signals/416 patients** sau khi loại 8 corrupted signals của 3 patients. [Prediction code](https://github.com/IPMI-ICNS-UKE/respiratory-motion-prediction) và data link được cung cấp công khai trên repository; database README ghi open access/anonymized ethics approval và MIT repository license.

Wimmert là benchmark có continuity/time axis và OOD protocol tốt cho scalar breathing signal, nhưng không có anatomy image, contour, pose/action hay treatment effect. Không được dùng nó để claim medical visual state; dùng nó để kiểm tra baseline, scaling, horizon và OOD fairness.

### 7.5 Pohl ETH/OvGU public examples — feasibility có điều kiện

**VERIFIED.** Official [Pohl repository](https://github.com/pohl-michel/2D-MR-image-prediction) includes preprocessed cine-MRI examples/pipeline. Paper mô tả 4 ETH sagittal sequences (200 frames, ~63 s, ~3.18 Hz) và 8 OvGU sequences (498 frames sau discard, ~83 s, 6 Hz). Đây là public data đủ để kiểm tra direct short-term geometric forecast và code path, nhưng quá ít sequence cho claim population-level clinical generalization.

## 8. Những claim hiện phải hạ cấp

| Claim dự định | Trạng thái sau audit |
| --- | --- |
| “Medical chưa có world model có state hình học” | **Bị bác bỏ** bởi Liu, Pham, Romaguera, Pohl, Gunnarsson |
| “Medical chưa có multi-step future motion” | **Bị bác bỏ**, nhưng nhiều paper dùng direct block, filtering hoặc reconstruction; cần phân loại contract |
| “Uncertainty-aware motion gating là mới” | **Bị bác bỏ** bởi EKF-GP/GPRN, Li và Romaguera sampling |
| “Centroid cine-MR prediction là novelty” | **Bị bác bỏ** bởi Li, Lombardo, Pohl, Shimizu |
| “Future-frame image quality chứng minh useful simulator” | **Không được hỗ trợ**; Jin/Chhatkuli có image/landmark endpoints nhưng không planning/closed-loop |
| “Learned model beats simple baseline” | **Chưa được phép** nếu chưa dùng patient split, same prefix, noise/OOD và direct-vs-recursive protocol; Li/Wimmert/Jöhl/Pohl là phản chứng mạnh |
| “Predicted motion improves treatment” | **Không được phép** nếu chỉ có observational forecast; cần physical calibration, gating/beam logs hoặc study design phù hợp |

## 9. Câu hỏi unresolved còn đáng giữ — INTERPRETATION / HYPOTHESIS

1. **Incremental state value:** sau khi có đủ last geometry, velocity, phase và history, state contour/DVF học được còn giảm future boundary error đáng kể trên held-out patients/scanners không?
2. **Recursive versus direct:** một state inference duy nhất có giữ được contour/geometry accuracy khi rollout 0.5–2 s recursive, hay direct horizon models chỉ che error accumulation?
3. **Calibration under irregular motion:** state/belief có dự báo được tail boundary error và ranking risk dưới breath-hold, amplitude shift, temporal jumps hoặc scanner shift tốt hơn EKF-GP/quantile không?
4. **Label/geometry sufficiency:** với public cine data chỉ có sparse labels, endpoint nào có thể chấm future state mà không dùng target-informed preprocessing hoặc full-clip segmentation?
5. **Task utility without causal overreach:** geometry forecast có cải thiện một retrospective tracking/gating proxy với duty-cycle constraint hay chỉ làm giảm pixel error; kết quả này không được gọi là treatment effect.

Không câu nào được chọn làm topic. Mỗi câu phải bị bác bỏ nếu baseline simple đạt tương đương hoặc dữ liệu không đóng được prefix/future contract.

## 10. Search log và mức đọc

### Truy vấn đã dùng

- `"world model" medical motion forecasting`, `"medical imaging" world model`, `"latent dynamics" respiratory motion`, `"cine MRI" future frame prediction`, `"anatomical deformation" forecasting`.
- `"PCA" respiratory motion prediction`, `"3D deformation field" cine MRI prediction`, `"manifold learning" high-dimensional respiratory state`, `"probabilistic 4D predictive model" radiotherapy`.
- `"online prediction" MRI-guided radiotherapy linear regression`, `"EKF" "Gaussian process" respiratory gating`, `"non-stationary transformers" liver motion cine MRI`, `"GAN ConvLSTM" cine-MR future images`.
- Forward/backward checks từ Pohl 2026 references, Gunnarsson 2024 related work, Shimizu 2026 references và Romaguera 2021 citations; DOI/title/author metadata kiểm tra thêm qua Crossref/PubMed khi publisher page bị giới hạn.

### Actual source depth

- **Full PDF/methods/evaluation:** Pohl 2026, Gunnarsson 2024, Liu 2016 (BioC full text), Pham 2019 (BioC full text), Li 2023 (PMC full text), Wimmert 2024 HTML, Frontiers 2026 HTML.
- **Official abstract + metadata, methods detail bounded:** Romaguera 2020, Romaguera 2021, Shimizu 2026, Jin 2025, Bukhari 2015/2016, Jöhl 2020.
- **Official project/repository audit:** Pohl, Wimmert prediction/database, TrackRAD2025, EchoNet-Dynamic.
- **Không tải patient images hoặc dataset cần DUA.** Chưa xác nhận executable reproduction của bất kỳ paper nào trong repo này.

## 11. Missing information trước khi chọn đề tài

1. TrackRAD release thực tế nhóm có thể tải: test cohort nào, cohort D exclusion, frame-rate/jump manifest, số future masks liên tiếp và scanner/center split.
2. Với EchoNet/ACDC: cadence thật, dense contour availability, prefix-only label protocol và số clip đủ ≥2 future horizons.
3. Exact endpoint: centroid, contour, DVF, area/volume, phase hoặc calibrated interval; chưa thể chọn khi endpoint chưa gắn với dataset public.
4. Có chấp nhận data-use agreement/non-commercial restrictions của EchoNet hay không; không suy access từ code license.
5. Có dữ liệu độc lập để đánh giá OOD/irregular breathing và patient/scanner split hay không; không dùng within-sequence metrics làm generalization.
6. Nếu muốn clinical-sounding gating claim: có physical-space calibration, acquisition latency và retrospective treatment/gating log được phép dùng không? Hiện dossier giả định là **UNKNOWN/không có**.

## 12. Kết luận audit — INTERPRETATION / HYPOTHESIS

Family A vẫn có giá trị nghiên cứu vì nó cho phép endpoint geometry và time scale rõ hơn C, nhưng novelty không nằm ở việc gọi một predictor là world model. Sau audit, hướng A chỉ có thể bảo vệ khi bài làm rõ state type, prefix-only inference, strong simple baselines, patient/scanner split, direct-vs-recursive rollout, uncertainty calibration và downstream proxy đã định trước. Dataset feasibility của TrackRAD/EchoNet/ACDC chưa đủ để chọn Q1/Q2/Q3 hôm nay. Giữ cả ba câu hỏi mở và tiếp tục audit metadata/endpoint trước khi quyết định.
