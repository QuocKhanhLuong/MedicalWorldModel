# Knowledge base — khung khái niệm ban đầu

Cập nhật: **2026-09-07**.

**Trạng thái:** bản tổng hợp từ thảo luận; các định nghĩa dưới đây là quy ước vận hành để thiết kế nghiên cứu, không phải tuyên bố đồng thuận duy nhất của lĩnh vực. Ví dụ là minh họa, không phải kết quả thực nghiệm. Metadata paper/dataset được quản lý riêng tại [REFERENCES.md](REFERENCES.md).

## 1. State của cái gì?

Đặt tên hệ thống và câu hỏi tương lai trước khi đặt tên latent.

| Hệ đang mô hình hóa | Input → state → transition → output |
| --- | --- |
| Chuyển động theo hô hấp | Lịch sử cine và mục tiêu đã xác định → hình dạng/vị trí, hướng chuyển động, bất định → diễn tiến theo thời gian → contour/tâm mục tiêu tương lai |
| Co bóp tim | Các frame quá khứ → hình dạng buồng tim, hướng co/giãn, tốc độ biến đổi → tiến triển động học → hình dạng/thể tích tương lai |
| Thu nhận ảnh | Các ảnh đã thấy và pose đã đo → giải phẫu đã biết, pose tương đối, vùng chưa biết → thay đổi pose/thao tác → quan sát dự kiến |
| Diễn biến tổn thương | Các lần khám quá khứ và khoảng thời gian thực → gánh nặng, phân bố không gian, xu hướng, bất định → diễn biến trong bối cảnh chăm sóc → tổn thương hoặc endpoint tương lai |

Chuyển động của tổn thương trong một đoạn cine không phải cùng bài toán với tăng trưởng bệnh qua nhiều lần khám. Dự án không cần mô hình hóa toàn bộ bệnh nhân; cần giới hạn hệ và những câu hỏi state phải trả lời.

## 2. Observation, state và latent

**Observation** là phép đo nhận được: ảnh, contour, pose, xét nghiệm, timestamp hoặc metadata. **State** là mô tả hiện tại của hệ đủ hữu ích cho phần tương lai đang quan tâm.

Biến state có thể đo/ước lượng trực tiếp, như vị trí hoặc thể tích; có thể ẩn, như vận tốc biến dạng không được đo; hoặc được biểu diễn bằng latent học từ lịch sử. Một latent dự đoán tốt không tự chứng minh nó tương ứng với trạng thái sinh học, một dấu ấn bệnh hoặc một hệ tọa độ có ý nghĩa lâm sàng.

Khi nhiều trạng thái tương thích với cùng một quan sát, nên nghĩ tới **niềm tin có bất định về state**, không mặc định quan sát xác định duy nhất trạng thái thật.

## 3. Vì sao cần lịch sử?

Ví dụ minh họa: cùng thể tích hiện tại nhưng trước đó tăng lên hoặc giảm xuống có thể dẫn đến hai dự báo khác nhau. Cùng hình dạng tức thời nhưng đang co hoặc giãn cũng tạo mơ hồ về tương lai.

Đó là lý do đặt giả thuyết cần history, không phải bằng chứng rằng mọi history đều có ích. So sánh current-only với history-aware prediction bằng cùng thông tin không gian, thời gian và chia tập. Nếu history không giúp, cần xem lại endpoint, dữ liệu hoặc nhu cầu mô hình động học.

## 4. Tự diễn tiến, hành động và thời gian

Không-action nghĩa là mô hình không nhận hành động điều khiển tường minh; không có nghĩa hệ hoàn toàn không chịu tác động bên ngoài. Trong cohort được chăm sóc, bỏ treatment khỏi input không biến dữ liệu thành bệnh sử tự nhiên không điều trị.

Khoảng thời gian `Δt` là điều kiện dự báo; nó không tự động là action. Chuyển vị đầu dò đã đo cũng khác lệnh điều khiển được gửi tới thiết bị. Dữ liệu của điều đã xảy ra không tự xác nhận đáp ứng dưới mọi lệnh có thể chọn.

## 5. Định nghĩa vận hành các loại mô hình

