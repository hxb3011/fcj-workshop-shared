---
title : "Kiểm thử thực tế cổng đăng ký"
date : 2026-05-02
weight : 2
chapter : false
pre : " <b> 4.5.2 </b> "
---

## 4.4.2 Kiểm tra thao tác đăng ký app

### Mục tiêu

Kiểm tra thao tác đăng ký app có hoạt động đúng như mong đợi hay không.

### Các bước thực hiện

Sau khi kiểm tra cấu hình hoàn tất, ta tiến hành đăng ký app theo các bước như sau:

1. Lấy địa chỉ của app đăng ký

![get address](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/001_get_address.png)

2. Dùng Postman gọi api lệnh đăng ký

![register app](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/002_register_app.png)

3. AWS sẽ gửi email xác nhận đến địa chỉ email mà ta đăng ký ở bước 2

![email confirm](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/003_email_confirm.png)

4. Xác nhận email đã đăng ký

![email subcribed](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/004_email_subcribed.png)

5. Xác nhận user mới đã tạo cho app được đăng ký

![user created](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/005_user_created.png)

6. Xác nhận user ứng với app đã cấp access key

![access key](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/006_access_key.png)

7. Xác nhận user ứng với app được cấp quyền đẩy log qua CloudWatch logs

![CloudWatch policy](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/007_cloud_watch_policy.png)

8. Xác nhận app đã tạo được lưu trong bảng AppClients trên DinamoDB

![database saved](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/008_database_saved.png)

### Mô tả

Thao tác đăng ký app hoạt động đúng như mong đợi.