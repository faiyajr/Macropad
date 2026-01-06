# RP2040 Mechanical Macropad 

Simple USB macropad using an RP2040 microcontroller, Cherry MX-style switches,
and a diode-protected key matrix for reliable key scanning.

---

## Overview

- MCU: RP2040
- Switches: Cherry MX–style mechanical switches
- Diodes: 1N4148 (through-hole)
- Matrix: Row/column diode key matrix
- Designed in: Altium Designer

Each key uses a series diode to prevent ghosting and allow multiple
simultaneous key presses.

---

## Key Electrical Design

- MX switch connected between column and diode
- Diode placed **in series** with each switch
- Diode orientation:  
  **Anode → Switch**, **Cathode → Row**
- Rows and columns connected to RP2040 GPIOs
- Internal pull-ups/down configured in firmware

Typical scan direction:
- Columns = outputs
- Rows = inputs

---

## Main Components

### Microcontroller
- **RP2040**
  - Common package: QFN-56
  - Example footprint (VERIFY):
    - `RP2040-QFN-56-7x7mm-P0.4mm`

### Key Switch
- **Cherry MX / MX-compatible**
  - Through-hole, PCB mount
  - Example footprint (VERIFY):
    - `MX-1U`
    - `MX-ALPS-1U`

### Diode
- **1N4148** (DO-35, through-hole)
  - Used for anti-ghosting in key matrix
  - Example footprint (VERIFY):
    - `DO-35`
    - `AXIAL-0.3`

---
### Case
  - Case designed in Siemens NX with a mechanical fit for the USB-C port for the RP2040
  - The Case Designed in Siemens NX is designed to fit the PCB and Cherry MX switch footprint
  - 

---

## Matrix Notes

- One diode per switch (required)
- Keep row/column traces short and consistent
- Ground pour recommended on top and bottom layers
- Add stitching vias near MCU and between pours

---

## Firmware (High-Level)

- USB HID keyboard
- Matrix scanning with debounce
- GPIO mapping matches PCB rows/columns

Compatible with:
- Pico SDK
- TinyUSB
- [QMK](https://qmk.fm/) (with custom RP2040 board definition)

---

## Status

- [x] Schematic complete
- [x] Key matrix defined
- [ ] Footprints verified
- [ ] PCB routing
- [ ] Firmware bring-up
