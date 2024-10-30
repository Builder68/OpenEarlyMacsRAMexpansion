# OpenEarlyMacsRAMexpansion

 ## SUMMARY

Unlike the Macintosh Plus, which offers a straightforward SIMM-based memory upgrade, expanding the memory of these early Macs is significantly more complex and requires additional components.
Back in the day, RAM expansion boards were available to increase the memory of early Macs. However, finding these boards in working condition has become increasingly challenging and expensive. The *Mac Rescue board*, one of the very few that provides full 4MB of RAM, is particularly rare.

This newly designed expansion board, paired with an auxiliary board I called **RAM Refresh Configurator**, provides a simple solution to increase memory up to 4MB. The circuitry is largely based on the *Macsnap 548E board from DOVE computer corp.* With a few modifications and enhancements, 4MB RAM was achieved, using higher-density FP DRAM ICs.

![Screenshot 2024-10-22 at 3 00 07 PM](https://github.com/user-attachments/assets/0927eb3d-6c0c-4479-a216-cbbe3e41b88d)
![Screenshot 2024-10-22 at 6 50 35 PM](https://github.com/user-attachments/assets/46a6b025-a1a6-4c5b-a361-0ad218c6825e)

The expansion board has been tested only with MacPlus / 512Ke ROMs. If a *ROM-INATOR board* is installed concurrently, it needs to be previously patched (instructions provided below. Many thanks to Golden Potato and SVGA for this solution!).

## KEY FEATURES

• Configurable to add up to 4MB of RAM, the maximum supported by early Macs.

• Compatible with Macintosh 128/512K using either Apple 128K ROM or ROM-INATOR, and the 512KE.

• Option to exclude the onboard memory bank using a DIP switch. (A must for Macintosh 128K).

• Solder jumpers to select among three memory size configurations (1MB, 2MB, or 4MB).

• Auxiliary board can be set to restore original configuration and disable the expansion board (DIP switch).

• No extensions or other software are required, and the Mac recognizes all the configured RAM at startup.


## INSTALLATION

Two options are available for installing these boards:

### •	Soldering piggyback sockets
  
This is the easiest method. Solder DIP sockets onto specific ICs (U5-11F, U5-11G, U12E, U13E, and U4F for the auxiliary board) on the logic board. Then, the boards connect through male pin headers to these sockets. *This task requires a certain degree of soldering expertise. Ensure that all pins from the DIP sockets are soldered securely and double-check the continuity between the base of the IC leg and the top of the pin socket.*

### • Relocating ICs to the expansion boards

Alternatively, you can use extra long pin header sockets like the ones used by the Mac’s-a-Million board by Sophisticated Circuits and relocate the mentioned ICs on the expansion board. 

### • Resistor Arrays RP2 & RP3

Additionally, resistor arrays RP2 and RP3 must be removed from the logic board, and 6 signals need to be collected through bodge cables.


## THE RAM REFRESH CONFIGURATOR

This versatile tiny board offers several handy features:

•	Intervene /CAS signals, handle RAM address bus and reconfigure the number of refresh cycles to give maximum compatability with FPM RAM ICs of 512 cycles. 

•	Disable the RAM expansion board trough a DIP switch, allowing to remove completely the expansion board and quickly restore the memory stock configuration.


### HANDLING OF THE ONBOARD MEMORY BANK

The onboard memory bank consists of 16 ICs of either 256Kbitx1bit (Macintosh 512K/KE) or 64Kbitx1bit (Macintosh 128K). 
The expansion board has a DIP switch that enables the option to include or exclude this memory bank withing the 4MB of RAM. 

On Mac 128K, the system memory bank must always be excluded. On Mac 512K/KE, it's optional. 


### STANDARD REFRESH CYCLES MODE

The standard refresh mode is the stock method used by the Mac 128/512/KE to generate DRAM refresh cycles.
Although the system memory ICs are 256 cycles/4ms, the ICs used in this RAM expansion board (AS4C1256KFO / 512 refresh cycles / 8ms), work perfectly!.

Somehow, these ICs are correctly refreshed within 8 ms in all their rows range, making them compatible with the system refresh circuitry. This refresh cycle mode has been working in the expansion board prototype installed on my Macintosh 512K without any kind of issues.
Using the default refresh mode requires fewer signals from the logic board, reducing the number wires needed to the board and some components no need to be populated in the auxiliary board. (U1, U2, and U3 can be omitted.)

For this mode, only 6 connections trough cables soldered to the LB are needed to J5 at the expansion board:

1.	/RAS - Left Leg of R42

2.	A19  - Pin #3 TSG  (D3)

3.	A20  - Pin #5 LS04 (D4)

4.	A17  - Pin #45 (CPU)

5.	A18 - Pin #46 (CPU) 

6.	A21 – Pin #50 (CPU)

Another 4 signals are collected directly by the auxiliary board and need to be wire from J3 to J5, which are from bottom to top on J3:

-	/CAS1

-	/CAS0

-	VID\u

-	C2M

**For this refresh mode, it is essential to verify that the MSRA8F signal is not connected from J3 on the auxiliary board to J5 on the expansion board. Failure to do so will result in a SAD MAC error during boot.**

Jumper settings for each refresh mode and other functionalities can be found at the end of this document. 

![LB_512K_scaled copy](https://github.com/user-attachments/assets/7516653b-66f9-4f18-a7ac-8dcdc91c0549)


### MACPLUS REFRESH CYCLES MODE

As the name suggests, this mode replicates how the Mac Plus generates RAM addresses for refresh cycles. In this mode, the RAM Configurator board generates address bits RA8 and RA0 as in the Mac Plus, subtituting it the default RA0 & RA8. A member of 68KMLA forums named *Golden Potato* was the one who figure out how to generate those bits. Thanks again Golden Potato!

Additionaly, a few more input signals picked up through cables soldered to specific points on the LB are needed for this mode, and all them this time go to J3 at the auxiliary board. 

 7.  A19 - Pin #7 (RP1 DIP resistor array, Later LB models) or same as connection point 2.
   
 8.  A20 - Pin #48 (CPU) or same as connection point 3.
 
 9.  A17 - Same as connection point 4.

10.  A18 - Same as connection point .5

11.  VA5 - PIN #13 - (U3G)
   
12.  VA13 - PIN #12 - (U3G)

13. /DMA - PIN #15 - (U2F)

**One of the legs of resistor R42 (LB) have to be opened and set the solder jumpers accordinly** *(See the table at end fo this document)*

**Finally, the signal MSRA8F present at J3 must be wired to J5, pin #1**.

**Failure to do any of the required connections mention above will result in a SAD MAC error during boot**

![LB_512K_scaled 2](https://github.com/user-attachments/assets/007c1723-e56c-4e4b-952f-53907c9661ce)


### 1204 REFRESH CYCLES MODE

This mode is for a memory expansion board with FP/EM DRAM ICs of higher density, and at this time is still under development.


## SOLDER JUMPER SETTINGS FOR MACINTOSH 512K / KE - Boards version 2

### STANDARD REFRESH MODE

| JUMPER          | 1MB    | 2MB      | 4MB         | 
|:---------------:|:------:|:--------:|:-----------:|
| JP1 / EXP.B V2  | 1-2    | 2-3      | 2-3         |
| JP2 / EXP.B V2  | 1-2    | 1-2      | 2-3         |
| JP3 / EXP.B V2  | 1-2    | 1-2      | 1-2         |
| JP4 / EXP.B V2  | 2-3    | 2-3      | 2-3         |
| JP5 / EXP.B V2  | 1-2    | 1-2      | 1-2         |
| JP1 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP2 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP3 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP4 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP5 / AUX.B V2  | 1-2    | 1-2      | 1-2         |

### MAC PLUS REFRESH MODE

| JUMPER          | 1MB    | 2MB      | 4MB         | 
|:---------------:|:------:|:--------:|:-----------:|
| JP1 / EXP.B V2  | 1-2    | 2-3      | 2-3         |
| JP2 / EXP.B V2  | 1-2    | 1-2      | 2-3         |
| JP3 / EXP.B V2  | 1-2    | 1-2      | 1-2         |
| JP4 / EXP.B V2  | 2-3    | 2-3      | 2-3         |
| JP5 / EXP.B V2  | 1-2-3  | 1-2-3    | 1-2-3       |
| JP1 / AUX.B V2  | 2-3    | 2-3      | 2-3         |
| JP2 / AUX.B V2  | 2-3    | 2-3      | 2-3         |
| JP3 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP4 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP5 / AUX.B V2  | 1-2    | 1-2      | 1-2         |

### 1024 REFRESH CYCLES MODE

| JUMPER          | 1MB    | 2MB      | 4MB         | 
|:---------------:|:------:|:--------:|:-----------:|
| JP1 / EXP.B V2  | 1-2    | 2-3      | 2-3         |
| JP2 / EXP.B V2  | 1-2    | 1-2      | 2-3         |
| JP3 / EXP.B V2  | 1-2    | 1-2      | 1-2         |
| JP4 / EXP.B V2  | 2-3    | 2-3      | 2-3         |
| JP5 / EXP.B V2  | 1-2-3  | 1-2-3    | 1-2-3       |
| JP1 / AUX.B V2  | 2-3    | 2-3      | 2-3         |
| JP2 / AUX.B V2  | 2-3    | 2-3      | 2-3         |
| JP3 / AUX.B V2  | 2-3    | 2-3      | 2-3         |
| JP4 / AUX.B V2  | 1-2    | 1-2      | 1-2         |
| JP5 / AUX.B V2  | 1-2    | 1-2      | 1-2         |

### EXPANSION BOARD DISABLED  & STOCK MEMORY CONFIGURATION RESTORED

| JUMPER          |        | 
|:---------------:|:------:|
| JP5 / AUX.B V2  | 2-3    |
| JP5 / AUX.B V2  | 2-3    |

** REMOVE THE EXPANSION BOARD BEFORE TURN ON **


