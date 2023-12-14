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