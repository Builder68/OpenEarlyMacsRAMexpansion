# Open Early Macs RAM Expansion
#
 ## SUMMARY

This upgrade utilizes 2MB x 16-bit RAM ICs with 1024 refresh cycles, providing up to 4MB of RAM for Macintosh 128K and 512K equipped with the 128KB ROM. 
Testing has confirmed compatibility with a Macintosh 512Ke, including concurrent use with the ROM-INATOR board. Furthermore, installing this memory expansion alongside a SCSI card (like the MacSnap SCSI) enables the 128KB ROM to identify the machine as a Mac Plus.

*Attention: Due to the way the ROM-INATOR board determines the Mac model it's installed on (Mac Plus or Mac 512Ke), its ROM image needs to be [patched](https://68kmla.org/bb/index.php?threads/early-macintosh-home-brew-4mb-memory-upgrade-board-development.47308/post-544271) before installing this RAM expansion board or any other RAM upgrade.*


## PROJECT STATUS

This project is fully functional on a Mac 512Ke. Although it's expected to work on Mac 128K or 512K systems with the 128KB ROM, this specific compatibility hasn't been tested yet.

## KEY FEATURES

* One single detachable RAM board, which taps several signals through bodge wires with JST connectors and either piggyback sockets or pin headers soldered to components on the LB.
* You can disable RAM expansion through DIP switches on the board.
* A solder jumper allows you to select between two memory size configurations: 2MB or 4MB.
* Compatible with FPM or EDO CMOS RAM ICs of 2MB x 16 bits.
* The PCB dimensions are designed to allow concurrent installation with [Demik's MacSnap SCSI replica board](https://github.com/demik/MacSnap-SCSI//) and a future Accelerator Board (still under development) based on [Bolle's Micromac Performer board clone](https://github.com/TheRealBolle/Performer-SE-PL-CL).
* No extensions or additional software are needed; Mac will automatically recognize all the configured RAM upon startup.
## ASSEMBLY

While the assembly process is straightforward, it can be challenging. Reflow soldering, or using solder paste and a heat gun, is highly recommended for the RAM chips and most SMD components. 

Although this might sound highly obvious, I must say it:

Please be sure to get the right schematics for your LB revision.

## SPECIAL THANKS

This project wouldn't be where it is today without the significant contributions of Golden Potato. His collaboration on developing and testing this design was instrumental. From the beginning, his desire was that this design should be free and open source with both of our names attached to it. 
#
#

### 1. RAM EXPANSION BOARD 
Front

![Screenshot 2025-04-09 at 10 08 55 AM](https://github.com/user-attachments/assets/de959ade-b2c9-4ae8-911b-d56883ff1fd2)



Back

![Screenshot 2025-04-09 at 9 39 32 AM](https://github.com/user-attachments/assets/46a13f87-a933-4e78-9750-3d6b5d64c997)


## 2. BOM


![Screenshot 2025-04-25 at 2 33 11 PM](https://github.com/user-attachments/assets/821c0caf-546c-44f0-92c2-87965683e375)


#
## 3. BEFORE INSTALLING 

### 3.1 Socket machine headers at RP2 & RP3 

Prior to installing the expansion board, resistor arrays RP2 and RP3 must be removed from the LB and replaced with socket pin machine headers.
#
## 4. INSTALLATION

### 4.1 Pin headers
  
Solder machine pin headers (male to male) onto ICs U11F, U11G, and U4F. Then, the board connects to these pin headers via sockets soldered on the backside of the expansion board.

Optionally, you can instead solder DIP sockets onto U11F, U11G, and U4F (piggybacked) and solder male-to-male pin headers to the expansion board.

## 5. Signals to JST connectors

The following tables shows the signals that are collected via bodged wires from the LB to the JST connectors J11 and J12:


### 5.1 J11

| SIGNAL          | Location       | Pin N° | Comment         |
|:---------------:|:--------------:|:------------:|:---------------:|
| /SNDPG2         |Pin N°5 - U2F   |1             |                 |
| /DMA            |Pin N°15 - U2F  |2             |                 |
| VA6             |Pin N°6 - U2F   |3             |                 |
| VA13            |Pin N°12 - U3G  |4             |                 |
| A18             |Pin N°46 - CPU  |5             |                 |
| VA5             |Pin N°13 - U3G  |6             |                 |

### 5.2 J12

| SIGNAL                | Location on LB   | Pin N° | Comment         |
|:---------------------:|:----------------:|:------------:|:---------------:|
| A17                   |Pin N°45 - CPU    |1             |                 |
| A20                   |Pin N°5 - U4D     |2             |                 |
| A19                   |Pin N°3 - U3D     |3             |                 |
| A21                   |Pin N°50 - CPU    |4             |                 |
| /RAS                  |Left Leg of R4 or Pin N°14 - 4D   |5             |                 | 
| R/WF                  |Right Leg of R33  |6             |                 |
#

![LB Signals to Expansion Card (JST Connectors)](https://github.com/user-attachments/assets/03796169-dac9-41c8-b6f6-86eaa0c76446)


## 6. Settings

### 6.1 RAM Expansion Board

#### 6.1.1 IC RAM Type (FPM / EDO)

Solder jumpers JP1 & JP2 selects between FPM or EDO RAM IC types

#### 6.1.2 RAM Size

|JP3              |RAM Size           |
|:---------------:|:-----------------:|
| 2-3             | 2MB               |
| 1-2.            | 4MB.              |


#### 6.1.3 RAM Expansion Enabling (SWB1 & SWB2)

SWB1
|S n°|Expansion RAM Enabled  |  Expansion RAM Disabled |
|:--:|:------------------:|:-------------------:|
| 1  | ON                 |               OFF   |
| 2  | OFF                |               ON    |
| 3  | ON                 |               OFF   |
| 4  | OFF                |               ON    |
| 5  | ON                 |               OFF   |
| 6  | OFF                |               ON    |

SWB2
|S n°|Expansion RAM Enabled  |  Expansion RAM Disabled |
|:--:|:------------------:|:-------------------:|
| 1  | ON                 |               OFF   |
| 2  | OFF                |               ON    |
| 3  | ON                 |               OFF   |
| 4  | OFF                |               ON    |
| 5  | ON                 |               OFF   |
| 6  | ON                 |               OFF   |
| 7  | OFF                |               ON    |
| 8  | OFF                |               ON    |

*Attention: double check all connections and DIP switch settings before power-up*

Good luck. Let us know how it goes here: https://68kmla.org/bb/index.php?threads/early-macintosh-home-brew-4mb-memory-upgrade-board-development.47308/
