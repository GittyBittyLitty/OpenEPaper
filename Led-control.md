The led of NRF based tags can be controlled by sending a command with the id 3 to the tag.

The led is controlled by the extended command data(12 Bytes)

The first Byte is split into two parts:

the first 4 bits will describe the mode of the led control. The interpretation of the following bytes changes per mode.

the second 4 bits are the duration of the led flashes in millisecond where 0 is mapped to half a ms and 15 is mapped to no off time. 15 WILL RUIN YOUR BATTERY LIFE. Everything higher than 3ms has a diminishing effect to visibility and 2ms is recommended as the bes compromise between power consumption and visibility.

## MODE 0 advanced sequence control 

`0220530A20530A20530A0A00`

meaning:

`0-----------------------` mode: 0

`-2----------------------` flash duration (ms; see above)

`--20--------------------` group 1: color in rgb 332 (rrrgggbb)

`----5-------------------` group 1: amount of flashes

`-----3------------------` group 1: flash speed (x10 ms)

`------0A----------------` group 1: delay after this flash group (seconds)

`--------20--------------` group 2: color in rgb 332 (rrrgggbb)

`----------5-------------` group 2: amount of flashes

`-----------3------------` group 2: flash speed (x10 ms)

`------------0A----------` group 2: delay after this flash group (seconds)

`--------------20--------` group 3: color in rgb 332 (rrrgggbb)

`----------------5-------` group 3: amount of flashes

`-----------------3------` group 3: flash speed (x10 ms)

`------------------0A----` group 3: delay after this flash group (seconds)

`--------------------0A--` repeats: how often to repeat sequence of group 1..3

`----------------------00` spare, always 00




## MODE 1 - 15 are reserved for future use and are used for off at the moment