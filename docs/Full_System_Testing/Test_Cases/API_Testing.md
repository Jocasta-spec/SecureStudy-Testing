# Tài liệu Kiểm thử API

## Tổng quan
Tài liệu này chứa các trường hợp kiểm thử cho API SecureInsure, tập trung vào các lỗ hổng bảo mật như CSRF, SQL Injection. Các kiểm thử được thực hiện bằng Postman và OWASP ZAP.

## Danh sách Trường hợp Kiểm thử

### 1. Trường hợp Kiểm thử Chức năng và Bảo mật API (Postman & OWASP ZAP)
| ID              | Mô tả                                | Các bước                                                             | Dữ liệu kiểm thử                      | Kết quả mong đợi                           | Kết quả thực tế                           | Đạt/Thất bại |
|-----------------|--------------------------------------|----------------------------------------------------------------------|---------------------------------------|--------------------------------------------|--------------------------------------------|-------------|
| TC_API_Secu_01  | Kiểm tra CSRF token trên /add        | 1. Gửi POST request tới http://localhost/API_Secu/add không kèm CSRF token bằng Postman.<br>2. Kiểm tra response.<br>3. Xác minh với OWASP ZAP Active Scan. | Email: testuser1@gmail.com           | Response: "403 Forbidden - Thiếu CSRF token" | Response: "403 Forbidden - Thiếu CSRF token" | Đạt      |
| TC_API_Secu_02  | POST /add với CSRF token hợp lệ      | 1. Gửi POST request tới http://localhost/API_Secu/add với CSRF token hợp lệ bằng Postman.<br>2. Kiểm tra response.<br>3. Xác minh không có lỗi CSRF với OWASP ZAP. | Email: testuser1@gmail.com<br>CSRF: valid_token | Response: "Thêm người dùng thành công"     | Response: "Thêm người dùng thành công"     | Đạt      |
| TC_API_Secu_03  | Chống SQL Injection trên /AdminUpdate| 1. Gửi POST request tới http://localhost/API_Secu/AdminUpdate với dữ liệu SQL Injection bằng Postman.<br>2. Kiểm tra response.<br>3. Chạy OWASP ZAP Active Scan để xác nhận không có lỗ hổng. | Role: "' OR '1'='1"                  | Response: "Cập nhật thành công" (không bị khai thác) | Response: "Cập nhật thành công" (không bị khai thác) | Đạt      |

### 2. Kiểm thử bằng OWASP ZAP

#### Quy trình kiểm thử
- **Mục tiêu**: Kiểm tra bảo mật các endpoint của API (/API_Secu) để phát hiện các lỗ hổng tiềm ẩn.
- **Công cụ**: OWASP ZAP kết hợp với Postman.
- **Các bước thực hiện**:
  1. Cấu hình Postman sử dụng proxy của OWASP ZAP:
     - Trong Postman: **Cài đặt** > **Proxy** > Đặt proxy là `localhost` và port `8081`.
     - Đảm bảo ZAP đang chạy và lắng nghe trên port `8081`.
  2. Chạy tất cả các endpoint trong Postman:
     - Gửi các request GET, POST với dữ liệu mẫu (VD: email, role).
     - ZAP tự động ghi nhận các request và response.
  3. Thực hiện Spider:
     - Trong ZAP, nhấp chuột phải vào site `http://localhost/API_Secu` > **Tấn công** > **Spider** > **Bắt đầu Quét** để khám phá các liên kết và tài nguyên.
  4. Thực hiện Active Scan:
     - Nhấp chuột phải vào `http://localhost/API_Secu` > **Tấn công** > **Active Scan** > **Bắt đầu Quét** để kiểm tra các lỗ hổng bảo mật.
  5. Ghi lại kết quả:
     - Kiểm tra tab **Cảnh báo** để liệt kê các lỗi phát hiện (VD: SQL Injection, Directory Browsing).
     - Chụp ảnh màn hình các lỗi và lưu vào thư mục `Screenshots/OWASP_Screenshots/`.

## Ghi chú
- **Công cụ sử dụng**: Postman cho kiểm thử chức năng API, OWASP ZAP (2.16.1) cho quét bảo mật.
- **Môi trường**: Localhost (XAMPP, MySQL), kiểm thử vào tháng 10 năm 2025.
- **Các sửa chữa đã thực hiện**: Xác thực CSRF token, sử dụng prepared statements.
- **Ảnh chụp màn hình**: [OWASP ZAP](docs/Screenshots/OWASP_Screenshots/zap_csrf_alert.png)
