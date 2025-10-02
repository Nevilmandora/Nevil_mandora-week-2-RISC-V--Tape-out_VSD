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

  ** RVMYTH: A simple RISC-V-based CPU core.

  ** PLL: An 8x Phase-Locked Loop for stable clock generation.

  ** DAC: A 10-bit Digital-to-Analog Converter for interfacing with analog devices.


* Its primary purpose is to integrate and test these IPs collaboratively and calibrate the analog part of the SoC.



