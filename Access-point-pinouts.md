In this table, you will find the pinouts for connecting an access point, for the different build environments.

| name | Simple AP | Mini AP v2 | Nano AP | Yellow AP / Mini AP v3 | AP and flasher | ESP32-C6 |
| ---- | --------- | ------- | ------- | --------- | -------------- | ---------|
| mcu | esp32 | esp32-s2 | esp32-s2 | esp32-s3 | esp32-s3 | |
| SS   | 5  | 11 | 38 | - | 4 | - |
| CLK  | 18 | 9  | 40 | - | 5 | - |
| MOSI | 23 | 10 | 39 | - | 7 | - |
| MISO | 19 | 8 | 33 | - | 6 | - |
| RESET| 2  | 13 | 37 | 47 | 15 | EN |
| POWER| 13+15 | 3V3 | 16+17+18+21 | -| 0 | - |
| TEST | -  | 12 | 36 | - | 17 | - |
| TXD  | 17 | 7 | 35 | 17 | 16 | 2 |
| RXD  | 16 | 6 | 34 | 18 | 18 | 3 |
| led  | 22 | 15 | 15 | 16 | 21 | 22, 23 |
| neopixel | - | 33 | - | 48 | 48 | - |
| debug-txd | -| -  | - | 19 | - | 16 |
| debug-rxd | -| -  | - | 20 | - | 17 |
| debug-prog | -| -  | - | 21 | - | 9 |
| TFT MOSI | - | - | - | 13 | - | - |
| TFT SCLK | - | - | - | 12 | - | - |
| TFT CS | - | - | - | 10 | - | - |
| TFT DC | - | - | - | 11 | - | - |
| TFT RST | - | - | - | 1 | - | - |
| GND | GND | GND | GND | GND | GND | GND |

Pins in the list for the esp32-c6 are to be connected to the corresponding pins on the Yellow AP, except for the led pins which are off course seperate.
For the other environments, the listed pins are te be connected to the corresponding pins on a ZBS-based tag.