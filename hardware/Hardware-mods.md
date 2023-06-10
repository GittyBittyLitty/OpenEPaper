During normal use, the tags sleeps most of the time. It wakes up every once in a while to check in with the Access Point to ask if there's any news. The time between check-ins is anywhere between 40 seconds and 10 minutes during normal use, or longer if the content is suitable for it (e.g. a date display that only changes once per day) and AP settings allow for it.

There are methods to wake the tag on request. For that, you have to modify the tag a bit. In the simplest form, you can add a push button between the 'TEST'-pin and ground, plus a capacitor of 100nF parallel to the switch contacts. The capacitor provides switch debouncing, and the tag firmware uses it to sense if a button switch is connected. You can find the TEST- and ground-pins at the debug connector at the back of the tag.

More interesting is to build the switch into the tag without using the debug connector, as soldering onto it prevents you from using a programming jig. 

<img src="hardware/IMG_1624.jpeg">
