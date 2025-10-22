# 🧮 Massive 7-Segment Display Grid (32×4)

This project is a large-scale LED display built using **32 MAX7219 driver ICs** and **4-digit 7-segment displays**, fully controlled by an **ESP32**.  
Each MAX7219 handles one display, and all are daisy-chained together for smooth, synchronized output.

---

## ⚙️ Features
- 32 × 4-digit 7-segment displays (128 digits total)
- 32 × MAX7219 driver ICs (handles multiplexing internally)
- Brightness control via potentiometer (connected to ISET pins)
- Stable 5 V power rail with decoupling capacitors
- ESP32 control (data, clock, and chip-select lines)
- Modular schematic made in **EasyEDA**

---

## 🧩 Hardware Overview

| Component | Quantity | Description |
|------------|-----------|--------------|
| ESP32 | 1 | Main controller |
| MAX7219 | 32 | LED driver ICs |
| 4-Digit 7-Segment Display | 32 | Common cathode type |
| Potentiometer | 1 | Brightness adjustment |
| Resistor (2.2 kΩ) | 1 | For ISET current reference |
| Capacitor (10 µF Electrolytic) | 32 | Power smoothing (per MAX7219) |
| Capacitor (0.1 µF Ceramic) | 32 | Noise filtering (per MAX7219) |

---

## 🔌 Connections

### ESP32 → MAX7219
| ESP32 Pin | MAX7219 Pin | Function |
|------------|-------------|-----------|
| GPIO (DIN) | Pin 13 | Data In |
| GPIO (CLK) | Pin 22 | Clock |
| GPIO (CS)  | Pin 21 | Chip Select (LOAD) |

**Daisy-chain:**  
`MAX1 DOUT → MAX2 DIN → ... → MAX32 DIN`  
CLK and CS shared across all MAX chips.

### Power
- 5 V → MAX7219 V+ (Pin 9)  
- GND → MAX7219 GND (Pin 19) and ESP GND  
- 3.3 V → ESP VCC

### Brightness Control
- 5 V → 2.2 kΩ resistor → Pot pin 1  
- Pot wiper → all MAX7219 ISET (Pin 18)  
- Pot pin 2 → GND  

---

## ⚡ Capacitor Placement
Each MAX7219 should have:
- 10 µF electrolytic (+ to 5 V, – to GND)  
- 0.1 µF ceramic (across 5 V and GND, any orientation)

---

## 🧠 How It Works
Each MAX7219 drives one 4-digit 7-segment display.  
They handle the multiplexing internally, so no external multiplexer is required.  
The ESP32 sends serial data to the first MAX, which passes it down the chain through DOUT → DIN.

---

## 🧰 Tools Used
- **EasyEDA** – schematic & PCB design  
- **ESP32** – microcontroller platform 

---

## 🧾 License
This project is open-source under the **MIT License**.  
Feel free to remix, modify, or build upon it.

---
> 💡 This entire project, including the schematic and PCB routing, was fully designed and built on a mobile device using EasyEDA Web.
