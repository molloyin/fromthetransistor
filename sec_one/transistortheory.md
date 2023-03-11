## transistors -> logic cells -> functional units -> computers

Transistors are cool as fuck--substantial active research--lots of variation in implementation. 
The basic throughline definition is: Semiconductor with 3 layers which controls the voltage flowing through a circuit by allowing current to flow/not flow (switch mode), and by amplifying a low current (amplifier mode). Another key capability, they can store charge in a capacitor(s) between the emmitter and collector! This charge is commonly used to implement computer memory... charge in capacitor == 1... to read this value, voltage is applied to the base, allowing the stored charge to flow to a sense amplifier/memory controler, which detects charge || no charge. In other words, transitor acts as a switch which controls the the flow of charge between the capacitor, and the bitline(wire between capacitor and memory controller)
To replenish the capacitor voltage, and protect memory from charge leaking over time, these circuits are refreshed at least once every few milliseconds. More on this later.

Combining transistors in a mindbogglingly-genius fashion (called a **Digital Circuit**) allows for logic table implementation; p, q, -p, -q, p|q, p&q, p->q, etc. This enables basic math operations like add/subtract/multiply/divide, using for example, the **Binary Addition Algorithm**. 
A program will specify which operations it wants performed on which data, from there the machine will know which digital circuit(s) to use for the operations specified. Can be thought of as a function, "my inputs are 1's and 0's, my function is the digital circuits, my output is what I want my machine to do... how can I adjust my input and function to create the desired output?"

> This is at the heart of how computers work, the ability to change the values in memory is the ability to change what those values represent and craft an experience for the user. 

e.g Sound recorded by mic -> string of binary representing that sound ->  speaker translates binary back into sound (high/low pressure zones).
Perhaps any experience can be represented in binary...

### Back to Transistors

A common transitor-type called an FET works like this, the 'base' is connected to the input circuit, the 'emitter (aka source)' and 'collector (aka sink)' are connected to the output circuit. When the transistor is in "switch" mode, if the base recieves a voltage, current can flow from the emitter to collector, if no voltage, current does not flow. When the transistor is in "amplifer" mode, the output voltage is proportional to the voltage supplied to the base... i.e if the emitter is a weak voltage, and a voltage is applied to the base, the collector will recieve a greater current. I'll skip the physics of how this works (capacitors, charge etc) for the sake of progress.
Compared to a logic table, the input to the base represents p,q... and the output of the emitter would represent whether something like p&q is true. Combining these logic systems (NOT, AND, OR, XOR, etc.) creates a digital circuit and allows for mathematical operations on memory.

In practice, the most common transistor in digital devices is the CMOS (allegedly). Due to it's low power consumption (consumes very little power when inactive/in steady state/not switching) battery life is saved as fuck... also, CMOSs offer high noise immunity--their process is not affected by electrical noise from other systems, aiding in high integration density (#transistors/area), compatability, and fewer hair pulling rage moments of clusterfucked retardery which technology likes to provide.


### Refresh

As mentioned earlier, in DRAM systems (the most commonly used type of memory in modern computers, including UMA), memory cells must be refreshed at least once every few milliseconds to prevent bit-flipping and consequent memory corruption. To achieve this, memory arrays in DRAM have their values read by a DRAM controller, and rewritten back to the capicators, restoring them to full charge if 1.
Refreshing can cause issues(performance hit, bit-flipping (row-hammer effect)) if another system is trying to read memory which is being refreshed. Many techniques used to mitigate this... including "hidden refresh" where mem-arrays are divided into sub-mem-arrays and normal read-write operations occur on some, while refreshing occurs on the others, switching as they go.

NOTE: refreshing is unique to DRAM architecture, other memory storage systems use techniques better suited to their particulars.


### SummmmmaaaaarrryYY!!!!!!!!!!

In short... transistor:
- Composed of three semiconductor layers: base, emitter, collector... the base controls flow between the em&co
- Capacitance capabilites between the em&co... in a floating gate transistor, turning off the base while current is flowing through will TRAP charge in the capacitor (floating gate capacitors have a capacitor completely wrapped in an insulating layer. Found in SSDs). DRAM capacitors are charged by appling voltage to the base, which is connected to the capacitor, which is two metal plates seperated by an insulating layer. 
Used to amplify voltage or act as compouter memory.
- Implement digital circuits, composed of logic cells, which to me are the most fundamental element of computer operations... they're how fucking computers WORK babbyyyy
- Implement memory, be it as a single flip-flop, an entire 3D array of DRAM, floating gates in SSD, or other. 


Logic Cell:
- Smallest combinational logic block in digital circuit design... consists of a few transistors and other electronical components, and performs a specific logic function, such as a gate(AND, NOT, OR), flip-flop, or multiplexer. They act as a bulding block for larger, more complex digital circuits.
- NOTE: logic cells sometimes larger than expressed above... consisting of multiple logic gates, etc, to perform a specific task.

Functional Units:
- The larger digital circuits your girlfriend told you not to worry about. They are hardware components that perform specific compututational tasks such as arithmetic/logic operations, memory access operations, encryption/decryption, or other. Examples include, arithmetic and logic units (ALUs), floating point units (PFUs), and I/O units. Usually implemented using many digital circuits/ logic blocks, registers, and other electronic components.
- FPGAs are functional units
- Definitions can get fuzzy, functional units inside functional units inside functional units inside a computer.