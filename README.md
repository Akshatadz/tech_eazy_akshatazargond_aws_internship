# AWS EC2 DevOps Automation - Internship Assignment 2 IAM + S3 + Automation
In Assignment 2, I improved my previous EC2 automation by adding IAM roles and S3 bucket integration.

## IAM Roles Created:
I created two IAM roles:

Role_A – This role has read-only permission to S3. It can only view or list the files in the bucket.

Role_B – This role has write-only permission, which means it can only upload files to the S3 bucket but can’t read or delete them.

## EC2 Instance:
Then I launched a new EC2 instance and attached Role_B using something called instance profile, so that the EC2 machine can upload logs to the S3 bucket securely without using any access keys.

## S3 Bucket:
I created a private S3 bucket called tech-eazy-akshata-logs in the Mumbai (ap-south-1) region.

After that, I added a lifecycle rule to the bucket. This rule automatically deletes logs after 7 days, so we don’t store unnecessary files and avoid extra charges.

## Script Updated:
I added one extra step in my deploy.sh script to create a dummy log file and upload it to the S3 bucket using this command:
aws s3 cp dummy.log s3://tech-eazy-akshata-logs/sample-log-<timestamp>.log
This shows that Role_B can successfully upload files.

## Role_A Verification:
Then I used Role_A to test whether I can list the files in the bucket using:
aws s3 ls s3://tech-eazy-akshata-logs
It worked, which confirms Role_A has correct read-only access.

## For Security:
I didn’t upload any .pem file or AWS credentials to GitHub.

All roles and permissions were attached properly.

The log upload was tested successfully.






## Author
Akshata Zargond
