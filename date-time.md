# Date and Time

- [DateTime](#datetime)
- [Time Delta](#time-delta)
- [Calendar](#calendar)

<br><br>
### datetime
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

### Time Delta
This module is used to perform date and time calculations. 
```Python
from datetime import date 
from datetime import time
from datetime import datetime
from datetime import timedelta

print(timedelta(days=365, hours=5, minutes=1)) # 365 days, 5:01:00
today  = datetime.now()
print(today + timedelta(days=60)) # 2019-03-29 18:41:46.720811
print(today - timedelta(days=57)) # 2018-12-02 18:42:36.774421
```
**timedelta** object takes the following parameters: days, seconds, microseconds, milliseconds, minutes, hours, weeks. 
To find past or future dates, simply use plus or minus sign with the required difference from current date.

### Calendar
Calendar related operations and displaying in formatted way.
```Python
import calendar

c = calendar.TextCalendar(calendar.MONDAY)
st = c.formatmonth(2017, 1, 0,0)
print(st)

hc = calendar.HTMLCalendar(calendar.MONDAY)
st = hc.formatmonth(2017, 1)
print(st)

#Output
'''
    January 2017
Mo Tu We Th Fr Sa Su
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29
30 31

<table border="0" cellpadding="0" cellspacing="0" class="month">
<tr><th colspan="7" class="month">January 2017</th></tr>
<tr><th class="mon">Mon</th><th class="tue">Tue</th><th class="wed">Wed</th><th class="thu">Thu</th><th class="fri">Fri</th><th class="sat">Sat</th><th class="sun">Sun</th></tr>
<tr><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="sun">1</td></tr>
<tr><td class="mon">2</td><td class="tue">3</td><td class="wed">4</td><td class="thu">5</td><td class="fri">6</td><td class="sat">7</td><td class="sun">8</td></tr>
<tr><td class="mon">9</td><td class="tue">10</td><td class="wed">11</td><td class="thu">12</td><td class="fri">13</td><td class="sat">14</td><td class="sun">15</td></tr>
<tr><td class="mon">16</td><td class="tue">17</td><td class="wed">18</td><td class="thu">19</td><td class="fri">20</td><td class="sat">21</td><td class="sun">22</td></tr>
<tr><td class="mon">23</td><td class="tue">24</td><td class="wed">25</td><td class="thu">26</td><td class="fri">27</td><td class="sat">28</td><td class="sun">29</td></tr>
<tr><td class="mon">30</td><td class="tue">31</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td></tr>
</table>
'''
```
```.HTMLCalendar``` return HTML code for the calendar in table format. ```Calendar.SUNDAY``` indicates that the first day 
in the formatted calendar will be Sunday. In the above example, ```Calendar.MONDAY``` is used. Hence, we can see in the output that the first day in the representation is Monday.
#### Iterating through dates of a month
```Python
import calendar

c = calendar.TextCalendar(calendar.MONDAY)
for i in c.itermonthdays(2017, 8):
    print(i, end = ' ')
print('')
for name in calendar.month_name:
    print(name, end = ' ')
print('')
for day in calendar.day_name:
    print(day, end = ' ')
'''
Output:
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 0 0 0
 January February March April May June July August September October November December
Monday Tuesday Wednesday Thursday Friday Saturday Sunday
'''
```

### [Back To Top](#date-and-time)