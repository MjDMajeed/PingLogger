# 📚 PingLogger v1.1 - Complete User Guide

**PingLogger** is a specialized network monitoring utility designed for **Plant Technicians, Automation Engineers, and IT Professionals**.

In an industrial plant environment, maintaining connectivity is critical. Whether you are troubleshooting **ETS (Energy Transfer Stations)**, monitoring **Servers & Routers**, or checking the status of **CCTV Cameras and Industrial PCs**, PingLogger helps you track uptime and detect connection drops instantly.

It allows simultaneous monitoring of multiple critical devices, logs uptime/downtime events for maintenance reports, and ensures continuous operation with auto-resume capabilities—making it an essential tool for **Automation Maintenance**.

---

## 🚀 Key Features

### 1. ⚡ Auto-Resume System
* **How it works:** The app continuously saves its state (Running/Stopped, Single/Multi Mode, Target IPs).
* **Scenario:** If your Control Room PC restarts due to a power cut or update, simply launch PingLogger (or let it auto-start). It will detect the improper shutdown and **immediately resume pinging** the last targets (e.g., your PLC or Gateway) without you clicking anything.

### 2. 🧹 Deep Cleaning (Smart Maintenance)
* **Startup Cleaner:** It scans the Windows Startup folder and removes broken or old shortcuts (e.g., `PingLogger v1.0.lnk`) to prevent duplicate startup entries that slow down the system.
* **Ghost Killer:** If an old instance of the app is stuck in the background (hidden), the "Kill Background Instances" button forcefully clears it using PID filtering to ensure fresh logging.

### 3. 🛡️ App Auto-Close (Safety Guard)
* **Purpose:** To prevent the app from running indefinitely on forgotten maintenance PCs.
* **Settings:** You can set it to close after `1 Week`, `1 Month`, or `1 Year`.
* **Default:** `Never` (But includes a **90-Day safety hard-limit**).
* **Action:** When the limit is reached, the app stops logging, removes itself from Startup, and closes completely to free up system resources.

---

## 📖 How to Use

### 🟢 Single Target Mode
*Best for: Detailed monitoring of one critical device (e.g., Main BMS Server).*

1.  **Enter IP:** Type the IP address (e.g., `192.168.1.100`) or Hostname.
2.  **Nickname:** Add a label like "Chiller Plant PLC" (Optional).
3.  **Action:** Click **[ START LOGGING ]**.
    * **Left Side:** Controls become disabled to prevent accidental changes.
    * **Right Side:** A large Command Prompt style window shows live ping replies.
4.  **History:** Your typed IP is automatically saved. To delete an old IP, select it and click the small **[ ✖ ]** button.

### 🟣 Multi-Target Mode
*Best for: Monitoring a whole network segment (e.g., All ETS stations).*

1.  **Activate:** Check the box **☑ Enable Multi-Target Mode**.
2.  **Add Devices:**
    * Enter IP -> Click **[ ADD + ]**.
    * Repeat this for up to 5 devices (e.g., ETS-1, ETS-2, Camera-Gate, etc.).
3.  **Start:** Click the purple **[ START MULTIPLE LOGGING ]** button.
4.  **Monitoring:**
    * The list will show **Status** (RUNNING/STOP) and **Reply Time** (e.g., `4ms` or `RTO`).
    * **Live Comparison:** Hold the **`Ctrl`** key and click on multiple IPs in the list. The right panel will split to show live logs for all selected devices stacked vertically.

---

## ⚙️ Settings Menu

### 🔹 General
* **Ping Interval:** Time between pings in milliseconds (Default: `1000` = 1 sec).
* **Auto-Scroll:** Keeps the log view focused on the newest entry.
* **Beep on Fail:** Plays a sound alert if a Request Timed Out (RTO) occurs (Useful for finding loose cables).
* **Minimize to Tray:** Hides the app from the taskbar when minimized (runs silently in the system tray).

### 🔹 Startup & Automation
* **ENABLE Startup:** Adds the app to Windows Startup folder.
* **Start Minimized:** App launches silently in the background on boot.
* **Resume Last Session:** **(Recommended ON)** Enables the crash-recovery/auto-resume feature for critical monitoring.

### 🔹 System Health
* **Kill Background Instances:** Manually triggers the cleanup logic for stuck processes and old shortcuts.
* **Auto-Close Timer:** Select a duration after which the app should self-terminate.

---

## 📂 Understanding Logs
Logs are saved in the `PingLogs` folder located next to the application executable.

* **File Naming:** `IP-Address_Date_Nickname.txt`
* **Content Example:**
    ```text
    Reply from 192.168.1.50: bytes=32 time=12ms TTL=115
    Request Timed Out
    [SYSTEM] Windows was OFF for: 0 Hours 5 Minutes
    ```
    *(The system downtime log helps track power failures in the control room).*

---

## ❓ FAQ / Troubleshooting

**Q: My Taskbar icon is missing?**
A: This is usually a Windows Cache issue. Try moving the `.exe` to a new folder or renaming it. The app has code to force the icon, so a reboot usually fixes it.

**Q: Why is "Kill Background" not deleting my shortcut?**
A: The cleaner specifically looks for shortcuts containing the word **"PingLogger"**. Ensure your shortcut is named correctly (e.g., `PingLogger.lnk`).

**Q: High Power Usage?**
A: Ensure you are using **v1.1 (Eco Mode)**. It optimizes disk writing (saves settings every 10s instead of 1s) and runs the ping process with IDLE priority.

---
*Developed by Majeed : Automation AI1*
