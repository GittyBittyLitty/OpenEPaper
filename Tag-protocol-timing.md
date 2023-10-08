Main priority when designing the protocol between the tags and the access point, was to be as efficient with battery usage was possible. Both listening and sending information is very resource intensive for the tag, so, it does that as little as possible. The tags spends most of the time sleeping. 

In short, the protocol works as follows: Once every 40 seconds, the tag sends a very short message to the AP (the 'checkin'), to let it know that it is still alive. The tag listens about 5(!) milliseconds if it gets a reply from the AP. Within that time, the AP lets the tag know if it has new information or not. If the AP has new information, the tag initiates a request for the information (most of the time, a new image to display), and the AP sends that data.

There is no way for the Access Point to communicate with the tag at any other time than during a checkin, as the tag is sleeping between checkins (except when the tag is actively asking for e.g. a new image to display).

Now, two things can happen: First, if the signal is very weak, it will drain the battery of the tag more. In that case, to keep the same average current use, it will slowly prolong the time between checkins, to a maximum of 10 minutes. So, if the reception is bad, checkins happen less often. If the reception gets better again, the checkin interval slowly improves to 40 seconds again.

Second, if the tag doesn't get any reply of the access point (because it is out of reach, or the access point is turned off), the tag slowly gives up to save battery. After about 14 attempts without reply, the tag will only try to checkin again once an hour, for a day. The next day, once every two hours. And from the day after, it only checks in once per day. All to save energy. Remember, the tag is unreachable between the checkins, so if you turned off your access point for a while, it will take one hour, two hours, or even a day, before the tag and the AP find eachother again if you start the AP again. After that, eventually the tag will check in every 40 seconds again.

You can see the checkins in the webinterface: at 'last seen' is will display the time since the last checkin, and at a checkin, the tag card on the website flashes briefly.

To save extra battery, in the AP settings, you can set the 'Maximum sleep'. If for example the maximum sleep is set to 1 hour, and you display the current date on a tag, the tag is set to sleep for one hour (or until midnight, whatever is shorter). During that hour, the tag is unreachable (as the date will not change). The actual sleep time is dependant on the settings of the selected content type.

So because of the restrictions on battery usage, it's not possible to make the tag react in real time. Most of the time, the delay will be about 40-60 seconds. 
