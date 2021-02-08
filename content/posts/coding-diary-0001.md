---
title: "Coding Diary 1: Understanding time zones and Python datetime's timezone"
date: 2021-01-30T21:24:30-08:00
draft: false
---

After a decade of surviving without understanding time zone properly, I've managed to learn about the topic today. I also learnt how to use Python datetime with timezone information.

I had always thought that time zones were something like UTC+7. Turned out it was wrong. It's a time offset, and time offsets are different from time zones.

A time offset is a number of hours before or after UTC. In some case an offset can be a number of hours and minutes. Examples of offsets are UTC-0500, UTC+0600, etc. With your time zone's offset, you can translate between UTC time and your time. Let's say you're living in Seattle summer, your offset will be UTC-0700. That means at UTC 00:00, you're still in the previous day at 17:00. When you're at 00:00, the UTC time is 07:00.

A time zone is a region on Eeath where every one shares a same clock. A time zone contains a location-related name or an identifier, and usually one offset. In some case a time zone can contain multiple offsets. I call those "umbrella" time zones, as they contain multiple time zones. Pacific time zone is such an "umbrella" one. It contains PDT and PST. Examples of time zones are "Central Standard Time", "Pacific Daylight Time", etc.

The West like complicating things so they change their time zone every 6 months.

There are a couple of time zone databases. The standard one, that is implemented in Linux, Mac, and most programming languages, is IANA/Olso Time Zone Database, AKA the TZ database. Identifiers in this database is super familiar, such as "America/Los_Angeles". The other database is a Microsoft one and I've decided to ignore it for now.

## Python datetime
The Python datetime class, `from datetime import datetime`, can be either 'naive' or timezone-aware. By default, `datetime` objects are naive, as they don't contain any timezone information. We can make it aware of time zones by setting non-null `tzinfo` attribute to the objects. `pytz` is a common implementation of `tzinfo`.

Following code shows that, by default, `datetime` objects are "naive":
```
>>> from datetime import datetime
>>> now = datetime.now()
>>> print(now)
2021-01-30 21:58:20.419069
>>> print(now.tzinfo)
None
```

We can make it timezone-aware:
```
>>> now_with_tz = datetime.now(tz=pytz.timezone('America/New_York'))
>>> print(now.hour, now_with_tz.hour)
21 1
>>> now_with_tz.tzinfo
<DstTzInfo 'America/New_York' EST-1 day, 19:00:00 STD>
```
