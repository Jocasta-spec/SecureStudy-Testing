# SecureStudy-Testing
**Dự án Kiểm thử Toàn diện & Kiểm thử Bảo mật**  
Hệ thống Thi Trắc nghiệm Trực tuyến Đa nền tảng (Web + Desktop Java + API)  
Đề tài: Nghiên cứu Bảo mật API và Ứng dụng trong Xây dựng Hệ thống Thi Trắc nghiệm Đa nền tảng  
GVHD: Thạc sĩ Võ Ngọc Tấn Phước

## Tổng quan
- **34 test cases kiểm thử toàn hệ thống** (chức năng + giao diện + luồng nghiệp vụ)  
- **23 test cases kiểm thử bảo mật chuyên sâu** (Authentication, CSRF, SQL Injection, RBAC, Input Validation)  
- Công cụ: Postman, OWASP ZAP 2.16.1, Manual Testing  

## Badges
![Postman](https://img.shields.io/badge/Postman-34_Tests-orange?style=flat&logo=postman)
![OWASP ZAP](https://img.shields.io/badge/OWASP_ZAP-23_Security_Tests-blue?style=flat&logo=owasp)
![Java](https://img.shields.io/badge/Java-Desktop_App-green?style=flat&logo=java)
![PHP](https://img.shields.io/badge/PHP-Web_&_API-blueviolet?style=flat&logo=php)
![MySQL](https://img.shields.io/badge/MySQL-Prepared_Statements-brightgreen?style=flat&logo=mysql)
![Security](https://img.shields.io/badge/Security-CSFR_&_SQLi_Mitigated-success)
![Passed](https://img.shields.io/badge/Test_Status-100%25_Passed-success)

## Kết quả nổi bật

| Loại kiểm thử            | Số lượng | Trạng thái      | Ghi chú                                      |
|--------------------------|----------|------------------|----------------------------------------------|
| Kiểm thử toàn hệ thống   | 34       | 100% Passed      | Bao gồm Web, Desktop App, API                |
| Kiểm thử bảo mật chuyên sâu | 23       | 100% Passed      | Tập trung CSRF, SQLi, RBAC, Token, Input Val |

**Các lỗ hổng đã được khắc phục:**
- CSRF Protection bằng X-CSRF-Token bắt buộc
- SQL Injection → dùng Prepared Statements
- RBAC nghiêm ngặt: Student/Lecturer không vào được Admin Panel
- Token lưu trữ mã hóa Base64 + tự động xóa khi logout

## Link quan trọng
- [34 Test Cases – Toàn hệ thống](docs/Full_System_Testing/Test_Cases/)
- [23 Test Cases Bảo mật – Chi tiết chuẩn hóa](docs/Security_Testing/Test_Cases/Security_Testing.md)
- [Báo cáo kiểm thử chính thức](docs/Test_Reports/Final_Test_Report.pdf)
- [OWASP ZAP Report (Clean)](docs/Full_System_Testing/owasp_report/)
- [Postman Collection – Full](docs/Full_System_Testing/postman_collection/)
- [Postman Collection – Security Only](docs/Security_Testing/postman_collection/)

## Contributors
- Nhóm 2 sinh viên

## License
[MIT License](LICENSE) – Tự do sử dụng cho mục đích học tập, nghiên cứu và bảo vệ đồ án
