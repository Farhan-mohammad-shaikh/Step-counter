# Step Counter

## 🔍 Overview

This project implements a **wearable step counter** that detects and counts steps from real-time motion data. It reads accelerometer signals from a sensor, processes them using an embedded algorithm, and outputs step counts on an interface.

The goal is to demonstrate real-time signal processing, efficient embedded programming, and accurate step detection suitable for wearable health tracking applications.

---

## 📌 Features

- Real-time step detection and counting
- Threshold-based filtering for noise suppression
- Low–power suitable for microcontroller platforms
- Configurable sensitivity
- Compact and optimized embedded C implementation

---

## 🧠 How It Works

The step detector works by analyzing vertical acceleration and identifying peaks that correspond to steps:

1. Read accelerometer data samples at a fixed rate
2. Apply simple signal processing (smoothing/thresholding)
3. Detect rising edges above threshold
4. Increment step count on valid peaks
5. Display or log the count as steps

This approach is lightweight and well-suited for constrained MCUs and real-time systems.

---

## 🛠️ Hardware Requirements

| Component | Purpose |
|-----------|---------|
| Accelerometer (e.g. MPU6050) | Motion sensing |
| Microcontroller (e.g. ARM Cortex-M, ESP32) | Data acquisition and processing |
| Power source | Battery or USB |

> Ensure the accelerometer is oriented consistently so that gravity-aligned axis data is available for step detection.

---

## 📋 Software Requirements

- C compiler (GCC, ARM-GCC, ESP-IDF, etc.)
- Make or build system
- Optional: serial monitor (for output)

---

## 💻 Building & Running

1. Clone the repository:

   ```bash
   git clone https://github.com/Farhan-mohammad-shaikh/Step-counter.git
   ```

2. Navigate to the project:

   ```bash
   cd Step-counter
   ```

3. Compile:

   ```bash
   make
   ```

4. Run (on target or simulator):

   ```bash
   ./step_counter
   ```

5. Observe step counts printed to console or displayed on device.

---

## 🧪 Example Output

```
Steps:  0
Steps:  1
Steps:  2
Steps:  2
Steps:  3
```

---

## 🧠 Algorithm Description

The step detection algorithm uses:

- **Smoothing** to reduce noise
- **Thresholding** to identify peaks
- **Debounce logic** to prevent double counting

Example pseudo-logic:

```c
if (accel > threshold && !step_pending) {
    step_pending = true;
} else if (accel < lower_threshold && step_pending) {
    steps++;
    step_pending = false;
}
```

This gives reliable step counts with minimal computation.

---

## 📈 Performance and Tuning

Adjust these parameters for best results:

- `threshold` — sensitivity of peak detection
- `debounce_time` — minimum time between valid steps

A higher threshold reduces false steps, but may miss small steps.

---

## 📦 Project Structure

```
Step-counter/
├── src/
│   ├── main.c
│   ├── step_detector.c
│   └── step_detector.h
├── Makefile
├── README.md
└── examples/
```

---

## 📍 Next Improvements

Here are some suggestions for future upgrades:

- ✔ Add **unit tests** for algorithm validation
- ✔ Add **hardware abstraction layer**
- ✔ Port to **BLE smartwatch platform**
- ✔ Add **step cadence and distance estimation**
- ✔ Export walking sessions to **CSV / BLE profile**
- ✔ Add **signal filtering (low-pass, high-pass)** for smoother readings
- ✔ Add **configuration UI** or mobile dashboard

Each of these increases usability, performance, or professional polish.

---

## 🧑‍💻 Contributions

Contributions are welcome!  
To contribute:

1. Fork the repo
2. Create a branch
3. Add features / tests
4. Open a pull request

---

## 🪪 License

MIT License

---

## 👤 Author

Farhan Mohammad Shaikh  
Embedded Systems | Real-Time Signal Processing | IoT

