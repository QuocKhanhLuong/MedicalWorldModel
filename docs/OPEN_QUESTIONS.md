# Câu hỏi nghiên cứu còn mở — chưa chọn topic

Ngày **2026-09-12**. **Toàn bộ câu hỏi, horizon đề xuất, ranking, novelty plausibility và ước lượng scope bên dưới là INTERPRETATION / HYPOTHESIS.** Chưa có thí nghiệm, xác nhận access hoặc quyết định chọn A/B/C. VERIFIED prior art nằm trong các liên kết và [matrix](PAPER_MATRIX.md); feasibility có giới hạn ở [dataset audit](DATASET_FEASIBILITY.md).

## Tám câu hỏi có thể bị bác bỏ

Mỗi câu hỏi giữ cấu trúc: Given observations → infer state → transition predicts future quantity over horizon → versus strong simple baseline → for a stated use case. Các horizon là thiết kế đề xuất, **không phải đặc tính dataset đã được xác minh**. Nếu cadence/visit coverage không phù hợp, sửa question trước khi thí nghiệm.

### Q1 — A: state giải phẫu có thêm giá trị dự báo motion?

**Câu hỏi.** Với một prefix cine-MRI cùng thời gian frame khả dụng, liệu mô hình có suy được state gồm contour/deformation, vị trí và vận tốc, mà transition dự báo centroid và boundary target sau **0.5/1/2 s** tốt hơn **constant velocity, periodic model và PCA+linear/Kalman với cùng prefix**, để **đánh giá bù latency trong target motion management**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Kiểm tra anatomy có thông tin motion ngoài coordinate history hay không; endpoint geometry có thể gắn latency |
| Prior art mạnh | [Pohl PCA forecast](https://arxiv.org/abs/2410.05882v3), [Li linear gating](https://doi.org/10.1186/s13014-023-02341-1), [EKF+GP](https://pubmed.ncbi.nlm.nih.gov/25489980/) |
| Novelty khả dĩ | Thấp nếu chỉ future-frame predictor; có thể ở phép kiểm chứng incremental state value dưới drift/shift. Chưa xác lập mới |
| Dữ liệu cần | TrackRAD hoặc cine continuous khác, cadence thật, ≥2 future targets có nhãn, patient/scanner split và contour reliability |
| Thí nghiệm tối thiểu | Cùng split/prefix, đo centroid mm và surface distance theo horizon; so geometry-only, history-direct và proposed predictive-state condition; patient-level confidence intervals |
| Falsification | State không cải thiện ngoài motion baseline trong uncertainty của đánh giá; hoặc gain mất khi matched preprocessing/history. Khi đó bỏ claim cần learned anatomical state |
| Rủi ro khoa học | Periodic/linear dynamics đã đủ; 2D không quan sát chuyển động ngoài mặt phẳng |
| Rủi ro dữ liệu | Sparse masks hoặc irregularly sampled frames không hỗ trợ targets đúng horizon |
| Causal allowed/not allowed | Cho phép claim predictive latency-compensation accuracy; không claim physiology identification, patient outcome hoặc safe beam control |
| Scope MICCAI ước lượng | Vừa nếu có multi-center held-out evaluation, strong baselines và state analysis; chỉ PSNR gain là scope yếu |

### Q2 — A: uncertainty có giúp chọn khoảng motion đáng tin?

**Câu hỏi.** Với cine history và target geometry đã quan sát, liệu mô hình có suy một **belief về vị trí/biến dạng**, mà transition dự báo **phân bố future boundary error ở 0.5/1/2 s** tốt hơn **Kalman/GP và residual-quantile calibrated simple predictor**, để **ước lượng trade-off giữa bỏ qua thời điểm không tin cậy và giữ thời lượng sử dụng được trong retrospective gating proxy**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Sai số trung bình thấp có thể che tail errors tại motion bất thường |
| Prior art mạnh | [Bukhari–Hong uncertainty-related gating](https://pubmed.ncbi.nlm.nih.gov/25489980/), [Li gating control](https://doi.org/10.1186/s13014-023-02341-1), [Pohl](https://arxiv.org/abs/2410.05882) |
| Novelty khả dĩ | Không mới ở “uncertainty + gating”; câu hỏi hẹp là calibration/coverage dưới shift với matched duty-cycle và geometry |
| Dữ liệu cần | Như Q1, thêm sufficient abnormal-motion episodes và label-error estimate; không giả định có beam delivery logs |
| Thí nghiệm tối thiểu | Fit calibration chỉ ở validation; coverage/sharpness và miss-risk–duty-cycle curves theo horizon/center; threshold do endpoint định trước |
| Falsification | Confidence không dự báo residual ngoài simple model hoặc advantage biến mất ở cùng empirical coverage/duty cycle |
| Rủi ro khoa học | Confidence chỉ đo segmentation quality; distribution shift phá calibration |
| Rủi ro dữ liệu | Tail events ít, masks không đủ dày để chấm missed motion; không có deliverable clinical threshold |
| Causal allowed/not allowed | Đánh giá forecast reliability và proxy utility; không nói giảm toxicity hoặc bảo đảm safe gating |
| Scope MICCAI ước lượng | Vừa nhưng cần đóng góp đánh giá rõ; dễ quá gần Q1 hoặc prior art nếu chỉ thêm uncertainty head |

### Q3 — A: cardiac prefix chứa gì ngoài phase tuần hoàn?

**Câu hỏi.** Với **chỉ đoạn đầu của một cardiac cine clip**, liệu mô hình có suy state **shape + phase + phase velocity**, mà transition dự báo **contour/diện tích buồng tim sau 10/20/30% một chu kỳ danh định xác định từ quá khứ** tốt hơn **last shape, periodic/Fourier và PCA phase model**, để **đánh giá dự báo motion trong acquisition latency**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Phân biệt reconstruction một chu kỳ với forecasting từ partial observation |
| Prior art mạnh | [Cardiac latent ODE](https://arxiv.org/html/2606.26718), [CardioSynth](https://papers.miccai.org/miccai-2025/0004-Paper2701.html), respiratory PCA là baseline transferable |
| Novelty khả dĩ | Protocol distinction có ý nghĩa nhưng không đủ tự thành method novelty; broad cardiac dynamics không mới |
| Dữ liệu cần | Continuous beat clips, prefix-defined rate, dense contours ở future frames. EchoNet là nguồn để audit; ACDC chỉ làm cycle/reconstruction control |
| Thí nghiệm tối thiểu | Define period từ observed history, không true end-cycle; held-out subjects; contour error/change error, stratify phase và irregular motion |
| Falsification | Periodic baseline ngang bằng; gains chỉ tồn tại khi dùng true future ED/ES để căn phase |
| Rủi ro khoa học | Task quá dễ/chu kỳ quá đều; morphology inference bị lẫn global phase fitting |
| Rủi ro dữ liệu | ED/ES sparse labels không chấm được các horizon; reconstructed cycles không phản ánh natural beat variation |
| Causal allowed/not allowed | Chỉ predictive motion; không suy cardiac function benefit hoặc bệnh lý từ latent |
| Scope MICCAI ước lượng | Nhỏ–vừa và rủi ro cao nếu thiếu dense annotations; cần clinical motion endpoint độc lập |

### Q4 — B: memory về anatomy đã thấy có dự báo được view mới?

**Câu hỏi.** Với **past US images cùng calibrated measured poses**, liệu mô hình có suy state **partial anatomy/coverage và predictive memory**, mà transition dự báo **landmarks hoặc target-view features ở query poses cách 5/10 frames (0.25/0.5 s tại 20 fps)** tốt hơn **nearest observed view, prefix-only volume reformat và current-image-plus-pose predictor**, để **đánh giá pose-conditioned view anticipation phục vụ acquisition guidance về sau**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Kiểm tra memory khi một view không đủ mô tả vùng anatomy, giữ endpoint có thể đo |
| Prior art mạnh | [Hu 2017](https://arxiv.org/abs/1707.05392), [EchoWorld](https://arxiv.org/html/2504.13065), [Fan](https://arxiv.org/html/2607.21918v2); TUS-REC reconstruction là comparator gần |
| Novelty khả dĩ | Không mới ở pose conditioning; có thể ở state/coverage sufficiency và geometry-aware evaluation. Chưa xác lập |
| Dữ liệu cần | TUS-REC2024 access; calibrated transform/time; landmark/feature target đáng tin; continuity và spatial coverage. Không cần giả định command/force |
| Thí nghiệm tối thiểu | Subject-disjoint split; past-only state; query pose được cấp rõ như điều kiện đánh giá; chấm landmarks/features và consistency theo seen/unseen coverage, cùng pose distance |
| Falsification | Gains mất sau khi match coverage và pose-distance, hoặc nearest-view/reformat bằng mô hình; memory ablation không ảnh hưởng |
| Rủi ro khoa học | Appearance và contact deformation không tách được; encoder distance thưởng shortcut; unseen anatomy không định danh từ history |
| Rủi ro dữ liệu | Calibration/contact/landmark quality; thiếu goal-plane labels; dataset reconstruction không có interactive trials |
| Causal allowed/not allowed | Cho phép conditional prediction theo measured/query pose; không claim command effects, contact simulator hoặc closed-loop planning |
| Scope MICCAI ước lượng | Vừa nếu có meaningful state/geometry tests; planning paper vượt scope dữ liệu hiện xác minh |

### Q5 — C: glioma state có dự báo được hai lần follow-up?

**Câu hỏi.** Với **hai MRI visits quá khứ, elapsed-time intervals được công bố và lesion measurements được audit**, liệu mô hình có suy state **spatial burden + patient-specific change rate/belief**, mà transition dự báo **lesion volume và change regions ở hai visits tương lai trong các cửa sổ đến 90/180 ngày đã định trước** tốt hơn **last mask, linear burden trend, deformation persistence và direct time-conditioned predictor**, để **đánh giá khả năng anticipate longitudinal lesion burden dưới observed care**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Kiểm tra future state thực, không chỉ tổng hợp ảnh plausible tại một visit |
| Prior art mạnh | [Petersen](https://arxiv.org/html/2106.12917), [ImageFlowNet](https://arxiv.org/html/2406.14794), [TaDiff](https://arxiv.org/html/2309.05406), [Pash](https://arxiv.org/html/2505.08927) |
| Novelty khả dĩ | Thấp ở generation/dynamics; có thể ở verified prefix, label robustness, multi-visit state/calibration evaluation trên release cụ thể |
| Dữ liệu cần | LUMIERE hoặc release có ≥4 usable visits/patient; timestamp uncertainty; expert-audited mask subset; documented care discontinuities nếu có. LUMIERE công bố relative weeks, không exact days ([D06](DATASET_FEASIBILITY.md#d06)) |
| Thí nghiệm tối thiểu | Đếm cohort trước; query theo reported intervals, chỉ gán window theo quy tắc có xét rounding đã định trước; fixed-prefix two-future evaluation; volume/change metrics, unconditional probability score và sensitivity theo time uncertainty |
| Falsification | Improvement mất với reliable masks/prefix-only registration; linear trend ngang bằng; model không vượt no-change tại lần future thứ hai |
| Rủi ro khoa học | Imaging phenotype không phải viable tumor biology; progression/regression và acquisition artifacts bị lẫn |
| Rủi ro dữ liệu | Không đủ 4-visit trajectories; dropout, treatment metadata thiếu; automask errors |
| Causal allowed/not allowed | Forecast under observed care; không treatment effect, untreated natural history hoặc protocol recommendation |
| Scope MICCAI ước lượng | Vừa–lớn; chỉ khả thi khi manifest và label audit qua gate. Không “bù” thiếu data bằng generating target |

### Q6 — C: state riêng bệnh nhân có hơn regional trend?

**Câu hỏi.** Với **hai T1-MRI quá khứ và actual dates**, liệu mô hình có suy state **regional anatomy và individual rate of change**, mà transition dự báo **regional volume change tại 12/24 tháng** tốt hơn **last measurement, individual linear trend, population mixed-effects model và auxiliary-volume predictor của BrLP**, để **đánh giá mô tả trajectory giải phẫu ở từng bệnh nhân**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Chấm đại lượng thay đổi khó hơn tái tạo anatomy gần như giữ nguyên |
| Prior art mạnh | [BrLP](https://arxiv.org/html/2502.08560), [Δ-LFM](https://arxiv.org/html/2512.09185), [Lachinov](https://arxiv.org/html/2211.04234), [SPIE assessment](https://pmc.ncbi.nlm.nih.gov/articles/PMC12726967/) |
| Novelty khả dĩ | Rất hạn chế nếu chỉ patient-specific generation; có thể ở history sufficiency/uncertainty và reuse state trên endpoints chưa fit |
| Dữ liệu cần | Approved ADNI/OASIS-3 snapshot; ≥2 past + suitable future visits, actual dates, segmentation error estimates; không future-informed templates |
| Thí nghiệm tối thiểu | Matched history; Δvolume MAE/bias/calibration theo region và horizon; held-out patient/site; second readout dùng state cố định như reuse test |
| Falsification | Regional trend bằng hoặc tốt hơn; downstream reuse chỉ tốt do age/diagnosis shortcut; gains mất sau independent segmentation |
| Rủi ro khoa học | Change nhỏ hơn measurement error; latent trajectory phản ánh population age hơn patient dynamics |
| Rủi ro dữ liệu | Permission/visit completeness; scanner/protocol changes; longitudinal preprocessing leakage |
| Causal allowed/not allowed | Predictive anatomical change; không biomarker validation, dementia diagnosis/treatment benefit từ latent |
| Scope MICCAI ước lượng | Vừa nhưng cạnh tranh prior art rất mạnh; cần result phân biệt rõ, không chỉ đổi generator |

### Q7 — C: uncertainty về lesion birth/growth trong MS

**Câu hỏi.** Với **hai MRI visits quá khứ cùng lesion labels/time**, liệu mô hình có suy state **lesion burden và belief về xuất hiện/tăng/giảm tổn thương**, mà transition dự báo **new-lesion count/location và volume ở một/hai annual follow-ups thực đo** tốt hơn **last-mask, linear burden và simple stochastic lesion-change baseline**, để **đánh giá độ tin cậy của dự báo imaging activity dưới observed care**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Multi-hypothesis chỉ có ích nếu chấm đúng occurrence/spatial burden, không chỉ thêm image diversity |
| Prior art mạnh | [ImageFlowNet MS](https://arxiv.org/html/2406.14794), [continuous glioma stochastic state](https://arxiv.org/html/2106.12917), [MS neural SDE](https://arxiv.org/html/2406.12807) dự báo clinical EDSS từ MRI/RCT inputs |
| Novelty khả dĩ | Bất định; disease-specific event evaluation có thể có giá trị nhưng broad stochastic medical prediction không mới |
| Dữ liệu cần | Nhiều labeled MS trajectories đủ depth và actual dates. ISBI2015 chỉ là pilot hiện biết; không giả định private cohort |
| Thí nghiệm tối thiểu | Trước hết inter-rater event consistency và protocol pilot; chỉ thử population comparison nếu có cohort đủ độc lập |
| Falsification | Event labels không ổn định giữa raters; probabilistic model không hơn persistence/stochastic baseline; không đủ two-future ground truth |
| Rủi ro khoa học | Lesion matching/resolution và rater noise chi phối model signal |
| Rủi ro dữ liệu | 5 labeled train subjects ở ISBI; test masks withheld; thiếu depth/treatment history |
| Causal allowed/not allowed | Forecast imaging events under care; không DMT efficacy hay causal clinical course |
| Scope MICCAI ước lượng | Chưa đủ data basis cho standalone paper; pilot nhỏ trước, không cam kết full study |

### Q8 — C: spatial response có ích ngoài functional tumor volume trend?

**Câu hỏi.** Với **pretreatment và early-treatment breast MRI visits, actual times và treatment information thực có trước cutoff**, liệu mô hình có suy state **regional lesion response + burden trend**, mà transition dự báo **FTV/lesion change tại mid- và end-treatment imaging landmarks** tốt hơn **FTV slope, mixed-effects và direct clinical/imaging predictor**, để **đánh giá response anticipation dưới phác đồ chăm sóc quan sát được**?

| Thành phần | Giả thuyết / điều kiện |
| --- | --- |
| Vì sao đáng quan tâm | Câu hỏi trực tiếp về state-level response tại nhiều mốc, không chỉ end-point classifier |
| Prior art mạnh | [Stowers biology+MRI response](https://pubs.rsna.org/doi/pdf/10.1148/ryai.240124), [MeWM](https://openaccess.thecvf.com/content/ICCV2025/html/Yang_Medical_World_Model_ICCV_2025_paper.html), [TaDiff](https://arxiv.org/html/2309.05406) |
| Novelty khả dĩ | Thấp ở treatment-associated simulation; cần kiểm tra spatial-state incremental value, public-data reproducibility và calibration chứ không “first biologic WM” |
| Dữ liệu cần | I-SPY2 access/manifest; ≥4 valid landmarks; matched modalities/FTV labels; actual intervals, arm/treatment timing; đủ overlap giữa groups |
| Thí nghiệm tối thiểu | Kiểm tra visit completeness trước; fixed-prefix future FTV/change score; test spatial input vs scalar trend dưới cùng covariates; explicit missingness analysis |
| Falsification | FTV slope dự báo tương đương; apparent gain do tương lai biết trước arm/response hoặc cohort selection; không có stable spatial targets |
| Rủi ro khoa học | Contrast enhancement/burden không đồng nhất viable cellularity; selection/assignment và response confounding |
| Rủi ro dữ liệu | Modality availability khác cohorts, sparse phases, labels/actual treatment dates thiếu |
| Causal allowed/not allowed | Conditional forecast dưới observed care; không individual treatment effect hoặc chọn phác đồ dù nguồn có trial origin |
| Scope MICCAI ước lượng | Lớn hơn nền CV hiện tại; cần breast imaging collaborator và longitudinal/clinical statistical expertise |

## Ranking để ưu tiên kiểm tra — INTERPRETATION / HYPOTHESIS

Thang **1–5**: 5 thuận lợi hơn cho clarity, novelty plausibility, data feasibility, evaluation, clinical relevance và CV fit; riêng **risk: 5 là rủi ro cao**. Data score phản ánh nguồn mô tả, không confirmed access. Clinical relevance là nhận định về khả năng nối endpoint, không clinical validation. Không cộng điểm thành một objective giả tạo; thứ tự là phán đoán ưu tiên điều tra, không quyết định paper topic.

| Ưu tiên audit | Q | Scientific clarity | Novelty plausibility | Data feasibility | Evaluation quality | Clinical relevance | Risk ↑ | CV fit |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Q1 A motion state | 5 | 2 | 4 | 5 | 4 | 3 | 5 |
| 2 | Q4 B acquisition memory | 5 | 3 | 3 | 4 | 3 | 3 | 5 |
| 3 | Q6 C anatomy trend | 4 | 2 | 3 | 4 | 3 | 3 | 4 |
| 4 | Q2 A calibrated motion | 4 | 2 | 3 | 5 | 4 | 4 | 4 |
| 5 | Q5 C glioma state | 4 | 3 | 2 | 4 | 4 | 5 | 3 |
| 6 | Q8 C breast response | 4 | 2 | 2 | 4 | 4 | 5 | 3 |
| 7 | Q3 A cardiac prefix | 4 | 2 | 2 | 3 | 3 | 4 | 4 |
| 8 | Q7 C MS events | 4 | 2 | 1 | 3 | 4 | 5 | 3 |

Điểm novelty thấp là chủ ý sau adversarial search; không có claim mới nào đã được xác nhận. Nếu dense labels Q1 không tồn tại ở public release hoặc TUS access không phù hợp, feasibility/ranking phải đổi. Không duy trì thứ hạng vì đã viết vào docs.

## Bốn câu hỏi mạnh nhất chưa giải quyết

1. **Q1:** với thông tin bằng nhau, anatomical predictive state có thêm giá trị ngoài motion history đơn giản?
2. **Q4:** memory về phần anatomy đã thấy có ích ngoài pose và spatial coverage, và có biết khi query không đủ support?
3. **Q5:** forecast lesion state có đứng vững ở hai future visits với reliable labels và prefix-only preprocessing?
4. **Q6:** patient-specific latent/geometry có hơn individual regional trend và đo được anatomy change thay vì similarity?

Q2 là hướng uncertainty độc lập hoặc phép kiểm tra bổ sung, chưa quyết định gộp với Q1. Các câu trên bao phủ A/B/C; chúng không chọn họ chiến thắng.

## Chính xác điều còn thiếu để chọn paper topic

| Thông tin còn thiếu | Vì sao thay đổi quyết định | Cách xác minh tiếp |
| --- | --- | --- |
| Access/license và release cụ thể | Dataset công khai theo mô tả chưa đủ chứng minh nhóm dùng được | Terms + approved download/manifest; giữ data ngoài public repo |
| Số subject có đủ past/future thật | Quyết định khả thi multi-step hay chỉ one-pair | Count subject/time/modality/label intersection, không ước lượng từ tổng images |
| Actual time và continuity | Quyết định horizon giây/ngày/tháng | Header/sidecar audit, gaps/reset/phase checks |
| Ground-truth target reliability | Error floor có thể lớn hơn change signal | Rater subset, mask provenance, landmark/change validation |
| Information available at cutoff | Quyết định có forecasting thật không | Audit registration/crop/template/covariates và test-time adaptation |
| Endpoint và latency/horizon có ý nghĩa | Chặn việc tối ưu arbitrary image metric | Trao đổi chuyên gia phù hợp với mỗi candidate, chốt intended-use test |
| Với B: command/contact/control state | Quyết định conditional view model hay controllable simulator | Schema actions/pose/force/latency/support; hiện UNKNOWN |
| Với C: care timeline và selection | Quyết định observed-care estimand; causal có bảo vệ được không | Treatment-time/missingness/assignment/confounding audit; hiện chưa đủ |
| Baseline headroom | Có thể khiến bài toán không cần learned dynamics | Reproduce simple baselines trước phương pháp mới |
| Capacity nghiên cứu thực tế | Annotation, compute và collaborator availability chưa được xác nhận | Ước lượng sau sample audit; không chọn backbone để thay việc này |

## Hành động nghiên cứu tiếp theo

1. Audit metadata nhỏ cho **một nguồn của mỗi A/B/C** nếu access cho phép; lập feasible temporal-contract table và số trajectory thực, chưa train mô hình lớn.
2. Chốt một endpoint/horizon có lý do với chuyên gia; đánh dấu label/care/pose nào quan sát được.
3. Chạy minimal simple-baseline headroom experiment với held-out patients và prefix-only preprocessing.
4. Tìm prior art lần nữa bằng chính **endpoint + state + horizon + dataset + baseline** đã thu hẹp, gồm backward/forward citations của đối chứng mạnh nhất.
5. Chủ dự án chọn bài toán sau khi thấy feasibility và kết quả bác bỏ/ủng hộ baseline hypothesis. Chỉ sau đó mới cân nhắc thiết kế phương pháp.

Không cần người nghiên cứu phê duyệt kiến trúc hoặc chọn modality để hoàn tất survey này; thông tin thiếu được ghi như điều kiện cho **bước nghiên cứu kế tiếp**, không ngụ ý đã có data hoặc kết quả.
