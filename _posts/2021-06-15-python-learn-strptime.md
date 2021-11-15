---
layout: post
tag: python-learn
title: "convert str to datetime object"
---

- datetime.datetime.strptime()

<!--more-->

## String to datetime object


```python
from datetime import datetime
bday = "04:30:00 Thursday July 9, 1987"
dt_bday = datetime.strptime(bday, "%H:%M:%S %A %B %d, %Y")
print (dt_bday)
```

    1987-07-09 04:30:00


## split a long fstring code


```python
a = "s-1"
b = "s-2"
c = "s-3"

string = f"""
| {a:4}\
| {b:4}\
| {c:4}\
|"""

print (string)
```


    | s-1 | s-2 | s-3 |

