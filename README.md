# VSD-Hardware Design Program

Documentation on SoC Design from Specifications to RTL to GDSII

- [WEEK_0](#WEEK_0)
  - [Introduction_to_Overall_RTL2GDS_Flow](#Introduction_to_Overall_RTL2GDS_Flow)
    An IP which is Silicon proven holds highest weightage.
A sigle chip cycle takes a duration of 14-16 months.
Out of this, nearly 4 months are taken to process the GDS data to be fabricated on silicon wafer.
Steps involved to convert to IP Specifications to RTL to GDSII for fabrication:
Step 1: 
Consider an Application written in C language, 
we use GCC (GNU(Gnu's Not Unix) Compiler Collection) to test the application and measure ouput O0.
Step 2:
Model the specifications in C-format, and test the application with this model.
In this particular case, we use RISC-V GCC to compile and test the application and measure O1.
O0 should be equal to O1.

With these steps we freeze the specifications.
Step 3:
Writing softcopy of Hardware.
Basic using Verilog.
Industries use advanced platforms like Bluespec, Chisel.
Again run the same application on this hardware and measure O2.
O1 should be equal to O2.



Step 4:
Dividing Verilog code as:
	Processor (Gate-level IPs need to be synthesizable )
	Peripherals/Ips 
		ANALOG, need not be synthesizable (DAC,ADC,PLL)
		Macros, need to be synthesizable (Ex.: Clock divider circuits)

Step 5:
SoC integration using GPIOs.
The same application is run on this Integarated SoC and ouput O3 is generated.
Finally, O0=O1=O2=O3
Step 6:
Mask Layout design, and generate GDSII(Graphical Data Stream Information Interchange)


Additional Info:
MicroProcessor is part of Microcontroller.
- [WEEK_1](#WEEK_1)
