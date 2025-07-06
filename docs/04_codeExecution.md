# Code Execution Steps:

## Step 1: Add Access Keys  
In your proj.py file, add the AWS credentials as shown below:  

```python
import boto3
polly = boto3.client("polly",
    aws_access_key_id="YOUR_ACCESS_KEY",
    aws_secret_access_key="YOUR_SECRET_KEY",
    region_name="us-east-1"
)
```


Replace YOUR_ACCESS_KEY and YOUR_SECRET_KEY with the keys you downloaded while creating the IAM user.

---

## Step 2: Add Object Detection and Polly Code  
In proj.py, write the code to:  
- Capture video using OpenCV  
- Use YOLOv5 to detect objects in real-time  
- Convert detected object names to speech using AWS Polly  
- Play the speech using playsound  

Refer to the file: code.md for full working code.

---

## Step 3: Run the Project in pycharm 

- Right-click proj.py and click Run in pycharm 
- Your webcam will turn on and start detecting objects  
- For each new object detected, AWS Polly will speak its name aloud  









