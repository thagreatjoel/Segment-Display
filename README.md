

# Segment Display Grid
This is a large led display built using MAX7219 drivers and 4digit 7segment display, controlled by a esp32. 
Each display handles a MAX7219 and every driver has capasitor for smooth power supply.

---
## Schematics
![Schematic](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6NTY1MCwicHVyIjoiYmxvYl9pZCJ9fQ==--0326cf0acdf77c2bdcafb0e65877407c0a8e5247/Schematic_Segment-Display_2025-10-26.jpg)
[[<img width="607" height="172" alt="17623208528351675285159586936277" src="https://github.com/user-attachments/assets/64dd1224-ce7b-480c-80f8-b815072c8e28" />](https://github.com/thagreatjoel/Segment-Display/blob/main/Images/simulation_image_bottom.png](https://github.com/thagreatjoel/Segment-Display/blob/main/Images/simulation_image_bottom.png))
)[
![Gerber2](<img width="607" height="172" alt="17623209187381733338747782117358" src="https://github.com/user-attachments/assets/a2c82b92-94a6-4e9e-a5b2-b808fd673c7e" />
)](https://github.com/thagreatjoel/Segment-Display/blob/main/Images/simulation_image_top.png)

---

## Hardwares

| Component | Quantity |
|------------|-----------|
| ESP32 | 1 | 
| MAX7219 | 16 | 
| 4-Digit 7-Segment Display | 32 |
| Potentiometer | 1 | 
| Resistor (2.2 kΩ) | 1 |
| Capacitor 10 µF (Electrolytic) | 16 |
| Capacitor 0.1 µF (Ceramic) | 16 | 

---

## Features
- there are 32 Displays and 32 drivers 
- brightness is controlled by potentiometer
- 5v is regulated to 3.3v by a regulator
- stable 5v power rail by decoupling capasitors

---

## Connections

# ESP32 → MAX7219
| ESP32 Pin | MAX7219 Pin | 
|------------|-------------|
| GPIO (DIN) | Pin 13 | 
| GPIO (CLK) | Pin 22 |
| GPIO (CS)  | Pin 21 | 

# MAX7219
max1 DIN -> ESP Pin13, max1 DOUT -> max2 DIN, max2 DOUT -> max2 DIN, ........

# Power
- 5 V -> Driver V+ (Pin 9)  
- GND -> Driver GND (Pin 19) and ESP GND  
- 3.3 V -> ESP VCC

# Brightness Control
- 5 V -> 2.2 kΩ resistor -> Pot pin 1  
- Pot wiper -> ISET (Pin 18)  
- Pot pin 2 -> GND  

---
## Why I Made This?
It all started when I saw a giant 7-segment display in a reel and thought, "i can totally make that!".. A few hours later, I was deep in EasyEDA on my phone. honestly, I like keeping it in front of my table to watch it having cool animations...

>  This entire project, including the schematic and PCB routing, was fully designed and built on a mobile device using EasyEDA Web.
