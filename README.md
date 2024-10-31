# OpenEarlyMacsRAMexpansion


 ## SUMMARY

Back in the day, RAM upgrades were available for the so called Early Macs (Macintosh 128K / 512K and 512Ke). However, finding these boards in working condition has become increasingly difficult. The *Mac Rescue* board, one of the few offering a full 4MB of RAM, is nearly impossible to obtain.

This newly designed expansion board, paired with an auxiliary **RAM Refresh Configurator board**, provides an affordable solution to increase memory up to 4MB.

The expansion board has been tested on a Macintosh 512K with Mac Plus/512Ke ROMs, and also with the *ROM-INATOR* board installed concurrently.

*Warning: Testing on a Mac 128K is still pending*  

*Attention: The ROM-INATOR detects the machine model by checking the available RAM size. Therefore, the ROM image needs to be patched before installing this board or any other RAM upgrade on early Macs*


## KEY FEATURES

• Configurable to add up to 4MB of RAM, the maximum supported by early Macs.

• Compatible with Macintosh 128/512K using either Apple 128K ROM or ROM-INATOR, and the 512KE.

• Option to use a DIP switch to swap the onboard memory with a memory bank from the expansion board (necessary for Macintosh 128K).

• Solder jumpers to select among three memory size configurations (1MB, 2MB, or 4MB).

• Auxiliary board can be set via a DIP switch to disable the expansion board, restoring the original configuration.

• No extensions or other software are required, and the Mac recognizes all the configured RAM at startup.

## WHAT YOU NEED

• LB schematics 

• 

• 

• 

• 

• 

## INSTALLATION

### Resistor R42 (LB)

Let's start the installation by opening one leg of resistor R42.
Then, solder one end of a bodged cable, at least 5 cm long, to the via where the left leg was connected. You need to do this as a first step because the expansion boards will later be on top of this connection point, making it much harder to make the connection.

*Please note this will only apply to LB revisions that have an R42 resistor and IC U13F populated. Early LB revisions from Macintosh 128K will not have these components.*


### Resistor Arrays RP2 & RP3 (LB)

In order to install the auxiliary board, resistor arrays RP2 and RP3 must be removed from the logic board (LB) and solder in their places socket pin headers. The auxiliary board will connect to these sockets via  J6 & J7 which are male to male pin headers (machined round type)

## Boards Install

### Option A: Soldering piggyback sockets
  
This is the easiest method. Solder DIP sockets onto ICs U11F, U11G, U12E, U13E, and U4F. Then, the boards connect to these sockets via male pin headers.

*Attention: This task requires basic soldering skills. Ensure that all pins from the DIP sockets are securely soldered and double-check the continuity between the IC leg base and the top of the pin socket.*

### Obtion B: Relocating ICs to the expansion boards

Alternatively, you can relocate the mentioned ICs to the expansion and auxiliary boards by soldering IC sockets in their places on the main board (LB) and using extra-long pin header sockets (like those used by the Mac’s-a-Million board by Sophisticated Circuits) for the expansion boards.



### Inputs signals trough wires

The following table shows the signals that are collected via bodged cables from the LB to the expansion board (J5):

*Please note that pin 1 of connector J5 is located at the top.*

| SIGNAL                | Location    | Pin N° on J5 | Comment         |
|:---------------------:|:-----------:|:------------:|:---------------:|
| /RAS |Left Leg of R4  |7            |              |                 |
| A19  |Pin N°3 - U3D   |2            |              |                 |
| A20  |Pin N°5 - U4D   |3            |              |                 |
| A21  |Pin N°50 - CPU  |4            |              |                 |

The following table shows the signals that are collected via bodged cables from the LB to the auxiliary board (J2):

*Please note that pin 1 of connector J5 is located at the top.*

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

The following table shows signals that are collected directly by the auxiliary board and need to be wired from J3 to J5:

*Please note that pin 1 of connector J3 is located at the bottom, whereas pin 1 of connector J5 is located at the top.*

| SIGNAL         | Pin N° on J3 Aux. B | Pin N° on J5 Exp.B  | Comment         | 
|:---------------:|:------:|:--------:|:-----------:|
| /MCAS0          |1       |9         |             |
| /MCAS1          |2       |8         |             |
| VID /u          |3       |7         |             |
| MC2M            |4       |6         |             |
| /MSRA8F         |5       |1         |             |
| /MSRA9F         |6       |NC        | Leave unconnected | 


Mac Plus Refresh Cycles Mode

This is the recommended default mode to be used with this version of the expansion board. In this configuration, the RAM configurator board mimics the Mac Plus's RAM address generation process to obtain 512 refresh cycles. It replicates the generation of RAM address bits RA8 and RA0, substituting the system's RA0 and RA8. This method was devised by Golden Potato, a member of the 68KMLA forums. Thank you, Golden Potato!

System Refresh Cycles Mode

Early Mac RAM ICs require just 256 refresh cycles every 4 milliseconds. The LB's circuitry generates these 256 RAM addresses sequentially every 4 milliseconds, refreshing the "rows" using the /RAS method (/RAS before /CAS).

Interestingly, I've discovered that at least the RAM ICs I've used on my expansion board function flawlessly without modifying the RAM address bus generation circuitry, even though their specifications indicate a requirement for 512 refresh cycles. This mode has been stable on my Mac 512K for several months.

While I haven't determined the exact reason for this unexpected behavior, I cannot confidently recommend it as the default choice. However, if you're aiming to minimize component and wire usage on the LB, and you're using the same RAM ICs I recommend, you can experiment with this mode with reasonable assurance.

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
