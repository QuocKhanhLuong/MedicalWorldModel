# Quy ước làm việc trong MedicalWorldModel

## Chỉ định của chủ dự án

Ngày 2026-09-07, chủ dự án chỉ định `QuocKhanhLuong/MedicalWorldModel` là repo chính thức và yêu cầu chủ động viết/cập nhật docs mỗi khi source of truth hoặc knowledge base có thay đổi. Quy ước áp dụng trong lượt làm việc có quyền truy cập repo, không đòi hỏi người dùng nhắc lại.

## Đọc trước khi làm

Đọc `README.md`, `docs/SOURCE_OF_TRUTH.md`, phần liên quan trong `docs/KNOWLEDGE_BASE.md`, `docs/RESEARCH_SETUPS.md`, `docs/REFERENCES.md` và các mục mới nhất trong `docs/CHANGELOG.md`. Luôn đọc phiên bản hiện tại trên nhánh đích trước khi sửa, không dùng trí nhớ hoặc bản cũ để ghi đè.

## Khi nào cập nhật

Cập nhật khi có quyết định hoặc thay đổi phạm vi; hiểu biết mới có ý nghĩa; kết quả đối chiếu nguồn; phát hiện sai và đính chính; thay đổi khả năng tiếp cận dữ liệu; giả thuyết/thí nghiệm mới; kết quả thí nghiệm kể cả kết quả âm; blocker hoặc hành động tiếp theo làm thay đổi tình trạng dự án. Không tạo commit cho lời chào, nhắc lại hoặc thay đổi không có nội dung mới.

## Ghi đúng mức độ chắc chắn

- `SOURCE_OF_TRUTH.md`: quyết định, ràng buộc và tình trạng thực tế đã được xác nhận. Không biến đề xuất của tác nhân thành lựa chọn của chủ dự án.
- `KNOWLEDGE_BASE.md`: định nghĩa vận hành, diễn giải, kết quả tìm hiểu; ghi rõ phần là quy ước, suy luận, giả thuyết hoặc có bằng chứng.
- `RESEARCH_SETUPS.md`: thiết lập ứng viên và điều kiện kiểm tra; chưa được chọn vẫn phải ghi là chưa chọn.
- `REFERENCES.md`: nguồn gốc, URL/DOI, phiên bản, ngày đối chiếu, trạng thái công bố, phát biểu được nguồn hỗ trợ và giới hạn. Chỉ đánh dấu đã kiểm chứng sau khi thực sự đọc nguồn gốc phù hợp.
- `CHANGELOG.md`: ngày theo Asia/Bangkok, thay đổi, căn cứ, ảnh hưởng, điều còn mở và việc tiếp theo.

Một câu trả lời trước của trợ lý hoặc một liên kết chưa đọc không đủ để coi là bằng chứng đã xác minh. Khi có sai sót, sửa nội dung hiện tại và ghi lại đính chính; không âm thầm xóa dấu vết quyết định quan trọng.

## Quy trình đồng bộ trong cùng lượt

1. Xác định phần thay đổi có ý nghĩa; đối chiếu trạng thái hiện có để tránh trùng.
2. Sửa tài liệu đúng chức năng, cập nhật các chỗ liên quan và nhật ký. Nội dung docs bằng tiếng Việt; giữ thuật ngữ, tên paper và định danh gốc khi cần.
3. Kiểm tra liên kết nội bộ, mức độ bằng chứng, các giả định dữ liệu và sự nhất quán giữa các tài liệu.
4. Đọc nhánh đích/HEAD hiện tại. Tôn trọng chính sách nhánh và không ghi đè thay đổi của người khác. Dùng commit tài liệu có nội dung rõ ràng; không force-push, không xóa hoặc sửa phần không liên quan.
5. Với cập nhật docs thông thường, đẩy lên nhánh mặc định nếu chính sách repo cho phép. Nếu nhánh yêu cầu PR, dùng nhánh docs và PR; không báo đã nhập vào main khi mới mở PR.
6. Đọc lại nội dung/commit trên GitHub. Báo SHA hoặc URL và file thay đổi. Khi ghi bị lỗi, nói rõ chưa đồng bộ, giữ bản nháp khi có thể; không tuyên bố thành công hoặc hứa thực hiện ngầm về sau.

Không coi quy ước này là GitHub Actions, cron, webhook hay bộ đồng bộ tự động đã triển khai. Không tự triển khai dịch vụ nền chỉ để thực hiện yêu cầu ghi docs.

## Giới hạn nghiên cứu và bảo mật

Không chọn backbone/kiến trúc thay cho việc định nghĩa hệ, state, transition, horizon và mục tiêu. Không ép dự án dùng siêu âm hoặc dữ liệu của paper dataset riêng. Không giả định đã có dữ liệu bệnh nhân, điều trị, pose đầu dò hay robot. Không coi latent là trạng thái lâm sàng có ý nghĩa khi chưa kiểm chứng; không đồng nhất dự báo quan sát với tác dụng nhân quả hoặc giá trị của một policy.

Repo công khai: không commit dữ liệu nhận diện bệnh nhân, ảnh chưa khử định danh, thông tin lâm sàng riêng tư, token, mật khẩu hay dữ liệu không được phép phân phối. Chỉ đưa nội dung liên quan dự án và phù hợp để công bố; không sao chép toàn bộ lịch sử trò chuyện hoặc thông tin cá nhân không liên quan.
