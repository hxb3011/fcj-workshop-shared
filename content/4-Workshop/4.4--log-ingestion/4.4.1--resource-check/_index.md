---
title: "Resource Check"
date: 2026-05-02
weight: 1
chapter: false
pre: "<b> 4.4.1 </b>"
---

## 4.4.1 Resource Check

### Objective

Verify the components in the log ingestion pipeline from CloudWatch to ensure that the system is correctly configured before testing.

---

### Verification

- SQS is properly connected to the Lambda Processor  

- Lambda Shipper is configured to receive logs from CloudWatch Logs  

![Resource check](/images/4-Workshop/4.4--log-ingestion/4.4.1--resource-check/resource1.png)  
![Resource check](/images/4-Workshop/4.4--log-ingestion/4.4.1--resource-check/resource2.png)  
*Figure 4.4.1-1: Verification of connections between CloudWatch, Lambda Shipper, Lambda Processor, and SQS.*

---

### Description

The system has been successfully configured with Lambda Shipper to receive logs from CloudWatch and forward them to SQS. Once messages are placed in SQS, the Lambda Processor is triggered to continue processing the data within the pipeline.
