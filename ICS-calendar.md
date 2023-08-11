There is a tiny rust program which "proxies" .ics file URLs into a JSON format: https://github.com/jhbruhn/ics-adapter

The usage is rather simple. It is recommended to run this as a Docker container. An example docker-compose configuration might look like this:

```yaml
version: "3"
services:
    calendar:
        image: ghcr.io/jhbruhn/ics-adapter:main
        ports:
            - "3000:3000"
        restart: unless-stopped
```

As you can see, you only have to forward port 3000 to wherever you like, in this case port 3000.
The URL you have to enter into the OEPL Google Calendar config then looks like this:
```
http://<docker-host>:3000/get?url=<ics-url>
```

With an actual .ics url, it looks like this:
```
http://192.168.178.42:3000/get?url=https://nextcloud.net/remote.php/dav/public-calendars/whateveryolo901i230ji
```

This URL then has to be entered into a `Google Calendar` URL field in the OEPL firmware.
