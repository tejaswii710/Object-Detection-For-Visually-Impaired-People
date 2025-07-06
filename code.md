# CODE 

## Step 1: Create proj.py File  
In PyCharm, right-click your project folder → select **New** → **Python File** → name it `proj.py` → press Enter.  
Now paste the full code (available in `code.md`) into this file.

```
import numpy as np
import cv2
import torch
import boto3
import time
import os
import re
from playsound import playsound

# Initialize AWS Polly client with your credentials
polly = boto3.client(
    "polly",
    aws_access_key_id="YOUR_ACCESS_KEY",
    aws_secret_access_key="YOUR_SECRET_KEY",
    region_name="us-east-1"
)



os.makedirs("audio_cache", exist_ok=True)
def speak(text):
    filename = f"audio_cache/{re.sub(r'[^a-zA-Z0-9]', '_', text)}.mp3"

    if not os.path.exists(filename):
        response = polly_client.synthesize_speech(
            Text=text,
            OutputFormat='mp3',
            VoiceId='Joanna',
            Engine='standard'
        )
        with open(filename, 'wb') as file:
            file.write(response['AudioStream'].read())

    playsound(filename)


speak("Attention! Object detection is starting.")

model = torch.hub.load('ultralytics/yolov5', 'yolov5s', pretrained=True)

# Initialize Webcam
print("Starting webcam... Press 'q' to exit.")
cap = cv2.VideoCapture(0)

last_speech_time = 0
last_detected_objects = set()

while True:
    ret, image_np = cap.read()
    if not ret:
        print("Failed to capture frame.")
        break


    results = model(image_np)
    df_result = results.pandas().xyxy[0]

    labels = df_result['name'].tolist()
    scores = df_result['confidence'].tolist()

    list_boxes = []
    for _, row in df_result.iterrows():
        xmin, ymin, xmax, ymax = int(row['xmin']), int(row['ymin']), int(row['xmax']), int(row['ymax'])
        list_boxes.append((xmin, ymin, xmax, ymax))


    for i, (xmin, ymin, xmax, ymax) in enumerate(list_boxes):
        cv2.rectangle(image_np, (xmin, ymin), (xmax, ymax), (255, 0, 0), 2)
        cv2.putText(image_np, f"{labels[i]}: {round(scores[i], 2)}", (xmin, ymin - 10),
                    cv2.FONT_HERSHEY_SIMPLEX, 0.9, (36, 255, 12), 2)

    cv2.imshow('Object Detector', image_np)
    current_time = time.time()
    unique_labels = set(labels) - last_detected_objects

    if unique_labels and (current_time - last_speech_time > 5):
        detected_text = f"Watch out! A {', '.join(unique_labels)} is nearby."
        print("Speaking:", detected_text)
        speak(detected_text)
        last_detected_objects = set(labels)
        last_speech_time = current_time
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
print("Exited object detection.")
```


