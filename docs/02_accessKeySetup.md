# AWS Access Key Setup for IAM User

After creating the IAM user, generate access keys to authenticate your application with AWS.

## Step 1: Open IAM User
- Go to **IAM → Users**
- Select the user: `object-detection-user`

## Step 2: Create Access Keys
- Open the **Security Credentials** tab
- Scroll to **Access Keys**
- Click **Create Access Key**

## Step 3: Select Use Case
- Choose: `Command Line Interface (CLI)`
- Click **Next → Create Access Key**

## Step 4: Download Access Credentials
- Click **Download .csv file**
- This file contains:
  - `Access Key ID`
  - `Secret Access Key`
> ⚠️ **Important:** You will not see the secret key again after this step.

These credentials will be used in your Python code to interact with AWS Polly.

