---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Serverless Log Management & Analytics Pipeline
## Một giải pháp AWS Serverless hợp nhất cho xử lý log mở rộng

### 1. Tóm tắt điều hành

Serverless Log Management & Analytics Pipeline được thiết kế để cung cấp khả năng thu thập và phân tích log tập trung cho nhiều ứng dụng chạy trên AWS. Nó hỗ trợ các luồng log khối lượng lớn từ nhiều nguồn, với khả năng mở rộng để xử lý hàng triệu sự kiện mỗi ngày. Pipeline tận dụng các dịch vụ AWS Serverless để cung cấp phân loại real‑time, lưu trữ dài hạn tối ưu, và phân tích tiết kiệm chi phí. Kiểm soát truy cập được quản lý thông qua AWS Identity and Access Management (IAM), đảm bảo việc sử dụng an toàn cho các nhóm được chỉ định.

### 2. Tuyên bố vấn đề
*Vấn đề hiện tại*

Application logs bị phân tán trên nhiều servers, khiến việc giám sát và phân tích tập trung trở nên khó khăn. Sự phân mảnh này dẫn đến kém hiệu quả trong việc khắc phục sự cố, chậm trễ trong việc có insights, và thách thức trong việc duy trì độ tin cậy của hệ thống.

*Giải pháp*

Pipeline tận dụng AWS CloudWatch Agent để thu thập logs và chuyển tiếp chúng đến CloudWatch, sau đó stream dữ liệu vào Amazon SQS để ingestion ổn định. AWS Lambda xử lý messages từ SQS theo thời gian thực, phân loại logs và lưu metadata trong DynamoDB (Hot Data) để truy vấn nhanh, trong khi raw payloads được lưu trữ trong Amazon S3 (Cold Data) cho phân tích dài hạn bằng Amazon Athena và AWS Glue. Thông báo lỗi được gửi qua Amazon SNS. Quyền truy cập người dùng được quản lý thông qua Amazon Cognito và IAM, cho phép đăng ký và đăng ký nhận cảnh báo SNS một cách an toàn. Đối với các truy vấn nâng cao, một ứng dụng dựa trên EC2 cung cấp quyền truy cập có kiểm soát vào Athena để phân tích logs.

*Lợi ích và hoàn vốn đầu tư (ROI)*

Giải pháp này thiết lập một hệ thống quản lý logs serverless hợp nhất, giúp giảm chi phí vận hành và cải thiện khả năng quan sát trên các ứng dụng phân tán. Phân loại real‑time tăng tốc quá trình khắc phục sự cố, trong khi lưu trữ tiết kiệm chi phí trên S3 hỗ trợ phân tích mở rộng. Bằng cách tự động hóa ingestion và alerting, các nhóm tiết kiệm đáng kể thời gian so với việc thu thập logs thủ công. Chi phí hàng tháng vẫn ở mức tối thiểu theo mô hình giá serverless của AWS, với ROI dài hạn đạt được thông qua cải thiện độ tin cậy, giảm downtime, và tối ưu hóa bảo trì.

### 3. Kiến trúc giải pháp

Pipeline sử dụng kiến trúc AWS serverless hoàn chỉnh để tập trung hóa việc thu thập, xử lý và phân tích logs trên các ứng dụng phân tán. Logs được thu thập thông qua CloudWatch Agents, được stream qua Amazon SQS để đảm bảo truyền tải ổn định, và được xử lý bởi AWS Lambda để phân loại real‑time. Metadata được lưu trong DynamoDB để truy vấn nhanh, trong khi raw payloads được lưu trữ trong Amazon S3 cho phân tích dài hạn với Athena và Glue. Notifications được xử lý bởi SNS và CloudWatch Alerts, đảm bảo phản hồi kịp thời đối với các bất thường. Đăng ký người dùng và kiểm soát truy cập được quản lý thông qua Cognito và IAM, với các ứng dụng ECS được tích hợp vào hệ thống để đảm bảo sử dụng an toàn. Kiến trúc được mô tả chi tiết bên dưới.

![Log Management Platform Architecture](/images/2-Proposal/platform_architecture_vi.jpeg)

*Dịch vụ AWS sử dụng*
- *Amazon Cognito*: Quản lý đăng ký và xác thực người dùng.
- *AWS IAM*: Cung cấp secure access keys và phân quyền dựa trên role.
- *Amazon ECS*: Đăng ký applications và liên kết chúng với user accounts.
- *Amazon DynamoDB*: Lưu trữ user metadata và thông tin đăng ký.
- *Amazon CloudWatch*: Tập trung hóa việc thu thập và giám sát logs.
- *CloudWatch Agent*: Thu thập logs từ EC2/ECS applications.
- *Amazon SQS*: Đảm bảo ingestion logs bất đồng bộ, đáng tin cậy.
- *AWS Lambda*: Xử lý và phân loại logs theo thời gian thực.
- *Amazon S3*: Lưu trữ raw logs cho phân tích dài hạn.
- *AWS Glue & Glue Catalog*: Tổ chức và chuyển đổi dữ liệu logs.
- *Amazon Athena*: Cho phép truy vấn SQL trên lịch sử log.
- *Amazon SNS*: Gửi alerts và notifications cho log error.
- *CloudWatch Alerts*: Phát hiện patterns bất thường và kích hoạt phản hồi.

*Thiết kế thành phần*
- *Identity & Access Layer*: Cognito xử lý đăng ký người dùng, IAM thực thi permissions, ECS/DynamoDB lưu trữ metadata của user và app.
- *Monitoring & Logging Layer*: CloudWatch Agent thu thập logs từ applications, tập trung trong CloudWatch.
- *ETL & Analytics Layer*: Lambda xử lý logs, Glue tổ chức dữ liệu, Athena cho phép truy vấn, và S3 cung cấp lưu trữ mở rộng.
- *Notification & Response Layer*: SQS xếp hàng events, SNS phân phối alerts, và CloudWatch kích hoạt phát hiện anomalies.

