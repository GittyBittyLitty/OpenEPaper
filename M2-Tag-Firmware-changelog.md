## v0027 - Cmd/redraw ##
- Fixes a bug that would cause inadvertent redraw even though the image remains the same
- Adds Command 33 to sample battery voltage

## v0026 ##
- Managed to free up a LOT of idata space. If you're not a developer, you probably don't care about this. (The ZBS243 has exactly 256 bytes of 'normal' memory. No, really.). Now 210 bytes stack!
- Fixes the LUT-issue that many people had
- No more corrupted images, ever (Probably. If the EPD misses a beat, this could still happen)
- Uses real MD5 checksums for both images and future OTA firmware updates
- Validates future OTA firmware updates with a magic number, preventing wrong files getting flashed
- Fixed a bug where a really cold tag might not boot due to a slower response from the EPD
- Shows 'update failed' screen when an invalid update is sent to the tag
- Reports back the 'failed update' status back to the AP
- Fixed a bug where a buttonized-M2 would repeatedly report back a pressed button
- Debugging messages over the serial link now optional, for more room in flash
- Improved font drawing, now uses far less flash space
- about 7K of flash is now available again

## 0025 - Bugfix ##
- Fixes a bug that would cause corrupted transfers

## 2.4 - Settings and EEPROM Loader ##
- It's now possible to 'clear' the tag settings; this can be done if the tag is power-cycled during the screen's first refresh
- Tag settings moved to eeprom instead of infopage, to avoid potential corruption
- Optional EEPROM-loader, to download/upload images from the EEPROM for slideshow purposes
- Improved power consumption for UC8151 tags (sleep was broken)
- Low-voltage detection for UC8151 now works (below 2.5 volts)
- Removed dead code, unused BMP handlers
- Fixed a bug that would sometimes cause failed OTA updates if the update was a certain size (thanks @atc1441)

## 2.2 - RFW patch
- Discovered new wake-reason register in radio memory space
- Added RF Wake messages to AP and associated preload screens

## 2.2 - Buttons and Preload ## 

- Preloaded images for buttons are now supported
- Optional preloaded UI images for splashscreen, deep sleep, no-ap and ap-found
- Preloading regular images now also possible (cache warming)
- Slideshow modes
- nextCheckin can now be specified in seconds for faster response times
	- msb 1 == seconds
	- msb 0 == minutes
- Added a command for deleting all EEPROM images
- 3 different external wake pins:
	- P1.0 TEST (button1)
	- P0.7 RXD (button2)
	- P0.3 _CS ('gpio') (default disabled, can be enabled in settings.h)
- Faster re-check-in after external wake
- Removed the 'scanning' screen, in line with the M3 firmware.

Note that buttons are detected by a small capacitor across the button on P1.0. If no capacitor is present, the firmware may not detect the presence of buttons and will disable the interrupt


### Using Slideshow-mode:

New commands:

0x05 - Remove all preloaded/cached images

0x06 - Fast slideshow mode

0x07 - Medium speed slideshow

0x08 - Slow slideshow mode

0x09 - Glacial slideshow mode

0x0F - Exit slideshow mode (enter normal mode)

After issueing one of the 'slideshow' commands, the tag will reboot into 'slideshow mode'. The tag will refuse to enter slideshow mode if no applicable 'slideshow'-type images are preloaded.

If a 'splash' image exists on the SPI EEPROM, it will first display this image. The tag will then do a short attempt to find an accesspoint and if so, will do a single data-available request. Only during the bootup process can the tag be resetted into 'normal' mode. To have the tag check-in with the AP again, remove batteries, shorten the contacts and insert batteries again to reboot the tag.

The tag will now display all images on the EEPROM marked as 'slideshow'-image. 

LUT's may be specified when loading the images to the tag. If a full-LUT-refresh isn't done regularly, the tag will automatically force a full-LUT every 15 images

It does take some energy to refresh the display often. Expect around these average currents for shortened LUTs:

Fast: (15 second interval) 400-850µA

Medium: (60 second interval) 100-250µA

Slow: (300 second interval) 30-50µA

Glacial (1800 second interval) 10µA


The battery symbol will show if during bootup the battery power was detected to be low. Since the radio is not being used during the slideshow, peak current draw is reduced, allowing for extended battery life.
