Field Programmable Gate Arrays are a mindblowingly good idea. Instead of computing the operation every time, they store all of the precomputed possible output values of that operation in a Look Up Table (small memory array), and the input is the index to the correct output. Some LUTs are reprogrammed on the fly by rewritting the values stored in memory as the program runs (changing boolean function (increased flexibility, greater cost to $ and elements of performance)), some are hard coded by the manufacturer and cannot be changed, rarely... they can be changed using special tools by the programmer. 
This possibility for reconfiguration are FPGAs primary distinction. The operations performed by the logic blocks; the interconnection sequence between different logic blocks (i.e. the path taken by the input before a final output is reached), and I/O block standards (what other systems the FPGA communicates with, and acceptable parameters) can all be configured to serve user needs.

This is how an FPGA is structured:
- I/O blocks attached to the chip boundary. These generally contain an input buffer (containing a Schmitt trigger), output drivers, and programmable I/O standards. They allow for communication with a range of external devices of various voltages and communicaton protocols. There is considerable wonderful trickery involved to ensure optimal signal quality and drive strength.
- Combinational Logic Blocks (CLB) are packed densly throughout the FPGA. These house LUTs, Flip-Flops, Multiplexers (MUXs), Routing Resources, SRAM, and sometimes distributed RAM. They are the workhorse of the FPGA/they perform the logical functions.    
    - Note: Flip Flops are used to store one bit of memory, or to synchronize the processes according to a clock input.
- Local Communication channels allow for high bandwidth, low latency communication within CLBs, or between neighbouring CLBs.
- Global Commincation channels allow for low bandwidth, high latency communication (compared to local) between CLBs throughout the FPGA.
- Routing matrices are 3D grid of wires fed by the communication channels which act like railroad switches. They customize the digital circuits by saying "go from this logic block, to this one". Brilliant engineering considering there can be hundreds to millions of logic cells within an FPGA. Naturally, there are fare more than one routing matrix per FPGA.
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
(plus analog :stuff)
+ parallel processing of data
+ even faster and larger than FPGAs
+ cheap (per piece)
- expensive (one time)
- non-reprogrammable
- Months from design to chip



To answer the courses more specific question--the logic blocks within FPGAs are buildable using transistors in the following manner... 

CLBs:
    Although the output values in the LUT are preprogrammed--allowing for the unit to skip the logical function computation--the LUT still needs to implement the logical function in order to generate an accurate lookup table.
    So, this logical (boolean) function is simulated by the relevant logic units, which of course is built, in part, out of transistors, as discussed in transistortheory.md.

I/O Units:
    As a functional unit, transisors just HAAAD to get involved again didnt they!!! I/O units require input buffers and ouput amplifers to mold signals into size and shapes that each side requires; they act as an interface. Both use transistors amplification powers in specific digital circuits to do what needs to be done... there's a lot of further complexity that I'm not touching right now... from CHATGPT: 
    
    > In addition to input buffers and output drivers, other transistor-based circuits can be used to implement different types of I/O functional units, such as data converters, signal filters, and timing generators. These circuits can be designed using different transistor topologies, such as CMOS, TTL, ECL, or BiCMOS, depending on the specific requirements of the system in terms of power consumption, speed, noise immunity, and signal integrity.

Routing matrices:
    Transistors act as the switches which control which CLBs are connected. The wires of the communication channels go through the routing matrix, transistors connect or disconnect these wires... more specifically, when a congifuration bit (implemented by a transistor) is 1, the current flows, when the config bit is 0, it does not. 
    Combining these configuration bits/switches and wires within the routing matrix allows for a programmable network of interconnections between logic units, allowing for a massive set of possible digital circuits.


### Logic Units Definition Detour

Logic gate:
    Boolean function implementation, with >= 1 input and 1 output.

Flip-Flop: 
    Impressive little fuckers. Using (genrally) a positive feedback loop of two transistors, they are able to store and output a bit of input, usually just for the length of one clock cycle, but can be minutes or HOURS (a lot compared to a 1.8GHz clock) at a time. 
    Lots of variation, but D flip-flops work thusly:
        Inputs: data (1 or 0), and clock signal
        Outputs: normal output, inverted output

    When clock transitions to rising edge (or falling edge, depends on implementation), the outputs update to match the data input... if no change in input, no change.
    The purpose of the inverted output (if normal is 1, inverted is 0 (no way!!!!)) is multifaceted... can act as a signal to other flip flops (logic craziness), create a delayed clock input for flip flops downstream (synchornizes the circuit), or for error detection/correction (can occur due to noise or other factors... having inverse gives a signal not vital to operation, but indicates what the output is... maybe the output and inverse are the same!! Disaster!!1!!!)

Multipler (Mux):
    These gentlemen kindly make digital circuits far more simple and streamlined. They receive a large number of inputs, and select a single one to be output... essentially a "signal selector." Otherwise each input would require a dedicated processing system... instead, it waits politely in the mux for it's turn to be processed.


### SummmaaAARRRRYYY!

FPGAs are dynamic functional units which a programmer can ask politely to do whatever he needs it to do.