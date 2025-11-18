# Báo cáo Thực hiện Kế hoạch Kiểm thử - Dự án SecureStudy-Testing

**Ngày**: 30 tháng 10 năm 2025  
**Tác giả**: Nhóm Dự án (2 Thành viên)  
**Người giám sát**: Thạc sĩ Võ Ngọc Tấn Phước  

## Tóm tắt

| Chỉ số          | Giá trị |
|-----------------|---------|
| Kế hoạch kiểm thử | 1       |
| Trường hợp kiểm thử | 34    |
| Đạt             | 28     |
| Thất bại        | 6      |

**Tiến độ thực hiện trường hợp kiểm thử**: 100% hoàn thành

## Chi tiết Trường hợp Kiểm thử

### 5.1. Yêu cầu tài nguyên kiểm thử
- **Phần cứng**: Máy tính có internet.
- **Phần mềm**: XAMPP, Chrome, Postman, Java JDK, Maven, OWASP ZAP.

### 5.2. Danh sách các tình huống kiểm thử

| ID trường hợp thử nghiệm | Mô tả trường hợp thử nghiệm                     | Trạng thái (P/F) | Số lỗi |
|--------------------------|------------------------------------------------|--------------------|--------|
| TC_CUSTOMER_WEB_LOGIN_01  | Đăng nhập thành công với tài khoản Customer qua /login | P                 | 0      |
| TC_CUSTOMER_WEB_LOGIN_02  | Đăng nhập thất bại với tài khoản Customer bị chặn qua /login | P                 | 0      |
| TC_ADMIN_WEB_ADDUSER_01   | Thêm Admin mới thành công                      | P                 | 0      |
| TC_ADMIN_WEB_ADDUSER_02   | Thêm Admin với email đã tồn tại                | P                 | 0      |
| TC_ADMIN_WEB_EDITUSER_01  | Sửa thông tin Khách hàng thành công            | P                 | 0      |
| TC_ADMIN_WEB_DELETEUSER_01| Xóa Khách hàng thành công                     | P                 | 0      |
| TC_LOGIN_APP_01           | Đăng nhập qua App với user không tồn tại (Lần 1) | F                 | 1      |
| TC_LOGIN_APP_02           | Đăng nhập qua App với user không tồn tại (Lần 2) | P                 | 0      |
| TC_LOGIN_APP_03           | Đăng nhập qua App với user admin bị chặn (Lần 1) | F                 | 1      |
| TC_LOGIN_APP_04           | Đăng nhập qua App với user admin bị chặn (Lần 2) | P                 | 0      |
| TC_ROLE_APP_01            | Phân quyền truy cập TaskPanel (Lần 1)          | F                 | 1      |
| TC_ROLE_APP_02            | Phân quyền truy cập TaskPanel (Lần 2)          | F                 | 1      |
| TC_ROLE_APP_03            | Phân quyền truy cập TaskPanel (Lần 3)          | P                 | 0      |
| TC_GETUSER_APP_01         | Hiển thị danh sách người dùng trên TaskPanel (Lần 1) | F                 | 1      |
| TC_GETUSER_APP_02         | Hiển thị danh sách người dùng trên TaskPanel (Lần 2) | F                 | 1      |
| TC_GETUSER_APP_03         | Hiển thị danh sách người dùng trên TaskPanel (Lần 3) | P                 | 0      |
| TC_ADDUSER_APP_01         | Thêm người dùng mới trên TaskPanel (Lần 1)     | F                 | 1      |
| TC_ADDUSER_APP_02         | Thêm người dùng mới trên TaskPanel (Lần 2)     | F                 | 1      |
| TC_ADDUSER_APP_03         | Thêm người dùng mới trên TaskPanel (Lần 3)     | P                 | 0      |
| TC_ADDUSER_APP_04         | Thêm người dùng với email đã tồn tại (Lần 1)   | F                 | 1      |
| TC_ADDUSER_APP_04         | Thêm người dùng với email đã tồn tại (Lần 2)   | P                 | 0      |
| TC_DELETEUSER_APP_01      | Xóa người dùng trên TaskPanel (Lần 1)          | F                 | 1      |
| TC_DELETEUSER_APP_02      | Xóa người dùng trên TaskPanel (Lần 2)          | F                 | 1      |
| TC_DELETEUSER_APP_03      | Xóa người dùng trên TaskPanel (Lần 3)          | P                 | 0      |
| TC_UPDATEUSER_APP_01      | Sửa thông tin người dùng trên TaskPanel (Lần 1)| F                 | 1      |
| TC_UPDATEUSER_APP_02      | Sửa thông tin người dùng trên TaskPanel (Lần 2)| F                 | 1      |
| TC_UPDATEUSER_APP_03      | Sửa thông tin người dùng trên TaskPanel (Lần 3)| P                 | 0      |
| TC_LOGOUT_APP_01          | Đăng xuất và quay lại màn hình đăng nhập (Lần 1)| F                 | 1      |
| TC_LOGOUT_APP_02          | Đăng xuất và quay lại màn hình đăng nhập (Lần 2)| F                 | 1      |
| TC_LOGOUT_APP_03          | Đăng xuất và quay lại màn hình đăng nhập (Lần 3)| P                 | 0      |
| TC_Token_Stored_01        | Kiểm tra token trong thư mục tokens được mã hóa| P                 | 0      |
| TC_API_Secu_01            | Kiểm tra yêu cầu CSRF token trên endpoint /add | P                 | 0      |
| TC_API_Secu_02            | Kiểm tra POST request tới /add với CSRF token hợp lệ | P                 | 0      |
| TC_API_Secu_03            | Kiểm tra chống SQL Injection trên /AdminUpdate | P                 | 0      |
| TC_API_SECURITY_ZAP_01            | Kiểm tra bảo mật endpoint API (/API_Secu) bằng OWASP ZAP qua proxy Postman | P                 | 4      |
### 5.3. Kiểm thử bằng OWASP ZAP
**Các lỗi phát hiện**: 

