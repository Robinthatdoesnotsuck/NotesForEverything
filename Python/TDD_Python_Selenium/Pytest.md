# Pytest for like testing idk

## What is it and why do I need it?

- It´s a testing framework for Unit Testing mostly, and in conjunction with other tech it can be used for [UI Testing](./Selenium_UI_testing.md)
- Pytest is a mature testing framework that lets us make unit test, integration test and all sort of tests
- This is achieved by the simple syntax it has making it easy to write test with fixtures, assertion, mocking, etc.
- It has easy integration capabilities, so you can stick it with other frameworks like django, flask, selenium, pygame, etc.
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

```python
    a = 10
    assert a

    b = "abc"
    assert b
```
  - Also used for normal boolean comparison between boolean data types
    - `` a = True `` ``assert a is True``

- We also have **approximation assertions**
  - This just gives us a more lax comparison between floating numbers
  - It has specific arguments for the decimal tolerance placement
  - ``assert 2.2 == pytest.approx(2.3, 0.1)``

## Handling Exceptions in test

- First we have to look into [**Context Managers**](../General_Python_Concepts/Medium_Specific_stuff.md)
- Then into [**Exceptions with Python**](../General_Python_Concepts/Medium_Specific_stuff.md)
- So now for the specifics on how pytest makes use of errors well to test stuff
  - It is more on making sure the error we expect on the specific erroneous case is raised
  - It goes something like this
  
```Python
      # here we have the imports from a script that divides stuff
      def test_divide_nombers():
        with pytest.raises(ZeroDivisionError):
          divide_numbers(10, 0)
```

  - Here we are just making sure that the error is raised properly as it was specified in the other script
  
```Python
      def divide_numbers(x, y):
        if y == 0:
            raise ZeroDivisionError("Cannot divide by zero")
        return x / y
```
  
  - One thing to note is that when using the context manager ``pytest.raises()``
  - We have to remember that the exception being raised must be the final line within the scope of the context manager

## Fixtures in pytest

It is another tool at our disposal, it is really useful cause it lets us create functions that returns objects for our test, this is useful when we are handling preconditions for tests in objects, data used, for test data, connections to other entities or just clean up after a test is done

- In fixtures we mostly ``return`` or ``yield`` the object in question
- If we have teardown code in the fixture it is recommended to use ``yield``

### Using Fixtures

- To use Fixtures in pytest we first have to define a ``conftest.py``
- These fixtures are handled automatically by ptests discovery and organization tools
- The ``conftest.py`` file has to be placed in the root test directory
- A fixture has to be defined with the ``@pytest.fixture`` decorator
- Like:
  
```Python
        @pytest.fixture
        def data():
          return {'key': 'value'}
        
        @pytest.fixture
        def lst():
          return [1, 2, 3, 4]
```
- Fixtures can have dependencies between them
```Python
        @pytest.fixture
        def data():
          return {'key': 'value'}
        
        @pytest.fixture
        def another_data(data):
          another_data = data.copy()
          another_data['another_key'] = 'another_value'
          return another_data
```
- Fixtures have scope, scope in the meaning of its life cycle
  - Scopes takes four parameters
    - Function
      - Default scope of a fixture, this means that it is called once for each test that uses it, the fixtures is destroyed after each test is finished
    - Class
      - The fixture is called once for each test class that uses it, it is destroyed once every test method is completed
    - Module
      - The fixture is called once per module it is destroyed when all tests in the module are done
    - Session
      - This means that the fixture its only use once per testing session, but makes this fixture available for all classes and modules, the fixture is destroyed when everything is done
  
```Python
      @pytest.fixture(scope = "session")
      def my_session_fixture():
        print("creating session fixture")
        yield
        print("Destroying session fixture")

      @pytest.fixture(scope = "module")
      def my_module_fixture():
        print("Creating module fixture")
        yield
        print("Destroying module fixture")

      @pytest.fixture(scope = "function")
      def my_function_fixture():
        print("Creating function fixture")
        yield
        print("Destroying function fixture")
```

- We also have an option to mark the fixtures to be auto-used
  - This means the fixtures sets itself up even if they are not listed in the parameters
  - This is useful when we have a database connection fixture
```Python
	@pytest.fixture(scope="session", autouse=True)
	def my_autouse_fixture():
		return [1, 2, 3]
	
    def test_autouse_fixture(my_autouse_fixture):
	    assert my_autouse_fixture == [1, 2, 3]
```

- There are mane built in fixtures in pytest
  - Since these are built-in we can use them without specifying the conftest.py file
  - Like:
    - tmpdir
      - Helps creating temp directory for testing
    - monkeypatch
      - It replaces an object or function with a new implementation
    - request
      - Gives us information about the current test request, such as the name of the test, module, function, etc.

## Markers

Markers are decorators that modify the behavior of the tests or some actions applying to them, this helps us in categorizing, skipping or parameterize the tests.

- Expected failure
  - It is a mark that expects the failure of a test
- Conditionally skipping tests
  - The marker tests a condition to execute a test, this is often used when our tests depend on external libraries or modules
- Or Skipping it without conditions
- For making Parameterized tests
  - We can specified different arguments and values for a test
  - This will cause it to iterate over every permutation of arguments
- Like
  
```Python
      @pytest.mark.xfail
      def test_fail_example():
          assert 1 + 1 == 3


      @pytest.mark.skipif(
          sys.version_info.major == 3 and sys.version_info.minor < 10,
          reason="Requires python 3.10",
      )
      def test_skipif():
          assert True


      @pytest.mark.skip(reason="Fokiu")
      def test_skip():
          assert 1 + 1 == 2


      @pytest.mark.parametrize(
          "test_input,expected_output", [("3+5", 8), ("2+4", 6), ("6*9", 54)]
      )
      def test_parametrized(test_input, expected_output):
          assert eval(test_input) == expected_output
```

- We can also use fixtures with marks
  - This makes it unnecesarry to call the fixture as a parameter on the test function
  - The drawback is that we can't access directly the fixture object
  
  - ```Python
      @pytest.mark.usefixtures("mark_fixture")
      def test_mark_fixture():
          assert True

- We can also combine the markers to create customizable tests
- It is useful when we have a lot of test that have to be filtered

  - ```Python
      @pytest.mark.skipif(sys.platform == "win32", reason="Test not supported on Windows")
      @pytest.mark.parametrize(
          "test_input,expected_output", [("3+5", 8), ("2+4", 6), ("6*9", 54)]
      )
      def test_multi_mark(test_input, expected_output):
          assert eval(test_input) == expected_output

- Pytest also has the capability of filtering test depending on the mark used on it
- It also let us create our custom markers
  - Like
  
  - ```Python
      @pytest.mark.name
      def test_example():
        pass

## Parametrizing tests

Pytest can load data from external sources

- To do this we just have to read de csv in somesort of way
  - Maybe with pandas or the csv module
- Then just parametrize the arguments of the inputs and the reader function

## Pytest command sheet

- For running a test
  - ``pytest test.py``
- For avoid capturing stdout and stderr, this means we can use print in our tests
  - ``pytest test.py -capture=no``
- For running pytest by filtering marks
  - ``pytest -m skip``
  - This will filter tests that have the ``@pytest.mark.skip``
