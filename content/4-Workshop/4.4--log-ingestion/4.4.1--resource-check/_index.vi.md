---
title: "Kiểm tra tài nguyên"
date: 2026-05-02
weight: 1
chapter: false
pre: "<b> 4.4.1 </b>"
---

## 4.4.1 Kiểm tra tài nguyên

### Mục tiêu

Kiểm tra các thành phần trong luồng ingest log từ CloudWatch nhằm đảm bảo hệ thống được cấu hình chính xác trước khi thực hiện kiểm thử.

---

### Kiểm tra

- SQS đã được kết nối với Lambda Processor  

- Lambda Shipper đã được cấu hình để nhận log từ CloudWatch Logs

![Resource check](/images/4-Workshop/4.4--log-ingestion/4.4.1--resource-check/resource1.png)  
![Resource check](/images/4-Workshop/4.4--log-ingestion/4.4.1--resource-check/resource2.png)  
*Hình 4.4.1-1: Kiểm tra kết nối giữa CloudWatch, Lambda Shipper, lambda Processor và SQS.*

---

### Mô tả

Hệ thống đã thiết lập thành công Lambda Shipper để nhận log từ CloudWatch và chuyển tiếp đến SQS. Khi message được đưa vào SQS, Lambda Processor sẽ được kích hoạt để tiếp tục xử lý dữ liệu trong pipeline.
