## 0026 - Universal FW
- Incorporates Jonas' changes for LED control
- Fixed 4.3" shutdown routine
- All M3 tags should now be able to use the same binary file
- Tag type, EPD type is determined in the 'customer' UICR data as set in factory

HOWEVER:
We haven't checked all types! I have been trying to determine how the tag finds out what kind of controller the EPD uses, and I may have gotten it all wrong! I -highly- suggest only updating tags one-at-a-time, and only if you want to try the new features.

If you want to help, dump the UICR from a tag, and let me know what type of tag is is/controller it uses.

## 0025 - LED control ##
-this firmware finally allows proper led control. This requires an AP update

## 0024 - Feature parity ##
This version more or less brings the M3 tags to the feature level of the M2 tags!
- Slideshows are now working
- Preloaded images for buttons / splashscreens are implemented
- 'Battery' and 'No-RF' overlay are now correctly placed on the screen
- UC-based 2.9" tags are now supported
- Settings now working
- Code cleanup
- FW-version is now shown in the webinterface (shown as "fw: 36")

Errata: FW still uses GPIOTE for buttons/NFC events. GPIOTE consumes quite a bit more power than should be needed. Turning it off certainly helps, and optimizes power consumption by about 50%, but buttons won't work. GPIOTE is turned off for the 4.3" tags, as they don't have any buttons
