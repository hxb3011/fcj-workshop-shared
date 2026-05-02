---
title: "processor-test"
date: 2024-01-01
weight: 3
chapter: false
pre: "<b>4.3 </b>"
---

## 4.3.2 Processor Test

### Mục tiêu

Kiểm tra luồng xử lý dữ liệu từ SQS đến Lambda Processor.

---

### Dữ liệu đầu vào

Dữ liệu test được mô phỏng dưới dạng các message log từ SQS, bao gồm các thông tin như `appId`, `level`, `message` và `timestamp`.

---

### Các bước thực hiện

Sau khi cấu hình xong các tài nguyên, tiến hành tạo test event để mô phỏng dữ liệu đầu vào từ SQS.

1. Tạo test event với tên **TextSendingMessage** và nhập dữ liệu vào phần *Event JSON*

![Create event](/static/images/4-Workshop/4.3.2--processor-test/create-event.png)  
*Hình 4.3.2-1: Tạo test event cho Lambda Processor.*

Dán json vào Event Json

![Create event](/static/images/4-Workshop/4.3.2--processor-test/add-json1.png)  
![Create event](/static/images/4-Workshop/4.3.2--processor-test/add-json2.png)  
*Hình 4.3.2-2: Dán Json vào event json.*

2. Thực thi Lambda để xử lý dữ liệu

![Lambda run](/static/images/4-Workshop/4.3.2--processor-test/lambda-run.png)  
*Hình 4.3.2-3: Lambda Processor được kích hoạt.*

---

3. Kiểm tra kết quả xử lý

- Dữ liệu log được lưu vào S3
Kết quả kiểm tra trên S3 cho thấy dữ liệu log đã được lưu trữ thành công sau khi Lambda xử lý.

![S3 result](/static/images/4-Workshop/4.3.2--processor-test/s3_1.png)  
![S3 result](/static/images/4-Workshop/4.3.2--processor-test/s3_2.png)  
*Hình 4.3.2-4: Log được lưu trữ trên S3.*

- Email thông báo được gửi thành công

![Email result](/static/images/4-Workshop/4.3.2--processor-test/email.png)  
*Hình 4.3.2-5: Email thông báo sau xử lý.*

---

### Mô tả luồng hoạt động

- Message được gửi vào SQS  
- Lambda Processor được kích hoạt  
- Dữ liệu được xử lý và:
  - Lưu vào S3  
  - Lưu vào DynamoDB  
  - Gửi thông báo qua SNS  

---

### Kết luận

Hệ thống xử lý log hoạt động chính xác, đảm bảo dữ liệu được lưu trữ và thông báo được gửi đầy đủ.
