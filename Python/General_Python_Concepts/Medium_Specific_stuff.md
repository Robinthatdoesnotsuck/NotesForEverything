# Specific Python lang shenanigans

## Context Managers

Context manager are a Python language tool that helps us handling resources that would be victim of race condition.

- This ensures that resources are properly used and then released
- The reserved word ``with`` its often used with context managers such as ``open()`` when using a file or in ``pytest.raises`` when handling exceptions

## Exceptions

Exceptions are events that disrupt the normal flow of a program in execution, such as an invalid operation, unexpected input or just a runtime error.

- The way Python handles exceptions is with the ``raise`` key word explicitly or automatically, but the automatic handling tends to just kill the program executing
- But once the exception is caught it can be handled using a try-except block, this helps us in how we handle an exception

```Python
    try:
        do_something
    except: TheError_that_the_do_something_can_have
        do_something_else
    else:
        if_at_the_end_there_is_no_exception
```

- There are multiple exceptions and conditions built-in
  - TypeError
  - ValueError
  - FileNotFoundError
  - IndexError
  - KeyError
  - ZeroDivisionError
  - NameError
