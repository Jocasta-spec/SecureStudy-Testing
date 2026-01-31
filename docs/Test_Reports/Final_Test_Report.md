<img width="1206" height="88" alt="image" src="https://github.com/user-attachments/assets/70b760cd-baec-4896-be69-61efb1294414" /># BÁO CÁO KIỂM THỬ TOÀN DIỆN & BẢO MẬT  
**DỰ ÁN SECURESTUDY – HỆ THỐNG QUẢN LÝ THI VÀ KIỂM TRA TRẮC NGHIỆM TRỰC TUYẾN ĐA NỀN TẢNG**  
**Đề tài:** Nghiên cứu Bảo mật API và Ứng dụng trong Xây dựng Hệ thống Thi Trắc nghiệm Đa nền tảng  
**GVHD:** Thạc sĩ Võ Ngọc Tấn Phước  
**Nhóm thực hiện:** 2 sinh viên  
**Ngày hoàn thành:** 14/11/2025  

## 1. Tóm tắt kết quả kiểm thử

| Chỉ tiêu | Số lượng | Trạng thái |
|---------|----------|------------|
| Tổng test case kiểm thử chức năng | 33 | 100% Passed (sau khi khắc phục lỗi) |
| Test case bảo mật chuyên sâu | 32 | 100% Passed |
| Tổng cộng | 65 | 100% Passed |
| Lỗ hổng Critical/High còn lại | 0 | Clean |

**Tiến độ:** 100% hoàn thành – Sẵn sàng bảo vệ & triển khai

## 2. Giai đoạn 1 – Kiểm thử chức năng toàn hệ thống (33 test cases)

**Thời gian thực hiện:** 30/08/2025 → 31/10/2025  
**Kết quả ban đầu:** 19 Passed – 14 Failed  
**Sau khi fix & retest lần 2–3:** Tất cả 33 test cases đạt Passed 100%

## 3. Giai đoạn 2 – Kiểm thử bảo mật chuyên sâu (32 test cases)

**Thời gian thực hiện:** 1/11/2025 → 14/11/2025  
**Công cụ:** Postman, Thunder Client (Lightweight Rest API Client for VS Code)
**Kết quả:** 32/32 Passed (100%)

### Phân loại test cases bảo mật

| Nhóm bảo mật                     | Số lượng | Kết quả |
|----------------------------------|----------|---------|
| CSRF Protection                  | 6        | Passed  |
| JWT & CRUD Security              | 5        | Passed  |
| RBAC                             | 11       | Passed  |
| SQL Injection                    | 7        | Passed  |
| Rate-limiting                    | 3        | Passed  |
| **Tổng**                         | **32**   | **100%** |

### Các biện pháp bảo mật đã triển khai

| Lỗ hổng | Biện pháp khắc phục đã áp dụng |
|--------|--------------------------------|
| CSRF | Hiện thực cơ chế chống CSRF theo mô hình Double-Submit Token |
| SQL Injection | Prepared Statements, Type Binding, Error Handling & Logging, Column Filtering |
| Weak Authentication | Google OAuth2 + JWT + kiểm tra status Active/Blocked |
| Insecure Token Storage | Web: Lưu JWT trong cookie HttpOnly + SameSite (Lax).<br>Desktop: In Memory Only – lưu trong RAM, xóa khi logout hoặc thoát ứng dụng. |
| Broken Access Control (RBAC) | JWT Claims (‘role’ trong payload), áp dụng thống nhất cho Admin – Teacher – Student |

## 4. Kết luận & Đề xuất

1. **Tất cả 65 test cases (33 chức năng + 32 bảo mật)** đều đạt Passed 100%.
2. Hệ thống SecureStudy đã thực thi bảo mật cho các lỗ hổng:
   - CSRF
   - SQL Injection
   - Broken Authentication & Access Control
   - Insecure Token Storage
   - Rate-limiting
3. **Sẵn sàng triển khai thực tế** và bảo vệ đồ án.

**Trạng thái dự án:**  
**100% TEST CASES PASSED – ZERO CRITICAL VULNERABILITIES**  
**READY FOR DEFENSE & DEPLOYMENT**

**Người thực hiện:** Nhóm 2 sinh viên  
**Giảng viên hướng dẫn:** ThS. Võ Ngọc Tấn Phước
