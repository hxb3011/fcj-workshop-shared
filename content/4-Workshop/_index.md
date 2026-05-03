---
title: "Workshop"
date: 2026-05-02
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

# Log Management System

#### Overview

In this workshop, we will build a **Serverless Log Management & Analytics Pipeline**. This unified solution is designed to collect, process, and analyze logs centrally for multiple applications running on the AWS platform.

The system addresses the challenge of log data being fragmented across various servers, enabling us to monitor and troubleshoot issues more effectively. Our core data flow will include:
*   **Collection:** Using CloudWatch Agent to centralize logs from various applications.
*   **Orchestration:** Leveraging Amazon SQS to ensure stable and asynchronous log ingestion.
*   **Processing:** Utilizing AWS Lambda to perform real-time log classification.
*   **Storage:** Metadata is stored in **DynamoDB (Hot Data)** for fast querying, while raw logs are saved in **Amazon S3 (Cold Data)** for cost-optimized long-term storage.
*   **Analytics & Alerting:** Using Amazon Athena to query historical logs and Amazon SNS to send instant error notifications.

#### Content

1. [Environment Preparation](4.1--preparation/)
2. [SNS Notification Service](4.2--sns-verification/)
3. [Data Processing Flow from SQS](4.3--lambda-processor/)
4. [Automated Log Ingestion Flow](4.4--log-ingestion/)
5. [Registration App Operation](4.5--registration-app/)
7. [Advanced Scaling Solutions](4.6--advanced-concepts/)
8. [Resource Cleanup](4.7--resource-cleanup/)