# Pytest for like testing idk

## What is it and why do I need it?

- It´s a testing framework for Unit Testing mostly, and in conjunction with other tech it can be used for [UI Testing](./Selenium_UI_testing.md)
- Pytest is a mature testing framework that lets us make unit test, integration test and all sort of tests
- This is achieved by the simple syntax it has making it easy to write test with fixtures, assertion, mocking, etc.
- It has easy integration capibilites, so you can stick it with other frameworks like django, flask, selenium, pygame, etc.
- The integration capabilites give it a miriad of extensibility with plugins, hooks and additions with other testing frameworks

### How does it works?

- In pytest there are two steps
  - **Test collection time:**
    - Here pytest just reads anything living in the test directory or anything test related to have a collection of what to do with it
  - **Test exectuion time:**
    - Pytest executes everything it collected

## The Framework itself

- **Assertions**
  - It will be our main tool for making sure a condition its fulfilled in a testing block
  - If it ain't fulfilled it just raises an ``AssertionError``

### Testing functions

- To work with it
  - We need something already built in python
    - Like a function, classes or whatever bro
  - Depending on what we are doing we would have to implement first what we are doing like class.py then in a tests folder or just creating another file in the same directory with the preffix of test so that pytest identifies what is a test and what is not
  - After that just create functions in the test script that have also the test preffix and importing the class or function you want from what you want to test
- Lets say addition.py

```python
def addition(x, y):
    return x + y
```

- And test_addition.py

```python
from addition import addition
def test_addition():
    assert addition(4, 5) == 9
```

- When executed if the test passed there will be a . next to it in the console output ``tests/test_addition.py .``
- But we can improve the tests cause unit test need to cover sufficient use cases
  - This means sometimes we have to test for the incorrect case, just to make sure that it something should throw an error it actually does
  
```python
from addition import addition
def test_addition():
    assert addition(4, 5) == 9

def test_addition_better():
    result = addition(4, 5)
    not_expected = 10
    assert not_expected != result, f"5 + 4 ain't 10"
```

### Testing classes

- Let's say we have class, how do we test it if we have to call functions to well test the functionality of anything
- With pytest we have two methods
  - One way is to just create a new class instance per test function in a class that just works as a forefront for testing
  - In the example we just create a class and poppulate with the test functions so that we can test everypart of the class
  - test_class.py first part

```python
class TestMyClass1:
    def test_addition(self):
        cls_ = MyClass()
        result = cls_.add(4, 5)
        assert result == 9

    def test_substraction(self):
        cls_ = MyClass()
        result = cls_.substract(5, 4)
        assert result == 1
```

- For the second method we can initialize like a mock class inside a ``setup_method()`` function, this cause pytest will look at each test_class and create it's own instance like the ``__init__()`` block and this will cause conflict.
- Then we just use the mock class for each function call

```python
class TestMyClass2:
    def setup_method(self):
        self.cls_ = MyClass()

    def test_addition(self):
        result = self.cls_.add(3, 4)
        assert result == 7

    def test_substraction(self):
        result = self.cls_.substract(4, 3)
        assert result == 1
```

### Assertion statement

- The assertion statement it's our basic tool for creating and testing, but it is differentiated in types of assertions
- Like **equality assertions**
  - It is a powerful tool that has the basic equal and negation comparisors
    - ``==``
    - ``!=``
  - But it also has some other comparing tools like in
    - In its used in the context of checking if a values is present in a collection or any type of data structure
      - ``assert 3 in [1, 2, 3, 4, 5]``
    - Or the lack of presence in it
      - ``asser 3 not in [1, 4, 5]``
    - It also works in dictionaries
      - ``assert a in {"a": 1,  "b": 2}``
  - The less, more or equal than works more in a way like pattern matching
    - As it works normaly
      - ``assert 1 + 3 <= 5``
    - Or in Lists
      - ``assert [1, 2, 3] <= [1, 2, 3, 4, 5]``
    - This works the other way around with more or equal than ``>=``

- The are also the **Boolean assertions**
  - This are for testing the existence of a value or the existence of anything in the context of the test or if a value is set in a variable

  - ```python
    a = 10
    assert a

    b = "abc"
    assert b

  - Also used for normal boolean comparison between boolean data types
    - `` a = True `` ``assert a is True``

- We also have **approximation assertions**
  - This just gives us a more lax comparison between floating numbers
  - It has specific arguments for the decimal tolerance placement
  - ``assert 2.2 == pytest.approx(2.3, 0.1)``
