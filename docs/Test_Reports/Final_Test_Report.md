# BÁO CÁO KIỂM THỬ TOÀN DIỆN & BẢO MẬT  
**DỰ ÁN SECURESTUDY – HỆ THỐNG QUẢN LÝ THI VÀ KIỂM TRA TRẮC NGHIỆM TRỰC TUYẾN ĐA NỀN TẢNG**  
**Đề tài:** Nghiên cứu Bảo mật API và Ứng dụng trong Xây dựng Hệ thống Thi Trắc nghiệm Đa nền tảng  
**GVHD:** Thạc sĩ Võ Ngọc Tấn Phước  
**Nhóm thực hiện:** 2 sinh viên  
**Ngày hoàn thành:** 14/11/2025  

## 1. Tóm tắt kết quả kiểm thử

| Chỉ tiêu                        | Số lượng | Trạng thái          |
|----------------------------------|----------|----------------------|
| Tổng test cases kiểm thử chức năng | 34       | 100% Passed (sau fix) |
| Test cases bảo mật chuyên sâu    | 23       | 100% Passed          |
| Tổng cộng                        | 57       | 100% Passed          |
| Lỗ hổng Critical/High còn lại    | 0        | Clean                |

**Tiến độ:** 100% hoàn thành – Sẵn sàng bảo vệ & triển khai

## 2. Giai đoạn 1 – Kiểm thử chức năng toàn hệ thống (34 test cases)

**Thời gian thực hiện:** 30/08/2025 → 31/10/2025  
**Kết quả ban đầu:** 19 Passed – 15 Failed  
**Sau khi fix & retest lần 2–3:** Tất cả 34 test cases đạt Passed 100%

## 3. Giai đoạn 2 – Kiểm thử bảo mật chuyên sâu (23 test cases)

**Thời gian thực hiện:** 1/11/2025 → 14/11/2025  
**Công cụ:** Postman, Thunder Client (Lightweight Rest API Client for VS Code)
**Kết quả:** 23/23 Passed (100%)

### Phân loại test cases bảo mật

| Nhóm bảo mật                     | Số lượng | Kết quả |
|----------------------------------|----------|---------|
| Authentication & Authorization   | 5        | Passed  |
| CSRF Protection                  | 3        | Passed  |
| SQL Injection (4 loại payload)   | 4        | Passed  |
| RBAC & IDOR                      | 3        | Passed  |
| CRUD + Input Validation          | 8        | Passed  |
| **Tổng**                         | **23**   | **100%** |

### Các biện pháp bảo mật đã triển khai & xác nhận thành công

| Lỗ hổng                     | Biện pháp khắc phục đã áp dụng                                    | Xác nhận bằng test case |
|-----------------------------|--------------------------------------------------------------------|--------------------------|
| CSRF                        | Bắt buộc header `X-CSRF-Token` trên mọi POST/PUT/DELETE            | TC_API_01, TC_API_02     |
| SQL Injection               | 100% Prepared Statements + bind param (cả single & multi-row)     | TC_SQLi-V1 → TC_SQLi-Spec|
| Weak Authentication         | Google OAuth2 + JWT + kiểm tra status Active/Blocked               | TC_WEB_01, TC_WEB_02     |
| Insecure Token Storage      | Mã hóa Base64 + tự động xóa khi logout (Preferences + DB)          | TC_Token_01, TC_LOGOUT_03|
| Broken Access Control (RBAC)| Kiểm tra role ở cả client & server-side                            | TC_ROLE_03               |
| Insecure Direct Object References (IDOR) | Kiểm tra owner + role trước khi GET/UPDATE/DELETE          | TC_GET_03                |
| Duplicate Email             | UNIQUE constraint DB + kiểm tra trước insert                      | TC_ADD_04, TC_WEB_ADD_02 |

## 4. Kết luận & Đề xuất

1. **Tất cả 57 test cases (34 chức năng + 23 bảo mật)** đều đạt Passed 100%.
2. Hệ thống SecureStudy đã thực thi bảo mật cho các lỗ hổng:
   - CSRF
   - SQL Injection
   - Broken Authentication & Access Control
   - Insecure Token Storage
   - Information Disclosure (.env, directory browsing)
3. **Sẵn sàng triển khai thực tế** và bảo vệ đồ án.

**Trạng thái dự án:**  
**100% TEST CASES PASSED – ZERO CRITICAL VULNERABILITIES**  
**READY FOR DEFENSE & DEPLOYMENT**

**Người thực hiện:** Nhóm 2 sinh viên  
**Giảng viên hướng dẫn:** ThS. Võ Ngọc Tấn Phước
