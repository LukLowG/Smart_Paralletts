## Software & Data Logging: Dual-Parallette Load Cell System

### Objective
Extend the HX711-based load cell scale example to support **two separate full-bridge configurations** (i.e., two parallettes with 4 load cells each), read from both via a single Arduino, calibrate independently, and log the weight distribution over time.

---

### Wiring Overview

Each parallette has:
- 4x 50kg half-bridge load cells (wired into 1 full Wheatstone bridge)
- 1x HX711 module

#### HX711 to Arduino Wiring:

| HX711 | Arduino | Description        |
|--------|---------|--------------------|
| DT1    | D2      | Data pin Scale 1   |
| SCK1   | D3      | Clock pin Scale 1  |
| DT2    | D4      | Data pin Scale 2   |
| SCK2   | D5      | Clock pin Scale 2  |
| VCC    | 5V      | Power              |
| GND    | GND     | Ground             |

---

### Arduino Code for Reading Both Scales

This sketch uses the [HX711 Arduino library](https://github.com/bogde/HX711):

```cpp
#include "HX711.h"

HX711 scaleLeft;
HX711 scaleRight;

// Define pins
#define DT1 2
#define SCK1 3
#define DT2 4
#define SCK2 5

// Calibration factors (update after calibration)
float calibLeft = -7050.0;
float calibRight = -7050.0;

void setup() {
  Serial.begin(9600);

  scaleLeft.begin(DT1, SCK1);
  scaleRight.begin(DT2, SCK2);

  scaleLeft.set_scale(calibLeft);
  scaleRight.set_scale(calibRight);

  scaleLeft.tare();
  scaleRight.tare();

  Serial.println("Taring done. Starting measurements...");
}

void loop() {
  float weightLeft = scaleLeft.get_units();
  float weightRight = scaleRight.get_units();

  Serial.print("Left: ");
  Serial.print(weightLeft);
  Serial.print(" kg\t");

  Serial.print("Right: ");
  Serial.print(weightRight);
  Serial.println(" kg");

  delay(200); // Adjust logging rate as needed
}
```

---

### Logging Options

#### Option A: Serial Logging (Simple)
- Open Serial Monitor or Plotter in Arduino IDE
- Save output manually as CSV or copy/paste into Excel/Notepad

#### Option B: Serial-to-CSV (Automated)
Use Python to read serial output and log it to a CSV:

```python
import serial
import time

ser = serial.Serial('COM3', 9600)  # Replace with your port
filename = "log.csv"

with open(filename, 'w') as f:
    f.write("Time,Left,Right\n")
    while True:
        line = ser.readline().decode('utf-8').strip()
        if "Left:" in line:
            timestamp = time.time()
            parts = line.replace("kg", "").split()
            left = parts[1]
            right = parts[3]
            f.write(f"{timestamp},{left},{right}\n")
            print(f"{timestamp},{left},{right}")
```

#### Option C: SD Card Logging
- Add an SD card module to Arduino
- Use SD library to write values in `.csv` format
- Good for untethered operation

---

### Calibration Notes
- Use a known weight (e.g. 1kg or 5kg)
- Upload calibration sketch from HX711 library examples
- Note the calibration factor and set it in the main sketch for each scale

---

Let me know if you'd like to integrate real-time plots, alerts for asymmetry, or a GUI!

