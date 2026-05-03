---
title : "Kiểm thử truy vấn toàn diện"
date : 2026-05-02
weight : 3
chapter : false
pre : " <b> 4.5.3 </b> "
---

## 4.4.3 Kiểm tra thao tác đăng ký app

### Mục tiêu

Kiểm tra thao tác đăng nhập, truy vấn log ở app phân tích có hoạt động đúng như mong đợi hay không.

### Lấy địa chỉ của app phân tích

![get address](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/001_get_address.png)

### Thực hiện đăng nhập bằng api đăng nhập bằng Postman để lấy access token

![login](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/002_login.png)

### Thực hiện lấy logs gần nhất với Api tương ứng bằng Postman và nhận kết quả

![hot log](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/003_hot_log.png)

### Thực hiện lấy logs cũ với Api tương ứng bằng Postman

- Gọi api lấy log cũ.

![query](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/004_query.png)

- Kết quả nhận được.

![cold log](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/005_cold_log.jpg)

### Mô tả

Các thao tác đăng nhập, truy vấn log ở app phân tích hoạt động đúng như mong đợi.