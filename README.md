### Bonfire Root Repository
Serves as a parent project to instantiate all Bonfire sub-projects.
It also acts as FuseSoC "cores-root".

#### Required Toolset
Bonfire relies on the following tools

* Xilinx Vivado (preferred Version 2018.1 or 2018.2) - for Xilinx Series 7 Devices
* Xilinx ISE 14.7 - for Spartan 6 Devices
* RISC-V GCC - preferably from [GNU MCU Eclipse Embedded GCC](https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases/tag/v7.2.0-4-20180606/)

* Optionally GHDL for simulation
* [FuseSoC](https://github.com/olofk/fusesoc) as package manager and build tool

* Optionally a port of [eLua](http://www.eluaproject.net/) is provided here: https://github.com/ThomasHornschuh/elua

#### Prebuild Bitstream Quick start guide
If you own a Digilent [Arty A35 Board](https://store.digilentinc.com/arty-a7-artix-7-fpga-development-board-for-makers-and-hobbyists/) a prebuild mcs File is available, which contains the Bonfire Implementation for Arty Board including a simple Boot Monitor and a ready to run eLua image.

##### Installation Instructions
1.  Download the mcs.zip file from [here](https://github.com/bonfireprocessor/bonfire/releases)
1. Unzip it
1. Connect you Arty Board to a USB connector (make sure that Vivado and the Xilinx cable drives are correctly installed)
1. Start Vivado (or the Vivado Labtools)
1. Open the Vivado Hardware Manager (it is available in the qick start pane)
1. Connect to the target board (the Arty, it is named xc7a35t_0 in the HW Manager screen)
1.  In the Hardware Manager window, under hardware right click your device and click Add Configuration Memory Devices
1. window will pop up. Search for “Micron” and select mt25ql128-spi-x1_x2_x4. Click OK on the next window asking if you want to program the configuration memory device.
2. In the following dialog box select the unpzipped .mcs file from step 1 as "Confiugration file". Start programming

##### Connect with a terminal program to the Board

The prebuild mcs image communicates with the usb-uart of the Arty Board with 500.000 Baud 8N1, without any handshaking.

The recommended tool for communication is minicom. In most cases the Arty UART is available under /dev/ttyUSB1, but it can be different.
Start minicom

`$minicom -D /dev/ttyUSB1 -b 500000 `

When pressing the "Prog" button on Arty the monitor boot message should appear. The is a prompt, when you enter "r" followed by <return> the eLua Image is loaded from Flash into memory and started.
The screen should look like as follows:

```
Bonfire Boot Monitor 0.3d (GCC 7.2.0)
MIMPID: 00010014
MISA: 40001100
UART Divisor: 165
Uptime 0 sec
DRAM Size 268435456 bytes
Cache size: 8192 bytes
Line size: 32 bytes
Cache lines: 256
Framing errors: 0
SPI Flash JEDEC ID: 0018ba20

>r
Reading Header
...OK
Boot Image found, length 462848 Bytes, Break Address: 00081f44
...OK
Cache 32768 bytes Flush read from 0fff8000
Heap: 000830b0 .. 0ffef7ff
eLua for Bonfire SoC 1.1
Build with GCC 7.2.0
Initalizing Ethernet core
__virt_timer_period 1666666

eLua v0.9-388-g7e7db3b  Copyright (C) 2007-2013 www.eluaproject.net
eLua#

```
Enter `help` to get a list of commands
```
eLua# help
Shell commands:
  help   - shell help
  lua    - start a Lua session
  ls     - lists files and directories
  dir    - lists files and directories
  cat    - list the contents of a file
  type   - list the contents of a file
  recv   - receive files via XMODEM
  cp     - copy files
  mv     - move/rename files
  rm     - remove files
  ver    - show version information
  mkdir  - create directories
  exit   - exit the shell
For more information use 'help <command>'.
eLua#
```
Enter
`lua /rom/life.lua`

to run the Game of Life demo programs
```
---------O---------------O------
----------O---------------------
-----OO---------O-O-------------
----OO---------OO-OO------------
---OO--O-OO-OOO---O-O----O------
--OO--OO-O---O------O---O-O-----
---O---OOO---O-----O----O-O-----
----OOO------O-O---------O------
-----OOO----OO-OO---------------
------------O-O--------------OO-
-------OO-------------------O--O
---------OO------------------OO-
--------O--O--------------------
---------O-O-------------O------
----------O-------------O-O-----
------------------------O-O-----
Life - generation 50, mem 22.8 kB
Execution time 6.721 sec (6720.62) ms
eLua#

```
For more information about eLua and the Lua Language go to the [eLua Project Page](http://www.eluaproject.net/) and to the [Lua Language Page](https://www.lua.org/)
