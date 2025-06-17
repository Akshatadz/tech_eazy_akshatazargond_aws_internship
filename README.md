# AWS EC2 DevOps Automation - Internship Assignment 2 IAM + S3 + Automation

## What I Did:
This assignment is about automating EC2, IAM Roles, and S3 using a shell script (deploy.sh).

## Steps I Followed:
# 1. Created IAM Roles:
Role_A: Can only read files from the S3 bucket.

Role_B: Can only upload (write) files to the S3 bucket.

# 2. Created S3 Bucket:
Name of the bucket: tech-eazy-akshata-logs

Region: ap-south-1 (Mumbai)

I added a lifecycle rule to delete logs automatically after 7 days.

# 3. Wrote a Shell Script (deploy.sh):
The script performs:

Launching an EC2 instance

Waiting to simulate some task

Uploading a dummy log file to the S3 bucket using:

aws s3 cp dummy.log s3://tech-eazy-akshata-logs/sample-log-<timestamp>.log
Stopping the EC2 instance to save cost

# 4. Attached Role_B to EC2:
While launching the EC2, I attached Role_B to it so that it can upload logs to S3 without needing credentials.

# 5. Verified:
I connected to the EC2 using:
ssh -i mykey.pem ec2-user@<public-ip>

Inside EC2, I uploaded the file to S3:
echo "Test log upload" > dummy.log
aws s3 cp dummy.log s3://tech-eazy-akshata-logs/

Used Role_A on another EC2 to list the uploaded file:
aws s3 ls s3://tech-eazy-akshata-logs/

## Security Notes:
I did not upload .pem or secret keys to GitHub.

Permissions are controlled using IAM roles only.

 ## How to Run:
Make sure AWS CLI is configured.

Ensure key pair mykey is created.

Run the script using:
bash deploy.sh
Connect to EC2 and test S3 upload.




## Author
Akshata Zargond
