# Electronics1-Temperature-Project
# [cite_start]Analog Thermometer Project [cite: 1]

[cite_start]This repository contains the design, calculations, and simulation of an analog thermometer circuit for the Electronics course at Sharif University of Technology. [cite: 1]

## Team Members
* [cite_start]Vahid Hamzeh (Student ID: 402101577) [cite: 2]
* [cite_start]Amirali Fazeli (Student ID: 402102198) [cite: 2]

## Overview
[cite_start]This project features the design of a thermometer circuit using a diode that is capable of measuring ambient temperature in the range of $0^{\circ}C$ to $100^{\circ}C$[cite: 4]. [cite_start]Because the voltmeter used for measurement operates within a $0V$ to $10V$ range [cite: 3][cite_start], the circuit utilizes a $10V$ ($V_{cc}$) power supply to match this exact scale[cite: 4]. 

### Circuit Schematic
![Circuit Schematic](image_path.png)

## Theory and Calculations
The primary temperature sensor in this design is a diode. [cite_start]The underlying principle is that the diode's forward voltage drop changes by approximately $2mV$ for every $1^{\circ}C$ change in temperature[cite: 4]. [cite_start]Therefore, across a $100^{\circ}C$ range, the voltage drop varies by about $200mV$[cite: 4]. 

[cite_start]To achieve the desired $10V$ output variation for the voltmeter, an Operational Amplifier (Op-Amp) with a gain of $50$ is required[cite: 4]. [cite_start]Furthermore, since the voltage change is negative as the temperature rises, an inverting amplifier configuration is implemented[cite: 5].

[cite_start]The governing equations for the design are as follows[cite: 5]:
* [cite_start]$\Delta V_{D}/\Delta T \approx -2mV/^{\circ}C$ [cite: 6]
* [cite_start]$V_{VM}(100^{\circ}C) = 10V$ [cite: 6]
* [cite_start]$\Rightarrow A_{V} = -50$ [cite: 6]

### Offset Adjustment
[cite_start]At $0^{\circ}C$, the voltage drop across the diode is approximately $0.7V$[cite: 7]. [cite_start]This baseline voltage must be subtracted from the amplifier's input to ensure the output reads $0V$ at zero degrees[cite: 7]. [cite_start]This reduction is achieved using a voltage divider network consisting of resistors R4 and R6[cite: 8].

### Final Component Values
[cite_start]In practice, assuming a baseline voltage ($V_{don}$) of $0.542V$, the resistor values were designed to be adjustable[cite: 8, 9, 10]. The selected component values are:
* [cite_start]$V_{don}=0.542V \Rightarrow R6=5.42k\Omega, R5=100k\Omega$ [cite: 11]
* [cite_start]$\Rightarrow R4=94.6k\Omega, R2=21.4k\Omega$ [cite: 12]
* [cite_start]$R3=1M\Omega$ [cite: 13]

[cite_start]*(Note: These resistor values were specifically chosen to ensure that the variations in diode current remain minimal during operation[cite: 14].)*

## Software Simulation
To verify and calibrate the circuit's performance, the following analyses were conducted:
1. [cite_start]**Diode Characteristics Extraction:** The `1N4148` diode was analyzed using `PSpice` software and its datasheet graphs to determine the exact forward voltage at various temperatures[cite: 16, 20].
2. [cite_start]**Temperature Sweep Analysis:** Using the `.step temp list` command and the `Sample Temp` tool in `LTSpice` [cite: 15, 117][cite_start], the circuit was simulated at temperatures of $0, 10, 20, 30, 40, 50, 60, 70, 80, 90,$ and $100^{\circ}C$[cite: 15, 117]. [cite_start]The simulation results confirmed that the circuit achieves an accurate temperature scaling with an allowable error margin of $5\%$[cite: 15].
