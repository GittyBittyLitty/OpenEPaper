## ESP32 binaries
For ESP32 binaries (excluding C6), the filename consists of:

~~~
PIOenvname[_full].bin
~~~

the `_full` designator is optional. The file with this designator can be flashed to the ESP directly and is used by [install.openepaperlink.de](https://install.openepaperlink.de/). Files without this designator are used for over the air (OTA) updates.

Examples:
~~~
OpenEPaperLink_Nano_AP_full.bin
# used to flash via USB

OpenEPaperLink_Mini_AP.bin
# used for OTA updates
~~~

## Tag binaries

For Tag binaries as found in `binaries/Tag` the filename consists of:

~~~
<tag-name>_[<full-or-ota>]_<version>.bin
~~~

The AP's auto update function uses the mapping defined in [`tagotaversions.json`](https://github.com/jjwbruijn/OpenEPaperLink/blob/master/binaries/Tag/tagotaversions.json) to select the right firmware for OTA updates based on the `hwType`, as defined in [`tag_types.h`](https://github.com/jjwbruijn/OpenEPaperLink/blob/master/tag_types.h).

### Overview

| Model | MAC ID | Firmware |
| ----- | ------ | -------- |
| 1.54″‐1.6″ ST-GR16000 | 341 | `SOL_M2_154_SSD_<version>.bin` |
| 1.54″‐1.6″ ST-GR160BN | 343 | ? |
| 1.54″‐1.6″ ST-GR1600N | 163 | ? |
| 2.2″ EL022H3WRA | B19 | `SOL_M3_Uni_<full\|ota>_<version>.bin` |
| 2.7″ ST‐GR27000 | 2F3 | work in progress |
| 2.9″ EL029D2WRA SubGHz | B23 | not (yet) supported |
| 2.9″ EL029GSWRN | B27 | work in progress |
| 2.9″ EL029H3WRA | B29 | `SOL_M3_Uni_<full\|ota>_<version>.bin` |
| 2.9″ ST-GM29XXF Low Temp | 2D1 | `SOL_M2_29_LT_<version>.bin` |
| 2.9″ ST‐GR29000 | 3B1 | `SOL_M2_29_SSD_<version>.bin` |
| 2.9″ ST-GR2900N | 3B3 | `SOL_M2_29_UC_<version>.bin` |
| 2.9″ ST-GR2900L | 3B3 | ? |
| 4.2″ ST-GR42003N2 | 483 | `SOL_M2_42_SSD_<version>.bin` |
| 4.2″ ST-GR42003N | 411 | ? |
| 4.2″‐ST‐GR4200C | B57 | ? |
| 7.5″ ST‐GR750BN | 743 | `SOL_M2_75_<full\|ota>_<version>.bin` |
| 13.3″ EL133C2WRN | BB7 | not (yet) supported |

### Tag-Name
The name of the tag as found in [`tag_types.h`](https://github.com/jjwbruijn/OpenEPaperLink/blob/master/tag_types.h).
It is composed of the following parts:

~~~
<manufacturer>_<brand>_<diplay-size>_<display-controller>
~~~

Examples:
~~~
SOL_M2_29_SSD_15.bin
# Firmware for a 2.9″ ZBS based tags with no mods to be put on the tag with version 15 

SOL_M3_Uni_full_16.bin
# Firmware to flash a M3 2.9″ tag with version 16
~~~

#### Manufacturer
- SOL => SOLUM
- TLSR => Controller used by the Hanshow 3.5″ tag

#### Brand
- M2 => Solum M2 Model
- M3 => M3 Newton 2.2″ Electronic Shelf Label by Solum

#### Display Size

The firmware for M3 tags is universal for all display sizes.

- 154 => 1.54″
- 29 => 2.9″
- 42 => 4.2″
- 29 => 2.9″
- 75 => 7.5″
- uni => universal firmware for all sizes of M3 tags

#### [Optional] Display Controller

Only used by M2 firmware.

- SSD => used for most common "normal" tags: ST‐GR16000, ST-GR29000
- LT => used for low temperature tags
- UC => used for NFC enabled tags

#### [Optional] Full or OTA

Some tags have different files for OTA and direct to tag flashing.
If this this is the case, this part can be `full` or `ota`.
This mainly concerns M3 tags and the M2 7.5″ ST‐GR750BN.
For most M2 tags there is only one binary, which can be used in both cases. 

### Version

The version of the firmware in hex format, always 2 digits.
