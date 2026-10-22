# 鈴Rin ✧ Suzu鈴 — Premium Motion Edition

## Chạy website
1. Giải nén ZIP.
2. Mở `index.html` bằng Chrome hoặc Microsoft Edge.
3. Website chạy trực tiếp trong trình duyệt, không cần cài đặt hoặc chạy file `.exe`.

## Hiệu ứng nâng cấp
- Nền cực quang tím chuyển động chậm.
- Cánh hoa/đốm sáng trôi qua màn hình.
- Ánh sáng dịu tương tác theo vị trí con trỏ.
- Intro xuất hiện mượt và các mục hiện dần khi cuộn.
- Thẻ kỷ niệm nghiêng 3D nhẹ khi rê chuột (máy tính).
- Nút có ánh sáng lướt qua, hover có chiều sâu.
- Tôn trọng cài đặt giảm chuyển động của hệ điều hành; có thể dùng nút ✦ trên giao diện để bật/tắt hiệu ứng.

### Chuyển cảnh (View Transitions)
- Màn hình mở đầu (intro curtain) khi vào trang lần đầu trong phiên làm việc.
- Thanh tiến trình cuộn mỏng ở đầu trang.
- Thẻ kỷ niệm "morph" mượt thành modal chi tiết khi mở (hiệu ứng shared-element, không phải bật/tắt đột ngột).
- Lưới kỷ niệm tự sắp xếp lại mượt mà (di chuyển + mờ dần) khi đổi bộ lọc cảm xúc, tìm kiếm, thêm/sửa/xoá hoặc khôi phục dữ liệu.
- Số liệu thống kê (kỷ niệm/hình ảnh/cảm xúc) đếm mượt thay vì nhảy số đột ngột.
- Các hiệu ứng chuyển cảnh dùng View Transitions API (Chrome/Edge); trên trình duyệt không hỗ trợ hoặc khi bật "giảm chuyển động", trang tự chuyển sang cập nhật tức thì, không bị lỗi hay giật.

## Trang quản trị (admin.html)
Mở `admin.html` (hoặc bấm biểu tượng ⚙ ở góc trên bên phải trang chính) để vào trang quản trị riêng, dùng chung dữ liệu với trang chính (cùng `localStorage`, cần mở cả hai từ cùng một nơi — ví dụ cùng host cùng domain, hoặc cùng mở trực tiếp bằng file trên máy).

- **Tổng quan**: số liệu nhanh (tổng kỷ niệm, ảnh, loại cảm xúc, dung lượng đã dùng, kỷ niệm gần nhất), biểu đồ kỷ niệm theo tháng và phân bố cảm xúc, danh sách 5 kỷ niệm mới nhất.
- **Kỷ niệm**: bảng quản lý toàn bộ dữ liệu — tìm kiếm, lọc theo cảm xúc, sắp xếp theo tên/ngày, sửa/xoá từng mục hoặc chọn nhiều mục để xoá hàng loạt.
- **Thống kê**: biểu đồ chi tiết hơn kèm bảng số liệu (cảm xúc phổ biến nhất, tháng nhiều kỷ niệm nhất, tỉ lệ có ảnh, độ dài câu chuyện trung bình).
- **Cài đặt**: chỉnh tên thương hiệu, khẩu hiệu, tiêu đề, mô tả, các trích dẫn và chọn 1 trong 4 bảng màu chủ đạo cho trang chính — không cần sửa code. Lưu xong, mở lại trang chính để thấy thay đổi.

## Nhiều ảnh cho một kỷ niệm
- Khi thêm/sửa kỷ niệm, nhấn vào ô hoặc kéo-thả để chọn **nhiều ảnh cùng lúc** (tối đa 12 ảnh/kỷ niệm, mỗi ảnh dưới 8 MB, JPG/PNG/WebP). Có thể chọn thêm nhiều lần, ảnh cũ không bị mất; xoá từng ảnh bằng nút "×" trên thumbnail. Ảnh đầu tiên là ảnh bìa hiển thị trên thẻ.
- Ảnh được nén/resize (tối đa 1600px) ngay trên trình duyệt trước khi lưu, để tiết kiệm dung lượng và tránh làm chậm trang.
- Mở chi tiết một kỷ niệm có nhiều ảnh sẽ hiện **gallery**: nút trước/sau, phím mũi tên trái/phải, vuốt trên điện thoại, và số thứ tự ảnh.
- Kỷ niệm có ảnh cũ (định dạng trước khi nâng cấp) vẫn hiển thị bình thường, không cần làm gì thêm.

## Dữ liệu & lưu trữ
Thông tin kỷ niệm (tên, ngày, cảm xúc, câu chuyện) lưu trong `localStorage` (khoá `rin-memory-garden-v1`). **Ảnh được lưu riêng trong IndexedDB** (kho dữ liệu lớn hơn nhiều so với localStorage) để tránh lỗi "hết bộ nhớ" khi có nhiều ảnh — mỗi kỷ niệm chỉ giữ tham chiếu đến ảnh, không nhúng trực tiếp ảnh vào localStorage nữa. Cài đặt giao diện lưu ở khoá `rin-memory-garden-settings-v1`.

Khi dùng chức năng **Sao lưu dữ liệu**, ảnh trong IndexedDB sẽ được đóng gói kèm vào file JSON xuất ra (tệp sẽ lớn hơn tương ứng với số ảnh), nên bản sao lưu luôn đầy đủ và có thể khôi phục trên máy/trình duyệt khác. Xóa dữ liệu trình duyệt (cả localStorage lẫn IndexedDB) có thể làm mất kỷ niệm chưa sao lưu.

## Lưu ý
Google Fonts cần kết nối Internet để tải font; các hiệu ứng và website cơ bản vẫn chạy cục bộ. Đây là website tĩnh, không có máy chủ/backend — trang quản trị cũng chạy hoàn toàn trên trình duyệt, không gửi dữ liệu đi đâu cả.
