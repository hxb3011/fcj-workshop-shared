---
title : "Testing the registration portal in practice"
date : 2026-05-02
weight : 2
chapter : false
pre : " <b> 4.5.2 </b> "
---

## 4.4.2 App Registration Operation Check

### Objective
Verify whether the app registration operation works as expected.

### Steps

After completing the configuration check, proceed with app registration using the following steps:

1. Retrieve the address of the registration app

![get address](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/001_get_address.png)

2. Use Postman to call the registration API command

![register app](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/002_register_app.png)

3. AWS will send a confirmation email to the address registered in step 2

![email confirm](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/003_email_confirm.png)

4. Confirm the registered email

![email subcribed](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/004_email_subcribed.png)

5. Verify that a new user has been created for the registered app

![user created](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/005_user_created.png)

6. Verify that the user associated with the app has been issued an access key

![access key](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/006_access_key.png)

7. Verify that the user associated with the app has been granted permission to push logs to CloudWatch Logs

![CloudWatch policy](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/007_cloud_watch_policy.png)

8. Verify that the created app has been saved in the **AppClients** table on DynamoDB

![database saved](/images/4-Workshop/4.5--registration-app/4.5.2--registration-test/008_database_saved.png)

### Description
The app registration operation works as expected.