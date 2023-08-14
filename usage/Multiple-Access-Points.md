Access Points within the same WiFi network automatically discover each other through UDP multicast and synchronize all tag information. For each tag, there is one AP (of your choice) that generates the content, but the tag receiving the content can be connected to a different AP elsewhere. This allows you to place a few APs in your house to extend the coverage while managing all tags and content from a single AP.

Give it a try!

![Multi AP screenshot](usage/multiap.jpg)

Some notes:

- If you have multiple access points, make sure every access point runs on a different channel. If multiple access points are on the same channel, they start fighting over ownership of a tag
- If a tag starts, it scans all possible channels for active access points. It chooses the one with the stongest signal, and sticks to it. Only if it cannot reach the access point after multiple tries (think hours, not seconds, as the tag checks in only once per 40 seconds anyway), it scans the network again to switch to a different access point.
- Of course you keep your access points updated with the latest firmware ;-) . But for the multiple AP feature, it's not strictly neccesairy. If the protocol might have a breaking change in the future, it will just stop exchanging some info.
- For every tag, you can choose any accesspoint to generate the content on. You can mix and match to your taste, although, if possible, it's probably most convenient to have one accesspoint act like a central place to render the images. For example, an access point that just has some tags connected and is not actively generating content, doesn't need all the fonts. Although the tag definition in /tagtypes should be in place for all access points that have either connected tags, or generating content.
