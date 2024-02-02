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
<name_of_tag>_[<full_or_ota>]_<version>.bin
~~~

### Nameoftag
The name of the tag as found in tag_types.h
Which follows the scheme
~~~
<manufacturer>_<brand>_<diplay-size>_<display-controller>
~~~
Examples:

~~~
SOL_M2_29_SSD_15.bin
# Firmware for a 2.9" ZBS based tags with no mods to be put on the tag with version 15 

SOL_M3_Uni_full_16.bin
# Firmware to flash a M3 2.9" tag with version 16
~~~

#### Manufacturer
- SOL => SOLUM
- TLSR => ?

#### Brand
- M2 => Solum M2 Model
- M3 => Solum M3 Model

#### Display Size
- 154 => 1.54″
- 29 => 2.9″
- 42 => 4.2″
- 29 => 2.9″
- 75 => 7.5″

#### Display Controller

- SSD => used for most common "normal" tags: ST‐GR16000, ST-GR29000
- LT => used for low temperature tags
- UC => used for nfc enabled tags

| Model | MAC ID | Firmware |
| ----- | ------ | -------- |
|ST-GR16000 | 341 | `SOL_M2_154_SSD_<version>.bin` |
|ST-GR160BN | 343 | ? |
|ST-GR1600N | 163 | ? |
|ST-GR29000 | 3B1 | `SOL_M2_29_SSD_<version>.bin` |
|ST-GR2900N | 3B3 | `SOL_M2_29_UC_<version>.bin` |
|ST-GM29XXF | 2D1 | `SOL_M2_29_LT_<version>.bin` |
|ST-GR42003N2| 483 | `SOL_M2_42_SSD_<version>.bin` ? |
|ST-GR750BN | 743 | `SOL_M2_75_<full\|ota>_<version>.bin` |

### Full or OTA
Some tags have different files for OTA and direct to tag flashing. If this this is the case, this part can be `full` or `ota`.
If not, this field is not present.

### Version
The version of the firmware in hex format, always 2 digits.

