# 9-bit SAR ADC Design using 180nm CMOS

Course Project for **EE617 - Mixed Signal VLSI Design** at IIT Dharwad.

---

# Overview

This project presents the design and simulation of a **9-bit Successive Approximation Register (SAR) Analog-to-Digital Converter (ADC)** using **SCL 180nm CMOS technology** in Cadence Virtuoso.

The objective of the project was to understand mixed-signal integrated circuit design by implementing the major building blocks of a SAR ADC including:

* Sample and Hold Circuit
* Binary-weighted Capacitor DAC
* StrongARM Latch Comparator
* SAR Control Logic

The SAR ADC architecture was chosen due to its low power consumption, moderate speed, and suitability for medium-resolution analog-to-digital conversion applications.

---

# Specifications

| Parameter      | Value                         |
| -------------- | ----------------------------- |
| Resolution     | 9-bit                         |
| Sampling Rate  | 20 kS/s                       |
| Input Range    | 0 – 0.8 V                     |
| Analog Supply  | 1.8 V                         |
| Digital Supply | 1.2 V                         |
| DAC Type       | Binary-weighted Capacitor DAC |
| Input Type     | Single-ended                  |
| Technology     | SCL 180nm CMOS                |

---

# SAR ADC Architecture

A Successive Approximation Register (SAR) ADC converts an analog input signal into its digital equivalent using a binary search algorithm.

The conversion process involves:

1. Sampling the input signal
2. Comparing the sampled voltage with DAC-generated reference voltages
3. Determining each output bit from MSB to LSB
4. Generating the final digital output code after successive comparisons

The SAR ADC provides an efficient trade-off between speed, power, and resolution, making it widely used in low-power mixed-signal systems.

---

# Sample and Hold Circuit

The Sample and Hold (S/H) circuit captures the analog input voltage during the sampling phase and holds the sampled value constant throughout the conversion process.

### Functions of Sample and Hold:

* Samples the input analog signal
* Maintains stable input during bit conversion
* Reduces signal variation during SAR operation

### Design Considerations:

* Charge injection minimization
* Clock feedthrough reduction
* Stable voltage retention during hold phase

The schematic implementation of the Sample and Hold circuit is available in:

```text id="d5bh9d"
schematics/sample_and_hold.png
```

---

# Binary-weighted Capacitor DAC

The DAC block generates reference voltages required for the SAR conversion process.

A binary-weighted capacitor array was implemented to perform digital-to-analog conversion during each bit trial.

### DAC Operation:

* Capacitors are switched according to SAR logic outputs
* Reference voltage is updated after every comparison
* DAC output approximates the input voltage successively

### Features:

* Binary-weighted capacitor architecture
* Efficient charge redistribution technique
* Suitable for low-power SAR ADC operation

The DAC behavioral implementation is available in:

```text id="84s7s8"
verilogA/dac_9_bit.va
```

---

# StrongARM Latch Comparator

A StrongARM latch comparator was used to compare the sampled input voltage with the DAC-generated voltage.

The comparator determines whether the DAC output is higher or lower than the sampled input and provides the decision bit to the SAR logic.

### Comparator Features:

* High-speed regenerative operation
* Low static power consumption
* Dynamic latch-based architecture

### Advantages:

* Fast decision making
* Low power operation
* Suitable for mixed-signal applications

Comparator schematic:

```text id="m9wd6e"
schematics/strong_arm_latch.png
```

---

# SAR Logic Controller

The SAR logic block controls the complete conversion sequence of the ADC.

It performs the binary search operation by:

* Setting trial bits
* Reading comparator outputs
* Updating DAC control signals
* Determining final digital output code

The SAR logic was implemented using Verilog-A behavioral modeling.

### Functional Flow:

1. MSB is initially set
2. Comparator decision is evaluated
3. Bit is retained or cleared
4. Process continues until LSB decision

Verilog-A implementation:

```text id="c9u6yo"
verilogA/sar_logic.va
```

---

# Tools Used

* Cadence Virtuoso
* Verilog-A
* Spectre Simulator
* Siemens Calibre
* SCL 180nm PDK

---

# Repository Structure

```text id="17sy2u"
.
├── README.md
├── Presentation_Slides.pdf
│
├── schematics/
│   ├── adc_9_bit.png
│   ├── sample_and_hold.png
│   └── strong_arm_latch.png
│
├── verilogA/
│   ├── sar_logic.va
│   └── dac_9_bit.va
```

---

# Learning Outcomes

Through this project, the following concepts were explored:

* SAR ADC architecture and operation
* Mixed-signal circuit design methodology
* Binary-weighted capacitor DAC implementation
* Dynamic comparator design
* Verilog-A behavioral modeling
* Cadence Virtuoso schematic design flow

---

# Author

Veenadhar
B.Tech Electrical Engineering
Indian Institute of Technology Dharwad
