---
layout: post
tag: python-learn
title: "try except else finally"
---

- try: something
- except Error: show an error msg
- else: do something if no exceptions
- finally: do something anyway even if there are exceptions

<!--more-->

## try...except...else...finally


```python
try:
    fpath = "D:\sample.txt"
    f = open(fpath, "r")
    
except FileNotFoundError:
    print ("File not exist!")
    
except Exception as err:
    print (repr(err))
    # all other exceptions
    
else:
    print (f.readlines())
    # run when no exceptions encounter
    
finally:
    print ("Goal!")
    # exception or not, run anyway
```

    File not exist!
    Goal!


## Custom exception


```python
class ValueBigError(Exception):
    pass
# create a custom exception

try:
    value = int(input("Integer from 1-10: "))
    if(int(value)>10):
        raise ValueBigError("Input is too big!")
        
except ValueError as err:
    print(repr(err))
    
except ValueBigError as err:
    print(repr(err))
    
else:
    print (f"You input {value}")
```

    Integer from 1-10: 30
    ValueBigError('Input is too big!')

