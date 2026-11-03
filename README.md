# Driver Safety Monitoring System

## 🚀 Live Demo
[Open Driver Safety Monitoring System](https://driver-drowsiness-detection-tiud.onrender.com)

## GitHub Repository
[View Source Code](https://github.com/Alekhya-004/Driver-drowsiness-detection)

## Abstract

This project implements a real-time driver safety monitoring web application that uses a YOLOv11 deep learning model to analyze live webcam or recorded video streams and classify driver behaviors into six categories: awake, distracted, eyes_closed, phone, smoking, and yawn.

The system continuously tracks these behaviors, applies frame-based thresholds to detect risky patterns such as prolonged eye closure, repeated yawning, distraction, phone usage, and smoking, and then triggers contextual audio/visual alerts to warn the driver.

For critical violations (eyes_closed, phone, and smoking), the application captures evidence images and automatically sends email notifications containing timestamps and violation details, supporting both individual safety and fleet-level audit logging.

The frontend provides a modern dashboard for starting webcam detection or uploading videos, viewing live detections and alert status, and configuring email settings.

## Features

- **Real-time Detection:** Continuous monitoring using YOLOv11 model.
- **Behavioral Alerts:** Context-aware alerts for yawn, eyes closed, distraction, phone, and smoking.
- **Email Notifications:** Automatic violation logging with evidence images.
- **Modern UI:** React-based frontend with Tailwind CSS.
- **Webcam & Video Support:** Works with live webcam or uploaded video files.

## Installation

1. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Ensure the model file `best (2).pt` is in the project root directory.

## Usage

1. Start the Flask backend server:
   ```bash
   cd backend
   python app.py
   ```
2. Open your browser:
   ```text
   http://localhost:5000
   ```
3. Configure email settings (optional) using the Email Config button.
4. Start detection using webcam detection or video upload.

## Alert System

- **Yawn (3+ consecutive):** Visual/audio alarm with manual stop button (auto-stops after 10 seconds).
- **Eyes Closed (3+ seconds):** Alarm and email with evidence image.
- **Distracted (4+ seconds):** Voice alert until the driver is awake.
- **Phone Detected:** Voice alert and email with evidence.
- **Smoking Detected:** Voice alert and email with evidence.

## Email Configuration

Configure SMTP settings in the UI:
- SMTP Server (default: smtp.gmail.com)
- SMTP Port (default: 587)
- Sender Email and Password
- Recipient Email

For Gmail, you may need to use an App Password instead of your regular password.

## Model Classes

The model detects six classes:
- awake
- distracted
- eyes_closed
- phone
- smoking
- yawn

## Project Structure

```text
.
├── backend/
│   ├── app.py
│   └── templates/
│       └── index.html
├── best (2).pt
├── data (1).yaml
├── requirements.txt
└── README.md
```

## Notes

- Detection thresholds are frame-based (not time-based).
- Voice alerts use the browser's Web Speech API.
- Violation images are saved in the `violations/` directory.
- Uploaded videos are saved in the `uploads/` directory.
