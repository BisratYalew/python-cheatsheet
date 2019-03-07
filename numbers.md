# Numbers

There are three numeric types in Python:
- int (e.g. 2, 4, 20)
    - bool (e.g. False and True, acting like 0 and 1)
- float (e.g. 5.0, 1.6)
- complex (e.g. 5+6j, 4-3j)



### Basic Functions
```python
a = pow(2, 3) ## Or: 2 ** 3
b = abs(5) ## <real> = abs(<num>)
```

### Constants
```python
from math import e, pi
```

### Trigonometry
```python
from math import cos, acos, sin, asin, tan, atan, degrees, radians
```

### Logarithm
```python
from math import log, log10, log2
<float> = log(<real> [, base])  # Base e, if not specified.
```

### Infinity, nan
```python
from math import inf, nan, isinf, isnan
```

#### Or:
```python
float('inf'), float('nan')
```

### Statistics
```python
from statistics import mean, median, variance, pvariance, pstdev
```

### Random
```python
from random import random, randint, choice, shuffle
<float> = random()
<int>   = randint(from_inclusive, to_inclusive)
<el>    = choice(<list>)
shuffle(<list>)
```


Combinatorics
-------------
* **Every function returns an iterator.**
* **If you want to print the iterator, you need to pass it to the list() function!**

```python
from itertools import product, combinations, combinations_with_replacement, permutations
```

```python
>>> product([0, 1], repeat=3)
[(0, 0, 0), (0, 0, 1), (0, 1, 0), (0, 1, 1), 
 (1, 0, 0), (1, 0, 1), (1, 1, 0), (1, 1, 1)]

>>> product('ab', '12')
[('a', '1'), ('a', '2'),
 ('b', '1'), ('b', '2')]

>>> combinations('abc', 2)
[('a', 'b'), ('a', 'c'), ('b', 'c')]

>>> combinations_with_replacement('abc', 2)
[('a', 'a'), ('a', 'b'), ('a', 'c'), 
 ('b', 'b'), ('b', 'c'), 
 ('c', 'c')]

>>> permutations('abc', 2)
[('a', 'b'), ('a', 'c'), 
 ('b', 'a'), ('b', 'c'), 
 ('c', 'a'), ('c', 'b')]
```
```python
 """


def test_integer_numbers():
    """Integer type
    Int, or integer, is a whole number, positive or negative,
    without decimals, of unlimited length.
    """

    positive_integer = 1
    negative_integer = -3255522
    big_integer = 35656222554887711

    assert isinstance(positive_integer, int)
    assert isinstance(negative_integer, int)
    assert isinstance(big_integer, int)


def test_booleans():
    """Boolean
    Booleans represent the truth values False and True. The two objects representing the values
    False and True are the only Boolean objects. The Boolean type is a subtype of the integer type,
    and Boolean values behave like the values 0 and 1, respectively, in almost all contexts, the
    exception being that when converted to a string, the strings "False" or "True" are returned,
    respectively.
    """

    true_boolean = True
    false_boolean = False

    assert true_boolean
    assert not false_boolean

    assert isinstance(true_boolean, bool)
    assert isinstance(false_boolean, bool)

    # Let's try to cast boolean to string.
    assert str(true_boolean) == "True"
    assert str(false_boolean) == "False"


def test_float_numbers():
    """Float type
    Float, or "floating point number" is a number, positive or negative,
    containing one or more decimals.
    """

    float_number = 7.0
    # Another way of declaring float is using float() function.
    float_number_via_function = float(7)
    float_negative = -35.59

    assert float_number == float_number_via_function
    assert isinstance(float_number, float)
    assert isinstance(float_number_via_function, float)
    assert isinstance(float_negative, float)

    # Float can also be scientific numbers with an "e" to indicate
    # the power of 10.
    float_with_small_e = 35e3
    float_with_big_e = 12E4

    assert float_with_small_e == 35000
    assert float_with_big_e == 120000
    assert isinstance(12E4, float)
    assert isinstance(-87.7e100, float)


def test_complex_numbers():
    """Complex Type"""

    complex_number_1 = 5 + 6j
    complex_number_2 = 3 - 2j

    assert isinstance(complex_number_1, complex)
    assert isinstance(complex_number_2, complex)
    assert complex_number_1 * complex_number_2 == 27 + 8j


def test_number_operators():
    """Basic operations"""

    # Addition.
    assert 2 + 4 == 6

    # Multiplication.
    assert 2 * 4 == 8

    # Division always returns a floating point number.
    assert 12 / 3 == 4.0
    assert 12 / 5 == 2.4
    assert 17 / 3 == 5.666666666666667

    # Modulo operator returns the remainder of the division.
    assert 12 % 3 == 0
    assert 13 % 3 == 1

    # Floor division discards the fractional part.
    assert 17 // 3 == 5

    # Raising the number to specific power.
    assert 5 ** 2 == 25  # 5 squared
    assert 2 ** 7 == 128  # 2 to the power of 7

    # There is full support for floating point; operators with
    # mixed type operands convert the integer operand to floating point.
    assert 4 * 3.75 - 1 == 14.0

```