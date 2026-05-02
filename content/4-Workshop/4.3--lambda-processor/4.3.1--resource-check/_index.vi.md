## 4.3.1 Kiểm tra tài nguyên

### Mục tiêu

Trước khi tiến hành kiểm thử, cần đảm bảo tất cả các tài nguyên đã được tạo và cấu hình chính xác.

---

### Kiểm tra DynamoDB

Kiểm tra hệ thống cho thấy đã tạo thành công 3 bảng:
- fcaj-v2-AppClients  
- fcaj-v2-AppLogs  
- fcaj-v2-NotiTTL  

![DynamoDB tables](/static/images/4-Workshop/4.3.1--resource-check/dynamodb.png)
*Hình 4.3.1-1: Các bảng DynamoDB đã được tạo thành công.*

---

### Kiểm tra SQS

Kiểm tra cho thấy queue `fcaj-v2-log-queue` đã được tạo và sẵn sàng sử dụng.

![SQS queue](/static/images/4-Workshop/4.3.1--resource-check/sqs.png)
*Hình 4.3.1-2: SQS queue được khởi tạo thành công.*

---

### Kiểm tra Lambda

Kiểm tra Lambda function đã được deploy và đã kết nối với SQS để nhận message tự động.

![Lambda trigger](/static/images/4-Workshop/4.3.1--resource-check/lambda.png)
*Hình 4.3.1-3: Lambda Processor đã được kết nối với SQS.*

---

### Kết luận

Tất cả các tài nguyên DynamoDB, SQS và Lambda Processor đã được cấu hình đầy đủ và sẵn sàng cho bước kiểm thử tiếp theo.
