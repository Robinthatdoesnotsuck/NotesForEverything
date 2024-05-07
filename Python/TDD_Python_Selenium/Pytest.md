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
