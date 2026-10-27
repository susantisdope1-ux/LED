# 8×8 LED Matrix PCB


---
## About

I got tired of wiring 64 LEDs each time I needed a small display so I decided to make one. This is a small 8x8 LED Matrix of green LEDs which can be powered by any microcontroller like Arduino or ESP32 or any other microcontroller for that matter.

This small project employs a **MAX7219 LED driver IC** which controls the entire **8x8 (64 LEDs) matrix** using just a few communication pins. The MAX7219 chip takes care of scanning rows and columns inside and communicates with the microcontroller via a **3-pin SPI interface (Data, Clock & Chip Select)**.

It was also a good chance to get some PCB designing practice, even routing 64 LEDs didn't seem that difficult until you actually do it.

---
## Characteristics

- 64 green LEDs in an 8x8 matrix formation
- Needs only 3 controlling pins - Data, Clock, and Latch
- Works fine with an Arduino, ESP32, STM32
- can work with 5V 
- Easy to solder, does not contain any difficult-to-solder elements
- Suitable for animation, scrolling texts, showing icons, or learning multiplexing basics

# 8×8 LED Matrix Images

## Schematic Design

<p align="center">
  <img width="700" alt="Schematic Design" src="https://github.com/user-attachments/assets/8abf495c-bdd5-4d88-b147-99726618a400" />
</p>

---

## PCB Layout

<p align="center">
 <img width="666" height="711" alt="Screenshot 2026-10-27 120910" src="https://github.com/user-attachments/assets/d474f2b6-706f-4f4f-bdf8-b95ce765a673" />

</p>

---

## 3D PCB View

<p align="center">
 
 <img width="782" height="657" alt="Screenshot 2026-10-27 121000" src="https://github.com/user-attachments/assets/aa7b11c6-993c-4348-a44a-6b522f09a7e7" />
<img width="632" height="601" alt="Screenshot 2026-10-27 120952" src="https://github.com/user-attachments/assets/2ba83648-cc6c-4edc-a900-58f2a60e7344" />

</p>
## Pinout

| Pin   | What it does  |
|-------|---------------|
| VCC   | 5V            |
| GND   | Ground        |
| DATA  | Serial data   |
| CLOCK | Shift clock   |
| LATCH | Storage clock |

---

## The Process

The LEDs are arranged in a matrix configuration, which means instead of powering all 64 LEDs separately, the circuit turns on one row of LEDs and then rapidly switches to the other rows. The column pins are controlled using the 74HC595 chips, and the 2N4402 transistors control the rows. Due to the rapid scanning of rows, the eye sees a complete image.

This is the whole concept behind it, which keeps the pin count low.

---

# Bill of Materials (BOM) and Cost

JLCPCB quote for **8x8 LED Matrix PCB (5 PCBs)**  
**Date:** 17 October 2026  
All prices are given in USD and can vary depending on availability and JLCPCB pricing policy.

---

## Components

| Designator | Component | Footprint | LCSC Part Number | Quantity (5 Boards) | Unit Cost | Total Cost |
|------------|-----------|-----------|------------------|---------------------|-----------|------------|
| LED1 - LED64 | Green LED 5mm (333-2SURD/S530-A3) | LED-5MM | [C87271](https://www.lcsc.com/search?q=C87271) | 325 | $0.0301 | $9.7825 |
| U5 | MAX7219N 8-Digit LED Driver IC | DIP-24 | [C492111](https://www.lcsc.com/search?q=C492111) | 5 | $1.8268 | $9.1340 |
| C20 | 100nF 50V X7R Ceramic Capacitor | 0805 | [C49678](https://www.lcsc.com/search?q=C49678) | 5 | $0.0205 | $0.1025 |
| C21 | 100µF 25V Electrolytic Capacitor | THT | [C47873](https://www.lcsc.com/search?q=C47873) | 10 | $0.0180 | $0.1800 |
| H1 | 2.54mm 1×5 Female Header | THT | [C50950](https://www.lcsc.com/search?q=C50950) | 5 | $0.0830 | $0.4150 |
| R1 | 16kΩ Resistor | THT | Not Selected | 5 | ~$0.010 | ~$0.050 |

---

# JLCPCB Manufacturing Cost

| Item | Cost |
|------|------|
| PCB Fabrication (5 pcs) | $4.00 |
| Setup Fee | $8.24 |
| Stencil | $1.55 |
| Components (selected parts) | $10.48 |
| SMT Assembly | $0.02 |
| Hand Soldering Labor | $3.61 |
| Manual Assembly | $11.47 |
| Nitrogen Reflow Soldering | $0.91 |
| **JLCPCB Assembly Total** | **$40.28** |

---
## Example Code (Arduino)

The following example is used to draw a smiley face on the 8×8 LED Matrix using the MAX7219 library.

```cpp
#include <LedControl.h>

// DIN, CLK, CS
LedControl matrix = LedControl(11, 13, 10, 1);

byte smiley[8] = {
  B00111100,
  B01000010,
  B10100101,
  B10000001,
  B10100101,
  B10011001,
  B01000010,
  B00111100
};

void setup() {
  matrix.shutdown(0, false);   // Wake up display
  matrix.setIntensity(0, 8);   // Brightness (0-15)
  matrix.clearDisplay(0);

  // Display the smiley
  for (int row = 0; row < 8; row++) {
    matrix.setRow(0, row, smiley[row]);
  }
}

void loop() {
  // Nothing to do
}
```

### Connections

| MAX7219 | Arduino |
|---------|----------|
| VCC | 5V |
| GND | GND |
| DIN | D11 |
| CLK | D13 |
| CS | D10 |

### Results

 The output obtained is that a smiley face will be displayed on the 8×8 LED Matrix after turning on the circuit.

## Reasons for building this 

Mainly to improve my PCB design skills. I wanted the layout to be tidy rather than a messy trace layout, and an LED grid of 64 LEDs was a good way to do that.

During the process, I learned a lot about:

- Planning out component placement and laying out the board before routing
- Routing a densely packed LED matrix 
- Decoupling capacitors and power delivery 
- Multiplexing LEDs and shift registers

---

## What we can do with it

- LED animations 
- Displaying icons and pixel art 
- Digital Clock 

---



---


---


## Credits

Created by **Sugam Pathak**.

If you love this project buy me a cup of cofee to help
