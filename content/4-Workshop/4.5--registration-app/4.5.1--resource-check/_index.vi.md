---
title : "Kiểm tra hạ tầng cổng đăng ký"
date : 2026-05-02
weight : 1
chapter : false
pre : " <b> 4.5.1 </b> "
---

## 4.4.1 Kiểm tra tài nguyên

### Mục tiêu

Kiểm tra App Đăng ký và App Truy vấn và Phân tích đã được cấu hình phù hợp nhằm đảm bảo hệ thống được cấu hình chính xác trước khi thực hiện kiểm thử.

### Kiểm tra các VPC đã tạo

Xác nhận rằng các VPC cho App Đăng ký, App Truy vấn và Phân tích đã được khởi tạo như sau:

![vpcs-check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/001_vpc_check.png)

### Kiểm tra các subnet đã tạo

Xác nhận rằng subnet tương ứng với các VPC đã được tạo:

![subnets-check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/002_subnet_check.png)

### Kiểm tra các route table đã tạo

Xác nhận rằng route table tương ứng với các subnets đã được tạo:

![route table check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/003_route_table.png)

### Kiểm tra các internet gateway đã tạo

Xác nhận rằng internet gateway tương ứng với các VPC đã được tạo:

![internet gateway check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/004_Internet_gateway.png)

### Kiểm tra các security group đã tạo

Xác nhận rằng security group tương ứng với các VPC đã được tạo:

![security group check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/005_security_group.png)

### Kiểm tra app đăng ký (Amazon ECS) đã tạo

Xác nhận rằng app đăng ký đã được tạo:

![app register check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/006_app_regist.png)

### Mô tả

Hệ thống đã thiết lập thành công các VPC và app đăng ký đã sẵn sàng  để nhận yêu cầu đăng ký app.
