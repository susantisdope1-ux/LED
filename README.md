
# 8×8 LED Matrix PCB

---

## About

I got tired of wiring 64 LEDs every time I needed a small display, so I decided to make my own 8×8 LED Matrix using green LEDs.

The board uses a **MAX7219 LED Driver IC** to control all 64 LEDs with just a few pins. It communicates with a microcontroller through a 3-wire interface (Data, Clock, and Latch).

It works with Arduino, ESP32, STM32, and other microcontrollers.

This project was also a good way to practice PCB designing. Routing 64 LEDs was fun, but definitely not as easy as I first thought!

---

## Characteristics

- 64 green LEDs in  8×8 matrix
- Requires 3 control pins
- Compatible with Arduino, ESP32, STM32, and other microcontroller 
- Works in 5V power


---

# 8×8 LED Matrix Images

## Schematic Design

<p align="center">
  <img width="700" alt="Schematic Design" src="https://github.com/user-attachments/assets/8abf495c-bdd5-4d88-b147-99726618a400" />
</p>

---

## PCB Layout

<p align="center">
  <img width="666" height="711" alt="PCB Layout" src="https://github.com/user-attachments/assets/d474f2b6-706f-4f4f-bdf8-b95ce765a673" />
</p>

---

## 3D PCB View

<p align="center">
  <img width="782" height="657" alt="3D PCB Front View" src="https://github.com/user-attachments/assets/aa7b11c6-993c-4348-a44a-6b522f09a7e7" />
  <img width="632" height="601" alt="3D PCB View" src="https://github.com/user-attachments/assets/2ba83648-cc6c-4edc-a900-58f2a60e7344" />
</p>

---

## Pinout

| Pin | Function |
|---|---|
| VCC | 5V Power |
| GND | Ground |
| DATA | Serial Data |
| CLOCK | Clock Signal |
| LATCH | Storage Clock |

---

## How It Works

The LEDs are arranged in rows and columns. Instead of controlling all 64 LEDs separately, the circuit quickly switches between rows to display an image.

The 74HC595 shift registers control the columns, while 2N4402 transistors handle the rows. This process is called **multiplexing** and helps reduce the number of control pins needed.

---

# Bill of Materials (BOM) and Cost


## Components

| Designator | Component | Footprint | LCSC Part Number | Quantity | Unit Cost | Total |
|---|---|---|---|---:|---:|---:|
| LED1–LED64 | Green LED 5mm | LED-5MM | [C87271](https://www.lcsc.com/search?q=C87271) | 325 | $0.0301 | $9.7825 |
| U5 | MAX7219N LED Driver | DIP-24 | [C492111](https://www.lcsc.com/search?q=C492111) | 5 | $1.8268 | $9.1340 |
| C20 | 100nF Ceramic Capacitor | 0805 | [C49678](https://www.lcsc.com/search?q=C49678) | 5 | $0.0205 | $0.1025 |
| C21 | 100µF Electrolytic Capacitor | THT | [C47873](https://www.lcsc.com/search?q=C47873) | 10 | $0.0180 | $0.1800 |
| H1 | 1×5 Female Header | THT | [C50950](https://www.lcsc.com/search?q=C50950) | 5 | $0.0830 | $0.4150 |
| R1 | 16kΩ Resistor | THT | Not Selected | 5 | ~$0.010 | ~$0.050 |

---

## JLCPCB Manufacturing Cost

| Item | Cost |
|---|---:|
| PCB Fabrication (5 pcs) | $4.00 |
| Setup Fee | $8.24 |
| Stencil | $1.55 |
| Components | $10.48 |
| SMT Assembly | $0.02 |
| Hand Soldering Labor | $3.61 |
| Manual Assembly | $11.47 |
| Nitrogen Reflow Soldering | $0.91 |
| **Total** | **$40.28** |

---

## Example Code (Arduino)

This example displays a simple smiley face on the LED Matrix using the MAX7219 library.

```cpp
#include <LedControl.h>

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
  matrix.shutdown(0, false);
  matrix.setIntensity(0, 8);
  matrix.clearDisplay(0);

  for (int row = 0; row < 8; row++) {
    matrix.setRow(0, row, smiley[row]);
  }
}

void loop() {
}
```

### Connections

| MAX7219 | Arduino |
|---|---|
| VCC | 5V |
| GND | GND |
| DIN | D11 |
| CLK | D13 |
| CS | D10 |

### Result

After powering up the circuit, a smiley face appears on the 8×8 LED Matrix.

---



---

## What Can You Make With It?

- LED animations
- Scrolling text
- Digital clocks
- Small DIY displays

---

## Credits

Created by **Sugam Pathak** for hack club.
