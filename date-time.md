# Data and Time

```python
from datetime import date 
from datetime import time
from datetime import datetime

>>> today = date.today()
>>> print(today)
2019-03-04

>>> print(today.day, today.month, today.year)
(4, 3, 2019)

>>> print(today.weekday()) ## returns an integers in the range 0 to 6, where 0 represents Monday and 6 represents Sunday.
0

>>> today = datetime.now()
>>> print(today)
2019-03-04 21:55:56.228000

>>> time = datetime.time(datetime.now())
>>> print(time) 
21:56:16.040000

```