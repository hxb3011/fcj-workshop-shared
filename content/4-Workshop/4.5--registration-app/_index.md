---
title : "VPC Endpoint Policies"
date : 2025-05-02
weight : 5
chapter : false
pre : " <b> 4.5. </b> "
---

The **user registration system** acts as the identity and access control layer across the entire log management pipeline. It ensures that only authenticated applications and users can participate in sending logs, querying, and analyzing data.  

The system is implemented using **Amazon Cognito, IAM, ECS, and DynamoDB**, enabling full lifecycle management of users—from registration, authentication, and authorization to storing application information.  

### Main objectives of the system:
- Provide a **centralized and secure** mechanism for registering applications and users.  
- Automate the process of granting permissions and generating access keys for new applications.  
- Ensure that registration data is stored and managed in DynamoDB to support future querying and analysis operations.  
- Integrate with other AWS services such as **CloudWatch** and **SNS** to enable monitoring and alerting.  

Contents:
1. [Check registration portal infrastructure](4.5.1--resource-check/)
2. [Registration portal practical test](4.5.2--registration-test/)
3. [Comprehensive query test](4.5.3--query-test/)