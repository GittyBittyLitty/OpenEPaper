The led of NRF based tags can be controlled by sending a command with the id 3 to the tag.

The led is controlled by the extended command data(12 Bytes)

The first Byte is split into two parts:

the first 4 bits will describe the mode of the led control. The interpretation of the following bytes changes per mode.

the second 4 bytes are the duration of the led flashes in millisecond where 0 is mapped to half a ms and 15 is mapped to no off time. 15 WILL RUIN YOUR BATTERY LIFE. Everything higher than 3ms has a diminishing effect to visibility and 2ms is recommended as the bes compromise between power consumption and visibility.

## MODE 0 advanced sequence control 

start of sequence 1

        uint8_t interloopdelayfactor = 100;
        u_int8_t loopdelayfactor = 100;
        
        uint8_t c1 = ledcfg[1];
        uint8_t c2 = ledcfg[4];
        uint8_t c3 = ledcfg[7];
        uint8_t loopcnt1 = (ledcfg[2] >> 4) & 0b00001111;
        uint8_t loopcnt2 = (ledcfg[5] >> 4) & 0b00001111;
        uint8_t loopcnt3 = (ledcfg[8] >> 4) & 0b00001111;
        uint8_t loop1delay = ledcfg[2] & 0b00001111;
        uint8_t loop2delay = ledcfg[5] & 0b00001111;
        uint8_t loop3delay = ledcfg[8] & 0b00001111;
        uint8_t ildelay1 = ledcfg[3];
        uint8_t ildelay2 = ledcfg[6];
        uint8_t ildelay3 = ledcfg[9];
        uint8_t grouprepeats = ledcfg[11];

## MODE 1 - 15 are reserved for future use and are used for off at the moment