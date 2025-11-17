# RC Gamepad Dongle Configurator

![RC Gamepad Configurator](../../assets/images/logo.png)

This is the desktop app that lets you configure your RC Gamepad Dongle. It handles all the channel mapping and protocol settings through a simple interface, so you don't need to mess with code or config files.

## What It Does

The configurator connects to your dongle over USB and lets you:
- Choose which RC protocol you're using (IBUS, PPM, SBUS, etc.)
- Map your RC channels to specific joystick controls
- Save your configuration directly to the dongle
- Load and backup your settings

Works on both Windows and Linux.

### Interface Overview

![General Configuration](../../assets/images/screenshots/configurator-general.png)
*General tab: Select your RC protocol and configure basic settings*

![Axes Configuration](../../assets/images/screenshots/configurator-axes.png)
*Axes tab: Map RC channels to joystick axes with real-time preview*

## Quick Start

### Windows
1. Download the latest `.exe` file from releases
2. Run the executable - no installation needed

### Linux  
1. Download the latest `.AppImage` file from releases
2. Make it executable: `chmod +x RC_Gamepad_Configurator-x86_64.AppImage`
3. Run: `./RC_Gamepad_Configurator-x86_64.AppImage`

### Running from Source
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cd src
python rc-gamepad-dongle.py
```

## Building the App

### Windows
```powershell
.\scripts\windows\build-exe.ps1
```
This creates an `.exe` file in `src\dist\` that you can run without installing Python.

### Linux
```bash
./scripts/linux/build-appimage.sh
```
This builds an AppImage in the `build/` folder that runs on most Linux distributions.

## Development Setup

Want to modify the configurator or run it from source? Here's what you need:

### Requirements
- Python 3.8 or newer
- PySide6 (Qt for Python)
- PyInstaller (for building executables)
- Pillow (image handling)

### Getting Started
```bash
pip install -r requirements.txt
```

## Configuration Files

The configurator uses these key files:
- **`../../assets/default.json`** - Default channel mappings
- **`assets/`** - UI assets (moved to `../../assets/`)

## More Info

Check the main project documentation in `../../docs/` for complete setup instructions.
