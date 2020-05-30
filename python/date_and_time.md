# Date and time

A universal approach to deal with date and time between computers is to use Unix timestamps. 
A Unix timestamp is a positive integer value representing the number of milliseconds since Jan 1st 00:00:00:000 UTC time. 
There is no confusion while transmitting dates and no need to define time zones.
Moreover it's easy to apply arithmetic operations between 2 timestamps to add or subtract a duration. 

## Get current Unix timestamp in ms

```python
from datetime import datetime

def now():
  return datetime.now().timestamp() * 1000

t = now()
```

## From local date to Unix timestamp

```python
from datetime import datetime

local_date = datetime(year=2015, month=1, day=1, hour=0)
t = local_date.timestamp() * 1000
```

## From Unix timestamp to local time

```python
from datetime import datetime

def now():
  return datetime.utcnow().timestamp() * 1000

local_date = datetime.utcfromtimestamp(now() / 1000)
```
