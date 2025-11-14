<h1 align="center">✨ AI Image Recognition Dictionary ✨</h1>

A multi-platform project combining hardware, AI, and mobile application features to help users learn English vocabulary through real-world object recognition.

---

## 📌 Overview

This system recognizes everyday objects using an **ESP32-CAM** with a **YOLOv8** model running on a **Django backend**.  
When the camera detects an object, the **Arduino Uno R3** triggers:

- A **speaker** to pronounce the English name  
- An **OLED screen** to display the word  

At the same time, the system sends the detection result (image + vocabulary) to a **.NET MAUI C# application**, allowing users to review and learn vocabulary.

---

## 👥 Team Members

- **4 members in total**  
- **My role:** Hardware & AI development (ESP32-CAM, Arduino, YOLOv8, Django, AI pipeline)

---

## ✨ Features

### 🔍 AI Recognition
- YOLOv8 object detection model  
- Django backend processes images and returns predictions  
- Supports common everyday objects  

### 📱 MAUI App Features
- Receives vocabulary + detected images via API  
- Stores learning history  
- Allows users to review, manage, and study detected words  

### 🔧 Hardware Integration
#### ESP32-CAM
- Captures images and sends them to the Django backend  

#### Arduino Uno R3
- **Speaker** → pronounces the English word  
- **OLED screen** → displays the detected word  

#### Communication
- ESP32 ↔ Arduino communication synchronizes detection and output  

---

## 🏗️ System Architecture

ESP32-CAM → Django Server (YOLOv8) → Arduino (Speaker + OLED)
↓
MAUI App (API)


---

## 🖥️ Technologies Used

### Backend & AI
- Python Django (REST API)  
- YOLOv8 (Ultralytics)  

### Mobile App
- .NET MAUI (C#)  
- REST API integration  

### Hardware
- ESP32-CAM  
- Arduino Uno R3  
- OLED Display  
- Speaker  

---

## 📡 Data Flow

1. User points the ESP32-CAM at an object  
2. ESP32-CAM captures an image → sends it to Django  
3. YOLOv8 model detects objects  
4. Django returns: **object name + confidence**  
5. Arduino receives the word and:  
   - Plays the English pronunciation  
   - Displays the word on the OLED screen  
6. Django sends the detection result to the MAUI App  
7. MAUI App stores **image + detected vocabulary**  

---

## 🧪 Example Use Case

- User points the camera at a **bottle**  
- Speaker pronounces: **"bottle"**  
- OLED displays: **BOTTLE**  
- MAUI app logs the detection into learning history  

---

## 🚀 How to Run

### 1️⃣ Backend (Django)

```bash
cd backend
pip install -r requirements.txt
python manage.py runserver

2️⃣ MAUI App

Open the project in Visual Studio

Build for Android or iOS

Run the solution

3️⃣ ESP32-CAM

Flash firmware

Update WiFi credentials + Django API endpoint

4️⃣ Arduino Uno

Upload the .ino file controlling the OLED + speaker

📚 Future Improvements

Offline AI detection

Add phonetic transcription (IPA)

Vocabulary categorization

Multi-language translation support

---
