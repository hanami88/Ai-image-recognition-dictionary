---<h1 align="center">✨ AI Image Recognition Dictionary ✨</h1>


# A multi-platform project combining hardware, AI, and mobile application to help users learn English vocabulary through real-world object recognition.

---

## 📌 Overview

**This system recognizes everyday objects using an ESP32-CAM with a YOLOv8 model running on a Django backend. When the camera detects an object, the Arduino Uno R3 triggers a speaker to pronounce the English name and displays the word on an OLED screen. Meanwhile, the system sends the detected data (image + vocabulary) to a MAUI C# application where users can review and learn vocabulary.

---

## 👥 Team Members

4 members total

My role: Hardware & AI development (ESP32-CAM, Arduino, YOLOv8, Django, AI pipeline)

## ✨ Features
# 🔍 AI Recognition

YOLOv8 object detection model

Django backend processes images and returns predictions

Supports common everyday objects

📱 MAUI App (C#)

Receives vocabulary + detected image via API

Saves learning history

Users can review and study detected words

🔧 Hardware Integration

ESP32-CAM captures images and sends to Django

🏗️ System Architecture

ESP32-CAM → Django Server (YOLOv8) → Arduino (Speaker + OLED)
                               ↓
                          MAUI App (API)


Arduino Uno R3 controls:

Speaker → pronounces the English word

🖥️ Technologies Used
Backend & AI

Python Django (REST API)

YOLOv8 (Ultralytics)

Mobile App

.NET MAUI (C#)

API integration for history storage

Hardware

ESP32-CAM

Arduino Uno R3

OLED Display

Speaker

📡 Data Flow

User points camera at an object

ESP32-CAM captures image → sends to Django

YOLOv8 model detects object

Django returns: object name + confidence

Arduino receives word and:

Plays English audio

Shows word on OLED

Django sends result to MAUI App

MAUI App saves vocabulary + image

🧪 Example Use Case

Point camera at a bottle

Speaker pronounces: “bottle”

OLED displays: BOTTLE

MAUI App logs the detection

🚀 How to Run
Backend (Django)
cd backend
pip install -r requirements.txt
python manage.py runserver

MAUI App

Open in Visual Studio

Build on Android or iOS

Run the project

ESP32-CAM

Flash firmware

Update WiFi credentials + Django API endpoint

Arduino

Upload .ino file controlling OLED + speaker

📁 Project Structure
project/
├── backend/       (Django + YOLOv8)
├── maui-app/      (.NET MAUI)
├── esp32/         (ESP32-CAM firmware)
├── arduino/       (Arduino Uno + OLED + speaker)
└── docs/

📚 Future Improvements

Offline detection

Add phonetic transcription

Vocabulary categories

Multi-language translation

📝 License

MIT License

🙌 Acknowledgments

Thanks to the project team and the open-source communities supporting YOLO, MAUI, and embedded development.



OLED screen → displays the word

ESP32 ↔ Arduino communication to synchronize detection & output
