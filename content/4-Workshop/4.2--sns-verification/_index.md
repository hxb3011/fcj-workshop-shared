---
title: "SNS Notification Service"
date: 2026-05-02
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

In this section, we will verify the configuration of Amazon SNS (Simple Notification Service). This component is responsible for sending instant alerts via Email when the system detects high-severity log errors.

### 1. Verify SNS Topic
After deploying the infrastructure, the system automatically created a Topic to serve as a message delivery hub.

1. Access the **Amazon SNS Console** and select **Topics**.
2. Confirm the existence of the Topic: `fcaj-v2-log-alerts-topic`.

![sns-topic-list](/images/4-Workshop/4.2--sns-verification/sns-topic-list.png)

### 2. Subscribe to Notifications
To receive alert emails, we need to subscribe our email address to the Topic found above.

1. Select the Topic `fcaj-v2-log-alerts-topic` and click **Create subscription**.
2. For **Protocol**, select **Email**.
3. For **Endpoint**, enter your personal email address.

![create-subscription](/images/4-Workshop/4.2--sns-verification/create-subscription.png)

The Log Management system supports segregating notifications by application. We can configure the subscription to only receive notifications for a specific `appId`.

*   In the **Subscription filter policy** section, enable this feature.
*   Assume the user has the appId `"app_c4f82f13"`.

![filter-policy](/images/4-Workshop/4.2--sns-verification/filter-policy.png)

Once configured, click **Create subscription** to complete the process.

![filter-policy-2](/images/4-Workshop/4.2--sns-verification/filter-policy-2.png)

### 3. Verify Subscription via Email
After clicking **Create subscription**, your status will appear as **Pending confirmation**.

1. Check the inbox of the email address you registered.
2. Look for an email from **AWS Notifications** and click the **Confirm subscription** link.

![email-confirmation](/images/4-Workshop/4.2--sns-verification/email-confirmation.png)

Upon clicking confirmation, you will see a success message in your browser.

![confirm-success](/images/4-Workshop/4.2--sns-verification/confirm-success.png)

### 4. Final Status Verification
Return to the Topic details page in the SNS Console; you should see that your subscription status has changed to **Confirmed**.

![confirmed-status](/images/4-Workshop/4.2--sns-verification/confirmed-status.png)

{{% notice info %}}
Email verification is a mandatory step. If you do not perform this step, you will not receive any notifications when the system encounters an error, even though the log processing logic is still functioning.
{{% /notice %}}

Our alert system is now ready. In the next step, we will proceed to check and operate the main data processing flow.