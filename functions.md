# Python Functions



- [Lambda](#lambda)
- [Declare Function](#lambda)
- [Document Function](#document-function)
- [Get Function Name](#get-function-name)
- [Arguments](#lambda)
- [Decorator](#lambda)
- [Generator](#lambda)
- [Annotation](#lambda)


<br><br>
### Lambda

```python
>>> fn = lambda x: x**3
>>> fn(2)
8

>>> (lambda x: x**3)(2)
9

>>> (lambda x: [x * _ for _ in range(10)])(3)
[0, 3, 6, 9, 12, 15, 18, 21, 24, 27]
```