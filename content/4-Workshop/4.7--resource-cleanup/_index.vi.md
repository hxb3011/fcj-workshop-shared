---
title: "Thu hồi tài nguyên"
date: 2026-05-02
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---
### 4.7 Thu hồi tài nguyên
- Việc dọn dẹp tài nguyên sau khi hoàn thành workshop là rất quan trọng nếu bạn không muốn bị phát sinh thêm chi phí sử dụng. Các hạ tầng như EC2, VPC và RDS vẫn sẽ tính phí nếu bạn không sử dụng chúng.

#### Dọn dẹp
- Vì toàn bộ hạ tầng được triển khai bằng Terraform, nên việc dọn dẹp chúng là rất đơn giản và an toàn.
1. Mở Terminal (bằng Command Prompt, Windows PowerShell hoặc VS Code) tại thư mục gốc chứa các file cấu hình của dự án (có phần mở rộng là .tf).
2. Gõ lệnh sau: *terraform destroy*.
4. Terraform sẽ liệt kê danh sách các tài nguyên sẽ bị xoá.
5. Sau khi liệt kê, Terraform sẽ yêu cầu bạn xác nhận có muốn xoá hay không. Lúc này bạn gõ *yes*.
6. Chờ cho quá trình dọn dẹp hoàn tất.

#### Lưu ý về S3 Bucket
- Nếu S3 bucket của bạn còn chứa dữ liệu (log), Terraform sẽ báo lỗi trong lúc dọn dẹp vì AWS không cho xoá bucket không rỗng. Trong trường hợp này:
1. Tại AWS Management Console, bạn điều hướng đến **S3** (gõ S3 vào ô Search), chọn **General purpose bucket**.
2. Chọn bucket chứa log và nhấn empty.
3. Ở màn hình xác nhận, gõ *permanently delete*.
4. Sau khi empty thành công, quay lại terminal và chạy lại lệnh *terraform destroy*.

#### Kiểm tra lại trên console
- Sau khi Terraform thông báo hoàn tất (**Destroy complete!**), bạn hãy truy cập vào AWS Management Console để kiểm tra và đảm bảo tất cả các tài nguyên đã được dọn dẹp.
1. Điều hướng đến **EC2**, xem các instance đã tạo (ở trạng thái **Terminated**).
2. Kiểm tra tiếp ở CloudWatch Log Groups, Glue Databases, Tables.
3. Kiểm tra IAM Roles, SNS, SQS.
4. Kiểm tra VPC và các dịch vụ liên quan.
