# OpenEarlyMacsRAMexpansion

 ## SUMMARY

Back in the day, RAM upgrades were available for Early Macs. However, finding these boards in working condition has become increasingly challenging. The *Mac Rescue board*, one of the very few that provides full 4MB of RAM, is almost unobtaniable.

This newly designed expansion board, paired with an auxiliary board I called **RAM Refresh Configurator**, provides a affordable solution to increase memory up to 4MB.

![Screenshot 2024-10-22 at 3 00 07 PM](https://github.com/user-attachments/assets/0927eb3d-6c0c-4479-a216-cbbe3e41b88d)
![Screenshot 2024-10-22 at 6 50 35 PM](https://github.com/user-attachments/assets/46a6b025-a1a6-4c5b-a361-0ad218c6825e)

The expansion board has been tested only on a Macintosh 512K with MacPlus / 512Ke ROMs, and also with the *ROM-INATOR board* is installed concurrently.

*Warning: testing on a Mac 128K still pending*  

*Attention: The ROM-INATOR detects the machine model by checking the RAM size available, so the ROM image need to be patched before installing this board or any other RAM upgrade on the early macs*

## KEY FEATURES

• Configurable to add up to 4MB of RAM, the maximum supported by early Macs.

• Compatible with Macintosh 128/512K using either Apple 128K ROM or ROM-INATOR, and the 512KE.

• Option to exclude the onboard memory bank using a DIP switch. (Mandatory for Macintosh 128K).

• Solder jumpers to select among three memory size configurations (1MB, 2MB, or 4MB).

• Auxiliary board can be set trough a DIP switch to disable the expansion board, restoring original configuration.

• No extensions or other software are required, and the Mac recognizes all the configured RAM at startup.


## INSTALLATION

### •	Option A: Soldering piggyback sockets
  
This is the easiest method. Solder DIP sockets onto the ICs U11F, U11G, U12E, U13E, and U4F. Then, the boards connect through male pin headers to these sockets.

*Attention: This task requires a certain degree of soldering expertise. Please ensure that all pins from the DIP sockets are soldered securely and double-check the continuity between the base of the IC leg and the top of the pin socket.*

### • Obtion B: Relocating ICs to the expansion boards

Alternatively, you can use extra long pin header sockets like the ones used by the *Mac’s-a-Million board by Sophisticated Circuits* and relocate the mentioned ICs on the expansion and auxiliary boards. 

### • Resistor Arrays RP2 & RP3

Resistor arrays RP2 and RP3 must be removed from the LB, and solder socket pin headers on the LB (round-machined type).

### Inputs signals trough wires

The following signals are collected trough bodge cables from the LB to the expansion board (J5):

*Attention: pin N°1 of J5 is at the top*

| SIGNAL                | Location    | Pin N° on J5 | Comment         |
|:---------------------:|:-----------:|:------------:|:---------------:|
| /RAS |Left Leg of R42 |7            |              |                 |
| A19  |Pin N°3 - U3D   |2            |              |                 |
| A20  |Pin N°5 - U4D   |3            |              |                 |
| A21  |Pin N°50 - CPU  |4            |              |                 |

The following signals are collected trough bodge cables from the LB to the auxiliary board (J2):

*Attention: pin N°1 of J2 is at the top*

| SIGNAL          | Location       | Pin N° on J2 | Comment         |
|:---------------:|:--------------:|:------------:|:---------------:|
| /SNDPG2         |Pin N°5 - U2F   |1             |                 |
| /DMA            |Pin N°15 - U2F  |2             |                 |
| VA6             |Pin N°6 - U2F   |3             |                 |
| VA13            |Pin N°12 - U3G  |4             |                 |
| A18             |Pin N°46 - CPU  |5             |                 |
| VA5             |Pin N°13 - U3G  |6             |                 |
| A17             |Pin N°45 - CPU  |7             |                 |
| A20             |Pin N°5 - U4D   |8             |                 |
| A19             |Pin N°3 - U3D   |9             |                 |

The following signals are collected directly by the auxiliary board and need to be wired from J3 to J5:

*Attention: pin N°1 of J3 is at the bottom, pin N°1 of J5 is at the top*.

| SIGNAL         | Pin N° on J3 Aux. B | Pin N° on J5 Exp.B  | Comment         | 
|:---------------:|:------:|:--------:|:-----------:|
| /MCAS0          |1       |9         |             |
| /MCAS1          |2       |8         |             |
| VID /u          |3       |7         |             |
| MC2M            |4       |6         |             |
| /MSRA8F         |5       |1         |             |
| /MSRA9F         |6       |NC        | Leave unconnected | 

  
Jumper settings for each refresh mode and other functionalities can be found at the end of this document. 

![LB_512K_scaled copy](https://github.com/user-attachments/assets/7516653b-66f9-4f18-a7ac-8dcdc91c0549)

Somehow, these ICs are correctly refreshed within 8 ms in all their rows range, making them compatible with the system refresh circuitry. This refresh cycle mode has been working in the expansion board prototype installed on my Macintosh 512K without any kind of issues.

The standard refresh mode is the stock method used by the Mac 128/512/KE to generate DRAM refresh cycles.
Although the system memory ICs are 256 cycles/4ms, the ICs used in this RAM expansion board (AS4C1256KFO / 512 refresh cycles / 8ms), work perfectly!.

, reducing the number wires needed to the board and some components no need to be populated in the auxiliary board. (U1, U2, and U3 can be omitted.)

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
*Attention: double check all connetions and DIP switch settings before power-up*
