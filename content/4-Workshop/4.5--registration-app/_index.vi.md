---
title: "Hệ thống đăng ký người dùng"
date: 2026-05-02
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

## 4.5. Hệ thống đăng ký người dùng

### Nội dung:
1.  [Kiểm tra hạ tầng cổng đăng ký](4.5.1--resource-check/)
2.  [Kiểm thử thực tế cổng đăng ký](4.5.2--registration-test/)
3.  [Kiểm thử truy vấn toàn diện](4.5.3--query-test/)

### Mục tiêu
Cung cấp một cơ chế an toàn và tập trung để đăng ký ứng dụng và người dùng, đảm bảo rằng chỉ các thực thể đã được xác thực mới có thể truy cập vào quy trình quản lý nhật ký.

### Kiến trúc
Hệ thống đăng ký được xây dựng trên **Amazon Cognito, IAM, ECS và DynamoDB**.

![struct](/images/4-Workshop/4.5--registration-app/architecture.jpeg)

- **Cognito** quản lý việc đăng ký và xác thực người dùng.

- **IAM** thực thi quyền truy cập dựa trên vai trò và tạo ra các khóa truy cập an toàn.

- **ECS** lưu trữ Ứng dụng Đăng ký, cung cấp API để đăng ký ứng dụng mới.

- **DynamoDB** lưu trữ siêu dữ liệu về các ứng dụng và người dùng đã đăng ký.

### Mô tả Kiến trúc
Các ứng dụng tương tác với **Ứng dụng Đăng ký (ECS)** để gửi yêu cầu đăng ký. Quy trình làm việc như sau:
1. Ứng dụng gọi API đăng ký.

2. Cognito xác thực danh tính người dùng và kích hoạt xác nhận qua email.

3. Sau khi được xác nhận, IAM tự động cấp cho người dùng mới các khóa truy cập và chính sách.
   
4. Ứng dụng được ghi lại trong **bảng AppClients trên DynamoDB**, đảm bảo khả năng truy vết và tích hợp với quy trình phân tích.

5. Người dùng đã đăng ký được cấp quyền đẩy nhật ký vào **CloudWatch Logs**, cho phép nhập dữ liệu liền mạch vào quy trình.

### Vai trò của ứng dụng đăng ký
- Cung cấp các điểm cuối API để đăng ký ứng dụng.

- Xác thực danh tính người dùng thông qua Cognito và xác nhận email.

- Tự động tạo người dùng IAM và cấp phát khóa truy cập.

- Lưu trữ siêu dữ liệu ứng dụng trong DynamoDB cho các truy vấn và phân tích trong tương lai.

- Cấp quyền CloudWatch cho các ứng dụng đã đăng ký để chuyển tiếp nhật ký.

### Kết quả
Các ứng dụng và người dùng được đăng ký, xác thực và cấp quyền cần thiết một cách an toàn. Hệ thống đảm bảo rằng chỉ các thực thể đã được xác thực mới có thể gửi nhật ký vào quy trình và truy vấn phân tích, do đó duy trì **tính bảo mật, khả năng mở rộng và độ tin cậy** trên toàn bộ hệ sinh thái quản lý nhật ký.
