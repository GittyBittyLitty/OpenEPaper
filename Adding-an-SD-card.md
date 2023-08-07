This guide is for adding ad SD card to a Nano AP. I will use this module: ![SD card module](https://electropeak.com/learn/wp-content/uploads/2019/05/ds3231-sd-module-pinout.jpg)

* In the platformio.ini, change the 'board_build.partitions' esp32_sdcard.csv.
* Add to the build_flags
	-D HAS_SDCARD

	-D USE_SOFTSPI

	-D SD_CARD_SS=11

	-D SD_CARD_CLK=9

	-D SD_CARD_MISO=8

	-D SD_CARD_MOSI=10


If you build it now, you'll get an error message. We need to change one more thing.
* In the storage.cpp, row 22 (at the time of writing with the 1.8 version), change 'VSPI' to 'HSPI'.
* Now upload as usual.

For the hardware side, solder the wires. Format the SD card and it should work!

![](https://i.imgur.com/ETUs1Gs.png)
