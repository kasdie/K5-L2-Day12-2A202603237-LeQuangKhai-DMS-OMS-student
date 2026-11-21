# Tự đánh giá — Lê Quang Khải · G07

## Tổng kết thực hiện

Em thực hiện bài lab DMS/OMS với bộ ảnh G07 gồm 22 khung hình: 16 ảnh OMS thuộc 8 cặp RGB–IR mô phỏng và 6 ảnh tài xế NIR thật. Em áp dụng Guideline Cabin v1.0 để kiểm tra loại đối tượng, vị trí ghế theo xe, trạng thái mặt–mắt và các điểm face13.

Em đối chiếu bài với Hoàng Kim Chi bằng công cụ cabin_check diff. Kết quả có 140 dòng bất đồng. Sau khi trao đổi, hai bạn thống nhất sửa 21 trường liên quan trạng thái mắt và cờ điểm mắt theo bản Chi. Ngoài ra, ba thuộc tính vị trí ghế của đồ vật được sửa theo quy ước hàng ghế sau.

Ở lần kiểm sau review với Chi, bản v2 có đủ 22 ảnh và đạt 0 lỗi, 0 cảnh báo. Sau đó em tiếp tục chỉnh sửa và lưu trên CVAT theo góp ý của mentor. Bản export_final_v2.zip hiện tại đã được cập nhật từ lần lưu mới nhất, có thay đổi ở 21/22 ảnh và vẫn đủ 22 tag frame_meta.

Kiểm tra bản cập nhật theo mentor hiện báo 4 lỗi occupied=yes ở child_seat của S01_ir, S01_rgb, S08_ir và S08_rgb vì schema Cabin v1.0 chỉ cho no/unknown; không có WARN. Học viên đã xác nhận mentor yêu cầu giữ occupied=yes ở bốn khung này. Đây là ngoại lệ so với schema Cabin v1.0; giữ nguyên bốn ERROR trong log để thể hiện đúng kết quả kiểm tra. Các nhãn mới được giữ nguyên, không tự đổi chỉ để hết lỗi kiểm tra. Kết quả script xác nhận các điều kiện mà script kiểm; chất lượng nhãn vẫn cần được đánh giá theo ảnh và guideline.

## 1. Tự rà soát 4 cảnh

Các sửa đổi dưới đây đã được ghi nhận trong lượt review trước góp ý mentor. Bản nhãn mới nhất đã tiếp tục được cập nhật sau lượt này. Bảng thể hiện lịch sử sửa của lượt review; bản xuất sau góp ý mentor được kiểm tra riêng trong check_final_v2.txt.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S02_rgb | object | Sai thuộc tính ghế | Đổi seat=driver thành rear_left theo quy ước ghế và vị trí đối tượng. | Có, trong bản v2 |
| S03_ir | Hai object | Sai thuộc tính ghế | Đổi seat=driver thành rear_middle và rear_right tương ứng. | Có, trong bản v2 |
| D04 | Các điểm mắt face13 | flag | Giữ hai mắt unknown; cập nhật cờ occluded của các điểm mắt theo kết quả review với Chi. | Có, trong bản v2 |
| D06 | Các điểm mắt phải | flag | Giữ mắt phải unknown; cập nhật cờ outside của bốn điểm mắt phải theo kết quả review với Chi. | Có, trong bản v2 |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Một số thuộc tính chưa được kiểm đồng bộ với điểm mặt; một số đồ vật OMS còn mang giá trị ghế mặc định driver.

Vì sao: Bản trước review còn các trường mặc định chưa được cập nhật đầy đủ. Trạng thái mắt unknown chưa được đối chiếu với mức quan sát được của từng điểm mắt; trường seat của một số box object chưa được chuyển về ghế sau phù hợp.

Lần sau tránh bằng cách: Kiểm theo thứ tự loại đối tượng → vị trí box → thuộc tính → cờ điểm → lưu. Với OMS, xác định ghế theo xe trước khi chọn seat. Với DMS, kiểm riêng từng mắt và từng điểm bị che; không suy rằng một điểm nhìn thấy được chỉ vì đã có tọa độ.

## 3. Ghi chú về disagreement_log

Ở D04, bản trước review của em ghi trạng thái mắt unknown nhưng các điểm mắt chưa được đánh dấu che khuất. Sau khi trao đổi, hai bạn thống nhất dùng cờ điểm mắt theo bản Chi và đã cập nhật trong bản v2. Em học được rằng trạng thái mắt và mức quan sát được của các điểm phải được kiểm cùng nhau; có tọa độ điểm không có nghĩa là điểm đó nhìn thấy rõ.

disagreement_log.csv đã ghi verdict=peer, quy tắc guideline và action cho 21 dòng thực sự được sửa theo thỏa thuận. Ba thay đổi seat của object được xử lý theo guideline, không sao chép các giá trị ghế trái/phải bị đảo trong bản đối chiếu.
