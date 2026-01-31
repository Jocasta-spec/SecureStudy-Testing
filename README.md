# SecureStudy-Testing
**Dự án Kiểm thử Toàn diện & Kiểm thử Bảo mật**  
Hệ thống Thi Trắc nghiệm Trực tuyến Đa nền tảng (Web + Desktop Java + API)  
Đề tài: Nghiên cứu Bảo mật API và Ứng dụng trong Xây dựng Hệ thống Thi Trắc nghiệm Đa nền tảng  
GVHD: Thạc sĩ Võ Ngọc Tấn Phước

## Tổng quan
- **33 test cases kiểm thử chức năng hệ thống** (tập trung kiểm thử các chức năng cốt lõi của hệ thống SecureStudy, đảm bảo chức năng hoạt động đúng thiết 
kế, góp phần giúp đề tài có tính thực tiễn khi triển khai an toàn cho API trên hệ thống).
- **32 test cases kiểm thử bảo mật** (CSRF Protection, JWT & CRUD Security, RBAC, SQL Injection, Rate-limiting).
- Công cụ: Manual Testing, Thunder Client, Postman.

## Badges
![Postman](https://img.shields.io/badge/Postman-API_Tests-orange?style=flat&logo=postman)
![Thunder Client](https://img.shields.io/badge/Thunder_Client-API_Tests-yellow?style=flat&logo=thunder-client)
![Java](https://img.shields.io/badge/Java-Desktop_App-green?style=flat&logo=java)
![PHP](https://img.shields.io/badge/PHP-Web_&_API-blueviolet?style=flat&logo=php)
![MySQL](https://img.shields.io/badge/MySQL-brightgreen?style=flat&logo=mysql)
![Security](https://img.shields.io/badge/Security-success)
![Passed](https://img.shields.io/badge/Test_Status-100%25_Passed-success)

## Kết quả nổi bật

| Loại kiểm thử            | Số lượng | Trạng thái      | Ghi chú                                      |
|--------------------------|----------|------------------|----------------------------------------------|
| Kiểm thử toàn hệ thống   | 33       | 100% Passed      | Bao gồm Web, Desktop App, API                |
| Kiểm thử bảo mật chuyên sâu | 32       | 100% Passed      | Tập trung CSRF, SQLi, RBAC, JWT & CRUD Security, Rate-limiting |


## Link quan trọng
- [33 Test Cases Chức năng](docs/Full_System_Testing/Test_Cases/)
- [32 Test Cases Bảo mật](docs/Security_Testing/Test_Cases/Security_Testing.md)
- [Báo cáo kiểm thử chính thức](docs/Test_Reports/Final_Test_Report.md)
- [Postman Collection – Full](docs/Full_System_Testing/postman_collection/)
- [Postman Collection – Security Only](docs/Security_Testing/postman_collection/)

## Contributors
- Nhóm 2 sinh viên

## License
[MIT License](LICENSE) – Tự do sử dụng cho mục đích học tập, nghiên cứu và bảo vệ đồ án
