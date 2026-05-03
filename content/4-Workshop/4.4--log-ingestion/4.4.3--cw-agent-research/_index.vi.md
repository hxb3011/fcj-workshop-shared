---
title: "Nghiên cứu CloudWatch Agent"
date: 2026-05-02
weight: 3
chapter: false
pre: "<b> 4.4.3 </b>"
---

## 4.4.3 Nghiên cứu CloudWatch Agent

### Mục tiêu

Tìm hiểu CloudWatch Agent và cách sử dụng để thu thập log từ hệ thống thực tế, từ đó mở rộng khả năng ingest dữ liệu cho pipeline.

---

### Tổng quan

CloudWatch Agent là một công cụ do AWS cung cấp, cho phép thu thập log và metric từ các máy chủ (EC2 hoặc on-premise) và gửi trực tiếp lên CloudWatch.

Khác với việc tạo log thủ công trong CloudWatch, CloudWatch Agent giúp tự động hóa quá trình thu thập log từ hệ thống, đặc biệt hữu ích trong môi trường production.

---

### Cách hoạt động

Quy trình hoạt động của CloudWatch Agent bao gồm:

- Cài đặt CloudWatch Agent trên máy chủ (EC2)  
- Cấu hình file agent (JSON hoặc wizard) để xác định log cần thu thập  
- Agent đọc log từ hệ thống (ví dụ: `/var/log/...`)  
- Gửi log lên CloudWatch Logs  
- Từ CloudWatch, log tiếp tục đi vào pipeline xử lý (Lambda Shipper → SQS → Lambda Processor)  

---

### Ứng dụng trong hệ thống

Trong hệ thống này, CloudWatch Agent có thể được sử dụng để:

- Thu thập log thực tế từ ứng dụng chạy trên EC2  
- Tự động gửi log lên CloudWatch mà không cần thao tác thủ công  
- Kết nối trực tiếp với pipeline ingest đã xây dựng ở phần 4.4  

---

### So sánh với cách ingest hiện tại

| Tiêu chí | Log thủ công | CloudWatch Agent |
|----------|-------------|------------------|
| Cách tạo log | Tạo test event | Tự động từ hệ thống |
| Tính tự động | Thấp | Cao |
| Ứng dụng thực tế | Hạn chế | Phù hợp production |

---

### Kết luận

CloudWatch Agent giúp tự động hóa quá trình thu thập log và mở rộng hệ thống ingest từ môi trường thử nghiệm sang môi trường thực tế. Đây là một thành phần quan trọng để xây dựng hệ thống giám sát và xử lý log hoàn chỉnh.
