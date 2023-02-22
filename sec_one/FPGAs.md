Field Programmable Gate Arrays are a mindblowingly good idea. Instead of computing the operation, they store all of the precomputed possible output values of that operation in a Look Up Table, and the input is the index to the correct output. This is configured by the programmer and can be reconfigured to perform different operations. 
This possibility for reconfiguration are FPGAs primary distinction, the operations performed by the logic blocks,the interconnection sequence between different logic blocks (i.e. the path taken by the input before a final output is reached), and I/O block standards (what other systems the FPGA communicates with, and acceptable parameters) can all be configured to serve user needs.

This is how an FPGA is structured:
- I/O blocks attached to the chip boundary. These generally contain an input buffer (containing a Schmitt trigger), output drivers, and programmable I/O standards. They allow for communication with a range of external devices of various voltages and communicaton protocols. There is considerable wonderful trickery involved to ensure optimal signal quality and drive strength.
- Combinational Logic Blocks (CLB) are packed densly throughout the FPGA. These house LUTs, Flip-Flops, Multiplexers (MUXs), Routing Resources, SRAM, and sometimes distributed RAM. They are the workhorse of the FPGA/they perform the logical functions.    
    - Note: Flip Flops are used to store one bit of memory, or to synchronize the processes according to a clock input.
- Local Communication channels allow for high bandwidth, low latency communication within CLBs, or between neighbouring CLBs.
- Global Commincation channels allow for low bandwidth, high latency communication (compared to local) between CLBs throughout the FPGA.
- Routing matrix is a 3D grid of wires fed by the communication channels which act like railroad switches. They customize the digital circuits vy saying "go from this logic block, to this one". Brilliant engineering considering there can be hundreds to millions of logic cells within an FPGA. Naturally, there are fare more than one routing matrix per FPGA.
- And more! Like DDR memory controllers, DSP blocks, Ethernet controllers, etc...


A given combination of logic blocks creates a digital circuit which performs a specific mathematical operation. Changing the combination changes the digital circuit and hence, the operation. There is a large range of digital circuits, the ability to customize the order of logic blocks allows you to implement complex digital circuits with relatively few logic blocks.

The logic functions in an FPGA are responsible for processing and manipulating input data as it flows through the FPGA. This includes operations such as filtering, modulation, demodulation, encryption, decryption, compression, decompression, and more. The specific logic functions used in an FPGA design depend on the requirements of the application and can be programmed and optimized for specific performance, power, and area constraints.


Why use FPGAs?
+ Implement any logic functionality
+ Change the design at any time
+ parallel processing of data
+ many I/O pins to interface other
electronics
- expensive (per piece)
- need lots of power / different voltages
- tricky board design (BGA chips, Multilayer, ...)
- complex tools
Microcontrollers?
+ cheap
+ easy to programm
+ simple board layout
- slow
- no parallel execution of tasks
- limited to internal execution set
ASICs?
+ Implement any logic functionality
(plus analog stuff)
+ parallel processing of data
+ even faster and larger than FPGAs
+ cheap (per piece)
- expensive (one time)
- non-reprogrammable
- Months from design to chip