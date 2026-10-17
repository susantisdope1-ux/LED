# 8×8 LED Matrix PCB

<p align="center">
  <img src="images/schematic.png" width="700" alt="Schematic">
</p>

<p align="center">
  <img src="images/pcb.png" width="700" alt="PCB Layout">
</p>

<p align="center">
  <img src="images/3d-front.png" width="340" alt="3D Front">
  <img src="images/3d-back.png" width="340" alt="3D Back">
</p>

---
## About

I was bored of manually wiring up 64 LEDs every time I needed a small display, so I designed one. It is a simple 8×8 LED matrix made of green LEDs that can be driven from an Arduino, ESP32, or almost any other microcontroller available.

It makes use of two **74HC595 shift registers** and eight **2N4402 PNP transistors**, thus, allowing to control the entire 64 LEDs array using **3 pins** (Data, Clock, Latch).

It was also a nice opportunity to gain some PCB design experience, routing 64 LEDs seemed quite easy but turns out otherwise once you start doing it.

---

## Features

- 64 green LEDs in an 8x8 arrangement
- Requires just 3 control pins: Data, Clock, Latch
- Can be used with an Arduino, ESP32, STM32, Raspberry Pi Pico, and any other microcontroller supporting 5V logic (or having proper level shifters)
- Easy to solder, no small or tricky components
- Small size
- Nice for animations, scrolling text, displaying icons, or studying multiplexing concepts
- 

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

## Reasons for building this 

Mainly to improve my PCB design skills. I wanted the layout to be tidy rather than a messy trace layout, and an LED grid of 64 LEDs was a good way to do that.

During the process, I learned a lot about:

- Planning out component placement and laying out the board before routing
- Routing a densely packed LED matrix 
- Decoupling capacitors and power delivery 
- Multiplexing LEDs and shift registers

---

## What you can do with it

- LED animations 
- Scrolling text 
- Displaying icons and pixel art 
- Digital Clock 
- Mini games 
- Status display

---

## Programming it 

Use anything that you want:

- Arduino IDE 
- PlatformIO 
- ESP-IDF
- STM32CubeIDE

---


---


## Credits

Created by **Sugam Pathak**.

If you love this project buy me a cup of cofee to help
