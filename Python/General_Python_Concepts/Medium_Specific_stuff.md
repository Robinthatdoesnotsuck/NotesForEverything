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
## Some error/dependencies handling
- If you have the error
```Bash
	: Symbol not found: _ffi_prep_closure
```
- Just
	- Setup the flags needed for brew to install and make the python version that is having this issue point to the correct library on the system
	- The error happens cause the python installation either local or globally is pointing to something that has the incorrect linkers for that .so
```Bash
export LDFLAGS="-L$(brew --prefix zlib)/lib -L$(brew --prefix bzip2)/lib -L$(brew --prefix openssl@1.1)/lib -L$(brew --prefix libffi)/lib"
export CPPFLAGS="-I$(brew --prefix zlib)/include -I$(brew --prefix bzip2)/include -I$(brew --prefix openssl@1.1)/include -I$(brew --prefix libffi)/include"
export PKG_CONFIG_PATH="$(brew --prefix openssl@1.1)/lib/pkgconfig:$(brew --prefix libffi)/lib/pkgconfig"
```
- Then we have to reinstall our python
	- ``pyenv uninstall x.x.x
	- ``pyenv install x.x.x
	- This will reinstall our python with the correct linking and the correct c libraries needed for our system
- Then we purge our pip cache on the poetry env
	- ``pip cache purge
- We hit the good old ``poetry install
- And that will be it