---
title: "Processor Test"
date: 2026-05-02
weight: 2
chapter: false
pre: "<b> 4.3.2 </b>"
---

## 4.3.2 Processor Test

### Objective

Validate the data processing flow from SQS to the Lambda Processor.

---

### Input Data

Test data is simulated as log messages from SQS, including fields such as `appId`, `level`, `message`, and `timestamp`.

---

### Implementation Steps

After configuring all required resources, a test event is created to simulate input data from SQS.

1. Create a test event named **TextSendingMessage** and input the data into the *Event JSON* section.

![Create event](/images/4-Workshop/4.3.2--processor-test/create-event.png)  
*Figure 4.3.2-1: Creating a test event for Lambda Processor.*

Paste the JSON data into the Event JSON section.

![Add JSON](/images/4-Workshop/4.3.2--processor-test/add-json1.png)  
![Add JSON](/images/4-Workshop/4.3.2--processor-test/add-json2.png)  
*Figure 4.3.2-2: Inputting JSON data into the test event.*

---

2. Execute the Lambda function to process the data.

![Lambda run](/images/4-Workshop/4.3.2--processor-test/lambda-run.png)  
*Figure 4.3.2-3: Lambda Processor execution.*

---

3. Verify the processing results

- Log data is stored in S3.  
  The S3 results confirm that the log data has been successfully stored after processing.

![S3 result](/images/4-Workshop/4.3.2--processor-test/s3_1.png)  
![S3 result](/images/4-Workshop/4.3.2--processor-test/s3_2.png)  
*Figure 4.3.2-4: Log data stored in S3.*

- Email notifications are successfully sent.

![Email result](/images/4-Workshop/4.3.2--processor-test/email.png)  
*Figure 4.3.2-5: Email notification after processing.*

---

### Workflow Description

- Messages are sent to SQS  
- Lambda Processor is triggered  
- Data is processed and:
  - Stored in S3  
  - Stored in DynamoDB  
  - Notifications are sent via SNS  

---

### Conclusion

The log processing system operates correctly, ensuring that data is processed, stored, and notifications are delivered successfully.
