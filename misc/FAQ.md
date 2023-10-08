### How much tags can the system handle?

* Using an ESP32 or ESP32-S2, you will get to about 30 tags. If you want more, you can use a ESP32-S3 with 16MB flash. A ESP32-C6 based AP is recommended for higher tag counts.

### How can I extend the reach of an Access Point?

* You can simply add more access points. See [[Zero-config Multiple Access Points|Multiple-Access-Points]]

### How about encryption?

* Encryption there is none. Probably that's why it's called OpenEPaperLink ;-) The IEEE 802.15.4 link between the Access Point and the tags is not encrypted, and also the multicast UDP messages on wifi for communication between the Access Points is also not encrypted. It's not needed, because the website to manage the tags doesn't have a password. The system is meant for hobbyist/home use. And because the system is so open, it's no fun for a hacker to hack it. :-D

### I don't like the artifacts of jpg images. Can I send images in PNG?

* If you're worried about bad quality JPG's, you're generating them wrong. Artifacts are really and easily avoidable. Please take a look at the [[Image specifications|Image-specifications]] and the python example at [[Push external image|Image-upload]]. Jpeg images are by far the most easy to generate for you, and at the ESP32 side, the easiest to decode. Decoding a PNG is much more memory/processor intensive, and although there are some libraries for it, there is no space left in the firmware. And really, it's doesn't have advantages regarding the quality of the image. Much more important is to disable antialiassing of your fonts/drawings. See the examples.

### I use an Access Point without PSRAM (like the ESP32), and I get crippled images on my 4.2" screens

* PSRAM is needed for holding a full image buffer of the 400x300 pixel 4.2" displays. Without PSRAM, we can only hold a 1 bit/pixel buffer. Only black is displayed, no red. And rendering a jpeg image is not working either. Please use a board with PSRAM, like a ESP-S2 (but watch out, there are also ESP32-S2 boards being sold without PSRAM).

### I use an Apple M1 Pro to compile the esp32 software. The website to manage the tags is not fully working.

* Sadly, compiling the esp32-scripts on an Apple M1 Pro (and probably M2 too) seem to cause problems. It compiles and boots nicely, but it results in weird runtime problems (the `sscanf` command doesn't do that it's supposed to do, and probabaly more issues). So, try to use another system. Intel-based MacBook Pro, Windows, and Linux all work fine.

### Does OpenEpaperLink operate over ZigBee? / Can I use my existing ZigBee stick as an Access Point?

* OpenEpaperLink employs IEEE 802.15.4 packets for transport, much like Zigbee. However, OpenEpaperLink is an entirely distinct protocol. The protocol itself is intentionally basic due to the inherent limitations of the tags. These tags possess minimal CPU power, necessitating a conservative use of the radio to extend battery life. In contrast, Zigbee is a considerably more complex protocol, rendering it unsuitable for the capabilities of these tags.

In theory, it's possible to reflash a ZigBee coordinator with firmware that enables its use in conjunction with a Python script, which would replace the ESP component of the conventional Access Point. However, you will lose the Zigbee functionality of the coordinator.

### Where can I purchase the tags? Is there a plug-and-play solution for an Access Point?

* To obtain used Solum tags, you can explore platforms like eBay or Tindie. If you're seeking a straightforward way to construct an Access Point, a kit is available for purchase at [this Tindie shop](https://www.tindie.com/stores/electronics-by-nic/). Additionally, if soldering isn't within your skillset, you have the option to order it pre-assembled. However, it's important to recognize that the entirety of the OpenEpaperLink project is intended for hobbyist tinkering. While efforts have been made to enhance user-friendliness, it's not designed as a completely ready-made solution.

### How can I import a tagDB (after update or new installation)
 * Overwrite `tagDB.json` inside the `current` folder
 * Reboot the AP (by power cycling or physical reboot button, do not use the reboot option in the website because that will save the current DB first) 

### Whay does the tag react slowly? How does the timing of the tag communication works?
See [[Timing of the tags|tag-protocol-timing]] for an explanation of the way the tag communicates with an Access Point.