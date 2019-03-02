Python Cheatsheet
=================

<sup>[Fork this on GitHub](https://github.com/BisratYalew/python-cheatsheet)
</sup>


## About
I have created this cheatsheet with intention of collecting python code snippets that I used on my projects/programs and from the internet for reducing coding hours and making other developers life easier.




String
------


### strip()
```python
<str>  = <str>.strip()           # removes characters from both left and right based on the argument

<str>  = <str>.strip('<chars>')  # removes all passed characters from both ends.

```



### ord()
```python
>>> ord('A'), ord('Z')
(65, 90)
>>> ord('0'), ord('9')
(48, 57)
>>> ord('a'), ord('z')
(97, 122)
>>> ord('B'), ord('Y')
(66, 89)
```


#### The in and not in Operators with string
```python 
>>> 'Python' in 'Python is great!'
True
>>> 'python' in 'Python'
True
>>> 'PYTHON' in 'Python is great!'
False
>>> '' in 'python'
True
>>> 'Python' not in 'python and javascript' ## Matches case
False
```
