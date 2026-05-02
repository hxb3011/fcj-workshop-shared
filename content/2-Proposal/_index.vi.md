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
Nền tảng áp dụng kiến trúc AWS Serverless để quản lý dữ liệu từ 5 trạm dựa trên Raspberry Pi, có thể mở rộng lên 15 trạm. Dữ liệu được tiếp nhận qua AWS IoT Core, lưu trữ trong S3 data lake và xử lý bởi AWS Glue Crawlers và ETL jobs để chuyển đổi và tải vào một S3 bucket khác cho mục đích phân tích. Lambda và API Gateway xử lý bổ sung, trong khi Amplify với Next.js cung cấp bảng điều khiển được bảo mật bởi Cognito.

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

*Dịch vụ AWS sử dụng*
- *AWS IoT Core*: Tiếp nhận dữ liệu MQTT từ 5 trạm, mở rộng lên 15.
- *AWS Lambda*: Xử lý dữ liệu và kích hoạt Glue jobs (2 hàm).
- *Amazon API Gateway*: Giao tiếp với ứng dụng web.
- *Amazon S3*: Lưu trữ dữ liệu thô (data lake) và dữ liệu đã xử lý (2 bucket).
- *AWS Glue*: Crawlers lập chỉ mục dữ liệu, ETL jobs chuyển đổi và tải dữ liệu.
- *AWS Amplify*: Lưu trữ giao diện web Next.js.
- *Amazon Cognito*: Quản lý quyền truy cập cho người dùng phòng lab.

*Thiết kế thành phần*
- *Thiết bị biên*: Raspberry Pi thu thập và lọc dữ liệu cảm biến, gửi tới IoT Core.
- *Tiếp nhận dữ liệu*: AWS IoT Core nhận tin nhắn MQTT từ thiết bị biên.
- *Lưu trữ dữ liệu*: Dữ liệu thô lưu trong S3 data lake; dữ liệu đã xử lý lưu ở một S3 bucket khác.
- *Xử lý dữ liệu*: AWS Glue Crawlers lập chỉ mục dữ liệu; ETL jobs chuyển đổi để phân tích.
- *Giao diện web*: AWS Amplify lưu trữ ứng dụng Next.js cho bảng điều khiển và phân tích thời gian thực.
- *Quản lý người dùng*: Amazon Cognito giới hạn 5 tài khoản hoạt động.

### 4. Triển khai kỹ thuật
*Các giai đoạn triển khai*
Dự án gồm 2 phần — thiết lập trạm thời tiết biên và xây dựng nền tảng thời tiết — mỗi phần trải qua 4 giai đoạn:
1. *Nghiên cứu và vẽ kiến trúc*: Nghiên cứu Raspberry Pi với cảm biến ESP32 và thiết kế kiến trúc AWS Serverless (1 tháng trước kỳ thực tập).
2. *Tính toán chi phí và kiểm tra tính khả thi*: Sử dụng AWS Pricing Calculator để ước tính và điều chỉnh (Tháng 1).
3. *Điều chỉnh kiến trúc để tối ưu chi phí/giải pháp*: Tinh chỉnh (ví dụ tối ưu Lambda với Next.js) để đảm bảo hiệu quả (Tháng 2).
4. *Phát triển, kiểm thử, triển khai*: Lập trình Raspberry Pi, AWS services với CDK/SDK và ứng dụng Next.js, sau đó kiểm thử và đưa vào vận hành (Tháng 2–3).

*Yêu cầu kỹ thuật*
- *Trạm thời tiết biên*: Cảm biến (nhiệt độ, độ ẩm, lượng mưa, tốc độ gió), vi điều khiển ESP32, Raspberry Pi làm thiết bị biên. Raspberry Pi chạy Raspbian, sử dụng Docker để lọc dữ liệu và gửi 1 MB/ngày/trạm qua MQTT qua Wi-Fi.
- *Nền tảng thời tiết*: Kiến thức thực tế về AWS Amplify (lưu trữ Next.js), Lambda (giảm thiểu do Next.js xử lý), AWS Glue (ETL), S3 (2 bucket), IoT Core (gateway và rules), và Cognito (5 người dùng). Sử dụng AWS CDK/SDK để lập trình (ví dụ IoT Core rules tới S3). Next.js giúp giảm tải Lambda cho ứng dụng web fullstack.

### 5. Lộ trình & Mốc triển khai
- *Trước thực tập (Tháng 0)*: 1 tháng lên kế hoạch và đánh giá trạm cũ.
- *Thực tập (Tháng 1–3)*:
    - Tháng 1: Học AWS và nâng cấp phần cứng.
        - Tháng 2: Thiết kế và điều chỉnh kiến trúc.
        - Tháng 3: Triển khai, kiểm thử, đưa vào sử dụng.
    - *Sau triển khai*: Nghiên cứu thêm trong vòng 1 năm.

### 6. Ước tính ngân sách
Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)
Hoặc tải [tệp ước tính ngân sách](../attachments/budget_estimation.pdf).

*Chi phí hạ tầng*
- AWS Lambda: 0,00 USD/tháng (1.000 request, 512 MB lưu trữ).
- S3 Standard: 0,15 USD/tháng (6 GB, 2.100 request, 1 GB quét).
- Truyền dữ liệu: 0,02 USD/tháng (1 GB vào, 1 GB ra).
- AWS Amplify: 0,35 USD/tháng (256 MB, request 500 ms).
- Amazon API Gateway: 0,01 USD/tháng (2.000 request).
- AWS Glue ETL Jobs: 0,02 USD/tháng (2 DPU).
- AWS Glue Crawlers: 0,07 USD/tháng (1 crawler).
- MQTT (IoT Core): 0,08 USD/tháng (5 thiết bị, 45.000 tin nhắn).

*Tổng*: 0,7 USD/tháng, 8,40 USD/12 tháng
- *Phần cứng*: 265 USD một lần (Raspberry Pi 5 và cảm biến).

### 7. Đánh giá rủi ro
*Ma trận rủi ro*
- Mất mạng: Ảnh hưởng trung bình, xác suất trung bình.
- Hỏng cảm biến: Ảnh hưởng cao, xác suất thấp.
- Vượt ngân sách: Ảnh hưởng trung bình, xác suất thấp.

*Chiến lược giảm thiểu*
- Mạng: Lưu trữ cục bộ trên Raspberry Pi với Docker.
- Cảm biến: Kiểm tra định kỳ, dự phòng linh kiện.
- Chi phí: Cảnh báo ngân sách AWS, tối ưu dịch vụ.

*Kế hoạch dự phòng*
- Quay lại thu thập thủ công nếu AWS gặp sự cố.
- Sử dụng CloudFormation để khôi phục cấu hình liên quan đến chi phí.

### 8. Kết quả kỳ vọng
*Cải tiến kỹ thuật*: Dữ liệu và phân tích thời gian thực thay thế quy trình thủ công. Có thể mở rộng tới 10–15 trạm.
*Giá trị dài hạn*: Nền tảng dữ liệu 1 năm cho nghiên cứu AI, có thể tái sử dụng cho các dự án tương lai.