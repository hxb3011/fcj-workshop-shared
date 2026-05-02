---
title: "Thu thập log"
date: 2024-01-01
weight: 3
chapter: false
pre: "<b>4.4 </b>"
---

## 4.4 Thu thập log

### Mục tiêu

Thu thập log từ hệ thống thông qua CloudWatch và đưa vào pipeline xử lý.

### Kiến trúc

Trong pipeline ingest, CloudWatch đóng vai trò thu thập log từ hệ thống. Lambda Shipper sẽ tiếp nhận log này và chuyển tiếp đến SQS để tiếp tục quá trình xử lý.


### Mô tả kiến trúc

Trong hệ thống này, log được phát sinh từ ứng dụng và gửi đến CloudWatch. Sau đó, CloudWatch thực hiện việc thu thập (ingest) log và kích hoạt Lambda Shipper để xử lý. Lambda Shipper sẽ chuyển tiếp dữ liệu đến SQS để tiếp tục pipeline xử lý.


### Vai trò của Lambda Shipper

- Tiếp nhận log từ CloudWatch  
- Xử lý và chuyển tiếp dữ liệu  
- Đưa log vào pipeline xử lý thông qua SQS  


### Kết quả

Log được thu thập (ingest) và chuyển vào hệ thống xử lý một cách tự động.
