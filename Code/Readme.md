The GAL code is stupid simple... but, hey, it's my first one to write equations for!

It basically goes like this: IF /BLK1 is low OR /BLK2 is low OR /BLK3 is low OR /RAM1 is low OR /RAM2 is low OR /RAM3 is low then /CS goes low. 

Where /BLK1, 2, and 3 and RAM 1, 2, and 3 are decoded RAM addressing signals tapped off the cartridge port and /CS is the chip select on the 32K x 8 SRAM.

![Pic of simulation testing done in WinCUPL](https://github.com/channelmaniac/VIC-20-Internal-RAM/blob/main/Code/WinCUPL%20Simulation.JPG)

What I'd like to do in a future revision is do the memory decoding in the GAL using 4 inputs from a BCD encoded switch to determine which banks to enable. This would allow for easy switching without having to disassemble the computer. It may take me a while to get that set of equations worked out. :) 
