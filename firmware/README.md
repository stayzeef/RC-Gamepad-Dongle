# RC Gamepad Dongle Firmware

This directory contains the Arduino firmware for the RC Gamepad Dongle. The firmware runs on an Arduino Pro Micro and handles converting RC signals into USB HID joystick commands.

## Building and Uploading

Make sure you have PlatformIO installed, then run:

```bash
cd firmware/
pio run --target upload
```

**Note:** If your Arduino Pro Micro doesn't have a bootloader or it's corrupted, you can use the ICSP header on the custom PCB to program it with an Arduino Uno. See the [Hardware Documentation](../hardware/README.md#programming-the-arduino-pro-micro) for detailed ICSP programming instructions.

## Firmware Features

- **Multiple RC Protocol Support**: IBUS, PPM, SBUS, CRSF, DSMX, DSM2, FPORT
- **Full HID Support**: 6 axes, 32 buttons, and 2 hat switches  
- **Configuration Mode**: Switch between config and joystick modes
- **Status LED**: Visual feedback with WS2812 LED
- **EEPROM Storage**: Saves configuration settings

## Hardware Connections

- **Pin 0 (RX)**: RC receiver signal input
- **Pin 3**: Mode switch (HIGH = config mode, LOW = joystick mode)
- **Pin 5**: WS2812 status LED (optional)
- **GND**: Ground connection
- **VCC**: 5V power

## Status LED Colors

| Color | Pattern | Meaning |
|-------|---------|---------|
| Blue | Solid | Configuration mode active |
| Green | Solid | Joystick mode, receiving RC data |
| Dim Green | Solid | Joystick mode, waiting for RC data |
| Red | Flashing | Error - check connections |
| Yellow | Flashing | Saving configuration |

## Supported RC Protocols

| Protocol | Status | Baud Rate | Notes |
|----------|--------|-----------|-------|
| IBUS | ✅ Tested | 115200 | Works with FlySky receivers |
| PPM | ✅ Tested | N/A | Standard 8-channel PPM |
| SBUS | ⚠️ Untested | 100000 | Requires hardware inverter |
| CRSF | ⚠️ Untested | 420000 | TBS Crossfire protocol |
| DSMX | ⚠️ Untested | 115200 | Spektrum DSMX |
| DSM2 | ⚠️ Untested | 115200 | Spektrum DSM2 |
| FPORT | ⚠️ Untested | 115200 | FrSky F.Port |

## Files

- `platformio.ini` - PlatformIO project configuration
- `src/main.cpp` - Main firmware source code
- `include/` - Header files directory
- `test/` - Unit test directory

For hardware wiring diagrams and PCB designs, see the `../assets/` and `../hardware/` directories.