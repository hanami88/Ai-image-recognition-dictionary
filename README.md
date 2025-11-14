# ✨ AI Image Recognition Dictionary

<div align="center">

A multi-platform project combining hardware, AI, and mobile application to help users learn English vocabulary through real-world object recognition.

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.0+-green.svg)](https://www.djangoproject.com/)
[![.NET MAUI](https://img.shields.io/badge/.NET%20MAUI-7.0+-purple.svg)](https://dotnet.microsoft.com/apps/maui)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-orange.svg)](https://github.com/ultralytics/ultralytics)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Technologies Used](#-technologies-used)
- [Data Flow](#-data-flow)
- [Hardware Components](#-hardware-components)
- [Installation & Setup](#-installation--setup)
- [Usage Example](#-usage-example)
- [Future Improvements](#-future-improvements)

---

## 📌 Overview

This system recognizes everyday objects using an **ESP32-CAM** with a **YOLOv8** model running on a **Django backend**. When the camera detects an object, the **Arduino Uno R3** triggers:

- 🔊 A **speaker** to pronounce the English name
- 📺 An **OLED screen** to display the word

Simultaneously, the system sends the detection result (image + vocabulary) to a **.NET MAUI C# application**, allowing users to review and learn vocabulary on their mobile device.

---

## ✨ Features

### 🤖 AI Recognition

- **YOLOv8** object detection model
- Django REST API backend for image processing
- Real-time predictions with confidence scores
- Supports common everyday objects

### 📱 MAUI Mobile App

- Receives vocabulary and detected images via API
- Stores complete learning history
- Interactive vocabulary review and management
- User-friendly interface for studying detected words

### 🔧 Hardware Integration

#### ESP32-CAM
- Captures high-quality images
- WiFi connectivity to Django server
- Low-power consumption

#### Arduino Uno R3
- **Speaker module** → Pronounces English words
- **OLED display** → Shows detected vocabulary
- Synchronized output with detection results

#### Communication Protocol
- ESP32 ↔ Arduino serial communication
- Real-time data synchronization

---

## 🏗️ System Architecture

```
┌─────────────┐
│ ESP32-CAM   │
│ (Video)   │
└──────┬──────┘
       │
       ▼
┌─────────────────────┐
│   Django Server     │
│   (YOLOv8 Model)    │
└──────┬──────────────┘
       │
       ├──────────────────┐
       ▼                  ▼
┌─────────────┐    ┌──────────────┐
│  Arduino    │    │  MAUI App    │
│ Speaker +   │    │  (Mobile)    │
│    OLED     │    └──────────────┘
└─────────────┘
```

---

## 🖥️ Technologies Used

### Backend & AI
- **Python Django** - REST API framework
- **YOLOv8** (Ultralytics) - Object detection
- **Django REST Framework** - API endpoints

### Mobile Application
- **.NET MAUI** (C#) - Cross-platform mobile app
- **REST API Integration** - Backend communication
- **MySQL** - Local data storage

<img width="1021" height="762" alt="image" src="https://github.com/user-attachments/assets/0151843d-7d7b-479f-8e87-41a89b107db6" />

<img width="1022" height="766" alt="image" src="https://github.com/user-attachments/assets/8066626a-7026-4221-9a1c-185c88fd8dfb" />

### Hardware
- **ESP32-CAM** - Camera module with WiFi
- **Arduino Uno R3** - Microcontroller
- **128x64 OLED Display** - Word display
- **DFPlayer Mini** - Audio playback module
- **Speaker** (3W-5W) - Audio output

<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/8f5a535b-a22b-4360-917f-73ab7abfb08a" />

---

## 📡 Data Flow

1. 📸 User points the **ESP32-CAM** at an object
2. 🌐 ESP32-CAM captures image → sends to **Django server**
3. 🧠 **YOLOv8 model** processes and detects objects
4. 📤 Django returns: **object name + confidence score**
5. 🎯 **Arduino** receives the word and:
   - 🔊 Plays the English pronunciation via speaker
   - 📺 Displays the word on OLED screen
6. 📲 Django sends detection result to **MAUI App**
7. 💾 MAUI App stores **image + vocabulary** in learning history

---

## 🔌 Hardware Components

| Component | Model | Purpose |
|-----------|-------|---------|
| Camera Module | ESP32-CAM | Image capture & WiFi |
| Microcontroller | Arduino Uno R3 | Hardware control |
| Display | OLED 128x64 (I2C) | Word visualization |
| Audio Module | DFPlayer Mini | MP3 playback |
| Speaker | 3W-5W | Audio output |
| Power Supply | 5V 2A | System power |

---

## 🚀 Installation & Setup

### 1️⃣ Backend (Django)

```bash
# Clone the repository
git clone https://github.com/hanami88/Ai-image-recognition-dictionary
cd Ai-image-recognition-dictionary/backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py migrate

# Start server
python manage.py runserver 0.0.0.0:8000
```

### 2️⃣ MAUI Mobile App

```bash
# Open project in Visual Studio 2022
# Build the solution
dotnet build

# Run on Android
dotnet run --project PBL5.csproj -f net8.0-android

# Run on iOS
dotnet run --project PBl5.csproj -f net8.0-ios
```

### 3️⃣ ESP32-CAM Firmware

```cpp
// Flash firmware using Arduino IDE
// Board: AI Thinker ESP32-CAM
// Upload Speed: 115200
```

### 4️⃣ Arduino Uno R3

```bash
# Open Arduino IDE
# Install libraries:
# - Adafruit_SSD1306
# - DFPlayer Mini Mp3
# Upload the sketch to Arduino Uno R3
```

---

## 🧪 Usage Example

**Scenario:** User points camera at a water bottle

1. 📸 ESP32-CAM captures the image
2. 🧠 YOLOv8 detects: **"bottle"** (confidence: 95%)
3. 🔊 Speaker pronounces: **"bottle"** /ˈbɑː.t̬əl/
4. 📺 OLED displays: **BOTTLE**
5. 📱 MAUI app logs:
   ```
   Object: Bottle
   Time: 2025-11-14 10:30:45
   Confidence: 95%
   Image: [thumbnail]
   ```

---

## 👥 Team

This project is developed by a team of **4 members**:

- **Hardware & AI Developer** - ESP32-CAM, Arduino integration, YOLOv8 model, Django backend
- **Mobile Developer** - .NET MAUI application
- **Backend Developer** - Django REST API
- **Hardware Designer** - Circuit design and assembly

---

## 🚀 Future Improvements

- [ ] **Offline AI Detection** - Run YOLOv8 directly on ESP32
- [ ] **Phonetic Transcription** - Display IPA pronunciation
- [ ] **Vocabulary Categories** - Organize words by topics
- [ ] **Multi-language Support** - Translation to Vietnamese, Spanish, etc.
- [ ] **Spaced Repetition** - Smart review algorithm
- [ ] **Voice Recognition** - Practice pronunciation
- [ ] **Cloud Sync** - Backup learning progress
- [ ] **Gamification** - Points, achievements, and streaks

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

<div align="center">

⭐ Star this repository if you find it helpful!

</div>
