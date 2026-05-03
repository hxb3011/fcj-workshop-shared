---
title: "Workshop"
date: 2026-05-02
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

# Hệ thống Quản Lý Log

#### Tổng quan

Trong bài thực hành này, chúng ta sẽ cùng nhau xây dựng một **Serverless Log Management & Analytics Pipeline**. Đây là một giải pháp hợp nhất giúp thu thập, xử lý và phân tích log tập trung cho nhiều ứng dụng chạy trên nền tảng AWS.

Hệ thống giải quyết vấn đề phân mảnh dữ liệu log trên nhiều máy chủ khác nhau, giúp chúng ta giám sát và khắc phục sự cố hiệu quả hơn. Luồng dữ liệu chính của chúng ta sẽ bao gồm:
*   **Thu thập:** Sử dụng CloudWatch Agent để tập trung log từ các ứng dụng.
*   **Điều phối:** Dùng Amazon SQS để đảm bảo việc tiếp nhận log ổn định và bất đồng bộ.
*   **Xử lý:** AWS Lambda thực hiện phân loại log theo thời gian thực.
*   **Lưu trữ:** Metadata được lưu tại **DynamoDB (Hot Data)** để truy vấn nhanh, trong khi raw log được lưu tại **Amazon S3 (Cold Data)** để lưu trữ dài hạn với chi phí tối ưu.
*   **Phân tích & Cảnh báo:** Sử dụng Amazon Athena để truy vấn log lịch sử và Amazon SNS để gửi thông báo lỗi tức thì.

#### Nội dung

1. [Chuẩn bị môi trường](4.1--preparation/)
2. [Dịch vụ thông báo SNS](4.2--sns-verification/)
3. [Luồng xử lý dữ liệu từ SQS](4.3--lambda-processor/)
4. [Luồng thu thập Log tự động](4.4--log-ingestion/)
5. [Vận hành App Đăng ký](4.5--registration-app/)
6. [Giải pháp mở rộng nâng cao](4.6--advanced-concepts/)
7. [Dọn dẹp tài nguyên](4.7--resource-cleanup/)

