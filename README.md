# RFID Door Lock & Tag Scanner (Arduino)

This repository contains two Arduino projects using the **RC522 RFID reader**, **I2C LCD display**, and **SG90 servo motor**:

1. **RFID Tag Scanner** → Reads RFID card UIDs and displays them on Serial Monitor + LCD.
2. **RFID Door Lock System** → Controls a servo-based lock that opens/closes only for an authorized RFID card.

---

## 📂 Project Structure

RFID-Door-Lock-System/
│
├── code1_rfid_scan/ → Basic RFID card scanner
│ └── rfid_scan.ino
│
├── code2_door_lock/ → Door lock control with authorized UID
│ └── door_lock.ino
│
└── README.md → Documentation

---

## ⚙️ Hardware Requirements

- Arduino Uno (or compatible)
- RC522 RFID module
- SG90 Servo motor
- 16x2 I2C LCD
- Jumper wires
- Breadboard
- RFID cards/tags

---

## 🔌 Wiring (Câblage)

### Arduino + SG90 Servo

- Brown (GND) → GND
- Red (VCC) → 5V
- Yellow (Signal) → D3

---

### Arduino + LCD (I2C)

- SCL → A5
- SDA → A4
- GND → GND
- VCC → 5V

---

### Arduino + RFID-RC522

- 3.3V → 3.3V
- RST → D9
- GND → GND
- IRQ → (not connected)
- MISO → D12
- MOSI → D11
- SCK → D13
- SDA (SS) → D10

---

## 🖥️ Code 1: RFID Tag Scanner

📌 Location: `code1_rfid_scan/rfid_scan.ino`

### 🔹 How it works:

- Waits for a card to be scanned.
- Displays UID on the LCD and Serial Monitor.
- Useful for **finding card UIDs** before programming them into the lock system.

### 🔹 How to test:

1. Upload the sketch to Arduino.
2. Open the Serial Monitor (**9600 baud**).
3. Place an RFID card near the reader.
4. The UID will appear on both the LCD and Serial Monitor.

---

## 🖥️ Code 2: RFID Door Lock System

📌 Location: `code2_door_lock/door_lock.ino`

### 🔹 How it works:

- Checks the UID of scanned cards.
- If the UID matches the stored **authorized UID**, the servo will:
  - Lock/unlock the door alternately.
- If the card is **not recognized**, “Wrong card!” is displayed.

👉 Default authorized UID in the code:

```cpp
String UID = "69 30 D5 A3";


Change this to match your own card’s UID from Code 1.

🔹 How to test:

Upload the sketch to Arduino.

Place an RFID card near the reader.

If the UID matches → Servo moves & LCD shows status.

If wrong card → LCD shows "Wrong card!".



🚀 Getting Started

1. Clone this repo:

git clone https://github.com/<your-username>/RFID-Door-Lock-System.git


2. Open the .ino file in Arduino IDE.

3. Install the required libraries:

MFRC522

LiquidCrystal_I2C

Servo

4. Upload the sketch to Arduino.


📷 Future Improvements

Multiple authorized UIDs

EEPROM storage for cards

Buzzer for feedback

Keypad + RFID dual authentication


✍️ Author: Abdallah Jbeli
📅 Year: 2025
```
