---
title : "Comprehensive query testing"
date : 2026-05-02
weight : 3
chapter : false
pre : " <b> 4.5.3 </b> "
---

## 4.4.2 App Registration Operation Check

### Objective
Verify whether the login and log query operations in the Analysis App work as expected.

### Retrieve the address of the Analysis App

![get address](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/001_get_address.png)

### Perform login using the login API via Postman to obtain an access token

![login](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/002_login.png)

### Retrieve the most recent logs using the corresponding API via Postman and receive the results

![hot log](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/003_hot_log.png)

### Retrieve older logs using the corresponding API via Postman
- Call the API to fetch older logs.

![query](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/004_query.png)

- Results obtained.

![cold log](/images/4-Workshop/4.5--registration-app/4.5.3--query-test/005_cold_log.jpg)

### Description
The login and log query operations in the Analysis App work as expected.