| Loại | Cam kết để phân loại trong dự án |
| --- | --- |
| Next-frame predictor | Dự đoán observation kế tiếp; chưa tự chứng minh state tái sử dụng hoặc rollout nhiều bước |
| Mô hình chuỗi thời gian | Mô hình hóa phụ thuộc theo thời gian; có thể hoặc không có state phù hợp với hệ đã định nghĩa |
| World model | Có state cập nhật từ quan sát, mô hình chuyển state theo thời gian/action nếu có, dự báo nhiều bước và kiểm chứng state cho mục tiêu đã đặt |
| Policy | Chọn hành động theo mục tiêu; không đồng nhất với mô hình dự đoán hậu quả |

Không bắt buộc world model sinh ảnh, có robot, có action hoặc dùng một họ kiến trúc nhất định. Một mô hình trạng thái–không gian đơn giản có thể đáp ứng quy ước này. Các nhóm khái niệm có thể giao nhau; tên gọi không thay thế thiết kế kiểm chứng.

## 6. Ký hiệu tối thiểu

Gọi `h_t` là lịch sử được phép biết ở thời điểm dự báo. Niềm tin về state là `b_t(s) = p(s_t = s | h_t)`. Biểu diễn học được có thể viết `z_t = E(h_t)`; không mặc định `z_t` bằng trạng thái sinh học thật.

Mô hình quan sát: `o_t ~ p(o_t | s_t, m_t)`, với `m_t` là metadata thu nhận.

Mô hình chuyển tiếp: `s_(t+Δ) ~ p(s_(t+Δ) | s_t, Δ, a_[t,t+Δ))`. Bỏ biến action nếu thiết lập không dùng action. Không đưa thông tin thực tế chỉ có trong tương lai vào điều kiện dự báo mà không nêu rõ đó là kịch bản được cung cấp trước.

Đầu ra có thể là ảnh, contour, vị trí hoặc chỉ số: `y_(t+Δ) ~ p(y | s_(t+Δ))`.

Câu hỏi kiểm tra state: sau khi có `z_t`, phần history bị bỏ đi còn giúp dự báo endpoint không? Đây là kiểm tra thực nghiệm có giới hạn, không phải chứng minh state đầy đủ cho mọi truy vấn.

## 7. Ba mức tuyên bố phải tách

**Dự đoán:** dự báo những diễn biến phù hợp với phân phối dữ liệu được đánh giá.

**Can thiệp:** dự báo hậu quả của việc chủ động thay đổi hành động. Không mặc định `p(Y | H, A=a) = p(Y | H, do(A=a))`. Treatment-conditioned prediction trên dữ liệu quan sát chưa tự xác lập hiệu ứng nhân quả.

**Hỗ trợ quyết định:** chứng minh dự báo làm lựa chọn tốt hơn theo utility, chi phí, rủi ro và bất định đã định nghĩa. Giảm sai số ảnh không tự chứng minh mức này. Policy được đánh giá chỉ trong chính world model của nó chưa đủ xác nhận giá trị ngoài hệ mô phỏng đó.

## 8. Hợp đồng đánh giá đề xuất

| Kiểm tra | Yêu cầu |
| --- | --- |
| Forecasting thực sự | Chỉ dùng prefix ở thời điểm suy luận; tách reconstruction/interpolation với dự báo |
| Nhiều bước | Báo cáo sai số theo horizon; tách rollout không nhận quan sát tương lai với tracking có cập nhật |
| Giá trị history | So với current-only và state đơn giản; dùng ablation phù hợp |
| Giá trị state | Kiểm tra nhiều endpoint độc lập; so với biến tường minh; không chỉ latent prediction error hoặc hình chiếu latent |
| Bất định | Đo hiệu chuẩn, độ bao phủ và độ rộng đồng thời |
| Tránh leakage | Chia theo bệnh nhân/người được quét; kiểm tra chuẩn hóa, registration, atlas và tạo map không dùng tương lai trái với thiết lập |
| Khái quát hóa | Đánh giá người/bệnh nhân chưa thấy; cơ sở/thiết bị mới nếu dữ liệu cho phép |
| Giá trị sử dụng | Metric gắn với hình học, chức năng hoặc endpoint đã định trước, không chỉ độ đẹp ảnh sinh |

Chưa có thực nghiệm nào xác nhận các giả thuyết của dự án. Quy trình này dùng để quyết định mô hình có cần thiết hay không trước khi tăng độ phức tạp.
