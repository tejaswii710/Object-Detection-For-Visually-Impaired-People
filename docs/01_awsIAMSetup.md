# AWS IAM User Setup

Follow these steps to set up an IAM user for accessing AWS Polly.

## Step 1: Login to AWS Console
- Visit the AWS Console at [https://aws.amazon.com/](https://aws.amazon.com/)
- Log in as Root User or IAM Administrator

## Step 2: Create a New IAM User
- Go to **IAM → Users → Add users**
- Enter a username: `object-detection-user`
- Click **Next**

## Step 3: Set Permissions
- Choose **Attach policies directly**
- Search for and select: `AmazonPollyFullAccess`
- **Do not attach** permissions for S3, EC2, or Lambda to avoid unexpected AWS charges

## Step 4: Create the User
- Click **Create User**

You’ve successfully created the IAM user for AWS Polly access.

