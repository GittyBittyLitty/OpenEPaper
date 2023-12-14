# Access Point - ESP
The Access Point ESP can be updated to the latest firmware version using the Update button under AP Config. It might fail to connect to GitHub to download part of the package - if this happens, keep trying. It will eventually download and complete.

Alternatively, the firmware can also be updated via the Install button on the [OpenEPaperLink website](https://openepaperlink.de/) (this only works in Chromium based browsers)

# Access Point - Display
This will be updated as part of the main update. You can also force an update of the display only by downloading the relevant firmware file e.g. [FW 1.7 for UK Segmented Tags](https://github.com/jjwbruijn/OpenEPaperLink/releases/download/1.7-beta/AP_FW_Segmented_UK.bin), renaming it to AP_force_flash.bin and uploading it to the root of the ESP filesystem.

# Individual Tags
These can be updated OTA by clicking on the tag on the AP webpage and choosing "Firmware Update" under the content menu, then picking a binary file (e.g. Tag_FW_2.9.bin) on the AP filesystem. Make sure that when you enter the filename, you enter a / at the start (and then enter the rest of the path if it's not in root folder). The latest firmware can be found in the [binaries folder](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/binaries) or the [ARM_Tag_FW folder](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/ARM_Tag_FW) on Github.
