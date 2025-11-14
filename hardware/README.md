# RC Gamepad Dongle Hardware

This folder contains the Arduino firmware and hardware documentation for the RC Gamepad Dongle.

## Building Your Dongle

You can build this project two ways: you can solder a frankenstein or build a custom PCB

### Option 1: Frankenstein Build

**What You'll Need:**
- Arduino Pro Micro (16MHz/5V version)
- 10kΩ resistor (for the mode switch pullup)
- Toggle switch (SPDT works great)
- WS2812 LED (optional, but helpful for status feedback)
- Breadboard and jumper wires / soldering iron and wire

**Wiring It Up:**

![Wiring Diagram](assets/ProMicroImplementation.fzpz_bb.png)

### Option 2: Custom PCB

The custom PCB includes everything you need in a compact package.

![PCB Schematic](PCB/SCH_RC-Gamepad-Dongle%20V0.1_1-P1_2025-11-13.png)

**PCB Features:**
- Hardware SBUS signal inverter
- Proper RC connectors for clean wiring
- Status LED

**Design Files (in `PCB/` folder):**
- **[Gerber files](PCB/Gerber_RC-Gamepad-Dongle_V0.1_2025-11-13.zip)**: Ready to upload to any PCB manufacturer
- **[Schematic](PCB/SCH_RC-Gamepad-Dongle%20V0.1_2025-11-13.pdf)**: Complete circuit diagram (PDF format)
- **[BOM](PCB/BOM_RC-Gamepad-Dongle%20V0.1_RC-Gamepad-Dongle%20V0.1_2025-11-13.xlsx)**: Full parts list with quantities
- **[DXF file](PCB/DXF_RC-Gamepad-Dongle%20V0.1_2025-11-13_AutoCAD2007.dxf)**: Mechanical dimensions for enclosure design

**Getting PCBs Made:**
1. Upload the [Gerber ZIP file](PCB/Gerber_RC-Gamepad-Dongle_V0.1_2025-11-13.zip) to your PCB manufacturer (JLCPCB, PCBWay, OSH Park, etc.)
2. Order the parts from the BOM spreadsheet
3. Solder the components yourself, or use a PCBA service

## Uploading Firmware

Make sure you have PlatformIO installed, then:

```bash
cd hardware/
pio run --target upload
```

## Supported RC Protocols

| Protocol | Status | Baud Rate | Notes |
|----------|--------|-----------|-------|
| **IBUS** | ✅ Tested | 115200 | Works great with FlySky receivers |
| **PPM** | ✅ Tested | N/A | Standard 8-channel PPM |
| **SBUS** | ⚠️ Untested | 100000 | Needs hardware inverter (included in PCB) |
| **CRSF** | ⚠️ Untested | 420000 | TBS Crossfire protocol |
| **DSMX** | ⚠️ Untested | 115200 | Spektrum DSMX |
| **DSM2** | ⚠️ Untested | 115200 | Spektrum DSM2 |
| **FPORT** | ⚠️ Untested | 115200 | FrSky F.Port |

**Note:** Only IBUS and PPM have been verified with actual hardware. The other protocols are implemented according to their specs but need testing. If you try one, let us know how it goes!

**Important:** Only connect one receiver at a time to avoid signal conflicts.

## RC Protocol Connections

### For Breadboard Builds
- **IBUS/PPM/CRSF/DSM/FPORT**: Connect directly to Pin 0 (RX)
- **SBUS**: Requires a hardware inverter circuit (see PCB design for reference)

### For PCB Builds
- **IBUS/PPM/CRSF/DSM/FPORT**: Use the IBUS port
- **SBUS**: Use the SBUS port

## Status LED Guide

If you added the WS2812 LED, here's what the colors mean:

| Color | Pattern | What It Means |
|-------|---------|---------------|
| **Blue** | Solid | Configuration mode is active |
| **Green** | Solid | Joystick mode, receiving RC data |
| **Dim Green** | Solid | Joystick mode, waiting for RC data |
| **Red** | Flashing | Error - check your connections |
| **Yellow** | Flashing | Saving configuration to memory |

## Joystick Controls

The dongle can emulate a full-featured USB joystick with:

**Analog Axes:**
- X, Y, Z axes
- Rx, Ry, Rz axes
- Rudder, Throttle, Accelerator, Brake, Steering

**Digital Controls:**
- 32 individual buttons
- 2 hat switches (8-direction controls)

You can map any RC channel (1-16) to any control, or leave controls unmapped if you don't need them.

## Troubleshooting

**LED not working?**
- Check the WS2812 wiring and power connections
- Make sure the LED data pin is connected to pin 5

**Computer not recognizing the dongle?**
- Verify your Arduino Pro Micro is functioning (should show up as a COM port)
- Try a different USB cable
- Check that the firmware uploaded successfully

**No RC data coming through?**
- Make sure your receiver is bound to your transmitter
- Check the protocol setting in the configurator matches your receiver
- Verify the receiver data wire is connected to pin 0
- For SBUS on breadboard, you need a hardware inverter

**SBUS not working on breadboard?**
- SBUS uses an inverted signal that needs hardware inversion
- Use the PCB design which has the inverter built-in, or add an inverter to your breadboard

## Files in This Folder

**Fritzing Diagrams (`assets/` folder):**
- `ProMicroImplementation.fzpz.fzz` - Editable Fritzing project file
- `ProMicroImplementation.fzpz_bb.png` - Breadboard wiring diagram
- `ProMicroImplementation2.fzpz_bb.png` - Alternative wiring view

**PCB Design (`PCB/` folder):**
- Gerber files for PCB manufacturing
- Schematic PDF
- Bill of materials spreadsheet
- Mechanical DXF drawings

**Firmware (`src/` folder):**
- `main.cpp` - Arduino firmware source code

## Need Help?

Check the main project README for more information, or open an issue on the GitHub repository if you run into problems.

## License

MIT License - see the main project for details.
