---
title: "CloudWatch Agent Research"
date: 2026-05-02
weight: 3
chapter: false
pre: "<b> 4.4.3 </b>"
---

## 4.4.3 CloudWatch Agent Research

### Objective

Study CloudWatch Agent and its usage for collecting logs from real systems, thereby extending the ingestion capability of the pipeline.

---

### Overview

CloudWatch Agent is a tool provided by AWS that enables the collection of logs and metrics from servers (EC2 or on-premises) and sends them directly to CloudWatch.

Unlike manually generating logs in CloudWatch, CloudWatch Agent automates the log collection process from the system, making it especially useful in production environments.

---

### How It Works

The workflow of CloudWatch Agent includes:

- Installing CloudWatch Agent on the server (EC2)  
- Configuring the agent using a JSON file or setup wizard to define which logs to collect  
- Reading logs from the system (e.g., `/var/log/...`)  
- Sending logs to CloudWatch Logs  
- From CloudWatch, logs continue through the processing pipeline (Lambda Shipper → SQS → Lambda Processor)  

---

### Application in the System

In this system, CloudWatch Agent can be used to:

- Collect real logs from applications running on EC2  
- Automatically send logs to CloudWatch without manual intervention  
- Integrate directly with the ingestion pipeline developed in section 4.4  

---

### Comparison with Current Ingestion Method

| Criteria | Manual Logs | CloudWatch Agent |
|----------|------------|------------------|
| Log generation | Test events | Automatic from system |
| Automation level | Low | High |
| Real-world applicability | Limited | Suitable for production |

---

### Status

This feature is currently under research and has not yet been fully implemented in the system.

---

### Conclusion

CloudWatch Agent enables automated log collection and extends the ingestion pipeline from a testing environment to a real-world deployment scenario. It is a key component for building a complete monitoring and log processing system.
