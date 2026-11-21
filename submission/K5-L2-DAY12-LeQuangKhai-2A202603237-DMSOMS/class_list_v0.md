# Danh sách lớp v0 — Lê Quang Khải · G07

Danh sách có AI hỗ trợ về nội dung và câu chữ, dựa trên GUIDE §3–4 và labels_cabin_v1.json. Các nhận xét về IR trong bảng là nguyên tắc sử dụng nhãn; quan sát thực tế của G07 được ghi riêng trong ir_log.csv. Hai câu hỏi cuối gắn với bất đồng đã xuất hiện trong các file nhãn, không khẳng định nguyên nhân thị giác khi chưa có quan sát bổ sung. Chưa có slide 54 để đối chiếu và chưa có phản hồi coach cho hai câu hỏi.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver | Định vị tài xế, phân biệt với người khác trước khi xét trạng thái mặt và tay. | Có thể dựa trên phần cơ thể thấy được và vị trí; không suy từ màu quần áo. |
| 2 | person / seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Mô tả cách đeo dây; không thấy rõ thì giữ unknown. | Phụ thuộc độ tương phản và che khuất; không khẳng định dây đang đeo nếu không thấy. |
| 3 | face / eye_left, eye_right | Mỗi mắt: open / closed / unknown | Cung cấp trạng thái từng mắt ở khung hiện tại; chuỗi thời gian mới giúp xét nhắm mắt kéo dài. Một ảnh closed không kết luận buồn ngủ. | Có thể, nhưng phản xạ kính, mặt nhỏ hoặc vật che có thể khiến unknown. |
| 4 | face / glasses | unknown / none / clear / sun | Ghi nhận vật cản vùng mắt và lý do giới hạn quan sát. | Có thể khó phân biệt loại kính trên NIR; không suy none chỉ vì thấy tròng trông trong. |
| 5 | face / gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Mô tả vùng nhìn để hỗ trợ phân tích chú ý khi có ngữ cảnh xe. Không chắc dùng other kèm ghi chú. | Dựa trên đầu và mắt khi thấy rõ; không dựa riêng vào màu. |
| 6 | face13 | 13 điểm mắt, mũi, miệng; cờ occluded / outside | Biểu diễn hình học mặt và tính quan sát được của từng điểm. Chỉ vẽ khi có mặt và chiều rộng box đạt 60 px. | Có thể khi đủ chi tiết; điểm bị che phải có cờ, không đặt đại cho đủ. |
| 7 | hand / whose, side, on_wheel | driver / passenger; left / right; yes / no / unknown | Phân biệt tay của ai, bên tay và tiếp xúc vô lăng. Tay không trên vô lăng không tự chứng minh hành vi nguy hiểm trong xe thử nghiệm tự lái. | Có thể theo hình dạng và tiếp xúc nhìn thấy; bàn tay bị che không được đoán. |
| 8 | phone / state | held / mounted / lap | Ghi nhận điện thoại và trạng thái đặt/cầm; cần thấy cạnh, góc hoặc màn hình trước khi vẽ. | Có thể thấy hình dạng; tay gần tai hoặc một vật tối chưa đủ để kết luận phone. |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | rear_left / rear_middle / rear_right | Xác định ghế có người lớn theo hệ tọa độ của xe. | Có thể từ cơ thể và vị trí. Camera nhìn về sau: trái ảnh là rear_right. |
| 2 | face | Box phần mặt thấy được | Bổ sung vị trí mặt người lớn trên ghế; OMS không vẽ face13. | Phụ thuộc phần mặt và chi tiết còn thấy; không vẽ khi quay đi hoặc che gần hết. |
| 3 | person / seatbelt | not_worn / unknown trong SVIRO | Ghi trạng thái dây khi quan sát được; chỉ ra giới hạn dữ liệu vì SVIRO không cung cấp mẫu người đeo dây. | Khi không thấy rõ, unknown; không sao chép kết luận từ ảnh RGB sang IR-sim. |
| 4 | child_seat / seat, occupied | Ghế theo xe; occupied = no / unknown | Phân biệt ghế trẻ em với người và đồ vật; không có giá trị occupied = yes trong schema bài này. | Có thể theo hình dạng, nhưng phần trong bị che thì occupied = unknown. |
| 5 | infant_seat / seat, facing | Ghế theo xe; rear / front | Nhận diện nôi/ghế em bé và hướng lắp, phục vụ mô tả bố trí cabin. Nhãn ghế trống không chứng minh có em bé. | Có thể theo hình dạng và hướng; nếu chưa xác định facing thì ghi ca khó hỏi coach, vì schema không có unknown. |
| 6 | object / seat, type | Ghế theo xe; bag / box / cup / other | Phân biệt đồ vật với người và ghế trẻ em, mô tả đồ vật đang chiếm chỗ. Vật trong child_seat có box riêng. | Có thể nhận bằng hình dạng, vị trí, ngữ cảnh; không đoán bằng màu, không chắc loại thì other. |
| 7 | frame_meta | modality: rgb / ir; light: day / night / unknown; camera_blocked: yes / no | Ghi điều kiện khung để phân tích chất lượng nhãn; với SVIRO đặt light = unknown. | Modality xác định từ nguồn tệp theo đề; không suy ngày/đêm từ độ sáng IR-sim. |

Ghế trống không phải label riêng của Cabin v1.0: không vẽ box, đếm trong ghi chú. Không thêm lớp mới vào project chỉ vì danh sách đề xuất nhắc tới một chức năng sản phẩm.

## Hai câu hỏi leo thang

1. **Tiêu chí ước lượng chắc vị trí điểm bị che:** GUIDE §4.6 quy định dùng occluded nếu ước lượng chắc vị trí và outside nếu không ước lượng được. Có ví dụ chuẩn hoặc tiêu chí cụ thể nào để hai người gán nhãn hiểu giống nhau mức “chắc vị trí”, nhất là khi mắt đang được ghi unknown trên NIR?
   - Khung ví dụ: **G07 D04.png**. Bản trước review ghi hai mắt unknown nhưng tám điểm mắt đều chưa bật occluded/outside; bản Chi bật occluded cho tám điểm đó. Đây là bất đồng cờ điểm thực sự được ghi trong XML.
   - Cách xử lý hiện tại: hai bạn đã thống nhất dùng cờ occluded của bản Chi và giữ eye_left/eye_right=unknown trong bản v2. Muốn xin coach ví dụ chuẩn để áp dụng nhất quán ở những khung tiếp theo. Không suy nguyên nhân phản xạ hay vật che chỉ từ cờ trong file nhãn.
2. **Quy ước xác định hướng nôi:** Với infant_seat.facing, rear/front được xác định theo hướng nhìn giả định của em bé hay theo bộ phận hình học nào của ghế? Có hình minh họa chuẩn cho các góc camera khác nhau, và xử lý thế nào khi chưa xác định được hướng trong schema không có unknown?
   - Khung ví dụ: **G07 S02_rgb.png**. Box infant_seat trong bản em có facing=rear, còn box tương ứng của Chi có facing=front; đây là bất đồng thuộc tính thực sự trong lượt diff.
   - Cách xử lý hiện tại: chưa áp dụng thay đổi facing trong lượt sửa cảnh báo, giữ rear trong bản v2 và ghi câu hỏi để xin coach tiêu chí. Không ghi là hướng đã được coach xác nhận, không tự thêm giá trị unknown ngoài schema.
