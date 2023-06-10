During normal use, the tags sleeps most of the time. It wakes up every once in a while to check in with the Access Point to ask if there's any news. The time between check-ins is anywhere between 40 seconds and 10 minutes during normal use, or longer if the content is suitable for it (e.g. a date display that only changes once per day) and AP settings allow for it.

There are methods to wake the tag on request. For that, you have to modify the tag a bit. In the simplest form, you can add a push button between the 'TEST'-pin and ground, plus a capacitor of 100nF parallel to the switch contacts. The capacitor provides switch debouncing, and the tag firmware uses it to sense if a button switch is connected. You can find the TEST- and ground-pins at the debug connector at the back of the tag.

More interesting is to build the switch into the tag without using the debug connector, as soldering onto it prevents you from using a programming jig. 
One of the options is to build in a reed relay.

Needed: 10 x 1.8mm reed relay (the bigger ones are too wide), 100nF 0603 capacitor, steady hands, knife, loupe, flux, good soldering station.

<img src="hardware/IMG_1624.jpeg?v4" width="800">

Identify the TEST pin via, right under the processor

<img src="hardware/IMG_1625.jpeg" width="800">

Scratch the solder mask with a knife to expose the copper. Don't hit the components around it. Don't scratch away the copper.

<img src="hardware/IMG_1627.jpeg" width="800">

Use flux and tin the scratched via, and a bit of the far most text (=GND)

<img src="hardware/IMG_1628.jpeg" width="800">

Solder one side of the reed relay to GND, make sure to stay away more than 4mm from the side of the PCB. At the other end of the reed relay, scratch a bit of the solder mask and solder one side of the capacitor. The other side of the capacitor connects with the reed relay.

<img src="hardware/IMG_1629.jpeg" width="800">

Use a thin wire to connect the TEST pad to the reed relay.

<img src="hardware/IMG_1631.jpeg" width="800">

With a knife or pliers, remove a bit of plastic of the casing.

<img src="hardware/IMG_1632.jpeg?v5" width="800">

Ready! You can close the case (it just fits!). Now the tag wakes up and checks in if you hold a magnet in front of the screen.

