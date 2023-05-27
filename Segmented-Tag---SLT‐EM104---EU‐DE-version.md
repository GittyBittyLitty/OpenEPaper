Segmented Display EPaper Pricetag, display segments are directly printed onto the PCB itself.

* ZBS243 SOC 256 bytes IRAM, 8kbyte XRAM, 64kbyte FLASH, 2.4 Ghz 802.15.4 radio
* SEM9010 - Segmented ePaper controller, somewhat similar to SSD1623L2

<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/6a6e5594-b3f7-49fc-bd2f-12cb8471ab97">

<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/fa08604e-85d8-4fdd-9f43-224b77fe316a">

<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/3bec811f-9b9f-44c2-ba44-b6fa153e5de5">


<br/><br/>Uses the same pinout as the SLT-EM007:<br/>
<img width="300" src="https://user-images.githubusercontent.com/2544995/227795256-bb5df6d6-abe5-4b94-9b4d-4931053de64a.png"><br/>
Be careful; the first column of pins carry EPD-waveforms, these are considered 'high' voltages for devices expecting logic level signals. Connecting these to a microcontroller might not end too well


Partial schematic<br/>
<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/63a2dea7-dcb6-4c13-bd82-4802888561e0"><br/>

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
Version:           | MD5 (first 10kbyte) | Original Tag Mac (as written on case)| Note
:------------------:|:-----------------------:|:--------------:|:---------------:
Unknown | 359B6E7FD250D327E585C951615F2A07 | C8BA94FF039DCFE41 | 
