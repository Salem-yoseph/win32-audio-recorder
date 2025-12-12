![Audio Recorder Cover](cover.png)

# 🎙️ Win32 Audio Recorder

A lightweight native Windows console audio recorder written in C using the WinMM (Windows Multimedia) API.  
Records microphone audio to PCM WAV files, supports **Start / Stop / Pause / Resume**, creates **new files automatically** for each session, and shows a live recording timer — all without external libraries.

---

## ✨ Features

- 🎚️ Start, Stop, Pause, and Resume recording  
- ♾️ Unlimited recording duration (streams directly to disk)  
- 💾 New WAV file created automatically for each session  
- ⏱️ Real-time recording timer  
- 🎤 Records from the default microphone  
- 🔧 Uses only built-in Windows APIs (`windows.h`, `mmsystem.h`, `winmm.lib`)  
- 📦 Outputs proper 16-bit PCM, 44.1 kHz WAV files  

---

## 🛠️ Build Instructions

### **Using MinGW/MSYS2 (Recommended)**  
> Open the **MSYS2 MinGW 64-bit** terminal, not PowerShell.

```bash
gcc record.c -o record.exe -lwinmm
