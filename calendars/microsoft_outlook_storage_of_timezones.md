# Microsoft Outlook storage of timezones in ICS files

Outlook uses [windows timezones](https://techsupport.osisoft.com/Documentation/PI-Web-API/help/topics/timezones/windows.html) when exporting calendar in ICS format. Meanwhile the rest of the world and libraries use the [IANA time zone database](https://www.iana.org/time-zones).

*Windows timezone:*

```
DTSTART;TZID=Eastern Standard Time:20200424T090000
DTEND;TZID=Eastern Standard Time:20200503T21000
```

*IANA timezone:*

```
DTSTART;TZID=America/New_York:20200424T090000
DTEND;TZID=America/New_York:20200503T21000
```

# Sources

* [Conversion from Windows to IANA time zone names](https://gist.github.com/jonmaim/846a03cda56e35a030fdf6f99b4b1820) 
