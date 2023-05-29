The NFC chip in some of the 2.9"/1.54" ZBS243-based tags by Solum is an NXP NT3H1101 / NT3H1201 NTAG I²C IC. It is connected to the I²C bus on the ZBS243, and uses some additional GPIO pins for signalling

* P1.3 - FD (Field Detect) - Used to signal the ZBS243 if there's currently
* P1.4 - I²C SCL
* P1.5 - I²C SDA
* P1.6 - NFC Power

NFC Power is supplied directly from the GPIO pin, and will also pull-up the I²C and FD signals.

The FD pin will be driven low by the NFC IC whenever it is activated by a nearby field. However, for the ZBS243 to wake up to this signal, it needs to be pulled-up so it'll recognize being driven low by the NFC chip. An obstacle here is the hardware design; the FD is pulled up by the NFC power-enable line. However, this will also enable the NFC IC, draining the battery. Pulling up only the FD by the SOC is the solution here, however, due to the resistors there, this will also backpower the NFC IC. Removing the FD-pullup resistor will prevent this.

<img width="300" alt="board" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/3a2b6585-88b3-4739-9335-935c71c3350b">

It's fairly easy to remove using a small screwdriver or even your fingernail.

OpenEPaperLink will, on bootup, try to see if it can use NFC wake by taking some measurements on the FD line. The capability flags are updated accordingly.

It's not impossible to 'retrofit' an NFC IC on a non-NFC capable tag; the IC's are about €1.50 and can be bought at DigiKey. Additionally, a few small passives will need to be added. For OpenEPaperLink, no new firmware needs to be installed; the NFC IC should be recognized at bootup.

PDF Datasheet
[NT3H1101_1201-1127167.pdf](https://github.com/jjwbruijn/OpenEPaperLink/files/11525339/NT3H1101_1201-1127167.pdf)
