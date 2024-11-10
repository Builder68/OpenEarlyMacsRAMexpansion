# OpenEarlyMacsRAMexpansion



 ## SUMMARY

Back in the day, RAM upgrades were available for the so called Early Macs (Macintosh 128K / 512K and 512Ke). Today, finding one of these boards in working condition has become challeging. The *Mac Rescue* board, one of the few offering a full 4MB of RAM, is nearly impossible to obtain.

This newly designed expansion board, paired with an auxiliary **RAM Refresh Configurator board**, provides an affordable solution to increase memory up to 4MB.

The expansion board has been tested on a Macintosh 512K with Mac Plus/512Ke ROMs, and also with the *ROM-INATOR* board installed concurrently.

*Warning: Testing on a Mac 128K with earlier LB revision is still pending*  

*Attention: For use concurrently with the ROM-INATOR, its ROM image needs to be patched before installing this board or any other RAM upgrade*

##
## KEY FEATURES

• Configurable to add up to 4MB of RAM.

• Compatible with Macintosh 128/512K using either Apple 128K ROM or ROM-INATOR, and the 512KE.

• DIP switch to swap the onboard memory with a memory bank from the expansion board (necessary for Macintosh 128K).

• Solder jumpers to select among three memory size configurations (1MB, 2MB, or 4MB).

• Auxiliary board can be set to disable the expansion board, restoring the original configuration.

• No extensions or other software are required, and the Mac recognizes all the configured RAM at startup.

##
## CONSTRUCTION
###
### 1. RAM EXPANSION BOARD (REV 2.0)

• Latest Schematics

