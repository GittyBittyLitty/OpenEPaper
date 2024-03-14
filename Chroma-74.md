## Specs
* TI CC1110 - 26Mhz 8051 32kB Flash / 4kB RAM
* 6.4 x 3.5 in ePaper display (BWR or BWY) 640x384px
* 1Mbyte SPI flash
* 6x CR2450 button cell
* SubGhz (868 Mhz / 915 Mhz) Radio

<img width="500" src="https://github.com/skiphansen/dmitrygr-einkTags/blob/master/assets/two_cats.png">

## Status

This tag is not supported by OpenEPaper link yet, but a port is in progress, 
see below for status.

If you are interested in playing with the Chroma 74 in the mean time an updated version of 
Dmitry Grinberg's original Chroma74 code and AP firmware can be found [here](https://github.com/skiphansen/dmitrygr-einkTags).

## OEPL port status
- [x] Dmitry's original code up and running
- [x] zbs243_Tag_FW recompiled for CC1110 processor (it **didn't fit** by a **LOT!**)
- [x] Comment out unneeded and optional code (still didn't fit)
- [x] Analyze memory map looking for areas to reduce RAM and code usage
- [x] Changed BLOCK_DATA_SIZE from 4096 (all CC1110/s RAM) to 1089 (11 * 99).
- [x] Added SubGhz support to an OEPL AP
- [x] Get pings between Tag and AP working
- [x] Create JSON type tag
- [x] Get Tag registration working with AP
- [x] Add support for 868 Mhz channels
- [x] Add support for channel selection to AP
- [x] Add detection of CC1101 presence to AP
- [x] Add sleep support
- [x] Get AP search working
- [ ] Modify image download routine for 1089 BLOCK_DATA_SIZE w/o changing OEPL protocol
- [ ] Get image download to flash from AP working
- [ ] Get Display image from flash working
- [ ] Get OTA FW updates from AP working
- [ ] Audit and optomize sleep current
- [ ] Send firmware PR for OEPL release (auto updates, etc)
- [ ] Start work on next tag (Chroma 42)

## History

This was one of the tags reverse engineered by [Dmitry Grinberg](https://dmitry.gr/?r=05.Projects&proj=29.%20eInk%20Price%20Tags) 
who's code is the basis of the OpenEPaperLink project.

This tag has been somewhat readily available for some time and multiple DIY 
projects have used it successfully.  

At the moment (March 2024) the tag is still available from multiple vendors on 
ebay.  

Several of the ads have been active for several months and ads with higher 
asking prices for multiple years.  

Even the higher priced units aren't completely outrageous ($44) but are 
close to the price of a new display from Waveshare.  

This tag is no longer in production, it was replaced by the Chroma 74 H+ which 
has a higher resolution screen and a more modern SOC.  From outward appearances 
the Chroma 74 and Chroma 74 H+ are identical.