**1. Lộ thông tin file .env**: [Kiểm tra scan](../Screenshots/OWASP_Screenshots/env_file_data_exposed.png)
- **Mức độ rủi ro**: Cao
- **Giải thích**: File `.env` chứa thông tin nhạy cảm như `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, thông tin kết nối database (`DBHOST`, `DBUSER`, `DBPASS`, `DBNAME`), và `ENCRYPTION_KEY`
- **Hậu quả**: 
    - Hacker có thể dùng `GOOGLE_CLIENT_ID` và `GOOGLE_CLIENT_SECRET` để giả mạo request Google API, truy cập trái phép dữ liệu người dùng hoặc thực hiện hành vi độc hại.
    - Thông tin database cho phép hacker kết nối trực tiếp, thực hiện SQL Injection, và thao túng dữ liệu.
    - Khóa mã hóa `HashKeyPass` bị lộ có thể dẫn đến giải mã token hoặc tạo token giả mạo, vi phạm bảo mật API.
    - Nguy cơ tấn công chuỗi cung ứng, ảnh hưởng đến server XAMPP và dịch vụ liên kết.

**2. Tấn công SQL Injection**: [Kiểm tra scan](../Screenshots/OWASP_Screenshots/SQL_Injection_endpoint_add.png)
- **Mức độ rủi ro**: Cao
- **Giải thích**: Phát hiện lỗ hổng SQL Injection trên endpoint `http://localhost/API_Secu/add`.  
- **Chi tiết**:
    - Test với payload `OR '1'='1'` không thành công, cho thấy một mức độ bảo vệ cơ bản.
    - Tuy nhiên, payload `139b88ec1c41cb5964e5d84f91121bf01ccc326f3df5bc3eb5b378f33dde08f6 AND 1=1 --` (một dạng SQL Injection phức tạp) đã vượt qua kiểm tra, có khả năng thực thi truy vấn trái phép.

**3. Application Error Disclosure**: [Kiểm tra scan](../Screenshots/OWASP_Screenshots/Application_Error_Disclosure_endpoint_update.png)
- **Mức độ rủi ro**: Trung bình
- **Liên quan đến API**: Nếu API trả về lỗi chi tiết (VD: stack trace, mã lỗi nội bộ) khi xử lý request (như /AdminUpdate), hacker có thể khai thác để tìm lỗ hổng logic hoặc SQL Injection.

**4. Directory Browsing**: [Kiểm tra scan](../Screenshots/OWASP_Screenshots/Exposing_API_structure.png)
- **Mức độ rủi ro**: Trung bình
- **Mô tả**: `<title>Index of /API_Secu</title>` – Điều này cho thấy khi truy cập /API_Secu/, server trả về danh sách các file/thư mục (VD: config/, vendor/) thay vì một trang hoặc API response.
- **Ảnh hưởng**: Server (Apache 2) cho phép duyệt thư mục, có thể lộ file nhạy cảm (VD: config database, source code). Hacker có thể:
    - Xem danh sách file (VD: config.php chứa thông tin database).
    - Tải file nhạy cảm, từ đó tấn công database hoặc endpoint API (VD: /AdminUpdate).
- **Nguy cơ**: Lộ cấu trúc API, file config (username/password database), hoặc mã nguồn, làm tăng nguy cơ tấn công SQL Injection hoặc lấy token.

## Kết luận
Tất cả 34 trường hợp kiểm thử đã được thực hiện. Trong đó, 19 trường hợp đạt, 15 trường hợp thất bại. Tuy nhiên, các trường hợp lỗi sau khi được chỉnh sửa và re-test, đã cho kết quả khả quan và được khắc phục. 
