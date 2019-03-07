# Classes


- [Definition](#class-definition)
- [Class Objects](#class-objects)
- [Instance Objects](#instance-objects)
- [Method Objects](#method-objects)
- [Inheritance](#inheritance)
- [Multiple Inheritance](#multiple-inheritance)

<br><br>
### Class Definition
Python is an object oriented programming language.
Almost everything in Python is an object, with its properties and methods.
A Class is like an object constructor, or a "blueprint" for creating objects..

```python
def test_class():
    """Class definition."""

    # Class definitions, like function definitions (def statements) must be executed before they
    # have any effect. (You could conceivably place a class definition in a branch of an if
    # statement, or inside a function.)

    class GreetingClass:
        """Example of the class definition
        This class contains two public methods and doesn't contain constructor.
        """
        name = 'Bisrat'

        def say_hello(self):
            """Class method."""
            # The self parameter is a reference to the class itself, and is used to access variables
            # that belongs to the class. It does not have to be named self , you can call it
            # whatever you like, but it has to be the first parameter of any function in the class.
            return 'Hello ' + self.name

        def say_goodbye(self):
            """Class method."""
            return 'Goodbye ' + self.name

    # When a class definition is entered, a new namespace is created, and used as the local scope —
    # thus, all assignments to local variables go into this new namespace. In particular, function
    # definitions bind the name of the new function here.

    # Class instantiation uses function notation. Just pretend that the class object is a
    # parameterless function that returns a new instance of the class. For example the following
    # code will creates a new instance of the class and assigns this object to the local variable.
    greeter = GreetingClass()

    assert greeter.say_hello() == 'Hello Bisrat'
    assert greeter.say_goodbye() == 'Goodbye Bisrat'

>>> print(type(content))
<class 'str'>
```



<br><br>
### Class Objects
Python is an object oriented programming language.
Almost everything in Python is an object, with its properties and methods.
A Class is like an object constructor, or a "blueprint" for creating objects..

```python

def test_class_objects():
    """Class Objects.
    Class objects support two kinds of operations:
    - attribute references
    - instantiation.
    """

    # ATTRIBUTE REFERENCES use the standard syntax used for all attribute references in
    # Python: obj.name. Valid attribute names are all the names that were in the class’s namespace
    # when the class object was created. For class MyCounter the following references are valid
    # attribute references:

    class ComplexNumber:
        """Example of the complex numbers class"""

        real = 0
        imaginary = 0

        def get_real(self):
            """Return real part of complex number."""
            return self.real

        def get_imaginary(self):
            """Return imaginary part of complex number."""
            return self.imaginary

    assert ComplexNumber.real == 0

    # __doc__ is also a valid attribute, returning the docstring belonging to the class
    assert ComplexNumber.__doc__ == 'Example of the complex numbers class'

    # Class attributes can also be assigned to, so you can change the value of
    # ComplexNumber.counter by assignment.
    ComplexNumber.real = 10
    assert ComplexNumber.real == 10

    # CLASS INSTANTIATION uses function notation. Just pretend that the class object is a
    # parameterless function that returns a new instance of the class. For example
    # (assuming the above class):
    complex_number = ComplexNumber()

    assert complex_number.real == 10
    assert complex_number.get_real() == 10

    # Let's change counter default value back.
    ComplexNumber.real = 10
    assert ComplexNumber.real == 10

    # The instantiation operation (“calling” a class object) creates an empty object. Many classes
    # like to create objects with instances customized to a specific initial state. Therefore a
    # class may define a special method named __init__(), like this:

    class ComplexNumberWithConstructor:
        """Example of the class with constructor"""
        def __init__(self, real_part, imaginary_part):
            self.real = real_part
            self.imaginary = imaginary_part

        def get_real(self):
            """Return real part of complex number."""
            return self.real

        def get_imaginary(self):
            """Return imaginary part of complex number."""
            return self.imaginary

    complex_number = ComplexNumberWithConstructor(3.0, -4.5)
    assert complex_number.real, complex_number.imaginary == (3.0, -4.5)
```





<br><br>
### Instance Object

```python
def test_instance_objects():
    # DATA ATTRIBUTES need not be declared; like local variables, they spring into existence when
    # they are first assigned to. For example, if x is the instance of MyCounter created above,
    # the following piece of code will print the value 16, without leaving a trace.

    # pylint: disable=too-few-public-methods
    class DummyClass:
        pass

    dummy_instance = DummyClass()

    # pylint: disable=attribute-defined-outside-init
    dummy_instance.temporary_attribute = 1
    assert dummy_instance.temporary_attribute == 1
    del dummy_instance.temporary_attribute
```

<br><br>
### Method Objects

```python
class MyCounter:
    """A simple example of the counter class"""
    counter = 10

    def get_counter(self):
        """Return the counter"""
        return self.counter

    def increment_counter(self):
        """Increment the counter"""
        self.counter += 1
        return self.counter


def test_method_objects():
    """Method Objects."""

  
    # object types can have methods as well. For example, list objects have methods called append,
    
    counter = MyCounter()
    assert counter.get_counter() == 10

    get_counter = counter.get_counter
    assert get_counter() == 10

  

    assert counter.get_counter() == 10
    assert MyCounter.get_counter(counter) == 10
```


<br><br>
### Inheritance
```python
# pylint: disable=too-few-public-methods
class Person:
    """Example of the base class"""
    def __init__(self, name):
        self.name = name

    def get_name(self):
        """Get person name"""
        return self.name


# The syntax for a derived class definition looks like this.
class Employee(Person):
    
    def __init__(self, name, staff_id):
        Person.__init__(self, name)
        # You may also use super() here in order to avoid explicit using of parent class name:
        # >>> super().__init__(name)
        self.staff_id = staff_id

    def get_full_id(self):
        """Get full employee id"""
        return self.get_name() + ', ' + self.staff_id


def test_inheritance():
    """Inheritance."""

    # There’s nothing special about instantiation of derived classes: DerivedClassName() creates a
    # new instance of the class. Method references are resolved as follows: the corresponding class
    # attribute is searched, descending down the chain of base classes if necessary, and the method
    # reference is valid if this yields a function object.
    person = Person('Bisrat')
    employee = Employee('John', 'A23')

    assert person.get_name() == 'Bisrat'
    assert employee.get_name() == 'John'
    assert employee.get_full_id() == 'John, A23'

    # Python has two built-in functions that work with inheritance:
    #
    # - Use isinstance() to check an instance’s type: isinstance(obj, int) will be True only if
    # obj.__class__ is int or some class derived from int.
    #
    # - Use issubclass() to check class inheritance: issubclass(bool, int) is True since bool is
    # a subclass of int. However, issubclass(float, int) is False since float is not a subclass
    # of int.

    assert isinstance(employee, Employee)
    assert not isinstance(person, Employee)

    assert isinstance(person, Person)
    assert isinstance(employee, Person)

    assert issubclass(Employee, Person)
    assert not issubclass(Person, Employee)
```



<br><br>
### Multiple Inheritance
```python

```