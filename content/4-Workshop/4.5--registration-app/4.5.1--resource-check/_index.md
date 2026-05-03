---
title : "Check the registration portal infrastructure"
date : 2026-05-02
weight : 1
chapter : false
pre : " <b> 4.5.1 </b> "
---

## 4.4.1 Resource Check

### Objective
Verify that the Registration App and the Query & Analysis App have been properly configured to ensure the system is correctly set up before testing.

### Check the created VPCs
Confirm that the VPCs for the Registration App and the Query & Analysis App have been initialized as follows:

![vpcs-check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/001_vpc_check.png)

### Check the created subnets
Confirm that the subnets corresponding to the VPCs have been created:

![subnets-check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/002_subnet_check.png)

### Check the created route tables
Confirm that the route tables corresponding to the subnets have been created:

![route table check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/003_route_table.png)

### Check the created internet gateways
Confirm that the internet gateways corresponding to the VPCs have been created:

![internet gateway check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/004_Internet_gateway.png)

### Check the created security groups
Confirm that the security groups corresponding to the VPCs have been created:

![security group check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/005_security_group.png)

### Check the created registration app (Amazon ECS)
Confirm that the registration app has been created:

![app register check](/images/4-Workshop/4.5--registration-app/4.5.1--resource-check/006_app_regist.png)

### Description
The system has successfully set up the VPCs, and the registration app is ready to receive registration requests.