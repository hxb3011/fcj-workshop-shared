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

### DynamoDB Verification

The system shows that three DynamoDB tables have been successfully created:
- fcaj-v2-AppClients  
- fcaj-v2-AppLogs  
- fcaj-v2-NotiTTL  

![DynamoDB tables](/images/4-Workshop/4.3--lambda-processor/4.3.1--resource-check/dynamodb.png)  

### SQS Verification

The queue `fcaj-v2-log-queue` has been successfully created and is ready for use.

![SQS queue](/images/4-Workshop/4.3--lambda-processor/4.3.1--resource-check/sqs.png)  

### Lambda Verification

The Lambda function has been successfully deployed and configured to be triggered by SQS.

![Lambda trigger](/images/4-Workshop/4.3--lambda-processor/4.3.1--resource-check/lambda.png) 

### Conclusion

All required resources, including DynamoDB, SQS, and Lambda Processor, have been properly configured and are ready for the testing phase.
