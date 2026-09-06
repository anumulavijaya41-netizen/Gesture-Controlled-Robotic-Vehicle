# 🤖 Gesture-Controlled Robotic Vehicle

> **A wireless robotic vehicle controlled using hand gestures with MPU6050, Arduino, and Bluetooth.**

![Project](docs/hardware/complete-setup.jpg)

---

## 📌 Overview

This project allows a robotic vehicle to be controlled using simple hand movements.

The **MPU6050** detects hand acceleration, the **transmitter Arduino** converts it into a movement command, and Bluetooth sends the command to the **receiver Arduino**. The receiver controls the motors through a motor driver.

```text
✋ Hand Gesture
      ↓
📐 MPU6050
      ↓
🟦 Arduino TX
      ↓
📡 Bluetooth
      ↓
🟦 Arduino RX
      ↓
⚙️ Motor Driver
      ↓
🤖 Robot Movement
```

---

## 🧩 System Block Diagram

![System Block Diagram](docs/architecture/complete-system.png)

### Transmitter

```text
Hand Gesture
     ↓
MPU6050
     ↓
Arduino
     ↓
Bluetooth TX
```

### Receiver

```text
Bluetooth RX
     ↓
Arduino
     ↓
Motor Driver
     ↓
DC Motors
     ↓
Robot
```

---

## ✋ Gesture Control

The system uses **acceleration thresholds** to identify hand movements.

| Gesture     | Condition | Command |
| ----------- | --------- | ------- |
| ⬆️ Forward  | `X ≤ -3`  | `a`     |
| ⬇️ Backward | `X ≥ 3`   | `b`     |
| ⬅️ Left     | `Y ≤ -3`  | `c`     |
| ➡️ Right    | `Y ≥ 3`   | `d`     |
| 🛑 Stop     | Otherwise | `e`     |

```text
'a' → Forward
'b' → Backward
'c' → Left
'd' → Right
'e' → Stop
```

---

## 🔩 Components

* Arduino ×2
* MPU6050 Motion Sensor
* Bluetooth Modules ×2
* Motor Driver
* DC Motors
* Robot Chassis & Wheels
* Battery / Power Supply

---

## 🔌 Main Connections

### MPU6050 → Arduino

```text
SDA → A4
SCL → A5
VCC → Power
GND → GND
```

### Bluetooth → Arduino

```text
TX → D2
RX → D3
VCC → Power
GND → GND
```

### Motor Driver

```text
D4 → Motor Control 1
D5 → Motor Control 2
D6 → Motor Control 3
D7 → Motor Control 4
```

---

## 📡 How Communication Works

```text
        TRANSMITTER
┌─────────────────────┐
│ Hand Gesture        │
│       ↓             │
│ MPU6050             │
│       ↓             │
│ Arduino             │
│       ↓             │
│ Bluetooth TX        │
└──────────┬──────────┘
           │
      📡 Bluetooth
           │
┌──────────▼──────────┐
│ Bluetooth RX        │
│       ↓             │
│ Arduino             │
│       ↓             │
│ Motor Driver        │
│       ↓             │
│ DC Motors           │
└─────────────────────┘
        RECEIVER
```

---

## 🛠️ Technologies

* **Arduino C/C++**
* **Arduino IDE**
* **MPU6050**
* **Bluetooth**
* **I²C Communication**
* **SoftwareSerial**
* **Embedded Systems**

---

## 📁 Project Structure

```text
gesture-controlled-robot/
│
├── README.md
├── LICENSE
│
├── src/
│   ├── transmitter/
│   │   └── TX_part.ino
│   ├── receiver/
│   │   └── RT_part.ino
│   └── bluetooth/
│       └── AT_command.ino
│
├── hardware/
│   ├── components.md
│   └── pin-connections.md
│
├── docs/
│   ├── architecture/
│   ├── tinkercad/
│   ├── wiring/
│   └── hardware/
│
└── demo/
```

---

## 🎨 Tinkercad Visualization

Tinkercad diagrams are included to make the hardware connections easier to understand.

![Tinkercad Circuit](docs/tinkercad/complete-circuit.png)

> **Note:** Tinkercad diagrams are used mainly for circuit and wiring visualization. Actual Bluetooth communication was tested on the physical hardware.

---

## 🚀 Features

* ✋ Hand gesture-based control
* 📡 Wireless Bluetooth communication
* 🤖 Real-time robotic movement
* 🎯 Forward, backward, left, right and stop
* 🔧 Modular transmitter and receiver design
* 📐 Sensor-based motion detection

---

## ⚠️ Current Limitation

The current system uses **fixed acceleration thresholds** for gesture detection rather than machine learning.

---

## 🔮 Future Improvements

* 🤖 ML-based gesture recognition
* 🚗 Speed control using PWM
* 📱 Mobile application
* 🎯 Adaptive gesture thresholds
* 📡 Longer-range communication
* 🛑 Emergency-stop mechanism

---

## 👥 Contributors

**Vijayalakshmi Anumula**

*Add team members here.*

---

## 📄 License

This project is licensed under the **MIT License**.

---

⭐ **If you found this project interesting, consider starring the repository!**

### 🚀 From a simple hand gesture to robotic movement!
