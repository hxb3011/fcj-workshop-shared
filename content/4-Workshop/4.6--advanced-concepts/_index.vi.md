---
title: "Giải pháp nâng cao"
date: 2025-05-02
weight: 6
chapter: false
pre: " <b> 4.6 </b> "
---
## 4.6 XỬ LÝ LOG THỜI GIAN THỰC VỚI AMAZON KINESIS

### 1. Đề xuất nghiên cứu mở rộng
- Do giới hạn về thời gian trong khuôn khổ kỳ thực tập và ưu tiên tính ổn định của hạ tầng cốt lõi, phần này được trình bày như một đề xuất nghiên cứu nâng cao. Mục tiêu là nâng cấp luồng dữ liệu từ xử lý theo đợt (*Batch Processing*) sang xử lý luồng thời gian thực (*Streaming Processing*) để tối ưu hóa khả năng phản ứng của hệ thống.

### 2. Mô tả giải pháp
- Hệ thống đề xuất sử dụng **Amazon Kinesis Data Firehose** như một giải pháp nâng cao nhằm truyền phát log trực tiếp từ CloudWatch Logs về S3 Data Lake thay vì đợi gom nhóm dữ liệu.
- Giải pháp này giúp giảm độ trễ của dữ liệu từ vài phút xuống vài giây, đảm bảo việc giám sát được các hệ thống nhạy cảm.

### 3. Kiến trúc cốt lõi
- **Kinesis Data Stream**: Đóng vai trò là đầu vào để tiếp nhận khối lượng lớn log đồng thời từ nhiều nguồn mà không làm nghẽn hệ thống.
- **Kinesis Data Analytics**: Thực hiện truy vấn SQL ngay lập tức nhằm phát hiện lỗi bất thường hoặc sự cố ngay lập tức.
- **Kinesis Data Firehose**: Tự động chuyển đổi định dạng dữ liệu sang Parquet trước khi lưu vào S3 nhằm tối ưu hoá chi phí và hiệu suất cho Athena.

### 4. Lợi ích
- **Phản ứng tức thì**: Nếu Kinesis Analytics phát hiện log có lỗi thì cảnh báo qua SNS sẽ được kích hoạt gần như ngay lập tức.
- **Khả năng mở rộng**: Hệ thống có thể xử lý hàng terabyte log mỗi giây mà không cần phải bảo trì hệ thống thủ công.
