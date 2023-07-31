# Access Point - ESP
The Access Point ESP can be updated to the latest firmware version using the Update button under AP Config. It might fail to connect to GitHub to download part of the package - if this happens, keep trying. It will eventually download and complete.

Alternatively, the firmware can also be updated via the Install button on the [OpenEPaperLink website](https://openepaperlink.de/) (this only works in Chromium based browsers)

# Access Point - Display
This will be updated as part of the main update. You can also force an update of the display only by downloading the relevant firmware file e.g. [FW 1.7 for UK Segmented Tags](https://github.com/jjwbruijn/OpenEPaperLink/releases/download/1.7-beta/AP_FW_Segmented_UK.bin), renaming it to AP_force_flash.bin and uploading it to the root of the ESP filesystem.

# Individual Tags
These cannot be updated OTA so must be done using the contacts on the back and a [ZBS flasher.](https://github.com/atc1441/ZBS_Flasher)
