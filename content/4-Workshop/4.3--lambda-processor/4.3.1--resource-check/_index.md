---
title: "Resource Check"
date: 2026-05-02
weight: 1
chapter: false
pre: "<b> 4.3.1 </b>"
---

## 4.3.1 Resource Check

### Objective

Before performing the test, it is necessary to ensure that all required resources have been properly created and configured.

---

### DynamoDB Verification

The system shows that three DynamoDB tables have been successfully created:
- fcaj-v2-AppClients  
- fcaj-v2-AppLogs  
- fcaj-v2-NotiTTL  

![DynamoDB tables](/status/images/4-Workshop/4.3--lambda-processor/4.3.1--resource-check/dynamodb.png)  
*Figure 4.3.1-1: DynamoDB tables have been successfully created.*

---

### SQS Verification

The queue `fcaj-v2-log-queue` has been successfully created and is ready for use.

![SQS queue](/status/images/4-Workshop/4.3--lambda-processor/4.3.1--resource-check/sqs.png)  
*Figure 4.3.1-2: SQS queue has been successfully created.*

---

### Lambda Verification

The Lambda function has been successfully deployed and configured to be triggered by SQS.

![Lambda trigger](/status/images/4-Workshop/4.3--lambda-processor/4.3.1--resource-check/lambda.png)  
*Figure 4.3.1-3: Lambda Processor is connected to SQS.*

---

### Conclusion

All required resources, including DynamoDB, SQS, and Lambda Processor, have been properly configured and are ready for the testing phase.
