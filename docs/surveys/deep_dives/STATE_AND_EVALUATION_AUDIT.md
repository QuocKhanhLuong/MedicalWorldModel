# Kiểm toán state và đánh giá — nghiên cứu sâu đợt 2

Đối chiếu **2026-09-12**, Asia/Bangkok. Mục tiêu: làm rõ **bằng chứng nào đủ để gọi một predictive state là hữu ích**, và những phép đánh giá nào dễ cho kết luận quá mức. Đây là nghiên cứu tài liệu; chưa chạy mô hình, chưa xác lập novelty và chưa chọn A/B/C.

**VERIFIED** bên dưới là nội dung đã đối chiếu trong nguồn gốc, không phải kết quả repo tái lập. **INTERPRETATION / HYPOTHESIS** là phân tích, phản ví dụ hoặc protocol đề xuất của chúng ta. Metadata canonical và phạm vi đọc nằm trong [paper matrix](../../PAPER_MATRIX.md). Các audit song song: [A](FAMILY_A_FORECASTING_AUDIT.md), [B](FAMILY_B_ACQUISITION_AUDIT.md), [C](FAMILY_C_LONGITUDINAL_AUDIT.md).

## 1. VERIFIED — predictive state không bắt đầu từ video foundation models

[Littman, Sutton và Singh, *Predictive Representations of State*, NeurIPS 2001](https://proceedings.neurips.cc/paper/2001/hash/1e4d36177d71bbb3558e43af9577d70e-Abstract.html) định nghĩa state bằng xác suất của một tập **future tests**: các chuỗi action–observation. Một PSR đúng phải đủ thông tin để suy xác suất của mọi test trong hệ. §1 và Theorem 1 trong [PDF gốc](https://proceedings.neurips.cc/paper/2001/file/1e4d36177d71bbb3558e43af9577d70e-Paper.pdf) nêu kết quả tồn tại linear PSR cho hệ biểu diễn được bằng finite POMDP; không chứng minh một encoder học từ MRI sẽ tìm được state đó. Paper nghiên cứu prediction, không cần reward hay thực hiện control.

**INTERPRETATION / HYPOTHESIS.** Có thể lấy nguyên tắc “state giữ thông tin cần cho tương lai” mà không bắt dự án dùng PSR hay POMDP. Trong A/C không có action quan sát được, test có thể là future geometry/burden tại các thời điểm xác định. “Predictive” là ý nghĩa được kiểm tra bằng đầu ra; nó không tự cung cấp tên gọi sinh học cho từng chiều latent. Một representation có thể đủ cho centroid 0.5 s nhưng thiếu thông tin cho deformation 2 s hoặc đáp ứng điều trị.

## 2. INTERPRETATION / HYPOTHESIS — hợp đồng state có thể bị bác bỏ

Gọi `H_t` là toàn bộ thông tin **thật sự có tại thời điểm dự báo**, `z_t = f(H_t)`, `Y` là target và `q` là query: horizon, view hoặc action nếu có. Tiêu chuẩn lý tưởng, giới hạn trong hệ và tập query đã định:

`P(Y | H_t, q) = P(Y | z_t, q)`.

Đây là cách vận dụng ý tưởng sufficiency của PSR, **không phải định lý về mô hình của dự án**. Kiểm tra trên dữ liệu hữu hạn chỉ có thể phát hiện thiếu thông tin hoặc cung cấp bằng chứng hỗ trợ trong phạm vi test; không chứng minh equality cho mọi bệnh nhân/tình huống.

| Phép kiểm tra đề xuất | So sánh phải giữ cố định | Kết quả bác bỏ / giới hạn diễn giải |
| --- | --- | --- |
| **History residual test** | Frozen state → target so với cùng state + lịch sử bổ sung có sẵn; cùng patient split và ngân sách chọn predictor | Lịch sử bổ sung còn cải thiện có ý nghĩa: state hoặc readout chưa giữ/khai thác đủ thông tin. Không cải thiện chưa chứng minh sufficiency vì readout/test có thể thiếu lực |
| **State reuse** | Một state cố định, readouts đơn giản cho ≥2 target/horizon đã định; đối chiếu direct history predictors | Chỉ có gain khi retrain toàn bộ cho mỗi target: yếu hơn claim reusable predictive state |
| **Aliasing test** | Hai lịch sử có current geometry gần nhau nhưng khác chiều vận động/coverage; phân nhóm chỉ từ prefix | State không phân biệt được hai tương lai: current appearance hoặc state quá nén. Không được dùng future truth để tạo nhóm “dễ” lúc inference |
| **Transition value** | Last-state persistence, velocity/periodic/mixed-effects, direct time-conditioned history predictor và model có transition | Gain mất khi baseline được cùng history/labels: chưa có bằng chứng transition/state mới cần thiết |
| **Observation update test** | Cùng budget/độ trễ quan sát; so dự báo trước và sau một quan sát mới | Assimilation cải thiện chỉ chứng minh lợi ích cập nhật; không gán gain đó cho autonomous rollout |
| **Nuisance stress** | Thay đổi intensity/crop/device trong phạm vi perturbation đã định; target geometry giữ nguyên | State thay đổi mạnh theo nuisance: yếu claim anatomy state. Bất biến với perturbation tổng hợp chưa chứng minh bất biến giữa scanner thật |
| **Composition test** | Cùng prefix/query: direct Δt₁+Δt₂ so với hai transition liên tiếp, đồng thời chấm against future truth | Hai đường dự báo đồng ý nhưng cùng sai vẫn thất bại. Với stochastic belief phải so phân bố/composition đúng, không ép hai random samples trùng nhau |

Không lấy linear-probe anatomy accuracy làm bằng chứng duy nhất: probe có thể đọc được current anatomy nhưng transition vẫn không dự báo được sự thay đổi. Cũng không bắt mọi state phải tối giản, Markov chính xác hoặc clinically interpretable mới đáng nghiên cứu. Cần nêu rõ **claim nhỏ nhất mà thí nghiệm thực sự kiểm tra**.

## 3. VERIFIED — benchmark CV đo nhiều thứ khác nhau

| Nguồn đã đọc methods/evaluation | Hệ → observation/state → transition/future → purpose | Đánh giá vượt perceptual quality | Giới hạn trực tiếp của protocol |
| --- | --- | --- | --- |
| [WorldSimBench, ICML 2025](https://proceedings.mlr.press/v267/qin25f.html), §3.2, Fig.3, §4.1 | Minecraft/CARLA/CALVIN → image + instruction, state tùy video model → generated future → video-to-action/goal policy thực thi | Environment counters, driving infractions, manipulation success | Replanning nhận observation mới sau một khoảng; success thuộc pipeline video model + adapter/controller |
| [WorldModelBench, NeurIPS 2025 Datasets and Benchmarks](https://proceedings.neurips.cc/paper_files/paper/2025/hash/4ec03ed08a3fcb59e1c815b5598beff1-Abstract-Datasets_and_Benchmarks_Track.html), §3–4 | Nhiều visual domains → text/first image → generated video → human/learned judge | Instruction completion, các nhãn vi phạm vật lý, human agreement | “Physics adherence” là annotation/judge về video; không phải đo phương trình vật lý hay executed action |
| [WorldArena, arXiv:2602.08971v2](https://arxiv.org/html/2602.08971v2), §3.2–3.4, Appendix A/B | RoboTwin → current image/action hoặc instruction → model rollout → policy data/evaluation/action adapter | Policy improvement, policy-ranking agreement với simulator, simulator task success | Policy evaluator dùng VLM chấm imagined video; action planner có IDM. EWMScore **chỉ** trung bình 16 video metrics sau chuẩn hóa |
| [WorldArena 2.0, arXiv:2605.17912v1](https://arxiv.org/html/2605.17912v1), §3–4, Tables1–3 | Visual/tactile manipulation → multimodal latent tùy model → observation/action trajectories → RL/data/planning | Tách UniVTAC tactile tasks, RoboTwin RL tests, LIBERO và AgileX real-robot tasks | Kết quả tactile Table1 là **simulation**; real-robot Table3 là track khác. Không gộp thành xác nhận tactile sim-to-real |
| [Physics-IQ / *Do Generative Video Models Understand Physical Principles?*, WACV 2026](https://openaccess.thecvf.com/content/WACV2026/html/Motamed_Do_Generative_Video_Models_Understand_Physical_Principles_WACV_2026_paper.html), §2.2–2.5, §4 | Recorded physical events → tối đa 3 s prefix hoặc switch frame → 5 s continuation → physics prediction diagnostic | Motion masks: nơi, thời điểm, lượng motion; hai takes thật để tham chiếu physical variability | Static cameras, input khác nhau theo model; score vẫn là proxy, không định lượng mọi physical parameter |

### INTERPRETATION / HYPOTHESIS — bốn bài học không nên chuyển nguyên xi

1. **Tên metric không phải đại lượng đã đo.** Appendix A của [WorldArena](https://arxiv.org/html/2602.08971v2) dùng monocular estimated depth có scale alignment, arm bounding-box trajectory và diversity giữa video cho các instruction. Diversity tự nó không chứng minh từng instruction được thực hiện đúng; depth suy từ ảnh không phải ground-truth mm. Với y khoa, đo đúng physical/anatomical quantity nếu claim dùng đơn vị đó.
2. **Điểm tổng hợp không thay clinical endpoint.** Giữ các kết quả geometry, uncertainty, task utility thành bảng riêng. Không cho image aesthetics bù trừ lỗi target position hoặc bỏ sót lesion trong một average.
3. **Success là bằng chứng hệ thống, cần attribution.** Video + inverse dynamics + controller có thể hữu ích; để quy gain cho state/transition, cần adapter và observation budget tương đương, thêm current-frame/direct-policy baseline. Với A/C không có policy, dùng downstream quantity hay retrospective decision proxy đã xác định.
4. **Đừng tạo hindsight alignment.** Time-warp có thể phù hợp chấm hình dạng trajectory nhưng xóa latency error. Scale alignment có thể phù hợp geometry tương đối nhưng xóa lỗi kích thước. Các phép này là supplementary diagnostics nếu use case cần đúng thời điểm/đơn vị thật.

**VERIFIED — khác phiên bản cần giữ.** WorldSimBench arXiv:2410.18072 xuất hiện 2024, canonical ICML 2025; danh sách tác giả arXiv và proceedings khác nhau, matrix dùng proceedings. WorldModelBench canonical có DOI 10.52202/085713-1834, không dùng số improvement trong abstract arXiv cũ thay số của bản công bố. WorldArena/2.0 hiện được ghi là preprints đã xác minh; việc có CVPR/IROS challenge không tự xác nhận main-conference paper. [WorldArena 2.0 leaderboard](https://worldarena-worldarena2-0.hf.space/?__theme=system) thông báo thay đổi scoring motion; audit này khóa các nhận xét phương pháp vào phiên bản paper, không khẳng định leaderboard hiện tại dùng công thức y hệt.

## 4. VERIFIED — uncertainty/calibration đã có prior art gần và mạnh

- [Sangalli et al., *Conformal Forecasting for Surgical Instrument Trajectory*, MICCAI 2025](https://doi.org/10.1007/978-3-032-05114-1_12), [accepted PDF](https://papers.miccai.org/miccai-2025/paper/0260_paper.pdf) §2.1–3/Table1: endoscopic detection history 64 frames → latent → tổng displacement tới 8 frames sau; conformal/CQR cho góc và độ dài, chấm coverage/width và joint corrections. **Joint ở đây là hai thành phần của endpoint displacement, không phải toàn bộ đường đi 8 bước.**
- [Laves et al., MELBA 2021](https://www.melba-journal.org/papers/2021:008.html), §2–4: sigma scaling, calibration diagrams, prediction intervals và rejection trong medical **image regression**. Đây là prior art cho calibration đơn giản; không phải temporal world model.
- [Zhou, Lindemann và Sesia, CAFHT, ICML 2024](https://proceedings.mlr.press/v235/zhou24l.html), §2–3/Theorem1 và Appendix A6: simultaneous trajectory coverage với **exchangeability giữa trajectories**, không cần independent steps trong mỗi trajectory. Protocol chính nhận ground truth từng bước trước dự báo bước kế; extension multi-step vẫn cập nhật theo quan sát mới. Conditional coverage theo loại trajectory được khảo sát thực nghiệm, không biến thành universal patient-specific guarantee.
- [Gneiting–Raftery, JASA 2007](https://doi.org/10.1198/016214506000001437), [author PDF](https://sites.stat.washington.edu/people/raftery/Research/PDF/Gneiting2007jasa.pdf) §4.2–4.3/§6: proper scoring rules cho predictive distributions, CRPS và energy score; strict propriety có điều kiện về lớp phân bố.
- [Scheuerer–Hamill, Monthly Weather Review 2015](https://doi.org/10.1175/MWR-D-14-00269.1), [NOAA PDF](https://repository.library.noaa.gov/view/noaa/22327/noaa_22327_DS1.pdf) §2–3/§5: energy score có thể kém nhạy với dependence errors trong các thí nghiệm; variogram score nhạy hơn trong các setup đó nhưng **không strictly proper**, có thể bỏ qua shared bias; cần kết hợp marginal/dependence/event diagnostics.

**INTERPRETATION / HYPOTHESIS — novelty bị thu hẹp.** “Calibrated medical forecasting”, “joint uncertainty” hoặc “first simultaneous trajectory intervals” đều không phải novelty có thể nhận chỉ bằng ghép tên kỹ thuật. Khoảng còn cần kiểm tra là tính hữu ích của **phân bố anatomy/burden theo nhiều future observations**, dưới đúng observation budget và shifts cụ thể, so với probabilistic baseline đã hiệu chuẩn.

### Một bất đồng với diễn giải nguồn, giải quyết bằng điều kiện toán học

**VERIFIED:** Sangalli §3 nêu lý do random calibration sampling và memoryless predictions cho exchangeability; §2.2 lại đặt exchangeability là giả định của **data distribution**. CAFHT §2.1 đặt giả định ở cấp trajectory. [Sangalli PDF](https://papers.miccai.org/miccai-2025/paper/0260_paper.pdf), [CAFHT PDF](https://raw.githubusercontent.com/mlresearch/v235/main/assets/zhou24l/zhou24l.pdf).

**INTERPRETATION / HYPOTHESIS:** Chạy predictor độc lập từng window không làm các overlapping windows trở thành exchangeable giữa patients/centers. Không kết luận paper sai toàn bộ; kết luận hẹp là lời giải thích đó chưa đủ để mang guarantee sang cohort của dự án. Khi calibration unit là patient/trajectory, phải đếm số unit đó; không dùng số frame làm số bệnh nhân độc lập.

## 5. INTERPRETATION / HYPOTHESIS — ba cấp uncertainty phải tách

| Cấp cần chấm | Câu hỏi thật | Thiết kế đề xuất |
| --- | --- | --- |
| Marginal theo horizon | Target tại mỗi horizon có đúng phân bố/interval? | CRPS cho quantity scalar; coverage + interval width; group/horizon curves |
| Joint trajectory | Tương lai của cùng một người có phụ thuộc thời gian đúng? | Score vector trajectory (energy + dependence diagnostic), simultaneous coverage, distribution của max error/first crossing |
| Decision/event | Sai số ảnh hưởng proxy đã định thế nào? | Event probability/reliability; miss-risk ở cùng duty cycle hoặc resource budget; tách false reassurance và abstention |

**Phản ví dụ toán học, không phải kết quả lâm sàng:** nếu 10 intervals có coverage 0.95 và các coverage events độc lập, xác suất tất cả cùng chứa truth là `0.95^10 ≈ 0.599`. Nếu phụ thuộc khác, giá trị khác. Vì vậy “95% ở mỗi frame” không đồng nghĩa “95% cho cả rollout”. Bonferroni/trajectory scores là prior art, không phải đóng góp mới của dự án.

**Kiểm tra để đánh giá metric trước mô hình:**

- Shuffle sample identity giữa horizons nhưng giữ nguyên marginal samples: marginal score không đổi, continuity/joint-risk có thể đổi. Một evaluation chỉ nhìn marginals sẽ không phát hiện.
- Add cùng một bias cho mọi thời điểm: pairwise temporal differences giữ nguyên. Variogram-only có thể bỏ sót, trong khi absolute quantity error tăng.
- Nhân uncertainty rộng lên: coverage có thể tăng nhưng forecasts kém hữu ích; phải chấm sharpness/proper score cùng coverage.
- Chọn best sample sau khi biết future truth: đó là oracle diagnostic; dùng nhiều sample không được tự cải thiện claim deployable point forecast.
- Chấm auto-segmentation của generated image: đo một chuỗi generator + segmenter. Cần kiểm tra target labels/segmenter error trên held-out real images và một subset manual nếu có; không coi segmenter output là biological truth.

Những phép này chỉ là **thiết kế falsification**, chưa được thực hiện trong repo. Khi state là latent không có calibrated decoder density, không báo pixel likelihood tùy tiện; có thể chấm distribution của measured quantities. Khi có missing future visits, không nội suy labels để biến một follow-up thành nhiều observations độc lập.

## 6. INTERPRETATION / HYPOTHESIS — template evaluation dùng được cho A/B/C

Trước bất kỳ benchmark model nào, ghi một **prediction contract**:

| Trường phải khóa | A | B | C |
| --- | --- | --- | --- |
| Thời điểm ra dự báo | Frame t, kể cả processing latency | Frame t và chỉ pose/history đã biết | Visit t và hồ sơ đã tồn tại tại visit t |
| Information budget | Bao nhiêu giây prefix; masks hiện tại đo hay suy? | Measured poses hay commanded actions; calibration và coverage | Bao nhiêu visits, modality, actual/rounded time và planned care có biết trước? |
| Query hợp lệ | Δt thực tính từ timestamps | Future pose query được cung cấp khác action phải chọn | Horizon/calendar interval khác realized future visit schedule |
| Future target | Centroid/boundary/deformation có labels thật | Image/anatomy/visibility ở measured target view | Burden/region/lesion quantity ở follow-up thật |
| Rollout mode | Fixed-prefix direct / recursive / assimilation tách riêng | Pose-conditioned synthesis / command rollout / closed-loop tách riêng | Fixed-prefix multi-visit / updating each visit tách riêng |
| Unit đánh giá | Patient/sequence; không random split các frame liền nhau | Subject/sweep; report covered vs unseen support | Patient; không trộn visits giữa splits |
| Utility claim tối đa của experiment offline | Latency/geometry proxy | Pose-conditioned prediction hoặc offline guidance proxy | Forecasting under observed care |

[Metrics Reloaded, Nature Methods 2024](https://doi.org/10.1038/s41592-023-02151-z) là nguồn **VERIFIED** cho nguyên tắc chọn metric theo domain interest, target, dataset và algorithm output. Framework đó tập trung classification/detection/segmentation; bảng temporal/probabilistic contract ở đây là **diễn giải mở rộng của dự án**, không phải protocol forecasting do paper đó xác nhận.

## 7. INTERPRETATION / HYPOTHESIS — thứ tự câu hỏi khoa học trước chọn topic

1. **Có target thật sau prefix không?** Kiểm tra manifest và sự liên tục; dense frames không đảm bảo dense anatomy labels, repeated series không đảm bảo repeated clinical visits.
2. **History mang thêm thông tin gì?** A: phase/direction/drift; B: spatial coverage/occlusion; C: patient-specific rate/observed-care history. So với baseline dùng đúng cùng thông tin.
3. **State có tạo giá trị đo được ngoài predictor trực tiếp?** Nếu không, đóng góp có thể là một forecasting benchmark/negative result; không cố cứu tên “world model”.
4. **Có đủ data cho uncertainty ở cấp cần dùng không?** Patient count, follow-up availability, calibration split và rare events phải kiểm tra trước coverage claims.
5. **Use case có thể kiểm chứng tới đâu?** Chưa có actions/outcomes/support thì dừng claim ở forecasting; chuyển sang guidance/planning cần evidence riêng.

Các protocol trên làm các câu hỏi Q1/Q2/Q4/Q5/Q6 chặt hơn, không chọn câu hỏi nào. Việc tiếp theo là dùng các [audit A/B/C](../RESEARCH_LOG.md) để xác định **data nào đáp ứng đúng contract**, rồi thảo luận mục tiêu khoa học với researcher.
