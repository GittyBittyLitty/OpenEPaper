# Troubleshooting an ESP32 / ESP-S2 based Access Point

When you make your own Access Point consisting of an ESP32 or ESP32-S2, and a epaper tag, some things can go wrong. This page lists the most common errors.

## Wiring errors

Pay very good attention on the correct wiring. If you use the pins as predefined in platformio.ini, you will be able to do OTA updates, which saves you a lot of time.

Pinout for ESP32 (Lolin32 lite): Use environment "Simple_AP":
| ESP32 pin | connect to tag pin |
|:---------:|:------------------:|
|     5     |         SS         |
|    18     |        CLK         |
|    23     |        MOSI        |
|    19     |        MISO        |
|     2     |       RESET        |
|  13 + 15  |        VCC         |
|    17     |         RX         |
|    16     |         TX         |
|    GND    |        GND         |


Pinout for ESP32-S2 (Wemos S2 mini): Use environment "OpenEPaperLink_Mini_AP"
| ESP32-S2 pin | connect to tag pin |
|:------------:|:------------------:|
|      11      |         SS         |
|       9      |        CLK         |
|      10      |        MOSI        |
|      8       |        MISO        |
|      13      |       RESET        |
|     VCC      |        VCC         |
|      7       |         RX         |
|      6       |         TX         |
|      12      |        TEST        |
|     GND      |        GND         |

## Wemos S2 mini clones, rebooting

There are many Wemos S2 mini clones with faults. Some of them reset during the establishment of the Wi-Fi connection. The reason for this is that the ENable line is not very stable. Luckily, it's easy to fix. You can place a capacitor of around 22uF between the legs of the reset switch or between EN and GND.

For a more in-depth explanation, you can refer to the following forum thread: [Wemos S2 Mini Wi-Fi connection reset issue](https://esp32.com/viewtopic.php?f=19&t=28506&start=10)
