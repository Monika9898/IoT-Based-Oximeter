# 💓 IoT Pulse Oximeter using NodeMCU, MAX30100, OLED & Blynk

This project is a real-time, IoT-enabled **pulse oximeter** that measures **heart rate (BPM)** and **blood oxygen level (SpO₂)** using the **MAX30100 sensor**. The values are displayed on a **0.96" OLED screen**, sent to the **Blynk app**, and also logged via the **Serial Monitor**.

> 🛠️ Built using **NodeMCU ESP8266**, this device enables wireless monitoring and is ideal for IoT and health-based learning projects.

---

## 📷 Real Project Output

![Real Project Output](Real_Output.jpg)

> OLED shows BPM and SpO₂ with a heart icon. MAX30100 glows red when finger is placed for detection.

---

## 🧾 Features

- 📟 Real-time Heart Rate & SpO₂ measurement
- 📱 Remote monitoring on Blynk App via Wi-Fi
- 🖥️ OLED display output with heart icon animation
- 🔧 Compact setup on breadboard
- 💬 Serial Monitor output for debugging

---

## 🧰 Components Used

| Component             | Description                 |
|----------------------|-----------------------------|
| NodeMCU ESP8266      | Wi-Fi-enabled microcontroller |
| MAX30100             | Pulse oximeter & heart rate sensor |
| OLED Display (0.96") | I2C interface, SSD1306 type |
| Breadboard + Wires   | For prototyping             |

---

## 🔌 Circuit Diagram

![Circuit Diagram](circuit_diagram.png)

### 🧷 Pin Connections

| Module       | Pin       | NodeMCU Pin |
|--------------|-----------|-------------|
| **MAX30100** | VCC       | 3V3         |
|              | GND       | GND         |
|              | SDA       | D2 (GPIO4)  |
|              | SCL       | D1 (GPIO5)  |
|              | INT       | D0 (GPIO16) |
| **OLED**     | VCC       | 3V3         |
|              | GND       | GND         |
|              | SDA       | D2 (shared) |
|              | SCL       | D1 (shared) |

> Note: MAX30100 and OLED share the same I2C bus (SDA/SCL).

---

## 🖥️ Software & Libraries

### ✅ Arduino IDE Setup

- Board: `NodeMCU 1.0 (ESP-12E Module)`
- Baud Rate: `115200`
- Port: Select appropriate COM port

### 📦 Required Libraries (Install via Library Manager)

- `MAX30100_PulseOximeter`
- `ESP8266WiFi`
- `Blynk` (Legacy or IoT version)
- `OakOLED` or `Adafruit_SSD1306`
- `Adafruit GFX`

---

## 📲 Blynk Configuration

1. Download the Blynk app
2. Create a new project (ESP8266 board)
3. Add:
   - Gauge for **V7** → Heart Rate (BPM)
   - Gauge for **V8** → SpO₂
4. Get your **Auth Token** and replace in code:

```cpp
char auth[] = "YOUR_BLYNK_AUTH_TOKEN";


🧠 Code Overview
Key logic used in the Arduino sketch:


Blynk.virtualWrite(V7, BPM);       // Send BPM to Blynk
Blynk.virtualWrite(V8, SpO2);      // Send SpO2 to Blynk

oled.setCursor(0, 0);
oled.println("Heart BPM");
oled.setCursor(0,16);
oled.println(pox.getHeartRate());


OLED displays values like:


Heart BPM
81.57
SpO2
95
💙 (heart bitmap)

 
🔮 Future Improvements
Replace MAX30100 with MAX30102 for better accuracy
