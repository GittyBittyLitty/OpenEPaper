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

## Mac settings

The 88MZ100 SOC has no separate config flash area. That means the MAC-address and other settings are a part of the firmware file. A little utility, '88MZ100_FW_Edit.py', can be used to change the mac-address and tag type.

To use this utility:
```
python 88MZ100_FW_edit.py <firmware file> -mac 0123456789ABCDEF -oepltype 0x05 -bpp 1
```

For M2 7.5 BWR tags, use ```-bpp 2 -oepltype 0x05```

For M2 7.5 BW tags, use ```-bpp 1 -oepltype 0x26```

### Complete instruction to flash a 7.5" tag with a USB-to-TTL module

Connect the wires as above. From the \OpenEPaperLink\Tag_Flasher folder, run:
```
88MZ100_FW_edit.py <firmware file> -mac 0123456789ABCDEF -oepltype 0x05 -bpp 1
88MZ100-Serial-Flasher.py COM27 write_flash <firmware file>
```
Of course, replace 028E204A7438 with the actual mac of the tag (see reverse side), and replace COM27 with the port of your USB-to-TTL module.