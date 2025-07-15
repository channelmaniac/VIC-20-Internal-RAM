# VIC-20-Internal-RAM
An internal RAM expansion board for the VIC-20.

The VIC-20 is an interesting computer, but has an oddity in that you're limited to one cartridge at a time... Do you use memory? Do you use some other hardware interface? I thought it was a bit silly so I created an internal memory upgrade board. I also did this as a learning experience as this is my first GAL to design the equations for. 

![VIC-20 PCB with internal RAM module installed](https://github.com/channelmaniac/VIC-20-Internal-RAM/blob/main/Installed.jpg)

This board uses a single 32K x 8 SRAM chip and a bank of 6 DIP switches to enable/disable individual banks of memory using the already decoded memory bank enables on the cartridge port:

These represent the 3K expansion cartridge:
* RAM 1 = 0400 - 07FF
* RAM 2 = 0800 - 0BFF
* RAM 3 = 0C00 - 0FFF

These represent the 8, 16, and 24K cartridges:
* Block 1 = 2000 - 3FFF
* Block 2 = 4000 - 5FFF
* Block 3 = 6000 = 7FFF

The board uses a few flying wires for the signals it cannot get from the CPU which include the above mention memory bank enables from the cartridge port plus the VR/W signal off the same cartridge port.

The only shortcoming with this board is that the DIPs are internal. This can cause problems with some game cartridges, notably the ones that use Block 1, 2, and/or 3 instead of Block 5 (A000 - BFFF) for the ROM addresses. Star Trek Strategic Operations Simulator is one such cartridge that uses Block 1 address space.

The PCB is easy to build, with only one surface mount part - the SOJ packaged static RAM chip. As for the GAL, any 16V8x should work for it. I used a GAL16V8A-25 in my initial build. GALs are reusable, so no need to go buy one if you have a scrap PCB you can salvage one from. I pulled the one I used off an old 8-liner gambling PCB that I already pulled the ROMs, SRAMs, and Z80 off of for use in repairing arcade game PCBs. You can use a right angle header for the flying wires or solder wires straight to the PCB, that's up to you, but for clearance, don't use a straight header or you'll hit the keyboard above the PCB. **The pins on the header connecting to the CPU socket must be trimmed to not interfere with the placement of the CPU socket on the PCB. Also, the pins on the DIP switches, GAL, and input header need to be trimmed to clear the ROM next to the CPU.** While it's not critical to clear the ROM if you have sufficient contact with the CPU socket, It personally bugs me to see a PCB touching chips under it and not seating down level in the socket.

It has been tested in the revision of VIC-20 that runs off a DC supply. It should fit in the older revision, but has not been tested in one as of yet.

![VIC-20 Dead Test Cart results for the RAM module](https://github.com/channelmaniac/VIC-20-Internal-RAM/blob/main/VIC-20%20DT.jpg)

Inputs are labeled on the bottom silk screen. DIP switch info is on the top silk screen.

The cartridge pins for connections are easy to access and are on the upper set so no need to try to get to the bottom row for attaching the wires.

Cartridge slot pin: Signal Name
* 10 - Block 1
* 11 - Block 2
* 12 - Block 3
* 13 - Block 5 (NOT USED)
* 14 - RAM 1
* 15 - RAM 2
* 16 - RAM 3
* 17 - VR/W
