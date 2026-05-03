---
title : "User Registration System"
date : 2026-05-02
weight : 5
chapter : false
pre : " <b> 4.5. </b> "
---

## 4.5. User Registration System

### Contents:
1. [Check registration portal infrastructure](4.5.1--resource-check/)
2. [Registration portal practical test](4.5.2--registration-test/)
3. [Comprehensive query test](4.5.3--query-test/)

### Objective
Provide a secure and centralized mechanism for registering applications and users, ensuring that only authenticated entities can access the log management pipeline.

### Architecture
The registration system is built on **Amazon Cognito, IAM, ECS, and DynamoDB**.

![struct](/images/4-Workshop/4.5--registration-app/architecture.jpeg)

- **Cognito** manages user registration and authentication.
- **IAM** enforces role-based access and generates secure access keys.
- **ECS** hosts the Registration App, exposing APIs for new application registration.
- **DynamoDB** stores metadata about registered applications and users.

### Architecture Description
Applications interact with the **Registration App (ECS)** to submit registration requests. The workflow is as follows:
1. The application calls the registration API.
2. Cognito validates the user identity and triggers email confirmation.
3. Once confirmed, IAM automatically provisions a new user with access keys and policies.
4. The application is recorded in the **AppClients table on DynamoDB**, ensuring traceability and integration with the analytics pipeline.
5. Registered users gain permissions to push logs into **CloudWatch Logs**, enabling seamless ingestion into the pipeline.

### Role of Registration App
- Expose API endpoints for application registration.
- Validate user identity through Cognito and email confirmation.
- Automate IAM user creation and access key provisioning.
- Persist application metadata in DynamoDB for future queries and analytics.
- Grant CloudWatch permissions to registered applications for log forwarding.

### Result
Applications and users are securely registered, authenticated, and provisioned with the necessary permissions. The system ensures that only validated entities can send logs into the pipeline and query analytics, thereby maintaining **security, scalability, and reliability** across the log management ecosystem.
