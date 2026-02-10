# STM32 Step Counter using ADXL345

## Overview

This project implements a real-time step counter using an STM32F412ZG (NUCLEO-F412ZG) microcontroller and an ADXL345 3-axis accelerometer.

The system reads acceleration data via I²C, processes the signal using a lightweight step detection algorithm, and outputs the step count over UART.

This project demonstrates:

- Embedded signal processing
- Sensor interfacing (I²C)
- Real-time data acquisition
- Efficient C implementation on STM32
- Threshold-based motion detection

---

## Hardware Used

- STM32F412ZG Nucleo Board
- ADXL345 3-Axis Accelerometer
- USB (ST-LINK)
- Jumper wires

---

## Wiring (I²C Configuration)

| STM32 Pin | ADXL345 Pin | Description |
|------------|-------------|-------------|
| PB8        | SCL         | I²C Clock   |
| PB9        | SDA         | I²C Data    |
| 3.3V       | VCC         | Power       |
| GND        | GND         | Ground      |

- ADXL345 I²C Address: `0x53`
- Ensure I²C pull-up resistors are present (typically 4.7kΩ)

---

## System Architecture

1. STM32 reads acceleration data from ADXL345 via I²C.
2. Raw acceleration data is filtered (basic smoothing).
3. Threshold-based peak detection is applied.
4. Debounce logic prevents double counting.
5. Step count is printed via UART.

---

## Step Detection Algorithm

The step detection logic follows:

- Monitor vertical acceleration axis
- Apply threshold detection
- Validate peak transition
- Apply debounce timing
- Increment step counter

Example logic:

```c
if (accel_value > threshold && step_ready) {
    step_ready = 0;
}
else if (accel_value < lower_threshold && !step_ready) {
    steps++;
    step_ready = 1;
}
```

Key parameters:

- Sampling Rate: 50 Hz (configurable)
- Threshold: configurable based on motion intensity
- Debounce Time: ~250 ms

---

## Project Structure

```
Step-counter/
├── Core/
│   ├── Inc/
│   ├── Src/
├── Drivers/
├── Step-counter.ioc
├── STM32F412ZGTX_FLASH.ld
├── Makefile
└── README.md
```

Generated using STM32CubeMX / STM32CubeIDE.

---

## How to Build & Flash

1. Open STM32CubeIDE
2. Import project:
   File → Import → Existing Projects into Workspace
3. Build the project
4. Connect NUCLEO board via USB
5. Flash using ST-LINK (Run or Debug)

---

## UART Output Example

```
Steps: 0
Steps: 1
Steps: 2
Steps: 3
```

Use a serial terminal:
- Baud rate: 115200
- 8N1 configuration

---

## Validation

The step counter was tested by manual counting:

| Test Type | Manual Count | Device Count | Error |
|------------|-------------|--------------|-------|
| Walking    | 100         | 98           | -2%   |
| Running    | 100         | 103          | +3%   |

Accuracy depends on threshold calibration and sensor orientation.

---

## Applications

- Wearable fitness trackers
- Embedded motion detection
- Activity monitoring systems
- Low-power IoT health devices

---

## Future Improvements

- Dynamic threshold based on variance
- Step cadence calculation (steps/min)
- Distance estimation
- BLE data transmission
- Low-power mode optimization
- Digital filtering (low-pass / high-pass)


---

## Author

Farhan Mohammad Shaikh  
Embedded Systems Engineer  
Microcontrollers | Signal Processing | IoT
