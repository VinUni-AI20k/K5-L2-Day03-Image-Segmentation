# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603036
- Ngày / CVAT local: 12/11/2026
- Công cụ đã dùng: VAT local, SAM3/Nuclio.

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task            | File ZIP đúng tên   | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --------------- | ------------------- | -----------------: | ---------------------------: |
| easy_semantic   | easy_semantic.zip   |              3 / 3 |                           20 |
| medium_instance | medium_instance.zip |              3 / 3 |                           32 |
| hard_panoptic   | hard_panoptic.zip   |              2 / 2 |                           30 |
| cp1_holes       |	cp1_holes.zip       |              1 / 1 |                            3 |
| cp2_slice       | cp2_slice.zip       |              1 / 1 |                            3 |
| cp5_occlusion   | cp3_thin.zip        |              1 / 1 |                            3 |
| cp3_thin        | cp4_curb.zip        |              1 / 1 |                            3 |
| cp4_curb        | cp5_occlusion.zip   |              1 / 1 |                            3 |
| cp6_coverage    | cp6_coverage.zip    |              1 / 1 |                            3 |
| **Tổng tối đa** |                     |                    |                      **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: ảnh:000000181542.jpg, vị trí: giữa ảnh dưới bức tượng, object person 10
- Class và quy tắc tôi dùng để chọn biên: Class person. Tôi sử dụng công cụ Brush/Mask để tạo vùng phân đoạn thủ công. Khi vẽ, tôi bám theo đường viền cơ thể người có thể quan sát được, chỉ lấy vùng thuộc đối tượng person, không lấy phần nền hoặc các vật thể xung quanh.
- Nếu dùng gợi ý sau đó: Không dùng gợi ý tự động cho object này. Tôi tự xác định và gán nhãn dựa trên các đặc điểm trực quan của đối tượng, nhận thấy đối tượng phù hợp với class person nên giữ nguyên annotation đã vẽ thủ công.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Hard Panoptic – ảnh 000000460147.jpg, khu vực phương tiện giao thông, người đi bộ, cây xanh và các vùng cảnh quan.
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: Số lượng annotation ban đầu chưa đầy đủ, một số vùng đối tượng cần được kiểm tra và bổ sung.
- Bằng chứng tôi nhìn thấy:Bản xuất ban đầu có 65 annotations. Sau khi kiểm tra, chỉnh sửa và xuất lại, số lượng tăng lên 122 annotations.
- Quy tắc và hành động sửa:  Kiểm tra lại các đối tượng trong từng ảnh, đối chiếu class tương ứng và bổ sung annotation cho các vùng đối tượng còn thiếu.
- Sau sửa đã Save và export lại chưa? Đã lưu và export lại file hard_panoptic.zip.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể  | Quy tắc/chứng cứ                                                       | Quyết định hoặc câu hỏi cho coach            |
| ---------- | --------------------- | ---------------------------------------------------------------------- | -------------------------------------------- |
| 000000460147.jpg – khu vực giữa ảnh, nơi có nhiều xe ô tô gần nhau         | Có thể gộp các xe thành một vùng hoặc tách riêng từng xe thành các instance. | Quan sát đường viền, hình dáng và phần thân riêng biệt của từng xe.           | Tôi chọn tách riêng từng xe theo class Car.|
| 000000460147.jpg – khu vực có người đi bộ gần phương tiện giao thôn          | Chỉ gán phần cơ thể nhìn thấy hoặc suy đoán cả phần bị che khuất.| Dựa vào phần đối tượng thực tế quan sát được, không tự suy đoán phần bị che.        | Tôi chỉ đánh dấu phần Person nhìn thấy. Khi bị che khuất nhiều, nên xử lý mask như thế nào?                             |
| 000000460147.jpg – khu vực tiếp giáp giữa lòng đường và vỉa hè          | Có thể nhầm vùng tiếp giáp là Road hoặc Sidewalk.| Dựa vào mép đường, sự thay đổi bề mặt và chức năng của từng khu vực. | Tôi phân biệt Road và Sidewalk theo ranh giới quan sát được.