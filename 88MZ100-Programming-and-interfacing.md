# Programming 88MZ100-based tags

88MZ100 based tags can be programmed over a serial interface. Using a USB-to-TTL module makes this pretty easy to do. The DTR line can be used to reset the CPU when needed. 

## Schematic for 7.5" tags (ST-GR750BN)
![image](https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/43906a62-0a7d-43a3-a25a-b20bed8f7f9a)

## Schematic for 4.2" tags (ST-GR42RG0)
![image](https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/bca64fb7-d2d4-4432-80c8-90c52ee9d6c0) <a href="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/0627e3e2-aada-4365-9f85-22661f5a9359"><img height="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/0627e3e2-aada-4365-9f85-22661f5a9359"></a>

The ST-GR42RG0 can also be programmed with the OEPL-Flasher, using the same jig as the ST-GR420B3N2. If you want to program them with the OEPL-Flasher, use the 88MZ100-OEPL-Flasher.py script.

For development purposes, using a bit of hot-glue and some wires, tags can easily be wired to connect to your PC. Please note however that for normal use, or in order to meaningfully monitor power consumption, the serial board must be removed.

The flasher scripts for use with these serial ports can be found [here](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Tag_Flasher). They are based on ATC1441's 88mz100 flasher python scripts, with only small modifications for use with the ESP32/AP-Flasher and automatic reset.

Checkout ATC1441's 88MZ100 page [here](https://github.com/atc1441/88MZ100)!

