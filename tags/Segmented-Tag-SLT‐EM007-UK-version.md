Segmented Display EPaper Pricetag, display segments are directly printed onto the PCB itself. The version on the pictures below is branded Samsung Electro-mechanics, before the spinoff to Solum occurred.

# Specs #
* [[ZBS 243 / SEM9110|ZBS243-(SEM9110)-SoC]] 8051 based core, 64kbyte flash, 8kbyte XRAM, 256 bytes iRAM 16 MHz, 802.15.4 2.4Ghz radio
* SEM9010 - Segmented ePaper controller, somewhat similar to SSD1623L2

# Photos #

<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/ca02f6a4-e093-40b7-a100-c2c00232e5e4">
<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/0d0849e1-1af5-4ba4-98eb-50f3c23d68ad">
<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/4ee24675-eb0a-4522-b41d-06e71d6519da">


# Programming #
Uses the same pinout as the SLT-EM104:<br/>
<img width="300" src="https://user-images.githubusercontent.com/2544995/227795256-bb5df6d6-abe5-4b94-9b4d-4931053de64a.png"><br/>
Be careful; the first column of pins carry EPD-waveforms, these are considered 'high' voltages for devices expecting logic level signals. Connecting these to a microcontroller might not end too well<br/>

The jig for 'segmented' tag can be used for programming, which can be found [here](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/OpenEPaperLink%20AP%20and%20Flasher/Jigs)

## Partial Schematic ##
<img width="300" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/63a2dea7-dcb6-4c13-bd82-4802888561e0"><br/>

# Pins to the EPaper Segmented-controller (SSD1623-ish)

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

# Original Firmware Files (dumped) #
Version | Type     | MD5 (first 10kbyte) | Original Tag Mac (as written on case)| Note
:------------------:|:----------:|:-------------:|:--------------:|:---------------:
[???](https://github.com/jjwbruijn/OpenEPaperLink/blob/master/fw_dumps/__0-840B2D904BB90131-SLT-EM007.bin) | SLT-EM007 | A27D978C48888FA045E8D3F90DC27029 | 840B2D904BB90131
