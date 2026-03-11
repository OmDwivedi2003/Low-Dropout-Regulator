
# Low Dropout Regulator (LDO) Design using Cadence Virtuoso

## Overview

This project focuses on the **design and analysis of Low Dropout Regulators (LDOs)** using **Cadence Virtuoso**. Two different LDO architectures have been implemented and analyzed:

* **PMOS based LDO**
* **NMOS based LDO**

The objective of this project is to study the **working principle, stability, and performance trade-offs of LDO regulators** under different operating conditions such as load variation and supply noise.

LDOs are widely used in **power management circuits of SoCs, microprocessors, mobile devices, and analog/mixed-signal ICs** because they provide **clean and stable output voltage with minimal dropout voltage**.

---

# What is a Low Dropout Regulator (LDO)?

A **Low Dropout Regulator (LDO)** is a **linear voltage regulator** that maintains a constant output voltage even when the input voltage is very close to the desired output voltage.

### Dropout Voltage

Dropout voltage is defined as:

[
V_{dropout} = V_{in} - V_{out}
]

An LDO is designed so that this voltage difference remains **very small**, allowing efficient regulation even with low input headroom.

---

# Basic Working Principle

An LDO operates using **negative feedback** to regulate the output voltage.

The output voltage is compared with a **reference voltage** using an **error amplifier**. The error amplifier adjusts the gate voltage of the **pass transistor**, controlling how much current flows from input to output.

If:

* **Vout decreases** → pass transistor conducts more current
* **Vout increases** → pass transistor conducts less current

This feedback loop maintains a **stable regulated output voltage**.

---

# Main Components of an LDO

An LDO typically consists of the following blocks:

### 1. Reference Voltage Source

Provides a **stable reference voltage (Vref)** used to regulate the output.

Examples:

* Bandgap reference
* Temperature-independent reference circuits

---

### 2. Error Amplifier

Compares:

```
Vref  vs  Feedback voltage
```

The difference is amplified and used to control the **pass transistor**.

Important characteristics:

* High gain
* Low offset
* Good stability

---

### 3. Pass Transistor

The pass device controls current flow from **Vin to Vout**.

Types:

* PMOS
* NMOS
* BJT (rare in CMOS processes)

---

### 4. Feedback Network

A **resistor divider** senses the output voltage.

[
V_out = V_ref *(1 + R_1/R_2)
]

---

### 5. Compensation Network

Ensures **loop stability** by controlling poles and zeros in the feedback loop.

Usually implemented using:

* Output capacitor
* Internal compensation capacitors

---

# Types of LDO Regulators

## 1️⃣ PMOS LDO

PMOS LDO uses a **PMOS transistor as the pass device**.

### Advantages

* Low dropout voltage
* No charge pump required
* Simpler gate control

### Disadvantages

* Larger transistor size required
* Lower current efficiency compared to NMOS

---

## 2️⃣ NMOS LDO

NMOS LDO uses an **NMOS transistor as the pass element**.

### Advantages

* Higher current drive capability
* Smaller transistor area
* Better performance in some high-current applications

### Disadvantages

* Requires **gate voltage higher than Vin**
* Often needs **charge pump or auxiliary circuit**

---

# Implemented Architectures

## NMOS Based LDO

Features:

* NMOS pass transistor
* Error amplifier control
* Feedback resistor network
* Compensation capacitor

Simulation analysis performed for:

* Line transient response
* Load transient response
* Loop gain
* PSRR
* Dropout voltage
* Quiescent current

---

## PMOS Based LDO

Features:

* PMOS pass transistor
* Error amplifier feedback control
* Resistor feedback network
* Output capacitor stabilization

Simulation analysis performed for:

* Line regulation
* Load regulation
* Stability analysis
* PSRR performance
* Dropout voltage

---

# Performance Parameters Analyzed

The following parameters were evaluated through Cadence simulations:

### 1. Dropout Voltage

Minimum difference between input and output voltage where regulation is maintained.

---

### 2. Line Regulation

Ability of LDO to maintain constant output voltage when **input voltage changes**.

[
Line\ Regulation = \frac{\Delta V_{out}}{\Delta V_{in}}
]

---

### 3. Load Regulation

Ability to maintain output voltage under **load current variations**.

[
Load\ Regulation = \frac{\Delta V_{out}}{\Delta I_{load}}
]

---

### 4. Power Supply Rejection Ratio (PSRR)

Ability of LDO to reject supply noise.

[
PSRR = 20 \log \left(\frac{V_{in}}{V_{out}}\right)
]

Higher PSRR indicates better noise rejection.

---

### 5. Loop Gain

Measures stability of the feedback system.

A stable LDO requires:

* Adequate **gain margin**
* Adequate **phase margin**

---

### 6. Transient Response

#### Line Transient

Output voltage response to sudden **input voltage changes**.

#### Load Transient

Output voltage response to **sudden load current changes**.

---

### 7. Quiescent Current

Current consumed internally by the LDO excluding load current.

Lower quiescent current is important for **battery-powered devices**.

---

# Simulation Results

Simulations were performed using **Cadence Spectre**.

Key analyses include:

* Dropout Voltage
* Line Transient Response
* Load Transient Response
* Loop Gain Analysis
* Power Supply Rejection Ratio (PSRR)
* Quiescent Current Measurement

Results are stored in the **Results** directory.

---

# Tools Used

* Cadence Virtuoso
* Spectre Simulator
* Analog Design Environment (ADE)

---

# Applications of LDO

LDO regulators are widely used in:

* Mobile processors
* SoC power management
* RF circuits
* Analog signal processing systems
* Battery powered electronics
* Sensor interfaces

---

# Repository Structure

```
Low-Dropout-Regulator
│
├── NMOS LDO
│   ├── Schematic
│   └── Results
│
├── PMOS LDO
│   ├── Schematic
│   └── Results
│
└── README.md
```

---

# Conclusion

This project demonstrates the **design and analysis of PMOS and NMOS based LDO regulators** in Cadence Virtuoso. Both architectures were evaluated based on key performance metrics such as **dropout voltage, PSRR, stability, transient response, and quiescent current**.

The study highlights the **trade-offs between PMOS and NMOS pass devices**, providing insights into their practical applications in modern **power management circuits for integrated systems**.

---
