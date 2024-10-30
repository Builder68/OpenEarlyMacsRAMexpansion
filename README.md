# OpenEarlyMacsRAMexpansion

 ## SUMMARY

Back in the day, RAM upgrades were available for Early Macs. However, finding these boards in working condition has become increasingly challenging. The *Mac Rescue board*, one of the very few that provides full 4MB of RAM, is almost unobtaniable.

This newly designed expansion board, paired with an auxiliary board I called **RAM Refresh Configurator**, provides a affordable solution to increase memory up to 4MB.

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
| /RAS |Left Leg of R4  |7            |              |                 |
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

### Opening trace at R42

One of the legs of resistor R42 (LB) have to be opened

### MACPLUS REFRESH CYCLES MODE

This is the deafult refresh cycle mode I recommend to set.

In this mode, the RAM configurator board replicates how the Mac Plus generates RAM addresses for refresh cycles. RAM address bits RA8 and RA0 are generated as in the Mac Plus, subtituting it the system RA0 & RA8. A member of 68KMLA forums named *Golden Potato* was the one who figure out how to generate those RAM address bits. Thanks again Golden Potato!

### SYSTEM REFRESH CYCLES MODE

The RAM ICs used by the early Macs need 256 refresh cycles withing every 4 ms. The sub-circuitry on the LB generates 256 RAM addresses secuentyally every 4 ms to refresh the "rows" using the /RAS method (/RAS before /CAS).

Just by pure accident, I figure out that at least the RAM ICs I used on the expansion board work flawesly without the need to modify the RAM address bus generation sub-circuitry, although the specification of those ICs clearly states that it needs 512 refresh cyles. This mode have been working now for months on my Mac 512K with no issues. 

Havin not found yet a clear explanation of why it works, I can´t recommend it as the default choice. But!.... if you wan´t to use less components and less wires to the LB, the   

### 1204 REFRESH CYCLES MODE

This mode is for a memory expansion board with FP/EM DRAM ICs of higher density (10 address bits), and at this time is still under development.

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
