# 🎙️ Win32 Audio Recorder

<p align="center">
  <img src="cover.png" alt="Audio Recorder Cover" width="800">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Language-C-blue.svg">
  <img src="https://img.shields.io/badge/Platform-Windows-0078D6.svg">
  <img src="https://img.shields.io/badge/Build-Passing-brightgreen.svg">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg">
  <img src="https://img.shields.io/github/stars/Salem-yoseph/win32-audio-recorder?style=social">
</p>

A lightweight native Windows console audio recorder written in C using the WinMM (Windows Multimedia) API.  
Supports **Start / Stop / Pause / Resume**, **unlimited recording**, **automatic WAV naming**, and **live timer display**.

---

## ✨ Features

- 🎚️ Start, Stop, Pause, and Resume recording  
- ♾️ Unlimited recording duration (streams directly to disk)  
- 💾 Auto-generated filenames (`record_001.wav`, `record_002.wav`, …)  
- ⏱️ Real-time recording timer  
- 🎤 Records from default Windows microphone  
- 🔧 Uses only built-in Windows APIs (`windows.h`, `mmsystem.h`, `winmm.lib`)  
- 📦 Outputs correct 16-bit PCM WAV files  

---

## 🛠️ Build Instructions

### 🔵 Using MSYS2 MinGW64 (Recommended)

> IMPORTANT: Run in **MSYS2 MinGW 64-bit Terminal**, NOT PowerShell.

```bash
gcc record.c -o record.exe -lwinmm
### 🟣 Using Microsoft Visual C++ (Developer Command Prompt)
cl record.c winmm.lib
▶️ Usage

Run:

record.exe

Keyboard Controls

Key  	Action
1	    Start recording
2	    Stop and save WAV file
3    	Pause recording
4   	Resume recording
5   	Exit program

Output Files Example

record_001.wav
record_002.wav
record_003.wav

🔧 Technical Overview

The program uses the WinMM WaveIn API for capturing microphone audio.

Audio Format

PCM

44.1 kHz

16-bit

Mono

Main WinMM Functions Used

waveInOpen — open default audio input

waveInPrepareHeader — prepare buffers

waveInAddBuffer — queue buffers

waveInProc — callback when filled

waveInStart — begin capture

waveInStop — stop capture

waveInClose — close device

WAV File Handling

Reserves 44-byte header

Streams PCM audio directly to disk

Updates header sizes on stop

This enables unlimited recording with low RAM usage.

🔊 Audio Pipeline Diagram

Microphone
    ↓
WinMM (waveInOpen)
    ↓
Audio Buffers (WAVEHDR)
    ↓
Callback (waveInProc)
    ↓
Write PCM to File
    ↓
After Stop → Fix WAV Header
    ↓
Your WAV File 🎧

📁 Project Structure
win32-audio-recorder/
│
├── record.c          # Main program
├── README.md         # Documentation
├── LICENSE           # MIT License
└── cover.png         # Banner image

🩹 Troubleshooting
❗ gcc: command not found

➡ You're in PowerShell.
Open MSYS2 MinGW 64-bit.

❗ undefined reference to waveInOpen

➡ Missing library:
-lwinmm

❗ Keys do not respond

➡ Click inside the terminal window to give it focus.

❗ No audio recorded

➡ Check Windows Settings → Privacy → Microphone → Allow apps to access microphone.

📜 License (MIT)
MIT License

Copyright (c) 2025 Salem

Permission is hereby granted...

🙏 Acknowledgments

Microsoft WinMM API

Win32 documentation & examples

Audio DSP & WAV format references
