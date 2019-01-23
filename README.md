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
If you own a Digilent [Arty A35 Board](https://store.digilentinc.com/arty-a7-artix-7-fpga-development-board-for-makers-and-hobbyists/) a prebuild mcs File is available and you can follow the [Quick Start Guide](https://bonfirecpu.eu/install.html)
