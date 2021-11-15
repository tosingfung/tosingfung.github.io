---
layout: post
tag: python-learn
title: "datetime"
---

- datetime.date(y,m,d)
- datetime.date.today()
- datetime.time(H,M,S)
- datetime.datetime.(y,m,d,H,M,S)
- datetime.datetime.now()
- datetime.datetime.utcnow()
- datetime.timedelta(days=?)
- dateutil.tz.gettz()

<!--more-->

## datetime.date(y,m,d)


```python
from datetime import date
# date.today()
bday = date(1981,9,5)
print (f"""
%Y: {bday:%Y}
%y: {bday:%y}
--------------------
%m: {bday:%m}
%B: {bday:%B}
%b: {bday:%b}
--------------------
%d: {bday:%d}
--------------------
%A: {bday:%A}
%a: {bday:%a}
""")
```

    %Y: 1981
    %y: 81
    --------------------
    %m: 09
    %B: September
    %b: Sep
    --------------------
    %d: 05
    --------------------
    %A: Saturday
    %a: Sat

## datetime.time(H,M,S)


```python
from datetime import time
teatime = time(15,25,35)
print (f"""
%H-%M-%S: {teatime:%H-%M-%S}
%I:%M %p: {teatime:%I:%M %p}
""")
```

    %H-%M-%S: 15-25-35
    %I:%M %p: 03:25 PM

## datetime.datetime(y,m,d,H,M,S)


```python
from datetime import datetime
# datetime.now()
bomb = datetime(2080,1,1,0,0,0)
print (bomb)
```

    2080-01-01 00:00:00


## datetime.datetime.now()


```python
from datetime import datetime
bomb = datetime(2080,1,1,0,0,0)
tick = bomb - datetime.now()
print (tick)
print (tick.days)
print (tick.days // 365)
```

    21383 days, 9:23:22.116035
    21383
    58


## datetime.timedelta()


```python
import datetime
now  = datetime.datetime.now()
span = datetime.timedelta(
    weeks=1,
    days=2,
    hours=3,
    minutes=4,
    seconds=5)
# timedelta is under datetime
# DO NOT: datetime.datetime.timedelta

print (now + span)
```

    2021-06-24 17:43:40.082602


## datetime.datetime.utcnow()


```python
from datetime import datetime
now    = datetime.now()
utcnow = datetime.utcnow()
print (now - utcnow)
```

    8:00:00


## dateutil.tz.gettz()


```python
from datetime import datetime
from dateutil.tz import gettz

now = datetime.now()
print (now)
print (now.astimezone(gettz("Europe/London")))
print (now.astimezone(gettz("America/Toronto")))
```

    2021-06-15 14:43:22.346340
    2021-06-15 07:43:22.346340+01:00
    2021-06-15 02:43:22.346340-04:00

