# Troubleshooting Usage

## Display Content of Tag not updating
### Situation
- The image gets updated at the AP, but doesn't show on the tag display
  - Image in AP is different from what is shown on tag display
- The tag is still connected to the AP and checks in
- The AP log shows the following lines
> 14:56:11 < 00000218C9073B10 reports xfer complete  
> 14:56:10 new image: /current/00000218C9073B10.pending  
> 14:56:10 Updating 00000218C9073B10  
> 14:56:09 Ok, done  
- Usually, there would be multiple such lines between `new image` and `xfer complete`:
> 15:10:20 < Block Request received for file /current/00000218A8743B13.pending block 1, len 640 checksum 33468  
> 15:10:19 < Block Request received for file /current/00000218A8743B13.pending block 0, len 4096 checksum 49644  

### Solution  
Try the following steps.
1. Reboot the tag via the AP
   - right click tag and choose `Reboot tag`
1. Configure the tag to show something different to get it going
   - example: current date
1. Perform an OTA firmware update of the tag from the AP
   - see [[Firmware Updates|Firmware-Updates]]


## Accidentally flashing AP Firmware onto Tag
### Situation
- Accidentally the AP firmware (`AP_FW_xx.yy.bin`) was flashed onto a tag via OTA
- The tag display shows `AP Mode`

### Solution
- Unfortunately, the only way to get a tag firmware (`Tag_FW_xx.yy.bin`) onto the tag is flashing via the tag contacts
  - The required jig depends on the tag
  - More information on [Tag Flasher](https://github.com/jjwbruijn/OpenEPaperLink/tree/master/Tag_Flasher)

## Tag is not working after Battery Change
### Situation
- Batteries of a tag were replaced, but tag is not starting (e.g. showing the previous display content)
- Even shorting the battery contacts won't help

### Solution
- Try to insert the batteries all in one
  - see [Getting started - Battery insert](https://github.com/jjwbruijn/OpenEPaperLink/blob/master/Hardware/OpenEPaperLink%20Mini%20AP/Getting%20Started.md#adding-tags)
  - at 12:25 min of [ESP32 controlled E-Paper price tags The OpenEPaperLink startup guide](https://youtu.be/Etonkolz9Bs?si=11eEj-10Ghm8n1p5&t=743)

## Custom Access Point Name for Wifi
### Situation
- OpenEPaperLink AP lists itself on the wifi as "OpenEPaperLink-xyz".
- Plan is to have a custom name for it.

### Solution
- Navigate to the AP settings (gear icon)
- Change `Alias` unter _Access Point config_ to desired name e.g., `epaperap` (shorter)
- Reboot AP
