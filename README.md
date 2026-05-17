# 📱 QuickChat — Bluetooth Messaging App

A real-time Bluetooth chat application for Android that allows two devices to connect, exchange text messages, and transfer files — just like WhatsApp, but over Bluetooth Classic.

---

## 🚀 Features

- 🔍 **Device Discovery** — Scan for nearby Bluetooth devices and connect with one tap
- 💬 **Real-Time Messaging** — Send and receive text messages instantly
- 📁 **File Transfer** — Send images, PDFs, and other files with a live progress bar
- 🟢 **Connection Status** — Clear indicators for connected, disconnected, and scanning states
- 🕐 **Message Timestamps** — Each message bubble shows the time it was sent
- ✅ **Delivery Receipts** — Know when your message has been received

---

## 📋 Requirements

- Android Studio **Hedgehog** or later
- Android SDK **21+** (Android 5.0 Lollipop and above)
- Two Android devices with **Bluetooth Classic** support
- Both devices must have Bluetooth **turned on** and be within range (~10 meters)

---

## 🛠️ How to Run

### Step 1: Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/QuickChat-Bluetooth.git
cd QuickChat-Bluetooth
```

### Step 2: Open in Android Studio
- Open **Android Studio**
- Click **File → Open**
- Select the cloned project folder

### Step 3: Sync Gradle
- Android Studio will automatically prompt to sync Gradle
- Click **Sync Now** if prompted

### Step 4: Grant Permissions
The app requires the following permissions (requested at runtime on Android 12+):
- `BLUETOOTH`
- `BLUETOOTH_ADMIN`
- `BLUETOOTH_CONNECT`
- `BLUETOOTH_SCAN`
- `ACCESS_FINE_LOCATION`
- `READ_EXTERNAL_STORAGE`

### Step 5: Build & Run
- Connect your Android device via USB or use an emulator
- Click the **Run ▶** button in Android Studio
- Select your device and click **OK**

### Step 6: Test with Two Devices
1. Install the app on **both devices**
2. On **Device A**: Tap **Scan** to discover nearby devices
3. On **Device B**: Make sure Bluetooth is on and the device is **discoverable**
4. On **Device A**: Tap on Device B from the list to connect
5. Once connected, start chatting!

---

## 📁 Project Structure

```
QuickChat-Bluetooth/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/quickchat/
│   │   │   │   ├── MainActivity.kt          # Main chat + device discovery UI
│   │   │   │   └── BluetoothService.kt      # Bluetooth connection & data transfer
│   │   │   ├── res/
│   │   │   │   ├── layout/
│   │   │   │   │   └── activity_main.xml    # Main layout
│   │   │   │   └── drawable/
│   │   │   │       └── bg_input.xml         # Input field background
│   │   │   └── AndroidManifest.xml
│   └── build.gradle
└── README.md
```

---

## 🔧 Technology Stack

| Component | Technology |
|-----------|-----------|
| Language | Kotlin |
| Platform | Android (Native) |
| Bluetooth | Bluetooth Classic (RFCOMM) |
| Min SDK | API 21 (Android 5.0) |
| IDE | Android Studio |

---

## 📡 How It Works

1. **Server Device** — Listens for incoming Bluetooth connections using `BluetoothServerSocket`
2. **Client Device** — Discovers and connects to the server using `BluetoothSocket`
3. **Messaging** — Data is sent as UTF-8 encoded byte streams over RFCOMM
4. **File Transfer** — Files are chunked into packets and reassembled on the receiver side

---

## 👨‍💻 Author

**[Niha Hawas]**

CNDC Assignment — Bluetooth Chat App

---

## 📄 License

This project is submitted as part of an academic assignment at SZABIST. All rights reserved.
