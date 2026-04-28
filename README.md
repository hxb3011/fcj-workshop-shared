🚀 AWS Serverless Log Management System: Hệ thống quản lý và giám sát Log tập trung được xây dựng trên nền tảng điện toán đám mây AWS. Dự án tập trung vào việc tối ưu hóa chi phí lưu trữ, đảm bảo tính toàn vẹn của dữ liệu log và hệ thống cảnh báo thông minh (Debounce logic).

📌 Tổng quan dự án: Dự án giải quyết bài toán tiếp nhận hàng triệu bản ghi log từ các ứng dụng Client khác nhau, thực hiện phân loại, lưu trữ lâu dài và cảnh báo tức thời khi có sự cố nghiêm trọng xảy ra.

Các công nghệ sử dụng:
Compute: AWS ECS Express Mode (Fargate) & AWS Lambda (Python).

Messaging: AWS SQS FIFO (Chống nghẽn & Đảm bảo thứ tự).

Storage: AWS S3 (Archive) & DynamoDB (Metadata/Hot data).

Notification: AWS SNS (Email Alert).

Security: AWS Cognito & API Gateway.

🏗️ Kiến trúc hệ thống (Workflow): Hệ thống vận hành qua 5 giai đoạn chính:

Giai đoạn 1 (Registration): Ứng dụng Client đăng ký qua giao diện chạy trên ECS Express Mode. Hệ thống cấp AppId và xác thực qua SNS.

Giai đoạn 2 (Ingestion): Log thô được đẩy vào SQS FIFO để đảm bảo không bị mất mát hoặc sai lệch thứ tự thời gian.

Giai đoạn 3 (Processing): AWS Lambda bóc tách JSON, phân loại mức độ lỗi (INFO, ERROR, CRITICAL).

Giai đoạn 4 (Storage): * Lưu chi tiết vào S3 theo phân vùng (Partitioning) /năm/tháng/ngày/AppId/ để tối ưu truy vấn Athena.

Lưu Metadata vào DynamoDB để hiển thị Dashboard thời gian thực.

Giai đoạn 5 (Monitoring & Alert): Kiểm tra Debounce logic trong DynamoDB để quyết định gửi cảnh báo qua SNS (tránh gửi lặp lại trong thời gian ngắn)

💡 Các điểm nổi bật về kỹ thuật: 
S3 Partitioning: Thiết kế đường dẫn giúp giảm thiểu lượng dữ liệu phải quét, tiết kiệm chi phí khi sử dụng Amazon Athena.

Debounce Alert: Giải thuật kiểm tra trạng thái trong 300 giây giúp hệ thống chỉ gửi 1 cảnh báo duy nhất cho cùng một chuỗi sự cố lặp lại.

Cloud Evolution: Chuyển đổi từ App Runner sang ECS Express Mode để đảm bảo tính bền vững và khả năng mở rộng trong tương lai.

Dự án được thực hiện phục vụ cho mục đích báo cáo workshop công nghệ AWS 2026.
