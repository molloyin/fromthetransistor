Covered in FPGAs.md... in brief:

Look up tables are in their simplest form, are a small memory array which store all possible outputs of a boolean function, the input is the index of the correct output... its like a virtual boolean function!

They become even more powerful when you can rewrite the memory cells to implement a different boolean function... creating different digital circuits without changing the hardware.


So.. in a FPGA with SRAM LUTS (reprogrammable)... not only can you create a new digital circuit by changing the boolean function performed by the LUT... but also by changing the CLB configuration using routing matrices.... complexity fucking explodes!