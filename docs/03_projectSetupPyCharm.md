# Project Setup in PyCharm

Follow the steps below to set up your real-time object detection project using PyCharm.

## Step 1: Prepare Project
- Open `proj.py` in PyCharm
- Ensure the support file `aimpolly.py` (or equivalent) is available in the same directory

## Step 2: Install Required Libraries
- boto3
- opencv-python
- torch
- torchvision
- playsound

## Install Required Libraries  
Open terminal inside PyCharm and run the following command to install all required packages:  

pip install boto3 opencv-python torch torchvision playsound  

This installs:  
- boto3: AWS SDK to use Polly  
- opencv-python: For webcam video feed  
- torch and torchvision: For using YOLOv5 model  
- playsound: To play .mp3 audio files  

---

