---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Serverless Log Management & Analytics Pipeline
## Unified AWS Serverless Solution for Scalable Log Processing

### 1. Executive Summary

The Serverless Log Management & Analytics Pipeline is designed to provide centralized log ingestion and analysis for diverse applications, running on AWS. It supports high‑volume log streams from multiple sources, with scalability to handle millions of events per day. The pipeline leverages AWS Serverless services to deliver real‑time classification, optimized long‑term storage, and cost‑efficient analytics. Access control is managed through AWS Identity and Access Management (IAM), ensuring secure usage across designated teams.

SERVERLESS LOG MANAGEMENT & ANALYTICS PIPELINE
1.Executive Summary
Dự án tập trung xây dựng một hệ thống quản lý và phân tích nhật ký (log) tập trung, sử dụng hoàn toàn kiến trúc Serverless trên nền tảng điện toán đám mây AWS. Hệ thống được thiết kế để giải quyết bài toán tiếp nhận dữ liệu log khổng lồ từ nhiều ứng dụng khác nhau, xử lý phân loại thời gian thực và lưu trữ tối ưu cho mục đích phân tích dài hạn.
2.Problem Statement
What’s the Problem
Log ứng dụng nằm rải rác trên nhiều máy chủ, gây khó khăn cho việc giám sát tập trung.
*The Solution
Hệ thống triển khai sử dụng cloudwatch agent gửi log lên vào cloudwatch , từ cloud watch sẽ gửi vào đường ống dữ liệu (SQS) tiếp nhận ổ định thông qua lambda , từ sqs gọi aws lambda để phân loại dữ liệu theo thời gian thực: lưu trữ metadata tại DynamoDB (Hot Data) để truy vấn nhanh và đẩy payload thô lên Amazon S3 (Cold Data) phục vụ phân tích lâu dài bằng Amazon Athena và Aws glue,nếu có lỗi sẽ báo qua SNS. Đồng thời triển khai một app đăng kí tài khoản sử dụng cognito và iam đăng kí người dùng vào sns. Với amazon athena thì triển khai một app sử dụng ec2 để đăng nhập và truy vấn dữ liệu log
3.Solution Architecture

### 2. Problem Statement
#### What’s the Problem?

Application logs are scattered across multiple servers, making centralized monitoring and analysis difficult. This fragmentation leads to inefficiencies in troubleshooting, delayed insights, and challenges in maintaining system reliability.

#### The Solution

The pipeline leverages AWS CloudWatch Agent to collect logs and forward them to CloudWatch, which then streams data into Amazon SQS for stable ingestion. AWS Lambda processes messages from SQS in real time, classifying logs and storing metadata in DynamoDB (Hot Data) for fast queries, while raw payloads are archived in Amazon S3 (Cold Data) for long‑term analytics using Amazon Athena and AWS Glue. Error notifications are sent via Amazon SNS. User access is managed through Amazon Cognito and IAM, enabling secure registration and subscription to SNS alerts. For advanced queries, an EC2‑based application provides controlled access to Athena for log analysis.

#### Benefits and Return on Investment

This solution establishes a unified, serverless log management system that reduces operational overhead and improves visibility across distributed applications. Real‑time classification accelerates troubleshooting, while cost‑efficient storage in S3 supports scalable analytics. By automating ingestion and alerting, teams save significant time compared to manual log collection. Monthly costs remain minimal under AWS’s serverless pricing model, with long‑term ROI achieved through improved reliability, reduced downtime, and streamlined maintenance.

### 3. Solution Architecture
The platform employs a serverless AWS architecture to manage data from 5 Raspberry Pi-based stations, scalable to 15. Data is ingested via AWS IoT Core, stored in an S3 data lake, and processed by AWS Glue Crawlers and ETL jobs to transform and load it into another S3 bucket for analysis. Lambda and API Gateway handle additional processing, while Amplify with Next.js hosts the dashboard, secured by Cognito. The architecture is detailed below:

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

### AWS Services Used
- **AWS IoT Core**: Ingests MQTT data from 5 stations, scalable to 15.
- **AWS Lambda**: Processes data and triggers Glue jobs (two functions).
- **Amazon API Gateway**: Facilitates web app communication.
- **Amazon S3**: Stores raw data in a data lake and processed outputs (two buckets).
- **AWS Glue**: Crawlers catalog data, and ETL jobs transform and load it.
- **AWS Amplify**: Hosts the Next.js web interface.
- **Amazon Cognito**: Secures access for lab users.

