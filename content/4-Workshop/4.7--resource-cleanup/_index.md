---
title : "Clean Up"
date : 2025-05-02
weight : 7
chapter : false
pre : " <b> 4.7. </b> "
---
### Clean Up Process
- Cleaning up resources after completing the workshop is important to optimize costs and keep your AWS environment organized. Resources such as EC2 instances, RDS, and others will continue to charge if they are not removed.

#### Clean up
- Since the entire infrastructure was deployed using Terraform, the clean up process is pretty straightforward.
1. Open Terminal (by either Command Prompt, Windows PowerShell, or VS Code) in the project's root directory (where the configuration files with the extension .tf are located).
2. Run the following command: *terraform destroy*.
3. Terraform will display the list of resources to be deleted. Review them.
4. You will see a confirmation. Type *yes* to confirm the deletion.
5. Wait for the resources to be deleted.

#### Quick note on S3 Buckets
- If your bucket still contains log data, Terraform will display an error because AWS does not allow the deletion of non-empty buckets. In that case:
1. In the console, go to the **S3 console** (by typing on search bar *S3*).
2. Select the log bucket and click empty.
3. In the confirmation screen, type *permanently delete*.
4. Once the bucket is empty, return to the Terminal and rerun the *terraform destroy* command.

#### Final Verification
- After Terraform reports success (**Destroy complete!**), visit the AWS Management Console to ensure the following key resources have been removed.
1. EC2 instances (check status: **Terminated**).
2. CloudWatch Log Groups, Glue Databases, Tables.
3. IAM Roles, SNS, SQS.
4. VPC and other services.
