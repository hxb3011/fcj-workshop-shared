---
title: "Workshop"
date: 2026-05-02
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

# Log Management System

#### Overview

**AWS PrivateLink** provides private connectivity to AWS services from VPCs or on-premises data centers without exposing traffic to the public internet.

In this lab, we will learn how to create, configure, and test VPC endpoints to allow your workloads to access AWS services without going through the public internet.

We will create two types of endpoints to access Amazon S3: gateway VPC endpoint and interface VPC endpoint. These two types of VPC endpoints provide various benefits depending on whether you access S3 from the cloud environment or from on-premises data centers.
+ **Gateway** - Create a gateway endpoint to send traffic to Amazon S3 or DynamoDB using private IP addresses. You route traffic from your VPC to the gateway endpoint using route tables.
+ **Interface** - Create an interface endpoint to send traffic to endpoint services using Network Load Balancer for traffic distribution. Traffic for the endpoint service is resolved using DNS.

#### Content

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Preparation](5.2-Prerequiste/)
3. [Accessing S3 from VPC](5.3-S3-vpc/)
4. [Accessing S3 from On-premises Data Center](5.4-S3-onprem/)
5. [VPC Endpoint Policies (additional)](5.5-Policy/)
6. [Resource Cleanup](5.6-Cleanup/)