### 4. Triển khai kỹ thuật
*Các giai đoạn triển khai*
1. *Architecture Design*: Xác định serverless log pipeline và tích hợp dịch vụ AWS (Tuần 1-2).
2. *Cost Estimation & Optimization*: Sử dụng AWS Pricing Calculator để dự báo chi phí và điều chỉnh thiết kế (Tuần 3-4).
3. *System Setup & Integration*: Cấu hình CloudWatch Agents, Lambda functions, và Glue jobs (Tuần 5-6).
4. *Testing & Deployment*: Xác thực ingestion, classification, và alerting workflows; triển khai production (Tuần 7-8).

*Yêu cầu kỹ thuật*
- *Log Sources*: Applications chạy trên EC2/ECS với CloudWatch Agents.
- *Data Pipeline*: CloudWatch → SQS → Lambda → DynamoDB/S3.
- *Analytics*: Athena queries trên dữ liệu S3, Glue ETL cho phân tích có cấu trúc.
- *Access Control*: Cognito cho xác thực người dùng, IAM cho permissions.
- *Notifications*: SNS và CloudWatch Alerts cho phát hiện anomalies.

### 5. Lộ trình & Mốc triển khai
- *Trước thực tập (Tuần 1-2)*: 2 tuần cho việc lập kế hoạch và xem xét phương pháp thu thập logs hiện tại.
- *Thực tập (Tuần 3-8)*:
    - Tuần 3-4: Nghiên cứu dịch vụ AWS và cấu hình CloudWatch Agents cho applications.
    - Tuần 5-6: Thiết kế và điều chỉnh pipeline architecture, tích hợp Lambda, SQS, DynamoDB, và S3.
    - Tuần 7-8: Triển khai, kiểm thử, và khởi chạy hệ thống đầy đủ với Glue jobs và Athena queries.
    - *Sau triển khai*: Tối ưu hóa, giám sát, và mở rộng ingestion logs trong vòng 1 năm.

### 6. Ước tính ngân sách
Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=80cb54c8b7d4fb953c3e3b6e9608818b6c73d2ed).

**Chi phí hạ tầng**
- **Amazon S3 Standard**: $0.43/tháng
  (10 GB lưu trữ, 2 GB quét bằng S3 Select, 3,000 requests, 2 GB inbound, 2 GB outbound)
- **AWS Lambda**: $0.20/tháng
  (2 triệu requests, 512 MB ephemeral storage)
- **Amazon Athena**: $0.15/tháng
  (100 queries/ngày, mỗi query quét 0.01 GB)
- **Amazon SQS**: $0.02/tháng
  (50,000 requests)
- **Amazon SNS**: $0.00/tháng
  (10 notifications, 10 requests)
- **Amazon DynamoDB**: $0.03/tháng
  (0.1 GB lưu trữ, item size 1 KB)
- **Amazon CloudWatch**: $0.15/tháng
  (metrics & events cơ bản)
- **AWS Glue**: $0.19/tháng
  (2 DPUs cho Spark job, 0.0625 DPUs cho Python Shell, 2 crawlers)
  
**Tổng**: ~$1.17/tháng, ~$14.04/12 tháng.
Không cần chi phí phần cứng vì hệ thống tận dụng hạ tầng AWS.

### 7. Đánh giá rủi ro
*Ma trận rủi ro*
- Log Volume Spikes: Tác động cao, xác suất trung bình.
- Service Misconfiguration: Tác động trung bình, xác suất trung bình.
- Cost Overruns: Tác động trung bình, xác suất thấp.
- Access Control Breach: Tác động cao, xác suất thấp.

*Chiến lược giảm thiểu*
- Log Spikes: Sử dụng SQS buffering và Lambda auto‑scaling.
- Misconfiguration: Quản lý hạ tầng bằng CloudFormation/CDK templates.
- Cost: Bật AWS budget alerts và tối ưu Glue/Athena queries.
- Access Control: Thực thi Cognito + IAM policies, bật MFA cho người dùng.

*Kế hoạch dự phòng*
- Pipeline Failure: Tạm thời lưu logs cục bộ trên EC2/ECS instances.
- Cost Issues: Roll back cấu hình bằng CloudFormation templates.
- Access Breach: Vô hiệu hóa IAM keys, kích hoạt SNS alerts, và khôi phục permissions.

### 8. Kết quả kỳ vọng
*Cải tiến kỹ thuật*:
Pipeline cho phép ingestion và analytics logs real‑time, thay thế việc thu thập thủ công phân tán trên nhiều servers. Nó cung cấp khả năng quan sát tập trung, khắc phục sự cố nhanh hơn thông qua metadata queries trong DynamoDB, và lưu trữ dài hạn mở rộng trong S3. Truy vấn SQL qua Athena giúp phân tích dễ dàng, trong khi alerts tự động qua SNS và CloudWatch giảm downtime.

*Giá trị dài hạn*:
Hệ thống tạo nền tảng dữ liệu logs trong 1 năm cho nghiên cứu vận hành và tối ưu hóa hiệu suất. Nó có thể tái sử dụng cho các dự án tương lai, đóng vai trò như một mô hình cho serverless data pipelines. Bằng cách giảm thiểu giám sát thủ công và tận dụng mô hình pay‑as‑you‑go của AWS, giải pháp đảm bảo hiệu quả chi phí, khả năng mở rộng, và độ tin cậy cho các ứng dụng cấp doanh nghiệp.
