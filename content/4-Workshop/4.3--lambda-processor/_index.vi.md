---
title: "Lambda Processor"
date: 2026-05-02
weight: 3
chapter: false
pre: "<b> 4.3 </b>"
---
#4.3. Lambda Processor

## Tổng quan

Trong hệ thống giám sát log, việc xử lý dữ liệu theo thời gian thực đóng vai trò quan trọng nhằm phát hiện sớm các sự cố. Do đó, phần này tập trung xây dựng một pipeline xử lý log sử dụng SQS và Lambda.


## Kiến trúc tổng quát
  SQS -> Lambda -> (DynamoDB / S3 / SNS)

## Mô tả kiến trúc

Trong kiến trúc này, SQS đóng vai trò là hàng đợi trung gian tiếp nhận các message log. Khi có message mới, Lambda Processor sẽ được kích hoạt tự động để xử lý dữ liệu. Sau đó, dữ liệu được lưu trữ vào DynamoDB, S3 và đồng thời gửi thông báo thông qua SNS.

## Vai trò của Lambda Processor

- Nhận message từ SQS  
- Xử lý dữ liệu log  
- Lưu trữ dữ liệu và gửi thông báo  

## Kết quả

Hệ thống xử lý log hoạt động xuyên suốt (end-to-end), đảm bảo dữ liệu được tiếp nhận, xử lý và lưu trữ đầy đủ.
