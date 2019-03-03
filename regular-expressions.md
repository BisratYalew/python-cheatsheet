
# Regular Expressions
Non-special chars match themselves. Exceptions are special characters:

```
\       Escape special char or start a sequence.
```

```
.       Match any char except newline, see re.DOTALL
```
```
^       Match start of the string, see 
re.MULTILINE
```
```
$       Match end of the string, see re.MULTILINE
```
```
[]      Enclose a set of matchable chars
```
```
R|S     Match either regex R or regex S.
```
```
()      Create capture group, & indicate precedence
After '[', enclose a set, the only special chars are:
```
```
]   End the set, if not the first char
```
```
-   A range, eg. a-c matches a, b or c
```
```
^   Negate the set only if it is the 1st char
```
## Regular Expression Examples
### re.findall()
```python
# split all string from a sentence
>>> import re
>>> source = "Python is great!"
>>> re.findall('[\w]+', source)
['Python', 'is', 'great!']
```

### Match hex color value
```python 
>>> re.match('^#?([a-f0-9]{6}|[a-f0-9]{3})$', '#ffffff')
<_sre.SRE_Match object at 0x0000000002F04120>
>>> re.match('^#?([a-f0-9]{6}|[a-f0-9]{3})$', '#cdcdcd')
<_sre.SRE_Match object at 0x0000000002EA3160>
```


### Match username doesn't have any special characters
```python
>>> re.match('^[a-zA-Z0-9-_]{3,16}$', 'Check') is not None
True
>>> re.match('^\w|[-_]{3,16}$', 'che%ck') is not None
False
```


### Match email address format
```python
re.match('^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$',
...          'check@example.com')
<_sre.SRE_Match object at 0x0000000002EA3180>
```