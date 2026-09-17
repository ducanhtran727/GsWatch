# Đánh giá UI/UX và frontend GsWatch

Ngày: 17/09/2026. Phạm vi: landing page `index.html`, ảnh sản phẩm và luồng đặt hàng hiện có. Đánh giá dựa trên mã nguồn, ảnh thật và kiểm thử trình duyệt; không có dữ liệu analytics, phỏng vấn hay thử nghiệm với khách hàng thật.

## Kết luận

Trang có nhận diện đỏ–đen rõ và sẵn ảnh sản phẩm thực tế. Tuy nhiên, thông tin khuyến mãi chiếm màn hình đầu trong khi đồng hồ chưa xuất hiện rõ; phần đặt hàng thiếu tổng tiền và có thể xác nhận thành công sai. Ưu tiên sửa là giúp khách hiểu sản phẩm, biết số tiền phải trả và nhận đúng trạng thái gửi đơn.

## Các vấn đề và hướng chỉnh sửa

| Mức | Quan sát ở bản ban đầu | Hướng chỉnh sửa |
| --- | --- | --- |
| Cao | Hero cao 100vh, nền sân vận động, chưa có ảnh đồng hồ riêng | Đưa ảnh thật lên hero, làm rõ GA-2100 Custom, giá, quà tặng và hành động đặt hàng/xem ảnh |
| Cao | Giá gạch ngang 2.222.000đ và 2.500.000đ không nhất quán | Giữ giá bán 889.000đ; bỏ giá tham chiếu và mức giảm 60% chưa có cơ sở thống nhất |
| Cao | Popup chọn ngẫu nhiên tên người mua; countdown tự reset | Bỏ thông tin mô phỏng gây hiểu nhầm |
| Cao | Chọn 2/3 chiếc có nhãn giảm 5%/10% nhưng thiếu tổng | Hiển thị tạm tính, giảm giá, vận chuyển và tổng thanh toán trước khi gửi |
| Cao | Mọi phản hồi fetch đều đi vào nhánh báo thành công; Purchase cố định 889.000đ | Chỉ xác nhận trên phản hồi thành công rõ ràng; tracking theo tổng đơn tại lúc gửi |
| Cao | Thiếu xử lý gửi lặp, timeout và trạng thái chưa xác nhận | Khóa trong lúc gửi, giữ dữ liệu khi lỗi, thông báo nội tuyến và không tự động gửi lại |
| Vừa | Ảnh vuông bị crop trong khung cao 400px; mô tả alt lệch ảnh | Hiển thị trọn ảnh, sửa caption/alt, cho mở ảnh lớn |
| Vừa | Phần order gồm ba phần tử flex rời: lợi ích, giá, form | Gộp thông tin sản phẩm và giá thành một cột, form thành cột còn lại; xếp dọc trên mobile |
| Vừa | Select bỏ outline nhưng thiếu focus thay thế; form thiếu autocomplete | Bổ sung focus rõ, nhãn và lỗi tương ứng, autocomplete và kiểm tra số điện thoại |
| Vừa | Review Facebook là HTML tĩnh với thao tác không hoạt động, thời gian tương đối và badge | Giữ nội dung phản hồi được cung cấp, bỏ các dấu hiệu tương tác/xác thực không có tích hợp thật |
| Vừa | Chữ đỏ tối, tiêu đề viết hoa nhiều, thiếu reduced-motion | Tăng khả năng đọc, giảm nhiễu thị giác, hỗ trợ người dùng giảm chuyển động |

## Quy tắc giá áp dụng

Giữ giá cơ sở và tỷ lệ giảm đã có trong trang, không tự làm tròn sang bảng giá khác:

| Số lượng | Tạm tính | Giảm | Tổng |
| --- | --- | --- | --- |
| 1 | 889.000đ | 0đ | 889.000đ |
| 2 | 1.778.000đ | 88.900đ (5%) | 1.689.100đ |
| 3 | 2.667.000đ | 266.700đ (10%) | 2.400.300đ |

## Giới hạn cần đối chiếu

- Chưa có mã backend Google Apps Script. Cần đối chiếu phản hồi thực tế với quy tắc xác nhận JSON `result: "success"` hoặc `success: true`. Phản hồi không xác định không được xem là đặt hàng thành công.
- Kiểm thử phải dùng phản hồi mô phỏng, không gửi đơn và sự kiện chuyển đổi thật. Kết quả mock không chứng minh backend sản xuất đã lưu đơn.
- Thông số sản phẩm, chính sách bảo hành, nguồn phản hồi khách hàng và thông tin thương hiệu do nội dung hiện có cung cấp, chưa được xác minh độc lập. Không bổ sung khẳng định mới.
- Cửa hàng chưa cung cấp số điện thoại/kênh liên hệ trực tiếp trong mã hiện tại. Cần thông tin thật để hỗ trợ khách khi trạng thái đơn chưa xác nhận.
