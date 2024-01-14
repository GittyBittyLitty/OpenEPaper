## Access Points

An OpenEpaperLink installation consists of different epaper tags, wirelessly connected to one or more Access Points. An access point is made of a esp32-family MCU, and some device that can talk IEEE 802.15.4. This can be a ZBS243-based tag, or better, an esp32-C6.
You can build one of the different access points models yourself, or you can order a kit or even a ready made one.

### AP Comparisation table

The following build environments are available. If you build one of these AP's, you can easily upload the firmware to your MCU via https://install.openepaperlink.de, and update new firmware releases over the air via the webinterface of the AP, without having to install Platform.io and Visual Studio Code. Also, you will find binaries of the firmware in the [releases](https://github.com/jjwbruijn/OpenEPaperLink/releases).

| name                   | Simple AP     | Mini AP v2        | Nano AP       | Yellow AP     | Mini AP v3    | AP and flasher |
| ---------------------- | ------------- | ----------------- | ------------- | ------------- | ------------- | -------------- |
| **based on**               | esp32         | esp32-s2          | esp32-s2      | esp32-s3      | esp32-s3      | esp32-s3       |
| **radio**                  | Segmented / 1.54” / 2.9” | Segmented tag     | 1.54” tag     | esp32-c6      | esp32-c6      | 1.54” tag      |
| **psram**                  | no            | 2MB               | 2MB           | 8MB           | 8MB           | 8MB            |
| **flash size**             | 4 MB          | 4MB               | 4MB           | 16MB          | 16MB          | 16MB           |
| **extras**                 | no display    | segmented display | 1.54” display | TFT display   | TFT display   | 1.54” display  |
| **Maximum amount of tags** | About 30      | About 30          | About 30      | a few hundred | a few hundred | a few hundred  |
| **maximum tag size**       | 2.9”          | any size          | any size      | any size      | any size      | any size       |
|                        |               |                   |               |               |                |                |
| **design by**              | nic           | jelmer            | atc1441       | atc1441       | nic           | jelmer         |
| **link/pcb/case design**             |             | [more info](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/OpenEPaperLink%20Mini%20AP)    | [more info](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/2.9-1.54%20NanoAP%20by%20ATC1441)          | [more info](https://www.github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/Yellow%20AP%20by%20ATC1441)          | [more info](https://github.com/nlimper/Mini-AP-v3) | [more info](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Hardware/OpenEPaperLink%20AP%20and%20Flasher)           |
| **note**              | Because of lack of psram, not recommended, will also be fully deprecated this year |             |             |             | [available ready made or as DIY kit on Tindie](https://www.tindie.com/stores/electronics-by-nic/) | Includes interface to flash tags    |

### Getting started video

[This video](https://www.youtube.com/watch?v=Etonkolz9Bs) shows you step by step and in seperate sections how to start from scratch: 
- Flash a custom firmware on the ZBS243 based E-Paper Price tags 
- How to connect such a display to an ESP32 as Access point 
- How to flash this Access Point 
- How to use the OpenEPaperLink firmware to drive displays wireless and simple

You can skip many of the steps in the video if you buy tags with pre-flashed firmware, and a ready made access point.

### Example: homemade access point with enameled copper wire  
If you want to make your own AP without using one of the available ready-made options, you can do this by soldering some wires to a [[segmented tag|Segmented-Tag-SLT‐EM007-UK-version]]

[<img width="250" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/746d78a4-6981-4676-a377-5b691b001f51">](https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/746d78a4-6981-4676-a377-5b691b001f51) 

Simplified circuit diagram

[<img width="450" alt="circuit" src="https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/3c38d0bf-c650-4c6f-8228-0183afe6c1ba">](https://github.com/jjwbruijn/OpenEPaperLink/assets/16150580/3c38d0bf-c650-4c6f-8228-0183afe6c1ba)

### Building the mini AP kit

A video showing how to build the mini AP (v1 or v2) kit:
https://www.youtube.com/watch?v=R-WRH9hXSpI

### Designing your own AP

If you design your own AP, there are a few points to keep in mind:
If you use the same components as an existing AP, try to use the same pinout if you want to have OTA. When using a ESP32-C6 as an AP, please copy the pinout of the Mini AP v3 or Yellow AP to be able to flash the ESP32-C6 via the other ESP32. Use a 16MB flash and 8MB ram ESP32-S3 module, other configurations are really hard to get working and will not get OTA. For the ESP32-C6, 4MB flash will do. The pinouts for the different build environments are listed [[on this page|Access-point-pinouts]]

### Why do I need an ESP32-S3 *and* a ESP32-C6?

You would think the ESP32-C6 can do IEEE 801.15.4 as well as WiFi, but the catch is... not at the same time! Because the AP has to receive unsolicited messages from the tags, it need to listen in IEEE 801.15.4 mode continuesly. There's no way to do WiFi communication in parallel to this.

### Can I use a Raspberry Pi and a CC2530 module

In theory it's possible to skip the esp32 entirely and use a Raspberry Pi and a CC2530. But you will miss out on most the the cool features that are build in on the esp32-based AP's, like Zero-config Multi-AP's (to extend the reach using multiple access points) and json templates. A rudimentory implementation of the protocol is [here](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/ARM_Tag_FW/cc2531_OEPL). But it's much easier to use one of the esp32-flavours for the access point, so you can just push jpg's or json templates.
