## For ESP32 binarys (excluding C6), the filename consists of:


***

**PIOenvname(_full).bin**

***


the _full designator is optional. The file with this designator can be flased to the ESP directly and is used by [install.openepaperlink.de](https://install.openepaperlink.de/). Files without this designator are used for OTA updates.

Examples:

OpenEPaperLink_Mini_AP.bin

OpenEPaperLink_Nano_AP_full.bin

## For Tag binarys (ap and non ap) the filename consists of:


***

**nameoftag-tagorap-custom-version-tagid-fullorota.bin**

***

Nameoftag: The name of the tag as found in tag_types.h

Tagorap: If this is firmware for tag operation, this field is "tag", if it is used as an AP, it should be "AP". If the ESP firmware(excluding C6) gets converted to this nomenclature down the line, it could be "esp" for that

Custom: "stock" for stock firmware. For custom firmware, for example bme280 => "bme280"

Tagid: The id of the tag as found in tag_types.h, in Hex always 2 digits

Version: The version of the firmware in decimal format, always 3 digit

Fullorota: Some tags have different files for OTA and direct to tag flashing. If this this is the case, this part can be "full" or "ota". If not, this field is not present

Examples:

SOLUM_29_SSD1619-tag-stock-015-01.bin

Firmware for a 2.9" ZBS based tags with no mods to be put on the tag with version 15 

SOLUM_M3_BWR_29-tag-stock-016-33-full.bin

Firmware to flash a M3 2.9" tag with version 16