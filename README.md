# Low-Noise Voltage Control Ring Oscillator using 28nm Technology node
This repository presents a low phase noise ring based voltage-controlled-oscillator (VCO) for ultra-wide band (UWB) applications. The circuit is implemented in a 28-nm CMOS technology using Synopsis Custom Compiler.
![image](https://user-images.githubusercontent.com/35188692/155860564-111e682f-d9be-4464-9dc6-4a7cab62911a.png)

# Table of Contents
* [Introduction](#Introduction)
* [Symmetrical Load Differential VCO](#Symmetrical-Load-Differential-VCO)
* [Limitations of the Symmetrical Load Differential VCO](#Limitations-of-the-Symmetrical-Load-Differential-VCO)
* [Proposed Delay Cell](#Proposed-Delay-Cell-Modified-Symmetrical-Load-Differential-VCO)
* [Tools Used](#Tools-Used)
* [Pre-Layout Schematics and Simulations](#Pre-Layout-Schematics-and-Simulations)
* [Spice file](#Spice-file) 
* [Spice simulation waveforms](#Spice-simulation-waveforms)
# Introduction
Common VCO implementations are LC oscillators and ring oscillators. In integrated circuits, the production of high-performance passive devices (such as inductors) is difficult since these devices occupy a large area and thus LC tank voltage-controlled oscillator becomes inappropriate. Concurrently, Ring Oscillator benefit from the rapid advance of the technology in IC industry, to occupy more and more small area on the chip, while keeping all its appealing characteristics such as the large frequency tuning range, and the good linearity,making it widely used in industrial products and academic designs.
# Symmetrical Load Differential VCO

# Limitations of the Symmetrical Load Differential VCO

# Proposed Delay Cell (Modified Symmetrical Load Differential VCO)
There are two additional elements used to design new differential VCO extension-
* SWING ENHANCED BLOCK
* SELF-EXCITATED TUBE


The main idea is to eliminate the drawbacks of the proposed VCO structure, while maintaining their advantages. This combination will help to design a new extension delay structure, so that a cascade of 3 stages of these units constitute a High-Performance Voltage-Controlled Oscillator (HPVCO), characterized by a stable output voltage with a wide range of frequencies controlled by the body bias control voltage.

* Swing Enhanced Block

As mentioned before the symmetrical load differential VCO has several drawbacks. To overcome these disadvantages, it is necessary to eliminate the correlation between the voltage control regulation and the output voltage of the oscillator. The addition of a CMOS inverter (M1 and M2) to construct a Swing-Enhanced Block (SEB) is the solution to avoid this problem. The structure of this block is a simple inverter, mainly used to enhance the output voltage swing. This Structure provides a stable output voltage swing not effected by the control voltage regulation. The SEB added introduces a new current that may affect the tail current (M8), which drives to the changes of the output frequency. To stabilize the tail current in the design process, there is a need to optimize the width size of M1 and M2.

* Self-Excited Tube

After adding the SEB, the output voltage swing is enhanced, but this structure affects the VCO sensitivity. The reduction of the VCO gain will narrow the frequency tuning range, which is a critical factor in the ring oscillator performance. To keep the advantage of the SEB, VCO sensitivity should be increased to optimize the range of voltage regulation. This issue is solved by adding a self-excited tube, represented by M6, M7 in the proposed design.

First, when the differential input is low, the differential output is high at a certain control voltage . As for the self-excitation tube structure, the source of M6 is at high potential, and the drain connected to the gate of M4 is at low potential. Since the two-stage source of the transistor can be
interchanged, M6 draws current from, and charges the gate of M4, resulting in the decrease of M4 charge current. On the other hand, when the differential input is high, the differential output is low. In this time, M6 discharges from the gate of M4 to, making the M4 gate potential decreases, resulting in M4 charge current to increase. The self-excited tube M6 alongside M4 function as a negative feedforward, adjusting the linearity and reducing the phase noise.

![image](https://user-images.githubusercontent.com/35188692/155860929-a2111577-a592-4d39-8611-5bf0f35fe310.png)
Fig.3 3-Stage Voltage Controlled Ring Oscillator

# Tools Used-
• Synopsys Custom Compiler:
 The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

• Synopsys Primewave:
 PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

• Synopsys 28nm PDK:
 The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.
 
 # Pre-Layout Schematics and Simulations-
 # Schematics:-
 Initially Schematic of the Proposed Delay cell was implemented and converted into a symbol so that it could be used directly as delay cell from the library and 3-stage ring oscillator can be constructed using this.
 file:///home/bhawarth/Pictures/Screenshot%20from%202022-02-21%2014-43-08.png![image](https://user-images.githubusercontent.com/35188692/155859787-604590eb-0b72-44c4-8c8e-c1658502849a.png)

file:///home/bhawarth/Pictures/Screenshot%20from%202022-02-21%2020-28-55.png![image](https://user-images.githubusercontent.com/35188692/155859888-e31abf7f-acaf-4fb9-9569-f0b7127b2ab1.png)

file:///home/bhawarth/Pictures/Screenshot%20from%202022-02-23%2019-28-55.png![image](https://user-images.githubusercontent.com/35188692/155859927-5607605f-97dc-4433-a992-d794b52e98ac.png)

# Simulations:-
## Transient Simulation:-

file:///home/bhawarth/Pictures/Screenshot%20from%202022-02-22%2011-42-47.png![image](https://user-images.githubusercontent.com/35188692/155860028-68c2f7bc-f0bc-49ef-9a46-9ac86d773a13.png)

file:///home/bhawarth/Pictures/Screenshot%20from%202022-02-22%2012-05-38.png![image](https://user-images.githubusercontent.com/35188692/155860047-6bdcfcb9-b617-4de4-8486-3c35f79e0b16.png)
