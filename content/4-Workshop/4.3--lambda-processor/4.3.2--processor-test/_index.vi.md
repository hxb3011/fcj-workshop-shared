---
title: "Processor Test"
date: 2026-05-02
weight: 2
chapter: false
pre: "<b> 4.3.2 </b>"
---

## 4.3.2 Kiểm thử Processor

### Mục tiêu

Xác thực luồng xử lý dữ liệu từ SQS đến Lambda Processor.

### Dữ liệu đầu vào

Dữ liệu kiểm thử được mô phỏng dưới dạng các log message từ SQS, bao gồm các trường như `appId`, `level`, `message` và `timestamp`.

### Các bước thực hiện

Sau khi cấu hình tất cả các tài nguyên cần thiết, tạo một test event để mô phỏng dữ liệu đầu vào từ SQS.

1. Tạo một test event tên **TextSendingMessage** và nhập dữ liệu vào phần *Event JSON*.

![Create event](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/create-event.png)  

Dán dữ liệu JSON vào phần Event JSON.

![Add JSON](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/add-json1.png)  
![Add JSON](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/add-json2.png)  

2. Thực thi Lambda function để xử lý dữ liệu.

![Lambda run](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/lambda-run.png)  

3. Xác minh kết quả xử lý

- Dữ liệu log được lưu vào S3.  
  Kết quả trên S3 xác nhận rằng dữ liệu log đã được lưu thành công sau khi xử lý.

![S3 result](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/s3_1.png)  
![S3 result](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/s3_2.png)  

- Thông báo email được gửi thành công.

![Email result](/images/4-Workshop/4.3--lambda-processor/4.3.2--processor-test/email.png)  


### Mô tả luồng xử lý

- Message được gửi đến SQS  
- Lambda Processor kéo message xử lí và xóa message đó trong sqs  
- Notification được gửi nếu như có log error
- Dữ liệu được xử lý và:
  - Lưu vào S3  
  - Lưu vào DynamoDB  
  - Gửi thông báo qua SNS  


### Kết luận

Hệ thống xử lý log hoạt động đúng, đảm bảo dữ liệu được xử lý, lưu trữ và gửi thông báo thành công.