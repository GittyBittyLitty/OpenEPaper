# THIS IS STILL WIP AND THE API IS NOT STABLE MAY NOT EVEN BE IMPLEMENTED

The led of NRF based tags can be controlled by sending a command with the id 100 to the tag.

The led is controlled by the extended command data(12 Bytes)

The first Byte is split into two parts:

the first 4 bits will describe the mode of the led control. The interpretation of the following bytes changes per mode.

the second 4 bytes are the duration of the led flashes in millisecond where 0 is mapped to half a ms and 15 is mapped to no off time. 15 WILL RUIN YOUR BATTERY LIFE. Everything higher than 3ms has a diminishing effect to visibility and 2ms is recommended as the bes compromise between power consumption and visibility.

## MODE 0 OFF

## MODE 1 normal flashing
Byte 1 RGB 332 color data
Byte 2 - 5 Time between flashes in ms 

## MODE 2 advanced sequence control 

start of sequence 1
Byte 1 bit 0 Red channel
Byte 1 bit 1 Green channel
Byte 1 bit 2 Blue channel
Byte 1 bit 3 - 7 time in ms between flashes with a tbd multiplier
Byte 2 bit 0 - 3 number of repetitions plus 1
end of sequence 1 
start of sequence 2
Byte 2 bit 4 Red channel
....
end of sequence 7

Byte 11 bit 4 - 7 delay between restart of the sequence in ms times tbd multiplier, 0 for no repeats 

## MODE 2 - 15 are reserved for future use