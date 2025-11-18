# BÁO CÁO KIỂM THỬ BẢO MẬT  
**SecureStudy – Online Examination System**  
**23 Test Cases Bảo mật – 100% Passed**

## 1. Thông tin chung
- **Số lượng test case thực hiện:** 23 test cases về bảo mật  
- **Phạm vi kiểm thử:** Web (PHP), Desktop App (Java Swing), API (PHP)  
- **Công cụ chính:** Postman Windowns 64-bit, OWASP ZAP 2.16.1
- **Môi trường:** Localhost (XAMPP 8.2 + JDK 25)  
- **Kết quả tổng thể:** **100% Passed**
## 2. Phân loại Test Cases

| Nhóm lỗ hổng                  | Số lượng | Tỷ lệ Pass | Ghi chú                                   |
|-------------------------------|----------|------------|-------------------------------------------|
| Authentication & Authorization| 5        | 100%       | OAuth2 + JWT + Block account + Logout     |
| CSRF Protection               | 3        | 100%       | X-CSRF-Token bắt buộc trên mọi state-changing request |
| SQL Injection                 | 4        | 100%       | Prepared Statements + bind param          |
| RBAC (Role-Based Access Control)| 3       | 100%       | Teacher không vào được Admin Dashboard    |
| CRUD + Input Validation       | 8        | 100%       | Duplicate email, IDOR, token storage      |
| **Tổng cộng**                 | **23**   | **100%**   |                                           |

## 3. Kết quả chi tiết (đã đạt Pass)

### Phần 1 – Authentication, CSRF, SQL Injection (12 test cases)

| Test ID          | Mô tả ngắn gọn                                           | Kết quả | Ghi chú |
|------------------|----------------------------------------------------------|---------|-------|
| TC_WEB_01        | Web – Đăng nhập OAuth → nhận JWT thành công              | Passed  | Dashboard Teacher hiển thị đúng |
| TC_WEB_02        | Tài khoản Teacher bị blocked → không vào được            | Passed  | Thông báo “Tài khoản bị chặn” |
| TC_APP_02        | App – User không tồn tại → báo lỗi rõ ràng               | Passed  | Redirect về trang hướng dẫn web |
| TC_APP_04        | Admin bị blocked → không vào TaskPanel                   | Passed  | Thông báo chi tiết + không leak token |
| TC_LOGOUT_03     | Đăng xuất → xóa hoàn toàn token (Preferences + DB)       | Passed  | Không đăng nhập lại được nếu không OAuth mới |
| TC_API_01        | POST /add thiếu CSRF token → 403 Forbidden               | Passed  | DB không thay đổi |
| TC_API_02        | POST /add có CSRF token hợp lệ → thành công              | Passed  | Bản ghi mới được tạo |
| TC_Token_01      | Token lưu trữ trong file được mã hóa Base64              | Passed  | Không đọc được bằng mắt thường |
| TC_SQLi-V1       | Payload `' OR '1'='1` → được lưu nguyên dạng chuỗi       | Passed  | Không bypass login hay query |
| TC_SQLi-Where    | Bypass WHERE clause bằng `--` → bị chặn                  | Passed  | Chỉ cập nhật đúng bản ghi hiện tại |
| TC_SQLi-Table    | DROP TABLE trong input → không thực thi                  | Passed  | DB không bị ảnh hưởng |
| TC_SQLi-Spec     | Multi-row insert với payload trong values → vẫn an toàn  | Passed  | Prepared statement bind từng giá trị riêng |

### Phần 2 – RBAC & CRUD / Input Validation (11 test cases)

| Test ID          | Mô tả ngắn gọn                                           | Kết quả | Ghi chú |
|------------------|----------------------------------------------------------|---------|-------|
| TC_ROLE_03       | Teacher không vào được Admin Dashboard                   | Passed  | Redirect + thông báo quyền |
| TC_ADD_01 / TC_ADD_03 | Chỉ admin mới thêm được user (App)                  | Passed  | Teacher thử → 403 |
| TC_GET_03        | Không lộ thông tin người dùng khác (IDOR)                | Passed  | Không lấy được danh sách ngoài role |
| TC_ADD_04        | Email trùng → báo lỗi, không thêm                        | Passed  | Cả Web và App đều chặn |
| TC_WEB_ADD_02    | Web – Email trùng → thông báo lỗi                        | Passed  | DB không bị duplicate |
| TC_UPDATE_03     | Sửa thông tin user thành công (App)                      | Passed  | JTable + DB đồng bộ |
| TC_DELETE_03     | Xóa user thành công (App)                                | Passed  | Soft delete hoặc hard delete đúng |
| TC_WEB_EDIT_01   | Web – Sửa thông tin người dùng thành công                | Passed  | Cập nhật tức thì |
| TC_WEB_DEL_01    | Web – Xóa người dùng thành công                          | Passed  | Danh sách refresh đúng |
| TC_GET_03 (lặp)  | Refresh danh sách không mất dữ liệu, không null          | Passed  | Ổn định sau nhiều lần refresh |


## 4. Các biện pháp bảo mật đã triển khai thành công
| Lỗ hổng          | Biện pháp khắc phục                                      | Trạng thái |
|------------------|-----------------------------------------------------------|------------|
| CSRF             | Bắt buộc header `X-CSRF-Token` trên mọi POST/PUT/DELETE   | Hoàn tất   |
| SQL Injection    | Sử dụng **Prepared Statements** + bind param 100%        | Hoàn tất   |
| Weak Auth        | Google OAuth2 + JWT + kiểm tra status (Active/Blocked)    | Hoàn tất   |
| Insecure Token Storage | Mã hóa Base64 + xóa token khi logout                | Hoàn tất   |
| Broken Access Control | Kiểm tra role ở cả client và server-side            | Hoàn tất   |
| Duplicate Email  | UNIQUE constraint + kiểm tra trước khi insert            | Hoàn tất   |

## 6. Kết luận
Sau 23 test case bảo mật và quá trình khắc phục liên tục:
- Hệ thống SecureStudy **đạt mức bảo mật như mong đợi**, sẵn sàng triển khai thực tế.
- Không phát hiện bất kỳ lỗ hổng Critical/High nào dựa trên các test cases đã tạo và thực thi.
- Đảm bảo an toàn dữ liệu đề thi, kết quả thi và thông tin người dùng.


**Trạng thái dự án:** **READY FOR DEPLOYMENT & DEFENSE**

**Ngày hoàn thành báo cáo:** 14/11/2025  
**Người thực hiện:** Nhóm 2  
**Giảng viên hướng dẫn:** ThS. Võ Ngọc Tấn Phước