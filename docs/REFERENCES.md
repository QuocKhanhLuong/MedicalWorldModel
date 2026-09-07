# Sổ nguồn tham khảo và xác minh

Cập nhật: **2026-09-07**.

## Trạng thái khởi tạo

Các tên và đường dẫn dưới đây được chuyển từ cuộc thảo luận trước khi khởi tạo repo. **Chưa được đối chiếu độc lập trong đợt đồng bộ docs này.** Đây là hàng đợi kiểm chứng, không phải bibliography đã xác thực hoặc bằng chứng về tính mới.

Không chuyển các con số dataset, ngày/phiên bản, venue, tình trạng accepted/published hoặc kết luận định lượng từ câu trả lời trước thành sự thật đã xác nhận chỉ vì chúng xuất hiện trong thảo luận. Nhất là các mục năm 2026 cần đối chiếu trực tiếp trước khi dùng trong đề cương.

`CẦN_XÁC_MINH` không có nghĩa công trình sai hoặc không tồn tại; nghĩa là hồ sơ repo chưa có đủ bằng chứng để sử dụng claim liên quan.

## Đầu mối từ thảo luận

| ID | Tên/nhãn được nhắc tới trong thảo luận | Đường dẫn được nhắc tới | Cần kiểm tra | Trạng thái |
| --- | --- | --- | --- | --- |
| REF-A01 | TrackRAD2025 | https://doi.org/10.57967/hf/4539 ; https://arxiv.org/abs/2503.19119 | Paper và data release; split công khai/riêng; cadence, gián đoạn, loại mục tiêu/nhãn; giấy phép | CẦN_XÁC_MINH |
| REF-A02 | Frame forecasting in cine MRI using the PCA respiratory motion model | https://arxiv.org/abs/2410.05882 | Tên đầy đủ, phiên bản, DOI/venue, baseline, horizon và dữ liệu đánh giá | CẦN_XÁC_MINH |
| REF-A03 | A Latent ODE Approach to Spatiotemporal Modeling of Cine Cardiac MRI | https://arxiv.org/abs/2606.26718 | Xác nhận định danh/tên/trạng thái; reconstruction từ cả chu kỳ hay forecasting từ prefix | CẦN_XÁC_MINH |
| REF-B01 | TUS-REC2024 | https://github-pages.ucl.ac.uk/tus-rec-challenge/TUS-REC2024/ ; https://arxiv.org/abs/2506.21765 | Phiên bản challenge; truy cập, đồng bộ pose, calibration, người/quỹ đạo; điều kiện sử dụng | CẦN_XÁC_MINH |
| REF-B02 | EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance | https://arxiv.org/abs/2504.13065 | Paper gốc/venue, định nghĩa state/action, đánh giá, dữ liệu và code thực sự phát hành | CẦN_XÁC_MINH |
| REF-B03 | Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound | https://arxiv.org/abs/2607.21918 | Xác nhận định danh/tên/phiên bản/trạng thái; pose đo so với command, lực tiếp xúc và policy evaluation | CẦN_XÁC_MINH |
| REF-C01 | LUMIERE | https://www.nature.com/articles/s41597-022-01881-7 | Paper/dataset gốc; số chuỗi hợp lệ, thời gian, segmentation tự động so với nhãn chuyên gia, metadata điều trị, giấy phép | CẦN_XÁC_MINH |
| REF-C02 | ImageFlowNet | https://arxiv.org/abs/2406.14794 | Tên/phiên bản/venue; thời gian không đều, dataset/split, rollout và baseline | CẦN_XÁC_MINH |
| REF-C03 | Learning Patient-Specific Disease Dynamics with Latent Flow Matching for Longitudinal Imaging Generation / Δ-LFM | https://arxiv.org/abs/2512.09185 | Định danh, phiên bản và trạng thái công bố; giả định progression, cá thể hóa và đánh giá | CẦN_XÁC_MINH |
| REF-C04 | Treatment-Aware Diffusion Probabilistic Model for Longitudinal MRI Generation and Diffuse Glioma Growth Prediction / TaDiff | https://arxiv.org/abs/2309.05406 ; https://github.com/samleoqh/TaDiff-Net | Paper gốc/venue; treatment metadata, thiết lập forecast, nhãn, code và giới hạn nhân quả | CẦN_XÁC_MINH |
| REF-K01 | Dreamer / tách world model và policy | https://www.nature.com/articles/s41586-025-08744-2 | Tên/phiên bản chính xác và phần chứng minh mối quan hệ model–policy | CẦN_XÁC_MINH |
| REF-K02 | Locatello và cộng sự / disentanglement | https://proceedings.mlr.press/v97/locatello19a.html | Phạm vi kết luận, giả định và điều không được suy ra về clinical latent | CẦN_XÁC_MINH |
| REF-K03 | Forecasting Treatment Responses Over Time Using Recurrent Marginal Structural Networks | https://papers.nips.cc/paper/7977-forecasting-treatment-responses-over-time-using-recurrent-marginal-structural-networks | Giả định nhân quả, time-varying confounding và giới hạn áp dụng | CẦN_XÁC_MINH |

## Hồ sơ tối thiểu khi nâng thành nguồn đã kiểm chứng

Ghi tên chính xác; tác giả; arXiv ID và version nếu có; DOI/URL publisher; ngày kiểm chứng; trạng thái tại thời điểm kiểm chứng. Tách kiểm tra metadata/abstract với đọc toàn văn và kiểm tra data release thực tế.

Với mỗi claim được đưa vào knowledge base hoặc đề cương, ghi rõ nguồn hỗ trợ, vị trí như mục/trang/bảng nếu có, phạm vi kết luận và điểm chưa chắc. Với dataset, phân biệt số bệnh nhân, study, video, frame và visit; phân biệt nhãn manual/automatic; tách split có thể truy cập khỏi test kín. Không tự suy từ mô tả dataset thành quyền truy cập của nhóm.

Không đánh dấu đã đọc full text khi chỉ xem abstract; không đánh dấu đã audit dữ liệu khi chỉ đọc paper. Khi nguồn đổi phiên bản hoặc claim bị sửa, cập nhật tài liệu liên quan và [CHANGELOG.md](CHANGELOG.md).
