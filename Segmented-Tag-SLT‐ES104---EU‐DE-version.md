Another segmented tag, with a rectangular screen instead of a mostly square one. This tag and the EM104 share the exact same firmware, despite being a completely different design.

* ZBS243 SOC 256 bytes IRAM, 8kbyte XRAM, 64kbyte FLASH, 2.4 Ghz 802.15.4 radio
* SEM9010 - Segmented ePaper controller, somewhat similar to SSD1623L2

<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/12bb0159-365a-46e8-bd35-6ab15ea3f245">
<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/c6149fab-3809-426c-8523-b0ce2a9afbdb">
<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/8a1a5ada-db62-40f0-ade4-a5810f4ce8cd"><br/>

<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/622856f1-a6f9-42bc-9ce6-330099fc309f"><br/>

<br/><br/>Uses a similar pinout to the SLT-EM105, however: VCC and GND pins are reversed!<br/>
<br/>

ZBS243 Pin                       |ePaper controller        | Note             
:-------------------------:|:-------------------------:|:-------------------------:
P2.0 | EPD_Busy 
P2.1 | _CS | Active low
P2.2 | Power 
P1.7 | _RESET | Active low
P1.6 | EXT_CLK | This is a 'function' on this pin on the ZBS243
P0.0 | SPI_CLK
P0.1 | MOSI
P0.2 | MISO 

Original Firmware Files (dumped)
Version | Type     | MD5 (first 10kbyte) | Original Tag Mac (as written on case)| Note
:------------------:|:----------:|:-------------:|:--------------:|:---------------:
[???](https://github.com/jjwbruijn/OpenEPaperLink/blob/master/fw_dumps/__0-C8BA94FF03546A5B0-SLT-ES104.bin) | SLT-ES104 | 359B6E7FD250D327E585C951615F2A07 | C8BA94FF03546A5B0