# TEAM — Ngày 12

Mã bộ ảnh: **G07** · Hình thức: **cá nhân, có review chéo**.

Tên và MSSV dưới đây lấy từ tên repository; học viên kiểm lại trước khi nộp.

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Lê Quang Khải | 2A202603237 | Đã gán và cập nhật theo mentor; kiểm bản mới còn 4 ERROR/0 WARN, ngoại lệ occupied=yes theo mentor, học viên đã xác nhận | Hoàng Kim Chi | 21/140 dòng đã xử lý ở lượt review trước góp ý mentor |

Người dùng đã xác nhận tên bạn review là Hoàng Kim Chi và cung cấp annotations.xml. Đã chạy diff với export riêng task 45 trên 22 tên ảnh/kích thước khớp nhau. XML của Chi không ghi mã nhóm; hai bản đã được dùng cho lượt review G07 theo thông tin ghép cặp do học viên cung cấp.

Học viên đã báo hoàn thành gán/sửa và lưu trên task 45. Bản trước review có 0 ERROR, 15 WARN. Theo thông báo hai bạn thống nhất sửa theo Chi, đã áp dụng 21 thay đổi về mắt/cờ điểm mắt và sửa 3 seat=driver của object OMS theo quy ước ghế; ở giai đoạn đó bản v2 đạt 0 ERROR/0 WARN và giữ nguyên tọa độ.

Sau góp ý mentor, học viên tiếp tục sửa và Save. Đã xuất lại bản nhãn mới nhất: đủ 22 ảnh, có thay đổi ở 21 ảnh; kiểm hiện tại có 4 ERROR occupied=yes tại S01_ir, S01_rgb, S08_ir, S08_rgb và 0 WARN. Học viên đã xác nhận mentor yêu cầu giữ occupied=yes ở bốn khung này; giữ nguyên nhãn và ghi ngoại lệ thay vì sửa schema hoặc che kết quả kiểm tra. Bản v2 hiện tại là bản sau góp ý mentor; các số liệu 0 ERROR/0 WARN ở trên mô tả lần kiểm trước đó.

Ca chưa thống nhất và đã hỏi coach: **chưa ghi nhận**. Đã ghi verdict=peer và action cho 21 dòng đã sửa; 119 dòng diff khác chưa được áp dụng trong lượt sửa cảnh báo này. Trong lượt sửa cảnh báo ban đầu, không áp dụng seat trái/phải bị đảo hoặc occupied=yes của bản Chi vì không khớp guideline/schema; bản sau góp ý mentor hiện có occupied=yes như ghi ở trên và được học viên xác nhận là yêu cầu của mentor.

## Cá nhân

### LeQuangKhai-2A202603237

- Phần mình làm: Hoàn thành và rà soát bộ 22 ảnh G07; đối chiếu với Hoàng Kim Chi; thực hiện các sửa đổi đã thống nhất và kiểm tra lại bản export sau review.
- Điều mình học được: Ghế trái/phải phải gọi theo xe, còn mắt và tay trái/phải gọi theo người. Review chéo giúp tìm bất đồng, nhưng mỗi quyết định sửa vẫn cần dựa vào guideline. Trạng thái mắt và cờ điểm mặt cần được kiểm đồng bộ, không chỉ kiểm vị trí box.

## Nhật ký IR

Học viên đã cung cấp và xác nhận bốn quan sát cho S02_ir, S03_ir, D04 và D06. ir_log.csv đã ghi đúng hai nguồn IR_sim và real_IR, hiện tượng quan sát và đề xuất xử lý nhãn. Các đề xuất trong nhật ký không tự động thay đổi nhãn trên CVAT; riêng D06 vẫn đề nghị kiểm lại cách dùng outside cho bốn điểm mắt phải trước khi chốt.
