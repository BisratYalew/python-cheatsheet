# Classes


- [Definition](#class-definition)
- [Class Objects](#class-objects)
- [Instance Objects](#instance-objects)
- [Method Object](#move-a-file)
- [Class and Instance Variables](#readline)
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