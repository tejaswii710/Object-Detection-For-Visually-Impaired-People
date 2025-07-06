# Real-Time Object Detection for Visually Impaired People Using AWS Polly

## Overview

This project aims to build a **real-time object detection system** that assists **visually impaired individuals** by identifying objects in their surroundings using a webcam and providing **audio feedback** through **AWS Polly**.

The system leverages **YOLOv5** for object detection and uses **AWS Polly** for converting the detected object labels into speech. The audio output is then played to the user, helping them understand their environment in real time.

## Objective

To build a real-time object detection system that:
- Detects nearby objects using a webcam.
- Identifies and labels them using a deep learning model (YOLOv5).
- Uses AWS Polly to convert object names into speech.
- Speaks out loud the detected objects for the benefit of visually impaired users.

---

## Hardware Requirements
- Laptop or PC with a functional webcam

## Software Requirements
- PyCharm IDE
- AWS Polly
- IAM User on AWS with appropriate permissions
- Python
- Required Python libraries: `boto3`, `torch`, `opencv-python`, `torchvision`


