#!/bin/bash

# --- Configuration ---
AMI_ID="ami-0f535a71b34f2d44a"
INSTANCE_TYPE="t2.micro"
KEY_NAME="mykey"
SECURITY_GROUP="launch-wizard-1"

# --- Step 1: Launch EC2 instance ---
echo "Launching EC2 instance..."
INSTANCE_ID=$(aws ec2 run-instances \
  --image-id $AMI_ID \
  --count 1 \
  --instance-type $INSTANCE_TYPE \
  --key-name $KEY_NAME \
  --security-groups $SECURITY_GROUP \
  --query "Instances[0].InstanceId" \
  --output text)

echo "✅ Instance launched with ID: $INSTANCE_ID"

# --- Step 2: Wait 15 minutes ---
echo "⏳ Waiting 15 minutes..."
sleep 900

# --- Step 3: Stop the instance ---
echo "🛑 Stopping EC2 instance..."
aws ec2 stop-instances --instance-ids $INSTANCE_ID

echo "✅ Instance $INSTANCE_ID has been stopped."
