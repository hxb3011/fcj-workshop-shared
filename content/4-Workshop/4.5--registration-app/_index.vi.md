---
title: "Hệ thống đăng ký người dùng"
date: 2026-05-02
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

Hệ thống đăng ký người dùng đóng vai trò là lớp nhận diện và kiểm soát truy cập trong toàn bộ pipeline quản lý log. Đây là thành phần đảm bảo rằng chỉ những ứng dụng và người dùng đã được xác thực mới có thể tham gia vào quá trình gửi log, truy vấn và phân tích dữ liệu. Việc triển khai hệ thống đăng ký dựa trên Amazon Cognito, IAM, ECS và DynamoDB, giúp quản lý vòng đời người dùng từ khâu đăng ký, xác thực, cấp quyền cho đến lưu trữ thông tin ứng dụng.

Mục tiêu chính của hệ thống:
- Cung cấp cơ chế đăng ký ứng dụng và người dùng một cách **tập trung, an toàn**.
- Tự động hóa việc cấp quyền và tạo access key cho ứng dụng mới.
- Đảm bảo dữ liệu đăng ký được lưu trữ và quản lý trong DynamoDB để phục vụ cho các thao tác truy vấn và phân tích sau này.
- Tích hợp với các dịch vụ AWS khác như CloudWatch, SNS để hỗ trợ giám sát và cảnh báo.

Nội dung:
1.  [Kiểm tra hạ tầng cổng đăng ký](4.5.1--resource-check/)
2.  [Kiểm thử thực tế cổng đăng ký](4.5.2--registration-test/)
3.  [Kiểm thử truy vấn toàn diện](4.5.3--query-test/)
