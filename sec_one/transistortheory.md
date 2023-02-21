transistors -> logic cells -> functional units -> computers

Transistors are cool as fuck--substantial active research--lots of variation in implementation. 
The basic throughline definition is: Semiconductor with 3 layers which controls the voltage flowing through a circuit by allowing current to flow/not flow (switch mode), and by amplifying a low current (amplifier mode).

Combining transistors in a mindbogglingly-genius fashion (called a **Digital Circuit**) allows for logic table implementation; p, q, -p, -q, p|q, p&q, p->q, etc. This enables basic math operations like add/subtract/multiply/divide, using for example, the **Binary Addition Algorithm**. 
A program will specify which operations it wants performed on which data, from there the machine will know which digital circuit(s) to use for the operations specified. Can be thought of as a function, "my inputs are 1's and 0's, my function is the digital circuits, my output is what I want my machine to do... how can I adjust my input and function to create the desired output?"

> This is at the heart of how computers work, the ability to change the values in memory is the ability to change what those values represent and craft an experience for the user. 

e.g Sound recorded by mic -> string of binary representing that sound ->  speaker translates binary back into sound (high/low pressure zones).
Perhaps any experience can be represented in binary...

### Back to Transistors

A common transitor-type called an FET works like this, the 'base' is connected to the input circuit, the 'emitter (aka source)' and 'collector (aka sink)' is connected to the output circuit. When the transistor is in "switch" mode, if the base recieves a voltage, current can flow from the emitter to collector, if no voltage, current does not flow. When the transistor is in "amplifer" mode, the output voltage is proportional to the voltage supplied to the base... i.e if the emitter is a weak voltage, and a voltage is applied to the base, the collector will recieve a greater current. I'll skip the physics of how this works (capacitors, charge etc) for the sake of progress.
Compared to a logic table, the input to the base represents p,q... and the output of the emitter would represent whether something like p&q is true. Combining these logic systems creates a digital circuit and allows for mathematical operations on memory.

In practice, the most common transistor in digital devices is the CMOS. Due to it's low power consumption (consumes very little power when inactive/in steady state/not switching) battery life is saved as fuck... also, CMOSs offer high noise immunity--their process is not affected by electrical noise from other systems, aiding in high integrations density (#transistors/area) and fewer hair pulling rage moments of clusterfucked retardery which technology likes to provide.