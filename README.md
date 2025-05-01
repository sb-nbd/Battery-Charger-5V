# PROJECT

## Analog Integrated Circuit Systems

### Li-Ion Battery Charging from 5V Source

**Author:** Cebanu Vitalie  

---

## 📑 Table of Contents

- Project Description
- Block Diagram
- Circuit Schematic
- Component Sizing
  - Duty Cycle
  - Inductor
  - Capacitor
  - Transistor
  - Schottky Diode
  - 555 Timer
  - Negative Feedback
  - LTM8067 Boost IC
- Simulations
- Practical Implementation
- Bibliography

---

## ⚙️ Project Description

The goal is to design a USB-powered **DC-DC converter** for charging lithium-ion batteries.

- **Input Voltage:** 5 VDC  
- **Output Voltage:** 3.75 VDC

The design uses a **buck topology** with a switch. Switching power supplies offer higher efficiency than traditional linear regulators and can boost, buck, or invert voltage. Some designs can also isolate input from output.

---

## 🔲 Block Diagram

*Check Word Document for more details*

---

## 🧮 Component Sizing

### 🔁 Duty Cycle (D)
PWM duty cycle in DC-DC converters:  
**D = Vout / Vin = 3.75V / 5V = 0.75**

### 🌀 Inductor
Using the formula:  
**L = (Vin * D) / (ΔI * f)**  
Assuming:
- Switching frequency `f = 20 kHz`
- Ripple current `ΔI = 50 mA`  
=> **L ≈ 937.5 µH ≈ 1 mH**

### ⚡ Capacitor
Using ripple voltage formula:  
**C = I / (ΔV * f)**  
- Voltage ripple: 0.01V  
=> **C = 250 µF**

### 🔲 Transistor (IRF510)
- N-channel power MOSFET
- Max drain-source voltage: 100V  
- Saturation resistance: ~0.54Ω  
- Suitable for high-speed, low-gate-drive applications

### ⚡ Schottky Diode (MBRS340TR)
- Low forward voltage drop
- Compact footprint
- Used in switching power supplies, converters, reverse battery protection

### ⏱️ 555 Timer
- RC charging generates PWM
- Time constant = R * C
- Switching frequency ≈ 20 kHz

### 🔁 Negative Feedback
- 555 output range: 0–3.33V
- Feedback voltage: ~3.125V using a voltage divider
- Auto-adjusts pulse width to stabilize output at 3.75V

### 🔋 LTM8067 Boost Converter
- Needed because IRF510 requires 10V to fully turn on
- LTM8067 doubles the 5V input to provide required gate drive
- Output voltage defined by feedback resistor network

---

## 🧪 Simulations

### LTM8067
- Reaches 10V output after a few milliseconds

### 555 Timer
- Output frequency ≈ 20kHz

### Output Signal
- Output stabilizes at 3.75V after ~300ms  
- Max fluctuation: **570 µV**

---

## 🔧 Practical Implementation

- Channel 1: Output voltage is 3.75V ±5%
- Channel 2: Negative feedback signal controls PWM width
- Gate voltage of transistor reaches 10V, ensuring full conduction

---

## 📚 Bibliography

1. Electronic Devices course notes  
2. Fundamentals of Electronic Circuits course notes  
3. [Analog: Buck Converter Tutorial](https://www.analog.com/en/technical-articles/dc-to-dc-buck-converter-tutorial.html)  
4. [Analog: Basic Linear Design Handbook](https://www.analog.com/media/en/training-seminars/design-handbooks/basic-linear-design/chapter9.pdf)  
5. [ElectroBOOM YouTube Channel](https://www.youtube.com/@ElectroBOOM)

---
