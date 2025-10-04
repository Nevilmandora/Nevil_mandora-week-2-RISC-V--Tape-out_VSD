# Part2 : labs (Hands-on Functional Modelling) of BabySoC Model

# Key Objective :

* To build a solid understanding of SoC fundamentals and practice functional modelling of the BabySoC using simulation tools (Icarus Verilog & GTKWave). 



## Introduction to VSDBabySoC :

* VSDBabySoC is a small yet powerful RISCV-based SoC.

* The main purpose of designing such a small SoC is to test three open-source IP cores together for the first time and calibrate the analog part of it. 

* VSDBabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices.





## What is SoC 

* The CPU, internal memory, I/O ports, analog processor, as well as additional application-specific circuit blocks, are all designed to be integrated on the same chip. SoCs differentiate themselves from traditional devices and PC architectures, where a separate chip is used for the CPU, GPU, RAM, and other essential functional components.

* An SoC is a single-die chip that has some different IP cores on it. These IPs could vary from microprocessors (completely digital) to 5G broadband modems (completely analog).


##  What is VSDBabySoC?

* VSDBabySoC is a compact SoC featuring:

  **RVMYTH: A simple RISC-V-based CPU core.**

  **PLL: An 8x Phase-Locked Loop for stable clock generation.**

  **DAC: A 10-bit Digital-to-Analog Converter for interfacing with analog devices.**


* Its primary purpose is to integrate and test these IPs collaboratively and calibrate the analog part of the SoC.

## Problem Statement :

This project delves into designing a compact, open-source System on Chip (SoC) based on RVMYTH, a RISC-V-based processor core. The SoC integrates a Phase-Locked Loop (PLL) for precise clock generation and control, alongside a 10-bit Digital-to-Analog Converter (DAC) for interfacing with external analog systems. By converting digital signals into analog, this DAC allows BabySoC to communicate with devices that accept analog inputs, such as televisions and mobile phones, enabling output in the form of audio or video. Ultimately, this Sky130-technology-based SoC aims to provide a highly documented, educational platform for learning and experimentation in digital-analog interfacing.


### What is SoC ?

* An SoC is a single-die chip that has some different IP cores on it. These IPs could vary from microprocessors (completely digital) to 5G broadband modems (completely analog).


### What is RVMYTH

* The RVMYTH core is a simple RISC V-based CPU designed for educational purposes and small-scale applications. It provides a practical example of a RISC-V processor implementation.


### What is PLL

* Phase-Locked Loop (PLL): A phase-locked loop or PLL is a control system that generates an output signal whose phase is related to the phase of an input signal. PLLs are widely used for synchronization purposes, including clock generation and distribution.


### What is DAC

* Digital-to-Analog Converter (DAC): A DAC is a system that converts a digital signal into an analog signal. DACs are widely used in modern communication systems, enabling the generation of digitally-defined transmission signals.


## Project Structure :

**src/include/ - This directory include all header files(.vh) and some macro definitions.**

**src/module/ - This directory include all the necessary verilog files like dac, pll, vsdbabysoc, testbench etc.. So all the .v files are here for all modules.**

**output/ - This directory includes all simulation output files after simulation.**



## VSDBabySoC Project Setup and Prepare Directory :

I crated this structure for the project.

     VSDBabySoC/
     ├── src/
     │   ├── include/
     │   │   ├── sandpiper.vh
     │   │   └── other header files...
     │   ├── module/
     │   │   ├── vsdbabysoc.v      # Top-level module integrating all components
     │   │   ├── rvmyth.v          # RISC-V core module
     │   │   ├── avsdpll.v         # PLL module
     │   │   ├── avsddac.v         # DAC module
     │   │   └── testbench.v       # Testbench for simulation
     └── output/
     └── compiled_tlv/         # Holds compiled intermediate files if needed




## Clone the project :

* We can clone the VSDBabySoC project structure from github or also you can create the project structure as mentioned above. and after create this type of project structure we can copy the content of the files from github repo and paste it in our structure of project and then we can done simulation.

         cd ~/VLSI

         cd ~/VLSI/VSDBabySoC/

         cd ~VLSI/VSDBabySoC/src/module/
         avsddac.v  clk_gate.v      pseudo_rand_gen.sv  rvmyth.v      testbench.rvmyth.post-routing.v  vsdbabysoc.v
         avsdpll.v  pseudo_rand.sv  rvmyth.tlv          rvmyth_gen.v  testbench.v
     
* follow above commands and check for the files that are included in src/module/

* if you have clone project from git then the structure is ready and if you have create the project structure then from git copy the content of all files in your project.


##  TLV to .v conversion of the rvmyth file :

* So in the module directory all .v files are present but for rvmyth .tlv file is there but for the simulation in iverilog we need .v file of rvmyth module.
so we need to convert that file to .v file.

       # Step 1: Install python3-venv (if not already installed)
       sudo apt update
       sudo apt install python3-venv python3-pip

       # Step 2: Create and activate a virtual environment
       cd ~/VLSI/VSDBabySoC/
       python3 -m venv sp_env
       source sp_env/bin/activate

       # Step 3: Install SandPiper-SaaS inside the virtual environment
       pip install pyyaml click sandpiper-saas

       # Step 4: Convert rvmyth.tlv to Verilog
       sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/


* After running the above commands the rvmyth.v file will be generated inside src/module/ directory. you can confirm that by listing files indide src/module/ directory.

* Now we are ready for the simulation.


## Simulation Steps :

* For the pre-synthesis simulation, run the following commands










