# OpenEarlyMacsRAMexpansion

 ## SUMMARY

Unlike the Macintosh Plus, which offers a simple SIMM-based memory upgrade, expanding the memory of these early Macs is significantly more complex and requires additional components.
Back in the day, RAM expansion boards were available to increase the memory of early Macs. However, finding these boards in working condition has become increasingly challenging and expensive. The *Mac Rescue board*, with an expansion RAM of 4MB, is particularly rare.
This newly designed expansion board, paired with an auxiliary board I called **RAM Refresh Configurator**, provides a flexible and customizable solution to increase memory up to 4MB. The circuitry is largely based on the *Macsnap 548E board from DOVE computer corp.* With a few modifications and enhancements, 4MB RAM is easily achievable using newer, higher-density FP DRAM ICs of 256Kb x 16 bits (512KB per IC).

![Screenshot 2024-10-22 at 3 00 07 PM](https://github.com/user-attachments/assets/0927eb3d-6c0c-4479-a216-cbbe3e41b88d)
![Screenshot 2024-10-22 at 6 50 35 PM](https://github.com/user-attachments/assets/46a6b025-a1a6-4c5b-a361-0ad218c6825e)

The expansion board has been tested only with 128K MacPlus / 512Ke ROMs. If a *ROM-INATOR board* is installed concurrently, it needs to be previously patched (instructions provided below. Many thanks to Golden Potato and SVGA for this solution!).


## KEY FEATURES

•	Configurable to add up to 4MB of RAM, the maximum supported by early Macs.

•	Compatible with Macintosh 128K (version 3 only), Macintosh 512K, and 512KE models (using *Apple 128K ROM or ROM-INATOR*).

•	Option to include or exclude onboard RAM bank for 512K/512KE models through a DIP switch (Version 3 only).

•	Soldered type jumpers to select among various memory configurations (1MB, 2MB, or 4MB).

•	Auxiliary board can be set to restore original configuration and disable the expansion board through a DIP switch (Version 3 only).

•	Auxiliary board allows customization of the number of refresh cycles (standard, Mac Plus-style, or 1024 refresh cycles).

•	No extensions or other software are required, and the Mac recognizes all the configured RAM at startup.


## INSTALLATION

Two options are available for installing these boards:

•	Soldering piggyback sockets
  
This is the easiest method and can be reversed. Solder DIP sockets onto specific ICs (U5-11F, U5-11G, U12E, U13E, and U4F for the auxiliary board) on the logic board. Then, the boards connect through male pin headers to these sockets.

• Relocating ICs to the expansion boards

Alternatively, relocate those ICs to the expansion boards and install pin header sockets (machine round type preferably) directly onto the logic board to make the connection.

Additionally, resistor arrays RP2 and RP3 must be removed from the logic board, and at least 4 to 6 signals (standard mode, depending the Mac model is 512 or 128) need to be collected through cables soldered to specific points on the logic board and brought to the expansion board using DIP connectors.


## THE RAM REFRESH CONFIGURATOR

This versatile tiny board offers several handy features:

•	Intervene /CAS signals, handle RAM address bus and select between 3 refresh cycles modes: Standard, Mac Plus, 1024 cycles (experimental). 

•	Disable the RAM expansion board trough a DIP switch, allowing to remove the board and restore the memory stock configuration.


### HANDLING OF THE ONBOARD MEMORY BANK

The onboard memory bank consists of 16 ICs of either 256Kbitx1bit (Macintosh 512K/KE) or 64Kbitx1bit (Macintosh 128K). 
The expansion board (version 3.0) has a DIP switch that enables the option to include or exclude the this memory bank withing the 4MB of RAM. 
On Mac 128K, the system memory bank must always be excluded. On Mac 512K/KE, it's optional. 
Excluding the aging onboard memory bank may reduce overall energy consumption and heat generated by the logic board.


### STANDARD REFRESH CYCLES MODE

The standard refresh mode is the stock method used by the Mac 128/512/KE to generate DRAM refresh cycles.
Although the system memory ICs are 256 cycles/4ms, the ICs used in this RAM expansion board (AS4C1256KFO / 512 refresh cycles / 8ms), work perfectly!.
Somehow, these ICs are correctly refreshed within 8 ms in all their rows range, making them compatible with the system refresh circuitry. This mode has been working in the expansion board prototype installed on my Macintosh 512K for a significant time without any kind of issues.
Using the default refresh mode requires fewer signals from the logic board, reducing the number of components to be populated in the auxiliary board. (U1, U2, and U3 can be omitted.)

For this mode, the connections trough cables you need is just 6 signals from the LB to J5 at the expansion board:

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

Signals from connection point 4. (A17), and 5, (A18) are need only for the Mac 128K.

Jumper settings for each refresh mode and other functionalities can be found at the end of this document. 

![LB_512K_scaled copy](https://github.com/user-attachments/assets/7516653b-66f9-4f18-a7ac-8dcdc91c0549)


### MACPLUS REFRESH CYCLES MODE

As the name suggests, this mode replicates how the Mac Plus generates RAM addresses for refresh cycles. In this mode, the RAM Configurator board generates address bits RA8 and RA0 as in the Mac Plus, subtituting it the default RA0 & RA8. A member of 68KMLA forums named Golden Potato was the one who figure out how to generate those bits. Thanks again Golden Potato!

An additional few input signals pickup trough cables soldered to specific points on the LB are needed for this mode, and all of them goes to J3 at the auxiliary board. The rest of the needed signals are taken trough the piggy back socket on U4F.

 7.  A19 - Pin #7 (RP1 DIP resistor array, Later LB models) or connection point 2.
   
 8.  A20 - Pin #48 (CPU) or same as connection point 3.
 
 9.  A17 - Same as connection point 4.

10.  A18 - Same as connection point .5

11.  VA5 - PIN #13 - (U3G)
   
12.  VA13 - PIN #12 - (U3G)

13. /DMA - PIN #15 - (U2F)

Finally, one of the legs of R42 have to be opened and set the solder jumpers accordinly *(See the table at end fo this document)*

![Uploading LB_512K_scaled 2.jpg…]()

### 1204 REFRESH CYCLES MODE

This mode is for a memory expansion board with FP/EM DRAM ICs of higher density, and at this time is still under development.


## SOLDER JUMPER SETTINGS

| Board | Jumper | Function | Mac 512K/KE | Mac 128K |
|:--- |:---:|:--- |:--- |: --- :|
| Expansion      | J1 | xxx | 1-2-3 | 1-2-3 |
| Expansion      | J2 | xxx | 1-2-3 | 1-2-3 | 
| Expansion      | J3 | xxx | 1-2-3 | 1-2-3 | 


| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
