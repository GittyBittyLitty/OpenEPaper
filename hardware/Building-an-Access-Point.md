## Access Points

An OpenEpaperLink installation consists of different epaper tags, wirelessly connected to one or more Access Points. An access point is made of a esp32-family MCU, and some device that can talk IEEE 802.15.4. This can even be another tag, or a esp32-C6.

### AP Comparisation table

The following build environments are available. If you build one of these AP's, you can easily upload the firmware via https://install.openepaperlink.de, and update new firmware releases over the air via the webinterface of the AP, without having to install Platform.io and Visual Studio Code.

| name                   | Simple AP     | Mini AP           | Nano AP       | Yellow AP     | AP and flasher |
| ---------------------- | ------------- | ----------------- | ------------- | ------------- | -------------- |
| **based on**               | esp32         | esp32-s2          | esp32-s2      | esp32-s3      | esp32-s3       |
| **radio**                  | Segmented / 1.54” / 2.9” | Segmented tag     | 1.54” tag     | esp32-c6      | 1.54” tag      |
| **psram**                  | no            | 2MB               | 2MB           | 8MB           | 8MB            |
| **flash size**             | 4 MB          | 4MB               | 4MB           | 16MB          | 16MB           |
| **extras**                 | no display    | segmented display | 1.54” display | TFT display   | 1.54” display  |
| **Maximum amount of tags** | About 30      | About 30          | About 30      | a few hundred | a few hundred  |
| **maximum tag size**       | 2.9”          | any size          | any size      | any size      | any size       |
|                        |               |                   |               |               |                |
| **design by**              | nic           | jelmer            | atc1441       | atc1441       | jelmer         |
| **link/pcb/case design**             |             | [more info](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/OpenEPaperLink%20Mini%20AP)    | [more info](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/2.9-1.54%20NanoAP%20by%20ATC1441)          | [more info](https://www.github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/Yellow%20AP%20by%20ATC1441)          | [more info](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/OpenEPaperLink%20AP%20and%20Flasher)           |
| **note**              | Because of lack of psram, not recommended | An improved version is also [available ready made, or as DIY kit, on Tindie](https://www.tindie.com/stores/electronics-by-nic/) |             |             | Includes interface to flash tags    |

https://www.youtube.com/watch?v=Etonkolz9Bs

## AP with segmented Tag
### Homemade access point with enameled copper wire  
[<img width="250" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/746d78a4-6981-4676-a377-5b691b001f51">](https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/746d78a4-6981-4676-a377-5b691b001f51) 

Simplified circuit diagram

[<img width="450" alt="circuit" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/3c38d0bf-c650-4c6f-8228-0183afe6c1ba">](https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/3c38d0bf-c650-4c6f-8228-0183afe6c1ba)

### Building the mini AP kit

A video showing how to build the mini AP kit:
https://www.youtube.com/watch?v=R-WRH9hXSpI

### Using a Raspberry Pi and a CC2530 module

In theory it's possible to skip the esp32 entirely and use a Raspberry Pi and a CC2530. But you will miss out on most the the cool features that are build in on the esp32-based AP's, like Zero-config Multi-AP's (to extend the reach using multiple access points) and json templates. A rudimentory implementation of the protocol is [here](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/ARM_Tag_FW/cc2531_OEPL). But it's much easier to use one of the esp32-flavours for the access point, so you can just push jpg's or json templates.
