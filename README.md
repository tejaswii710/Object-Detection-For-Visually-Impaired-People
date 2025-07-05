# Object Detection 
Real Time Object Detection For Visually Impaired People - By using a webcam, the system can identify and label various objects in the video feed and gives us the audio of the detected objects in the video feed by using AWS Polly. This project aims real voice feedback for visually impaired people to detect their surroundings using Amazon web services.


PROJECT TITLE:
Real-Time Object Detection for Visually Impaired People Using AWS Polly

OBJECTIVE:
To build a real-time object detection system that helps visually impaired individuals by detecting nearby objects and reading them aloud using AWS Polly's Text-to-Speech service.

HARDWARE AND SOFTWARE REQUIREMENTS:

HARDWARE:
Laptop/PC with webcam

SOFTWARE:
PyCharm IDE
AWS Polly
IAM User on AWS
OpenCV
YOLOv5 or similar object detection model
Python packages: boto3, torch, opencv-python, etc.

IMPLEMENTATION STEPS:

IMPLEMENTATION STEPS FOR AWS:
AWS IAM USER SETUP
Step 1: Login to AWS Console
Go to AWS Console
Log in as Root User or IAM Admin

Step 2: Create a New IAM User
Go to IAM → Users → Click Add users
Enter username: object-detection-user
Click Next

Step 3: Set Permissions
Select: Attach policies directly
Search for AmazonPollyFullAccess and check it
Do not select permissions for S3, EC2, or Lambda to avoid charges

Step 4: Create User
Click Create User

Generate Access Keys (After IAM User is Created)
Go to IAM → Users → Select object-detection-user
Open Security Credentials tab
Scroll to Access Keys → Click Create Access Key
Choose use case: "Command Line Interface (CLI)"
Click Next → Create Access Key
Download .csv file containing:
1.Access Key ID
2.Secret Access Key
NOTE: You will not see the secret key again!

IMPLEMENTATION STEPS FOR PROJECT SETUP IN PYCHARM:

Step 1: Clone/Prepare Your Project
Open proj.py in PyCharm
Make sure aimpolly.py 

Step 2: Install Required Libraries
bash
Copy
Edit
pip install boto3 opencv-python torch torchvision

Step 3: Add Access Keys
In proj.py, locate the AWS Polly credentials section:

polly = boto3.client("polly",
    aws_access_key_id="YOUR_ACCESS_KEY",
    aws_secret_access_key="YOUR_SECRET_KEY",
    region_name="us-east-1"
)

Step 4:Run the Project

Run proj.py in PyCharm
The webcam will activate and start object detection
Detected objects will be passed to AWS Polly
Polly will convert text to speech and read aloud

Step 5: Post Execution
Go back to IAM → object-detection-user → Security Credentials
Click Access Keys → Action → Deactivate(This avoids accidental AWS usage)
