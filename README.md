# AWS EC2 DevOps Automation - Internship Assignment 1

## Description
This script automates the following:
- Launching an EC2 instance (Amazon Linux 2023, t2.micro)
- Waiting 15 minutes (simulated workload)
- Stopping the instance to save cost

## Files
- `deploy.sh` : Main automation script (renamed from `.txt`)
- `mykey.pem` : EC2 key pair used to launch instance (not uploaded for security)

## Technologies Used
- AWS CLI
- EC2
- Bash Script
- IAM User with programmatic access


## ✅ Assignment 2: IAM + S3 + Automation

### What Was Done:

1. IAM Roles Created:

- Role_A: Read-only access to S3
- Role_B: Write-only (upload only) access to S3

2. EC2 Instance:

- Launched EC2 with Role_B attached
- Verified Role_B can upload files to S3

3. S3 Bucket:

- Bucket name: tech-eazy-akshata-logs
- Created in region: ap-south-1
- Lifecycle rule: auto-delete logs after 7 days

4. deploy.sh Script Updated:

- Script uploads a dummy log file to the S3 bucket:
  aws s3 cp dummy.log s3://tech-eazy-akshata-logs/sample-log-<timestamp>.log

5. Role_A Tested:

- Verified that Role_A can list files in the S3 bucket using:
  aws s3 ls s3://tech-eazy-akshata-logs




## Author
Akshata Zargond