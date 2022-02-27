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
* [Netlist of the Circuit](#Netlist-of-the-Circuit)
* [Author](#Author)
* [Acknowledgements](#Acknowledgements)
* [References](#References)


# Introduction
Common VCO implementations are LC oscillators and ring oscillators. In integrated circuits, the production of high-performance passive devices (such as inductors) is difficult since these devices occupy a large area and thus LC tank voltage-controlled oscillator becomes inappropriate. Concurrently, Ring Oscillator benefit from the rapid advance of the technology in IC industry, to occupy more and more small area on the chip, while keeping all its appealing characteristics such as the large frequency tuning range, and the good linearity,making it widely used in industrial products and academic designs.


![image](https://user-images.githubusercontent.com/35188692/155887395-090cdf7e-5b5e-4718-b1d9-84ee6c7a11a9.png)

# Symmetrical Load Differential VCO

For VCO's conventional design, due to the wide range of oscillator applications in different environmental requirements, VCO has different structural and performance parameters. The basic circuit structure of this study is designed and implemented using the symmetrical load differential VCO structure.

![image](https://user-images.githubusercontent.com/35188692/155882747-f26eb414-c88b-4f50-b25a-09b98b07b233.png)

Fig.1 PMOS Symmetric Load Differential VCO


# Limitations of the Symmetrical Load Differential VCO
* In the VCO delay unit circuit, the control signal is added to the gate of the tail current tube, in order to achieve a working delay unit with voltage control. Therefore, there is a need to design a new delay unit circuit, so that the cascade of differential VCO has a wide voltage regulation (tuning) range and a full swing output signal.
* Single-ended ring oscillators suffer from the low phase noise performance and frequency limitations, therefore other architectures can be applied.

# Proposed Delay Cell (Modified Symmetrical Load Differential VCO)
There are two additional elements used to design new differential VCO extension-

[1] SWING ENHANCED BLOCK

[2] SELF-EXCITATED TUBE

![image](https://user-images.githubusercontent.com/35188692/155887047-77af5262-865a-4675-8519-de6ca41a7b49.png)


The main idea is to eliminate the drawbacks of the proposed VCO structure, while maintaining their advantages. This combination will help to design a new extension delay structure, so that a cascade of 3 stages of these units constitute a High-Performance Voltage-Controlled Oscillator (HPVCO), characterized by a stable output voltage with a wide range of frequencies controlled by the body bias control voltage.

<b>• Swing Enhanced Block:</b></br>
As mentioned before the symmetrical load differential VCO has several drawbacks. To overcome these disadvantages, it is necessary to eliminate the correlation between the voltage control regulation and the output voltage of the oscillator. The addition of a CMOS inverter (M1 and M2) to construct a Swing-Enhanced Block (SEB) is the solution to avoid this problem. The structure of this block is a simple inverter, mainly used to enhance the output voltage swing. This Structure provides a stable output voltage swing not effected by the control voltage regulation. The SEB added introduces a new current that may affect the tail current (M8), which drives to the changes of the output frequency. To stabilize the tail current in the design process, there is a need to optimize the width size of M1 and M2.

<b>• Self-Excited Tube:</b></br>
After adding the SEB, the output voltage swing is enhanced, but this structure affects the VCO sensitivity. The reduction of the VCO gain will narrow the frequency tuning range, which is a critical factor in the ring oscillator performance. To keep the advantage of the SEB, VCO sensitivity should be increased to optimize the range of voltage regulation. This issue is solved by adding a self-excited tube, represented by M6, M7 in the proposed design.

First, when the differential input is low, the differential output is high at a certain control voltage . As for the self-excitation tube structure, the source of M6 is at high potential, and the drain connected to the gate of M4 is at low potential. Since the two-stage source of the transistor can be
interchanged, M6 draws current from, and charges the gate of M4, resulting in the decrease of M4 charge current. On the other hand, when the differential input is high, the differential output is low. In this time, M6 discharges from the gate of M4 to, making the M4 gate potential decreases, resulting in M4 charge current to increase. The self-excited tube M6 alongside M4 function as a negative feedforward, adjusting the linearity and reducing the phase noise.

![image](https://user-images.githubusercontent.com/35188692/155881503-0af6d76e-4a60-4784-8add-9e889e1c2beb.png)

Fig.3 3-Stage Voltage Controlled Ring Oscillator

# Tools Used-
<b>• Synopsys Custom Compiler:</b></br>
The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

<b>• Synopsys Primewave:</b></br>
 PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

<b>• Synopsys 28nm PDK:</b></br>
 The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.
 
 # Pre-Layout Schematics and Simulations-
 # Schematics:-
 Initially Schematic of the Proposed Delay cell was implemented and converted into a symbol so that it could be used directly as delay cell from the library and 3-stage ring oscillator can be constructed using this.
![image](https://user-images.githubusercontent.com/35188692/155859787-604590eb-0b72-44c4-8c8e-c1658502849a.png)
Fig.4 Proposed Delay Cell Schematics

![image](https://user-images.githubusercontent.com/35188692/155882176-4947a80c-0a3e-4a32-a263-798c5b8bc44f.png)
Fig.5 Symbol view of the Delay Cell

![image](https://user-images.githubusercontent.com/35188692/155859888-e31abf7f-acaf-4fb9-9569-f0b7127b2ab1.png)
Fig.6 Schematic of Single Stage Delay Cell

![image](https://user-images.githubusercontent.com/35188692/155859927-5607605f-97dc-4433-a992-d794b52e98ac.png)
Fig.7 3-Stage Voltage Controlled Ring Oscillator

# Simulations:-
## Transient Simulation:-
After creating and saving the schematic go to 'Tools' and open 'Primewave' to start the simulation. In the Primewave select the 'model file' i.e the '28nm PDK's .lib file presentin the HSPICE folder. After this select the 'tran' analysis in the analysis window and give the 'Start', 'Stop', and 'Step Size' parameters and save it. Then add the outputs which needs to be plotted by selecting the nets on the schematic.

![image](https://user-images.githubusercontent.com/35188692/155860028-68c2f7bc-f0bc-49ef-9a46-9ac86d773a13.png)
Fig.8 Transient Response of a single stage Delay Cell

![image](https://user-images.githubusercontent.com/35188692/155860047-6bdcfcb9-b617-4de4-8486-3c35f79e0b16.png)
Fig.9 Transient Response of 3-stage VCO

## Parametric Sweep:- 

![image](https://user-images.githubusercontent.com/35188692/155882240-15a7e9c4-c90c-4b53-9b3f-20cd781b8dbd.png)
Fig.10 Control Voltage vs Frequency graph for 1.2V Supply Voltage


# Netlist of the Circuit:

Refer to the netlist of the Delay cell here: <a href='differential_CSVCO.cir.out'>Netlist</a>

Refer to the netlist of the 3-Stage Voltage Controll Ring Oscillator here: <a href='bg_delay_cell_prac1.cir.out'>Netlist</a>


# Author:
• Bhawarth Gupta, B.Tech(ECE), Bharati Vidyapeeth (Deemed University) College of Engineering, Pune

# Acknowledgements:
• <a href='https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/'>Cloud Based Analog IC Design Hackathon</a></br>
• <a href='https://www.synopsys.com/'>Synopsys India</a></br>
• <a href='https://www.vlsisystemdesign.com/'>VLSI System Design (VSD) Corp. Pvt. Ltd India</a></br>

# References:
[1] H. Bazzi, M. A. Chanine, A. Mohsen and A. Harb, "A low-noise voltage-controlled ring oscillator in 28-nm FDSOI technology," 2017 29th International Conference on Microelectronics (ICM), 2017, pp. 1-4, doi: 10.1109/ICM.2017.8268826.
