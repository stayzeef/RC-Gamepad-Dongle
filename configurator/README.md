# RC Gamepad Dongle Configurator

![RC Gamepad Configurator](assets/logo.png)

This is the desktop app that lets you configure your RC Gamepad Dongle. It handles all the channel mapping and protocol settings through a simple interface, so you don't need to mess with code or config files.

## What It Does

The configurator connects to your dongle over USB and lets you:
- Choose which RC protocol you're using (IBUS, PPM, SBUS, etc.)
- Map your RC channels to specific joystick controls
- Save your configuration directly to the dongle
- Load and backup your settings

Works on both Windows and Linux.

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

### Running from Source
```bash
cd src
python rc-gamepad-dongle.py
```

## More Info

Check out [scripts/README.md](scripts/README.md) for more detailed build instructions and troubleshooting tips.
