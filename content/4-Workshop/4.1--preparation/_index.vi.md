---
title : "Chuẩn bị môi trường"
date : 2026-05-02
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

Trong phần này, ta sẽ thực hiện chuẩn bị các công cụ quản trị cần thiết và tiến hành khởi tạo hạ tầng tự động trên AWS bằng Terraform để phục vụ cho dự án Log Management.

### 1. Chuẩn bị công cụ quản trị

Trước khi bắt đầu, hãy đảm bảo máy tính cá nhân đã được cài đặt và cấu hình đầy đủ các công cụ sau:

*   **AWS CLI:** Đã cấu hình bộ Access Key/Secret Key có quyền **AdministratorAccess**.
*   **Terraform:** Phiên bản từ 1.0 trở lên để thực thi mã nguồn hạ tầng.

### 2. Khởi tạo hạ tầng với Terraform

Hạ tầng mạng và lưu trữ cốt lõi sẽ được triển khai tự động giúp đảm bảo tính nhất quán.

1. Di chuyển vào thư mục chứa mã nguồn của Workshop.
2. Thực hiện các lệnh sau để khởi tạo:

```bash
# Khởi tạo môi trường Terraform
terraform init

# Kiểm tra các tài nguyên dự kiến khởi tạo
terraform plan

# Thực thi triển khai hạ tầng lên AWS
terraform apply -auto-approve
```

{{% notice info %}}
Quá trình khởi tạo hạ tầng có thể mất vài phút để AWS thiết lập đầy đủ các tài nguyên Networking.
{{% /notice %}}

### 3. Kiểm tra tài nguyên hạ tầng

Sau khi Terraform hoàn tất, ta cần truy cập **AWS Management Console** để xác minh các tài nguyên nền tảng đã được khởi tạo thành công.

#### 3.1. Hệ thống mạng ảo (VPC)

Xác nhận rằng các VPC sau đã được tạo:

![vpc-check](/images/4-Workshop/4.1--preparation/vpc-check.png)

#### 3.2. Hệ thống lưu trữ (Amazon S3)

Dữ liệu log sau xử lý sẽ được lưu trữ tại S3. Hãy đảm bảo các bucket sau tồn tại:

![s3-check](/images/4-Workshop/4.1--preparation/s3-check.png)

#### 3.3. Danh mục dữ liệu (AWS Glue)

Để Athena có thể đọc được cấu trúc log trong S3, một Crawler đã được thiết lập sẵn:
*   **Tên crawler:** `fcaj-v2-log-crawler`.
*   **Trạng thái:** Phải ở trạng thái **READY**.

![glue-check](/images/4-Workshop/4.1--preparation/glue-check.png)

Chúc mừng bạn đã hoàn thành bước thiết lập hạ tầng nền tảng. Trong bước tiếp theo, chúng ta sẽ cấu hình dịch vụ thông báo SNS.