<div align="center">

# 📱 QuickChat — Bluetooth Chat Application

<img width="360" height="806" alt="quickchat" src="https://github.com/user-attachments/assets/8c3177f3-57cd-406d-a4b8-878131d97f3d" />

<br><br>

<img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=flat-square&logo=android&logoColor=white"/>
<img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white"/>
<img src="https://img.shields.io/badge/Transport-Bluetooth Classic-0082FC?style=flat-square&logo=bluetooth&logoColor=white"/>
<img src="https://img.shields.io/badge/Min API-21-orange?style=flat-square"/>
<img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
<br><br>

[Features](#-features) · [How to Run](#-how-to-run) · [How to Connect](#-how-to-connect--chat) · [Protocol](#-protocol-design) · [Permissions](#-permissions)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [How to Connect & Chat](#-how-to-connect--chat)
- [Protocol Design](#-protocol-design)
- [Permissions](#-permissions)
- [Demo Video](#-demo-video)
- [Assignment Info](#-assignment-info)

---

## 🔍 Overview

QuickChat is an Android application that lets two smartphones communicate directly over **Bluetooth Classic (RFCOMM)** — completely offline, no Wi-Fi or mobile data needed. It works like a standard messaging app (WhatsApp-style UI) but over a direct Bluetooth connection.

Built as part of the **CNDC assignment** at SZABIST Islamabad, the app covers device discovery, real-time messaging, file transfer with progress tracking, delivery receipts, and message timestamps.

---

## ✨ Features

| Feature | Status |
|--------|--------|
| 🔍 Device Discovery — scan & list nearby Bluetooth devices | ✅ Done |
| 💬 Real-Time Text Messaging — send & receive instantly | ✅ Done |
| 📁 File Transfer — images, PDFs with live progress bar | ✅ Done |
| 🟢 Connection Status — connected / disconnected / scanning indicators | ✅ Done |
| 🕐 Message Timestamps — time shown on every message bubble | ✅ Done |
| ✅ Delivery Receipts — sender notified when message is received | ✅ Done |

---

## 🛠 Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Kotlin |
| Platform | Android (Native) |
| Bluetooth | Bluetooth Classic — RFCOMM / SPP |
| Min SDK | API 21 (Android 5.0+) |
| IDE | Android Studio |
| UI | XML Layouts |

---

## 📁 Project Structure

```
bluetooth-chat-application/
├── .idea/                          ← Android Studio project settings
├── app/                            ← Main application module
│   └── src/
│       └── main/
│           ├── java/com/example/quickchat/
│           │   ├── MainActivity.kt        ← Chat UI + device discovery
│           │   └── BluetoothService.kt    ← Connection + data transfer
│           ├── res/
│           │   ├── layout/
│           │   │   └── activity_main.xml  ← Main UI layout
│           │   └── drawable/
│           │       └── bg_input.xml       ← Input field background
│           └── AndroidManifest.xml        ← Permissions & app config
├── gradle/                         ← Gradle wrapper files
├── .gitignore                      ← Git ignored files
├── README.md                       ← Project documentation
├── build.gradle.kts                ← Project build config
├── gradle.properties               ← Gradle properties
├── gradlew                         ← Gradle wrapper (Linux/Mac)
├── gradlew.bat                     ← Gradle wrapper (Windows)
├── settings.gradle.kts             ← Project settings
├── protocol design document.pdf   ← Protocol design document
└── quickchat.jpeg                  ← App screenshot
```

---

## 🚀 How to Run

### Prerequisites
- Android Studio **Hedgehog** or later
- Two Android devices (API 21+) with Bluetooth support
- USB cable for initial installation

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/QuickChat-Bluetooth.git
cd QuickChat-Bluetooth
```

**2. Open in Android Studio**
```
File → Open → Select the project folder
```

**3. Sync Gradle**
> Android Studio will prompt automatically — click **Sync Now**

**4. Build & Install on both devices**
```
Run ▶ → Select your device → OK
```
> Repeat for the second device.

---

## 🔗 How to Connect & Chat

1. Open QuickChat on **both devices**
2. On **Device A** → tap **Scan** to search for nearby devices
3. On **Device B** → make sure Bluetooth is ON and device is **discoverable**
4. On **Device A** → tap Device B's name from the list to connect
5. Once connected → type a message and tap **Send** ✈️
6. To send a file → tap the **📎 attachment button** and pick a file

---

## 📡 Protocol Design

> 📄 See the full **[Protocol Design Document]([./Protocol_Design_Document.pd](https://github.com/nihahawas/bluetooth-chat-application/blob/master/protocol%20design%20document.pdf)f)** for byte-level details, flow diagrams, and error handling.


---

## Quick Summary

QuickChat uses a custom binary protocol over RFCOMM. Every packet has a **5-byte header** followed by a variable-length payload:


[ TYPE (1 byte) ][ LENGTH (4 bytes) ][ PAYLOAD (LENGTH bytes) ]


| Type Code | Packet Name | Purpose |
|-----------|-------------|---------|
| `0x01` | TEXT_MESSAGE | A chat text message |
| `0x02` | FILE_START | Announces a file transfer with metadata |
| `0x03` | FILE_CHUNK | One 4 KB piece of the file |
| `0x04` | FILE_END | End of file + MD5 checksum for verification |
| `0x05` | ACK | Delivery acknowledgement (success/failure) |
| `0x06` | PING | Keep-alive signal |

---

## 🔐 Permissions

The following permissions are required and requested at runtime on Android 12+:

| Permission | Required For | Android Version |
|------------|-------------|-----------------|
| `BLUETOOTH` | Basic Bluetooth operations | All versions |
| `BLUETOOTH_ADMIN` | Device discovery & pairing | All versions |
| `BLUETOOTH_CONNECT` | Connecting to paired devices | Android 12+ |
| `BLUETOOTH_SCAN` | Scanning for nearby devices | Android 12+ |
| `ACCESS_FINE_LOCATION` | Bluetooth device discovery | Android 6+ |
| `READ_EXTERNAL_STORAGE` | Picking files to send | All versions |

---

## 🎥 Demo Video

> 📹 **[Watch Demo Video](#)** 

The demo shows:
- Two real Android devices connecting over Bluetooth
- Sending and receiving text messages in real time
- Transferring a file with the progress bar

---

## 📚 Assignment Info

| Field | Detail |
|-------|--------|
| Student | Niha Hawas |
| Program | BSCS-6B |
| Institute | SZABIST Islamabad |
| Course | CNDC — Computer Networks & Data Communications |
| Assignment | Bluetooth Chat Application |
| Year | 2026 |

---

## 👨‍💻 Author

Developed by: Niha Hawas
- 🐙 GitHub: [github.com/nihahawas](https://github.com/nihahawas)
- 💼 LinkedIn: [linkedin.com/in/nihahawas45](https://linkedin.com/in/nihahawas45)

---

<div align="center">
Made with ❤️ by <strong>Niha Hawas</strong> — SZABIST Islamabad 2025
</div>

---
