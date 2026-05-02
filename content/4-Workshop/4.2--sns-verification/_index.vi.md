---
title: "Dịch vụ thông báo SNS"
date: 2026-05-02
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

Trong phần này, chúng ta sẽ kiểm tra cấu hình của dịch vụ Amazon SNS (Simple Notification Service). Đây là thành phần chịu trách nhiệm gửi cảnh báo tức thời qua Email khi hệ thống phát hiện các log có mức độ lỗi nghiêm trọng.

### 1. Kiểm tra SNS Topic
Sau khi triển khai hạ tầng, hệ thống đã tự động tạo một Topic để làm kênh trung gian truyền tin.

1. Truy cập vào **Amazon SNS Console**, chọn mục **Topics**.
2. Xác nhận sự tồn tại của Topic: `fcaj-v2-log-alerts-topic`.

![sns-topic-list](/images/4-Workshop/4.2--sns-verification/sns-topic-list.png)

### 2. Đăng ký nhận thông báo (Subscription)
Để nhận được email cảnh báo, chúng ta cần đăng ký địa chỉ email của mình vào Topic trên.

1. Chọn Topic `fcaj-v2-log-alerts-topic` và nhấn **Create subscription**.
2. Tại mục **Protocol**, chọn **Email**.
3. Tại mục **Endpoint**, nhập địa chỉ email cá nhân của bạn.

![create-subscription](/images/4-Workshop/4.2--sns-verification/create-subscription.png)

Hệ thống quản lý Log hỗ trợ phân tách thông báo theo từng ứng dụng. Chúng ta có thể cấu hình để chỉ nhận thông báo từ một `appId` cụ thể.

*   Tại mục **Subscription filter policy**, bật tính năng này lên.
*   Giả sử người dùng có appid `"app_c4f82f13"`.

![filter-policy](/images/4-Workshop/4.2--sns-verification/filter-policy.png)

Sau khi cấu hình xong ta bấm **Create subscription** để tạo Subscription

![filter-policy-2](/images/4-Workshop/4.2--sns-verification/filter-policy-2.png)

### 3. Xác thực đăng ký qua Email
Sau khi nhấn **Create subscription**, trạng thái của bạn sẽ là **Pending confirmation**.

1. Kiểm tra hộp thư đến của email bạn đã đăng ký.
2. Tìm thư từ **AWS Notifications** và nhấn vào liên kết **Confirm subscription**.

![email-confirmation](/images/4-Workshop/4.2--sns-verification/email-confirmation.png)

Sau khi nhấn xác nhận, bạn sẽ nhận được thông báo thành công trên trình duyệt.

![confirm-success](/images/4-Workshop/4.2--sns-verification/confirm-success.png)

### 4. Kiểm tra trạng thái cuối cùng
Quay lại trang chi tiết Topic trong SNS Console, bạn sẽ thấy Subscription của mình đã chuyển sang trạng thái **Confirmed**.

![confirmed-status](/images/4-Workshop/4.2--sns-verification/confirmed-status.png)

{{% notice info %}}
Việc xác thực Email là bước bắt buộc. Nếu không thực hiện bước này, bạn sẽ không nhận được bất kỳ thông báo nào khi hệ thống gặp lỗi dù logic xử lý log vẫn hoạt động.
{{% /notice %}}

Chúng ta đã sẵn sàng hệ thống cảnh báo. Bước tiếp theo, chúng ta sẽ tiến hành kiểm tra và vận hành luồng xử lý dữ liệu chính.