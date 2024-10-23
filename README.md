# OpenEarlyMacsRAMexpansion

SUMMARY

Unlike the Macintosh Plus, which offers a simple SIMM-based memory upgrade, expanding the memory of these early Macs is significantly more complex and requires additional components.
Historically, RAM expansion boards were available to increase the memory of early Macs. However, finding these boards in working condition has become increasingly challenging and expensive. The Mac Rescue boards, capable of reaching 4MB, are particularly rare.
This newly designed expansion board, paired with an auxiliary board, provides a flexible and customizable solution to increase memory up to 4MB. The circuitry is largely based on the renowned Macsnap 548E (1.5 MB RAM) expansion board from DOVE Inc. With minor modifications and enhancements, 4MB RAM is easily achievable using newer, higher-density DRAM FP ICs.

![Screenshot 2024-10-22 at 3 00 07 PM](https://github.com/user-attachments/assets/0927eb3d-6c0c-4479-a216-cbbe3e41b88d)
![Screenshot 2024-10-22 at 6 50 35 PM](https://github.com/user-attachments/assets/46a6b025-a1a6-4c5b-a361-0ad218c6825e)

The expansion board requires 128K ROMs. If a ROM-INATOR board is installed concurrently, it needs to be patched (instructions provided below).

KEY FEATURES

•	Configurable to add up to 4MB of RAM, the maximum supported by early Macs.

•	Compatible with Macintosh 128K, 512K, and 512KE models (using Apple 128K ROM or ROM-INATOR).

•	Option to include or exclude onboard RAM bank for 512K/512KE models through a DIP switch.

•	Soldered type jumpers to select among various memory configurations (1MB, 2MB, or 4MB).

•	Auxiliary board can be set to restore original configuration and disable the expansion board through a DIP switch.

•	Auxiliary board allows customization of the number of refresh cycles (standard, Mac Plus-style, or 1024 refresh cycles).

•	No extensions or other software are required, and the Mac recognizes all the configured RAM at startup.