• Latest Gerber files
### 1.1 Components
#### 1.1.1     Resistors
| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|2.2K ohm 0805 Resistor |8            |              |                 | 
|47 ohm 0805 Resistor   |16           |              |                 |
|1K ohm 0805 Resistor   |2            |              |                 |
#### 
#### 1.1.2 Capacitors

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|10uF Tantalum Capacitor|1            |  [293D106X9010C2TE3](https://www.mouser.com/ProductDetail/74-293D106X9010C2TE3)|   |
|100nF 0805 Multilayer Ceramic Capacitor |29           |              |                 |
####
#### 1.1.3 Semiconductors

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|5V 256K x 16 CMOS DRAM (fast page mode)   |8            |[AS4C256K16F0-60JC](https://www.utsource.net/pro/AS4C256K16F0-60JC.html?srsltid=AfmBOort4nx-luAnQ9rYHgn0u1JrMKh2p2SnMiqUe_HYeLMkHxX2aOso)                                                   |   |
|5V 8-bit buffer/line driver, 3-states     |2            |[74HCT244](https://www.mouser.com/ProductDetail/771-74HCT244D-T)|     |
|5V 3 to 8 line decoder demultiplexer      |2            |[74AHCT138](https://www.mouser.com/ProductDetail/771-AHCT138D118)|  | 
|5V dual 4-bit multiplexer                 |2            |[74HCT253](https://www.mouser.com/ProductDetail/771-HCT253D653) |     | 
|5V quad 2-input NAND gate                 |1            |[74HCT32](https://www.mouser.com/ProductDetail/771-74HCT32D-T) |     | 
####
#### 1.1.4 Sockets & Pinheaders
#####
##### Option N°1: Pin Headers & PiggyBack Sockets Install (Removable)

*Attention: Clearance between LB and EB will be approx. 12.7 mm, allowing for the LB to slide back on the metallic rails of the case with no interference. No Through-Hole Mount components are installed on the EB for this option.*

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
| DIP-20 IC Chip Socket 2.54mm Pitch 7.6mm Flat Pins |2            |[DIP-20_FP](https://www.amazon.com/uxcell-2-54mm-Soldering-Socket-Adaptor/dp/B07H3RPFH8/ref=sr_1_3?crid=2AAD93YCWMVIH&dib=eyJ2IjoiMSJ9.6rmeeWM4h6g26z0fF63UVOQBFD-LY572b8sE6Kwfb46kzqcsdJvKzEFnzfhSIdAwsuqcWDpDLJj2Oti_vD6p8fpeCsuMI993gmlABOKltN3lKmSxixw9XLjJH7muzdcxx5D0xDImA1dHnck_T9dc8W93a5LaqLHKh_ePhn_39s1udbXTR77i_F_zIucm3cKNmHkN4nzuJcKCB4kohj35bIPE2ApCTL3GoYCQTWGhc.kuVyk9TBJDEDQ9C8tdMgAusFZUh16W4Kn76WCFhgiQ4&dib_tag=se&keywords=dip+sockets+2.54+mm+20&qid=1731069402&sprefix=dip+sockets+2.54+mm+20%2Caps%2C218&sr=8-3)              |Flat Pins Soldering| 
| DIP-16 IC Chip Socket 2.54mm Pitch 7.6mm Flat Pins |2            |[DIP-16_FP](https://www.amazon.com/Uxcell-a11090300ux0244-2-54mm-Socket-Adaptors/dp/B0079SM1LW/ref=sr_1_3?crid=3M210B1RLHYSC&dib=eyJ2IjoiMSJ9.yineh7dbus9HEsJfsGH3_ClMOLEVwf48Z8De29l_YNoGtqEnB3tJyRem-zre07ujnL2TVvvco8eNgvti2jm33CcLyhH6U8PqRWmaaaLEjJr2N3zYNPC2qB9pAX1UW_nH8ozCvKjCdbLYAzu-9tqIig_TJYqLxoH7n4VqFM2st4Kt-TMeYwoZHiOQBwCx7e21wEb46F8zvW9XvW_nHaPshvztxEOVDYZ9SdTvv7pO12s.dVQZb8SDUPE-DL8tchl75I0Dl3JAkO5fDYRe4af360w&dib_tag=se&keywords=dip+sockets+2.54+mm+16&qid=1731069778&sprefix=dip+sockets+2.54+mm+16%2Caps%2C297&sr=8-3)              |Flat Pins Soldering| 
| 1x40 2.54mm Pin Male Pin Header STD            |2            |             | need 72 pins  |
| 1x40 Right Angle 2.54mm Male Pin Header STD    |1            |             | need 9 pins  |

##### Option N°2: Connectors & Sockets Install (ICs U12E, U13E, U11F, and U11G are relocated to the Expansion Board)

*Attention: There will be a 9.5mm gap between the Logic Board and the Expansion Board, leaving enough space for the Through-Hole Mount ICs relocated on socket connectors to not interfere when it's slid back on the metallic rails*

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
| 1x64P Elevated Socket Conn 2.54mm            |2            | [316-93-164-41-007000](https://www.digikey.com/en/products/detail/mill-max-manufacturing-corp/316-93-164-41-007000/357031?s=N4IgTCBcDaIMwEYBsBaAnHFyAsLsJQAZCB2YwkAXQF8g)| Standoff Height = 10.2 mm / need 72 pins soldered to EB|
|2.54mm 40x1 Female Pin Header Strip, Machine Round Pins|2            |             |Need 72 pins, soldered to LB|

#### 1.1.5 Spacer

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
| Brd Spt Snap Lock Nylon 1/2"   |1            |[36-8892-ND](https://www.digikey.com/en/products/detail/keystone-electronics/8892/2746017)| Length for Piggyback Install 12.7 mm  |
| Brd Spt Snap Lock Nylon 1/2"   |1            |[36-8891-ND](https://www.digikey.com/en/products/detail/keystone-electronics/8891/2746016)| Length for Connectors & Sockets Install 9.5 mm  |

#### 1.1.6 DIP Switch

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
| SMD Slide DIP Switch 8P   |1            |[653-A6H-8101](https://www.mouser.com/ProductDetail/Omron-Electronics/A6H-8101?qs=Rh%252BaoYk36r6BMZDoR1skvA%3D%3D)|   |

#### 1.1.7 Diodes

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
| Zener Diode ZNR SOD123 500MW   |2            |[863-SZMMSZ5V1T1G](https://www.mouser.com/ProductDetail/onsemi/SZMMSZ5V1T1G?qs=k%252Be6uhf5HI1HqLTFyqTq7w%3D%3D)|   |


### 2. RAM REFRESH CONFIGURATOR BOARD (REV 2.0)

• Latest Schematics

• Latest Gerber files
### 2.1 Components
#### 2.1.1 Resistors

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|2.2K ohm 0805 Resistor |3            |              |                 | 
|47 ohm 0805 Resistor   |12           |              |                 |

 
#### 2.1.2 Capacitors

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|100nF 0805 Multilayer Ceramic Capacitor |3           |              |                 |

#### 2.1.3 Semiconductors

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|5V dual 4-bit multiplexer|2            |[74HCT253](https://www.mouser.com/ProductDetail/771-HCT253D653) |     | 
|5V Quad 2-input multiplexer|1            |[74HCT257](https://www.mouser.com/ProductDetail/771-HCT257D653) |     | 

#### 2.1.4 Sockets & Pinheaders

##### Option N°1: Pin Headers & PiggyBack Sockets Install (Removable)

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
| DIP-16 IC Chip Socket 2.54mm Pitch 7.6mm Flat Pins |1            |[DIP-16_FP](https://www.amazon.com/Uxcell-a11090300ux0244-2-54mm-Socket-Adaptors/dp/B0079SM1LW/ref=sr_1_3?crid=3M210B1RLHYSC&dib=eyJ2IjoiMSJ9.yineh7dbus9HEsJfsGH3_ClMOLEVwf48Z8De29l_YNoGtqEnB3tJyRem-zre07ujnL2TVvvco8eNgvti2jm33CcLyhH6U8PqRWmaaaLEjJr2N3zYNPC2qB9pAX1UW_nH8ozCvKjCdbLYAzu-9tqIig_TJYqLxoH7n4VqFM2st4Kt-TMeYwoZHiOQBwCx7e21wEb46F8zvW9XvW_nHaPshvztxEOVDYZ9SdTvv7pO12s.dVQZb8SDUPE-DL8tchl75I0Dl3JAkO5fDYRe4af360w&dib_tag=se&keywords=dip+sockets+2.54+mm+16&qid=1731069778&sprefix=dip+sockets+2.54+mm+16%2Caps%2C297&sr=8-3) |Flat Pins Soldering| 
|Conn Socket 64P        |2            | Need 20 pins|
|2.54mm 40x1 male to male header Strip, Machine Round Pins STD height |1            | |Need 20 pins|
|2.54mm 40x1 female to male header Strip, Machine Round Pins STD |1            | |Need 40 pins: two sets of two rows of 1x10P pile-up|
|1x40 Right Angle 2.54mm Male Pin Header STD    |1            |             | need 16 pins  |

##### Option N°2: Connectors & Sockets Install (Relocate U12E, U13E, U11F, and U11G to the Expansion Board)

| Part description      | Quantity    | Supplier     | Notes           |
|:---------------------:|:-----------:|:------------:|:---------------:|
|1x64P Elevated Socket Conn 2.54mm         |2            | [316-93-164-41-007000](https://www.digikey.com/en/products/detail/mill-max-manufacturing-corp/316-93-164-41-007000/357031?s=N4IgTCBcDaIMwEYBsBaAnHFyAsLsJQAZCB2YwkAXQF8g)| need 72 pins             |


## 3. BEFORE INSTALLING

### 3.1 Resistor R42

Let's start the installation by opening  a leg of resistor R42 (U13G side).
Then, solder one end of a bodged cable of at least 5 cm long, to the pad where the left leg was connected. You need to do this as a first step because the EB will later be on top of this connection point.

*Please note this will only apply to LB revisions that actually have an R42 resistor and IC U13F populated. Early LB revisions from Macintosh 128K will not have these components.*


### 3.2 Resistor Arrays RP2 & RP3 

Prior to install the auxiliary board, resistor arrays RP2 and RP3 must be removed from the LB and solder in their places socket pin headers. 

## 4 INSTALLING BOARDS

### 4.1 Option A: Soldering piggyback sockets
  
This is the easiest method. Solder DIP sockets (flat pins soldering) onto ICs U11F, U11G, U12E, U13E, and U4F. Then, the boards connect to these sockets via std male pin headers.

*Attention: This task requires good soldering skills. Ensure that all pins from the DIP sockets are securely soldered and double-check the continuity between the LB pad and the top of the pin socket.*

### Obtion B: 4.2 Relocating ICs to the expansion boards

Alternatively, you can relocate the mentioned ICs to the expansion and auxiliary boards by soldering IC sockets in their places on the main board (LB) and using extra-long pin machine header sockets for the expansion boards.

### 5 INPUTS VIA WIRES

The following table shows the signals that are collected via bodged cables from the LB to the EB (J5):

*Please note that pin 1 of connector J3 is located at the top.*

| SIGNAL                | Location on LB   | Pin N° on J5 | Comment         |
|:---------------------:|:-----------:|:------------:|:---------------:|

| /RAS |Left Leg of R4  |7            |              |                 |
| A19  |Pin N°3 - U3D   |2            |              |                 |
| A20  |Pin N°5 - U4D   |3            |              |                 |
| A21  |Pin N°50 - CPU  |4            |              |                 |

The following table shows the signals that are collected via bodged cables from the LB to the auxiliary board (J3):

*Please note that pin 1 of connector J3 is located at the top.*

| SIGNAL          | Location       | Pin N° on J3 | Comment         |
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
| RA8             |Left Pad R42    |9             |R42 must be open |

The following table shows signals that are collected directly by the auxiliary board and need to be wired from J2 to J5:

*Please note that pin 1 of connector J2 is located at the bottom, whereas pin 1 of connector J5 is located at the top.*

| SIGNAL         | Pin N° on J2 Aux. B | Pin N° on J5 Exp.B  | Comment         | 
|:---------------:|:------:|:--------:|:-----------:|
| /MCAS0          |1       |9         |             |
| /MCAS1          |2       |8         |             |
| VID /u          |3       |7         |             |
| MC2M            |4       |6         |             |
| /MSRA8F         |5       |1         |             |
| /MSRA9F         |6       |NC        | Leave unconnected / Not used| 

## 6 JUMPER $ SWITCH SETTINGS

### Mac model

### RAM Size

### Refresh Mode

### System RAM Bank

### Restore Memory System

Mac Plus Refresh Cycles Mode

This is the recommended default mode to be used with this version of the expansion board. In this configuration, the RAM configurator board mimics the Mac Plus's RAM address generation process to obtain 512 refresh cycles. It replicates the generation of RAM address bits RA8 and RA0, substituting the system's RA0 and RA8. This method was devised by Golden Potato, a member of the 68KMLA forums. Thank you, Golden Potato!

System Refresh Cycles Mode

Early Mac RAM ICs require just 256 refresh cycles every 4 milliseconds. The LB's circuitry should then only generates these 256 RAM addresses sequentially every 4 milliseconds, refreshing the "rows" using the /RAS method (/RAS before /CAS).

Interestingly, I’ve discovered that at least the RAM ICs I’ve used on my expansion board function flawlessly without modifying the RAM address bus generation circuitry, even though their specifications indicate a requirement for 512 refresh cycles. I haven’t yet figured out if this is due to the LB actually generating 512 refresh cycles from the point of view of the IC, or if the IC only needs address variations between RA0-RA7 for RAM refresh. Anyway, this mode has been stable on my Mac 512K for several months.

While I haven't determined the exact reason for this unexpected behavior, I cannot confidently recommend it as the default choice for any other scenario where the LB, the ROM image, and the RAM IC model is the same as mines. However, if you're aiming to minimize wiring from the LB, and you're using the same RAM ICs I recommend, you can implement this mode with reasonable assurance.

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
