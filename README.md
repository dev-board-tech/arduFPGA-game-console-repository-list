### This is a map on how to use repositories on this collection.

A brief list of designs, boot loaders and applications in order to easily identify the necessary modules and customize them according to your necessities:

1. #### Schematics:
 1. arduFPGA-game-console schematic:
    * The schematic of the arduFPGA-game-console board.
    * The schematic of the arduFPGA-iCE40UP5K board.

1. #### Designs:
 1. [HDL Atmega/Atxmega core IP](https://github.com/dev-board-tech/hdl-core-mega-xmega) :
    * Is the Atmega/Atxmega soft-core HDL design that can be used in designs by people that are familiar with Atmega/Atxmega microcontrollers on arduFPGA-game-console board.
 1. [HDL RISC-V version 1 core IP](https://github.com/dev-board-tech/hdl-core-riscv-lite):
    * Is the first version of a RISC-V32I soft-core HDL design that is split in two, one version with separate BUS'es one for instruction fetch and one for data load/store, and one soft-core with single BUS, unfortunately this core is not optimized on running on arduFPGA-game-console, running at up to 5Mhz in both single/dual BUS mode because there is a need for a large number of registers to create 32 registers with 32 bits, so it uses BLOCK RAM as registers latching the outputs at negative clock, this core include a nested interrupt controller with configurable number of interrupt lines ***DEPRECATED***.
 1. [HDL RISC-V version 2 core IP](https://github.com/dev-board-tech/hdl-core-riscv-lite-v2):
    * Is the second version of a RISC-V32I soft-core HDL design better optimized on running on arduFPGA-game-console being able to configure it on single/dual BUS running at frequencies up to 15Mhz without timing violations and up to 22Mhz overclocked, this core include an nested interrupt module with configurable number of interrupt lines.
 1. [HDL IO IP's (PIO, UART, SPI, TWI...)](https://github.com/dev-board-tech/hdl-core-common):
    * Is the repository with all the IO's that can be wired to the Atmega/Atxmega and RISC-V cores or be used in custom standalone designs.
 1. [HDL Atmega32U4 design template](https://github.com/dev-board-tech/arduFPGA-mega-design-template-simple):
    * Is the template that allow developers to have a very easy on starting building an Atmega32u4 compatible microcontroller.
 1. [HDL Arduboy emulator](https://github.com/dev-board-tech/arduFPGA-iCE40UP5K-arduboy-emulator):
    * Is the complete design of strictly necessary modules to compose an Atmega32u4 microcontroller allowing most of ArduBoy compatible Games/Applications to run, this design contains even more modules that allow it to optionally output the display content to a VGA compatible screen, to set the volume of the headphones, include a Atmega UART to USB adaptor module to connect the arduFPGA-game-console directly to the PC and communicate through emulated UART interface.
 1. [HDL/APP Mini tank controller](https://github.com/dev-board-tech/arduFPGA-game-console-simple-tank-demo):
    * Is a very simple application for arduFPGA-game-console that allow users to control a mini tank using this board.
 1. [HDL/APP LYRA crypto wallet as template](https://github.com/dev-board-tech/arduFPGA-game-console-lyra-wallet):
    * A complete design and application as Proof Of Concept for arduFPGA-game-console to be used as a digital cryptocurrency hardware wallet.

1. #### Bootloaders:
 1. [arduFPGA-game-console first stage boot-loader](https://github.com/dev-board-tech/arduFPGA-mega-first-stage-boot-loader):
    * This boot-loader is the heard that beat in the background without even the application knowing that run, this boot-loader load the second stage boot-loader or user application into the program memory of a compatible microcontroller design and pass the control to it, this boot-loader include a service routine that is called every 1mS by a dedicated interrupt line called NMI (Non Makeable Interrupt) allowing this boot-loader to change design settings if INT button in combination with another button are press, if INT button is short press the boot-loader will load the second stage boot loader into program memory and pass the control from user application to the second stage boot-loader that is a GUI explorer.
 1. [arduFPGA-game-console second stage boot-loader GUI](https://github.com/dev-board-tech/arduFPGA-mega-second-stage-boot-explorer):
    * This boot-loader is a simple GUI uSD explorer that facilitate the user to navigate thru uSD directories to select applications to load and run, if this boot-loader has taken the control from an user application will save the EEPROM content to uSD with the same name as the application but with .eep extension, when user selects an application to load an run this boot-loader will load the EEPROM content from uSD before passing the control to the user application if a file with the same name as the loaded application and .eep extension is found, as well before loading user application the second stage boot-loader will search in the same directory of the application for the design to be written to the FPGA and the compatible second stage boot-loader if they are found or updated.

1. #### Debuggers:
 1. [arduFPGA debugger PC tool](https://github.com/dev-board-tech/arduFPGA-external-programing-tool):
    * In order to use this debugger tool the first stage boot-loader need to include the debug section and the user application not to use the same UART interface as the debug section in first stage boot-loader.
 1. [arduFPGA debugger PC interface](https://github.com/dev-board-tech/arduFPGA-debugger):
    * A graphical interface for easy read/write edit memory content on a design that include the debug section in the first stage boot-loader.

1. #### Applications:
 1. [HDL/APP Mini tank controller](https://github.com/dev-board-tech/arduFPGA-game-console-simple-tank-demo):
     * Is a very simple application for arduFPGA-game-console that allow users to control a mini tank using this board.
 1. [HDL/APP LYRA crypto wallet as template](https://github.com/dev-board-tech/arduFPGA-game-console-lyra-wallet):
 * A complete design and application as Proof Of Concept for arduFPGA-game-console to be used as a digital cryptocurrency hardware wallet.

1. #### Utilities:
 1. [File translators](https://github.com/dev-board-tech/intel-hex-to-rtl-mem):
    * A console application that allow for automatically convert bin or hex files into mem files that can be used as ROM content into the designs, can be used in post build events command line.

1. #### SDK's:
 1. [Multiplatform SDK](https://github.com/dev-board-tech/multiPlatformCPP-SDK):
    * A multiplatform CPP SDK with a lot of libraries and drivers for standalone application development.
