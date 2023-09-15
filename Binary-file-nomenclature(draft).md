## For ESP32 binarys (excluding C6), the filename consists of:


***

**PIOenvname(_full).bin**

***


the _full designator is optional. The file with this designator can be flased to the ESP directly and is used by [install.openepaperlink.de](https://install.openepaperlink.de/). Files without this designator are used for OTA updates.

## For Tag binarys (ap and non ap) the filename consists of:


***

**Tagid_fullorota_tagorap_version_nameoftag.bin**

***

Tagid: The id of the tag as found in tag_types.h

Fullorota: Some tags have different files for OTA and direct to tag flashing. If this this is the case, this part can be "full" or "ota". If not, this field should be "combined"

Tagorap: If this is firmware for tag operation, this field is "tag", if it is used as an AP, it should be "AP". If the ESP firmware(excluding C6) gets converted to this nomenclature down the line, it could be "esp" for that

Version: The version of the firmware in decimal format

Nameoftag: The name of the tag as found in tag_types.h