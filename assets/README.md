# Project Assets

This directory contains all centralized assets for the RC Gamepad Dongle project.

## Directory Structure

### `images/`
Contains all images, logos, diagrams, and visual assets:
- **`logo.png`** - Main project logo (256x256)
- **`logo_512.png`** - High-resolution logo (512x512) 
- **`logo.ico`** - Windows icon format (generated during build)
- **`custom-pcb.jpg`** - Photo of the assembled custom PCB
- **`original.jpg`** - Original photo/reference
- **`original.xcf`** - GIMP project file for logo editing
- **`ProMicroImplementation.fzpz_bb.png`** - Breadboard wiring diagram
- **`ProMicroImplementation2.fzpz_bb.png`** - Alternative wiring view
- **`screenshots/`** - Application screenshots and interface documentation
  - **`configurator-general.png`** - General configuration tab interface
  - **`configurator-axes.png`** - Axes mapping configuration interface

### `fritzing/`
Contains Fritzing circuit design files:
- **`ProMicroImplementation.fzpz.fzz`** - Editable Fritzing project file for breadboard layout

### `desktop/` 
Contains desktop application integration files:
- **`rc-gamepad-configurator.desktop`** - Linux desktop entry for configurator
- **`rc-gamepad-dongle.desktop`** - Linux desktop entry for main application

### Root Level Files
- **`default.json`** - Default channel configuration template used by the configurator

## Usage Notes

- Images are referenced by the configurator application and build scripts
- Fritzing files can be opened with Fritzing for editing circuit diagrams  
- Desktop files are used by Linux builds for application integration
- All paths in the codebase have been updated to reference this centralized location

## File Sizes

Most image files are optimized for both quality and size. The high-resolution logo (512x512) is used for application icons and documentation.