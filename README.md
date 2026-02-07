# Step Counter Firmware for STM32F412ZG

![STM32F412ZG](https://www.st.com/content/ccc/resource/technical/document/datasheet/group0/5f/5d/42/63/6d/3f/4c/2b/DM00105618.pdf/files/DM00105618.pdf/jcr:content/translations/en.DM00105618.pdf)

Firmware for a step counter implemented on the **STM32F412ZG Nucleo board** using the **ADXL345 accelerometer**. The firmware features real-time accelerometer data acquisition, step detection, and display output.

---

## Features

- ✅ **6-axis accelerometer support** using ADXL345
- ✅ **Real-time step counting** using a custom step-detection algorithm
- ✅ **Low-latency display output** for immediate feedback
- ✅ Optimized for **embedded low-power operation**
- ✅ Easily extendable for wearable or IoT applications

---

## Hardware Requirements

- STM32F412ZG Nucleo board
- ADXL345 accelerometer (I2C interface)
- Optional: LCD/OLED display for real-time output
- Standard development peripherals (USB, jumper wires, breadboard)

---

## Software Requirements

- STM32CubeIDE (or compatible IDE)
- STM32 HAL libraries
- I2C driver support for ADXL345
- Standard C compiler for ARM Cortex-M4

---

## Project Structure

Step-counter/
│
├─ Core/ # Core firmware logic
├─ Drivers/ # HAL and peripheral drivers
├─ .mxproject # STM32CubeMX configuration
├─ STM32F412ZGTX_FLASH.ld # Linker script for Flash
├─ STM32F412ZGTX_RAM.ld # Linker script for RAM
└─ README.md # This file

## 📷 System Diagram

```text
+----------------+       I2C       +-----------------+
| STM32F412ZG    | <-------------- | ADXL345         |
| Nucleo Board   |                 | Accelerometer   |
|                |                 +-----------------+
|                |
|  Step Detection Algorithm         +----------------+
|  - Filtering                     | Display / Serial|
|  - Peak Detection                 +----------------+
+----------------+







