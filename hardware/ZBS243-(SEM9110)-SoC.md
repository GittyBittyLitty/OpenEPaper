This is a Solum/Samsung Electromechanics SoC made for Zigbee applications. It uses an 8051 core, and has support for 2.4Ghz radio. There is no datasheet available, but Dmitry Grinberg [reverse engineered](https://dmitry.gr/?r=05.Projects&proj=30.%20Reverse%20Engineering%20an%20Unknown%20Microcontroller) almost all parts of this SoC! This was based on the original firmware on the tags, and as the tags don't use all features, such as AES, not all features could be documented.


In addition to Dmitry's work, some of the improvements made by ATC1441 were also integrated into the OpenEPaperLink codebase

This SoC and others in the ZBS24x family seem to be capable of more features, but without a datasheet or reference code using these features, it's doubtful if we'll ever be able to use it.

<img width="500" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/2544995/c49975d8-c63e-48ba-8776-3dc8abff0e8a">


## Specs 
* 8051 based core
* 64kbyte flash
* 8kbyte XRAM
* 256 bytes IRAM
* 16Mhz clock
* +- 1µA Sleep
* SPI / UART / I²C / RF Wake (undocumented) / 2.4GHz 802.15.4 Radio
 
<img width="500" alt="board" src="https://user-images.githubusercontent.com/2544995/227795788-249fe764-816e-48da-9932-0b70dad87f47.png">