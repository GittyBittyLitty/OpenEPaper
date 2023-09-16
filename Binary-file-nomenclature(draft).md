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

**Tagid_fullorota_tagorap_custom_version_nameoftag.bin**

***

Tagid: The id of the tag as found in tag_types.h, always 3 digit

Fullorota: Some tags have different files for OTA and direct to tag flashing. If this this is the case, this part can be "full" or "ota". If not, this field should be "combined"

Tagorap: If this is firmware for tag operation, this field is "tag", if it is used as an AP, it should be "AP". If the ESP firmware(excluding C6) gets converted to this nomenclature down the line, it could be "esp" for that

Custom: "stock" for stock firmware. For custom firmware, for example bme280 => "bme280"

Version: The version of the firmware in decimal format, always 3 digit

Nameoftag: The name of the tag as found in tag_types.h

Examples:

001_combined_tag_stock_015_SOLUM_29_SSD1619.bin

198_ota_ap_stock_016_ESP32_C6

051_full_tag_015_SOLUM_M3_BWR_29.bin