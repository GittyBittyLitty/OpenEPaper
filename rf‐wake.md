## rf wake

The M2 tags have an RF-wake feature that uses a burst on 2.4ghz to wake the tag up. Can be used to force a check-in to the AP when the tag is sleeping. However:
1. It consumes energy to keep it enabled (not an awful lot, but not it's not free)
2. The range is incredibly short. Think a couple of centimeters, tops. You have to bring a transmitter pretty close to the wake antenna and blast an unmodulated 2.4ghz signal

The RF-wake is basically a tuned length of pcb trace on a glorified GPIO-pin, it's more inductive coupling than anything else.

To build this, you will need an esp32 + nRF24L01 module.

```
#include <Arduino.h>
#include <SPI.h>

#include "RF24.h"
#include "printf.h"

RF24 radio(2, 4);

void setup() {
    Serial.begin(115200);
    if (!radio.begin()) {
        Serial.println(F("radio hardware is not responding!!"));
        while (1) {
        }
    }
    radio.setPALevel(RF24_PA_MAX);
    radio.setChannel(52);
}

void loop() {
    Serial.println("doing tx!");
    radio.begin();

    for (uint8_t c = 0; c < 20; c++) {
        radio.startConstCarrier(RF24_PA_MAX, 1);
        delay(10);
        radio.stopConstCarrier();
        delay(10);
    }

    Serial.println("done");
    while (1) {
        yield();
        delay(10);
    }
}
```