### Component Design
- **Edge Devices**: Raspberry Pi collects and filters sensor data, sending it to IoT Core.
- **Data Ingestion**: AWS IoT Core receives MQTT messages from the edge devices.
- **Data Storage**: Raw data is stored in an S3 data lake; processed data is stored in another S3 bucket.
- **Data Processing**: AWS Glue Crawlers catalog the data, and ETL jobs transform it for analysis.
- **Web Interface**: AWS Amplify hosts a Next.js app for real-time dashboards and analytics.
- **User Management**: Amazon Cognito manages user access, allowing up to 5 active accounts.

### 4. Technical Implementation
**Implementation Phases**
This project has two parts—setting up weather edge stations and building the weather platform—each following 4 phases:
- Build Theory and Draw Architecture: Research Raspberry Pi setup with ESP32 sensors and design the AWS serverless architecture (1 month pre-internship)
- Calculate Price and Check Practicality: Use AWS Pricing Calculator to estimate costs and adjust if needed (Month 1).
- Fix Architecture for Cost or Solution Fit: Tweak the design (e.g., optimize Lambda with Next.js) to stay cost-effective and usable (Month 2).
- Develop, Test, and Deploy: Code the Raspberry Pi setup, AWS services with CDK/SDK, and Next.js app, then test and release to production (Months 2-3).

**Technical Requirements**
- Weather Edge Station: Sensors (temperature, humidity, rainfall, wind speed), a microcontroller (ESP32), and a Raspberry Pi as the edge device. Raspberry Pi runs Raspbian, handles Docker for filtering, and sends 1 MB/day per station via MQTT over Wi-Fi.
- Weather Platform: Practical knowledge of AWS Amplify (hosting Next.js), Lambda (minimal use due to Next.js), AWS Glue (ETL), S3 (two buckets), IoT Core (gateway and rules), and Cognito (5 users). Use AWS CDK/SDK to code interactions (e.g., IoT Core rules to S3). Next.js reduces Lambda workload for the fullstack web app.

### 5. Timeline & Milestones
**Project Timeline**
- Pre-Internship (Month 0): 1 month for planning and old station review.
- Internship (Months 1-3): 3 months.
    - Month 1: Study AWS and upgrade hardware.
    - Month 2: Design and adjust architecture.
    - Month 3: Implement, test, and launch.
- Post-Launch: Up to 1 year for research.

### 6. Budget Estimation
You can find the budget estimation on the [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01).
Or you can download the [Budget Estimation File](../attachments/budget_estimation.pdf).

### Infrastructure Costs
- AWS Services:
    - AWS Lambda: $0.00/month (1,000 requests, 512 MB storage).
    - S3 Standard: $0.15/month (6 GB, 2,100 requests, 1 GB scanned).
    - Data Transfer: $0.02/month (1 GB inbound, 1 GB outbound).
    - AWS Amplify: $0.35/month (256 MB, 500 ms requests).
    - Amazon API Gateway: $0.01/month (2,000 requests).
    - AWS Glue ETL Jobs: $0.02/month (2 DPUs).
    - AWS Glue Crawlers: $0.07/month (1 crawler).
    - MQTT (IoT Core): $0.08/month (5 devices, 45,000 messages).

Total: $0.7/month, $8.40/12 months

- Hardware: $265 one-time (Raspberry Pi 5 and sensors).

### 7. Risk Assessment
#### Risk Matrix
- Network Outages: Medium impact, medium probability.
- Sensor Failures: High impact, low probability.
- Cost Overruns: Medium impact, low probability.

#### Mitigation Strategies
- Network: Local storage on Raspberry Pi with Docker.
- Sensors: Regular checks and spares.
- Cost: AWS budget alerts and optimization.

#### Contingency Plans
- Revert to manual methods if AWS fails.
- Use CloudFormation for cost-related rollbacks.

### 8. Expected Outcomes
#### Technical Improvements: 
Real-time data and analytics replace manual processes.
Scalable to 10-15 stations.
#### Long-term Value
1-year data foundation for AI research.
Reusable for future projects.