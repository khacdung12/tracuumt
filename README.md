# Tra cứu định lượng ma túy – Android v1.0

Ứng dụng Android nhẹ dạng WebView **dùng ngoại tuyến** cho Điều 249, 250 và 251 BLHS, đối chiếu Luật 86/2025/QH15. Giao diện tiếng Việt. Không cần tài khoản, không có quảng cáo, không xin quyền truy cập Internet, vị trí, tệp, máy ảnh hoặc danh bạ. Các đường liên kết pháp luật mở bằng trình duyệt bên ngoài (khi có mạng).

## Tạo APK bằng GitHub, không cần cài Android Studio

1. Giải nén ZIP này vào máy tính. Tạo một **repository GitHub** và tải lên toàn bộ các tệp/thư mục trong dự án, bao gồm thư mục `.github` (thư mục ẩn).
2. Mở tab **Actions** > **Build Android APK** > **Run workflow** (hoặc đẩy mã vào nhánh `main` để tự chạy).
3. Sau khi workflow chạy thành công, mở tác vụ đó, mục **Artifacts**, tải `TraCuuMaTuy-Android-APK`.
4. Giải nén artifact để lấy `app-debug.apk`. Chép APK vào điện thoại Android và chạm file để cài; nếu máy hỏi, cho phép cài ứng dụng từ nguồn này.

APK bản `debug` được ký tự động bằng khóa phát triển của môi trường CI; phù hợp dùng thử hoặc cài nội bộ, KHÔNG dùng như bản phát hành có chữ ký ổn định. Để cập nhật trên các lần build khác nhau mà không gỡ ứng dụng cũ, cần tạo APK release và ký bằng cùng khóa riêng được quản lý an toàn.

## Cách build trong Android Studio

1. Dùng Android Studio với JDK 17. Open thư mục dự án này.
2. Sync Gradle. Chọn Build > Build APK(s), file debug xuất tại `app/build/outputs/apk/debug/app-debug.apk`.

## Cảnh báo nghiệp vụ

- Kết quả chỉ đánh giá theo **định lượng một loại chất**, không tự động kết luận khởi tố hoặc xác định mức án.
- Chưa xử lý tổng định lượng tương đương khi có nhiều loại ma túy, tình tiết tăng nặng, tái phạm hoặc chuyển tiếp trước 01/7/2025.
- Mua bán Điều 251 không có ngưỡng tối thiểu cho khoản 1.
- Bản luật cần đối chiếu trước khi áp dụng vào vụ án cụ thể: https://xaydungchinhsach.chinhphu.vn/toan-van-luat-so-86-2025-qh15-sua-doi-bo-sung-mot-so-dieu-cua-bo-luat-hinh-su-119250723084702787.htm

## Nội dung kỹ thuật

- `app/src/main/assets/index.html`: giao diện, thuật toán, dữ liệu ngoại tuyến.
- `app/src/main/java/vn/tracuu/matuy/MainActivity.java`: màn hình Android WebView tối giản.
- `.github/workflows/build-apk.yml`: tạo APK qua GitHub Actions.

Không có SDK Android trong môi trường tạo dự án nên **APK chưa được biên dịch và kiểm thử trên thiết bị**. Cần chạy workflow hoặc build trên Android Studio trước khi sử dụng.
