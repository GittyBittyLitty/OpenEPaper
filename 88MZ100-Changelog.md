## v0027
* Greatly reduced EPD booster, resulting in much less EPD power consumption
* Will now work down to approximately 2 volts (if your batteries would support any currents at that low a voltage)
* No more red-bleed in large areas with black/red

## v0027 beta - Compression and proper UI fonts ##

* Moved various parts to C++, most parts compiled with -O3
* Improved stability, watchdog now runs properly
* Improved icons for no-RF and low battery
* Common codebase for protocol and drawing text and icons with M3 firmware
* Moved 'settings' and 'profile' to the back of the flash space, to allow universal firmwares in the future
* Support for *much* larger firmware's in the future
* Software version now correctly reported
* Sending Full DataAvailReq packets works reliably
* MD5 validation for both firmware and images
* Firmware magic number is validated when doing OTA updates to ensure the correct file is flashed 
* Simplified EPD driver for UC8159
* Reduced power consumption
* Introduces OEPLfs in order to reduce codesize and keep data out of RAM
* Introduces EPD-driver abstraction layer
* Uses compression on images and icons
* This version supports compression of the transferred image data, when the AP supports it
  * Uses zlib for compression, with a fixed window(dictionary) size of 8192
  * Reduces unnecessary block transfers

### Known issues ###
* Due to larger size, this version cannot be flashed from previous versions! You'll need to flash to v0026 first!
* Waking the tag up from NFC will crash and reboot the tag

## v0026 Trampoline ##
* Supports flashing to v0027
* Displays when it's safe to update to v0027