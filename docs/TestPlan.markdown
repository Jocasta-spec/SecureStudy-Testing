# Kế hoạch Kiểm thử cho Hệ thống SecureStudy

## 1. Giới thiệu
### 1.1 Mục đích
Kế hoạch kiểm thử này phác thảo chiến lược kiểm thử cho hệ thống SecureStudy, một hệ thống quản lý thi và kiểm tra trực tuyến, truy cập qua nền tảng web và desktop, sử dụng API PHP, Google OAuth và JWT để xác thực.

### 1.2 Phạm vi
- **Nền tảng Web:** 
  - **Quản trị viên:** Đăng nhập, xem/sửa thông tin cá nhân, quản lý người dùng/khóa học, đăng xuất.
  - **Giáo viên:** Đăng nhập, xem thông tin khóa học, xem thông tin bài kiểm tra, xem thông tin cá nhân, chỉnh sửa thông tin cá nhân, xem thông tin chi tiết bài làm học sinh, đăng xuất.
  - **Học sinh:** Đăng nhập, xem thông tin khóa học, xem thông tin cá nhân, chỉnh sửa thông tin cá nhân, xem thông tin chi tiết bài làm cá nhân, xem thông tin bài kiểm tra, đăng xuất.
- **Ứng dụng Desktop:** 
  - **Quản trị viên:** Đăng nhập, quản lý người dùng/khóa học, đăng xuất.
  - **Giáo viên:** Đăng nhập, tạo đề thi/kiểm tra, tạo bài thi/kiểm tra, xem chi tiết khóa học, xem danh sách học sinh, xem danh sách bài thi/kiểm tra, xem chi tiết bài làm học sinh, đăng xuất.
  - **Học sinh:** Đăng nhập, xem danh sách các lớp đang theo học, xem danh sach bài thi/kiểm tra cần làm, làm bài thi/kiểm tra, xem chi tiết bài thi/kiểm tra đã làm, đăng xuất.
- **API:** Các endpoint an toàn cho xác thực và quản lý dữ liệu.

### 1.3 Mục tiêu
- Xác thực các yêu cầu chức năng và phi chức năng.
- Đảm bảo tuân thủ bảo mật với Google OAuth và JWT.
- Xác nhận triển khai tốt các bảo mật cho các rủi ro CSRF, RBAC, SQLi.

## 2. Chiến lược Kiểm thử
### 2.1 Cấp độ Kiểm thử
- **Kiểm thử Đơn vị:** Các thành phần riêng lẻ (endpoint API, phần tử UI).
- **Kiểm thử Tích hợp:** Tích hợp giữa web, desktop và API.
- **Kiểm thử Hệ thống:** Chức năng toàn diện trên các nền tảng.
- **Kiểm thử Chấp nhận:** Xác nhận theo yêu cầu người dùng.

### 2.2 Loại Kiểm thử
- **Kiểm thử Chức năng:** Xác minh tất cả các use case (ví dụ: đăng nhập, quản lý người dùng).
- **Kiểm thử Bảo mật:** Kiểm tra OAuth, CSRF, bảo vệ SQL injection, token an toàn.
- **Kiểm thử Hiệu suất:** Đánh giá với 2 người dùng đồng thời trên localhost.
- **Kiểm thử Tương thích:** Xác nhận trên các trình duyệt và hệ điều hành đã chỉ định.

### 2.3 Môi trường Kiểm thử
- **Phần cứng:** Máy tính tiêu chuẩn với Windows 11.
- **Phần mềm:** XAMPP, PHP, Java (Maven), Chrome, Edge, Postman, OWASP ZAP.
- **Mạng:** Localhost (http://localhost/API_Secu).

## 3. Lịch trình Kiểm thử
| **Giai đoạn**          | **Ngày Bắt đầu** | **Ngày Kết thúc** | **Thời lượng** | **Người phụ trách**     |
|-------------------------|------------------|-------------------|---------------|-------------------------|
| Kiểm thử Đơn vị         | 30/08/2025       | 06/09/2025        | 1 tuần         | Võ Phạm Đăng Khoa       |
| Kiểm thử Tích hợp       | 07/09/2025       | 20/09/2025        | 2 tuần         | Nguyễn Thị Cẩm Tú       |
| Kiểm thử Hệ thống       | 21/09/2025       | 01/11/2025        | 6 tuần         | Cả hai                  |
| Kiểm thử Chấp nhận      | 02/11/2025       | 15/11/2025        | 2 tuần         | Cả hai                  |

## 4. Sản phẩm Kiểm thử
- Trường hợp kiểm thử (ví dụ: TC_LOGIN_APP_01, TC_ADMIN_WEB_ADDUSER_01).
- Kết quả và nhật ký kiểm thử.
- Báo cáo lỗi (ví dụ: BUG-TC_LOGIN_APP_01).
- Báo cáo tóm tắt kiểm thử cuối cùng.

## 5. Vai trò và Trách nhiệm
- **Nguyễn Thị Cẩm Tú:** Phát triển UI web, kiểm thử, tài liệu hóa.
- **Võ Phạm Đăng Khoa:** Phát triển API, kiểm thử bảo mật, tích hợp.

## 6. Rủi ro và Giải pháp
- **Rủi ro:** Vấn đề tích hợp giữa web và desktop.
  - **Giải pháp:** Kiểm thử tích hợp sớm.
- **Rủi ro:** Lỗ hổng bảo mật.
  - **Giải pháp:** Sử dụng OWASP ZAP để kiểm tra bảo mật.
- **Rủi ro:** Quy mô kiểm thử hạn chế.
  - **Giải pháp:** Lên kế hoạch kiểm thử trên server thực tế trong tương lai.

## 7. Phê duyệt
- **Được Phê duyệt Bởi:** Nguyễn Thị Cẩm Tú và Võ Phạm Đăng Khoa
- **Ngày:** 29/08/2025