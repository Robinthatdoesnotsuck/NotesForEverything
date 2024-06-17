# Go for big poopoo stupid babies

## Declaring Variables

We go by parts a simple variable would look like this:

``var foo string = "bar"``

- ``var`` is the declaration for defining a variable
- ``foo`` the name of the variable
- ``string`` the type of our variable
- ``="bar"`` the initial value of it

We can also declare multivariables with a simple ``var`` statement

```Go
    var (
        Debug bool = false
        LogLevel string = "info"
        startUpTime time.Time = time.now
    )
```

Using this type of notation or full var notation it's not kinda normal, it is used sometimes when you have constant values that have to be controlled.

- So the simplified helps in the last example since a lot of the values make the type inference easier for the compiler.
- This will print the same stuff as above, cause if something doesn't have an initial value asigned, Go will automatically asigned what would be the 0 value for that data type, in this case for bool the initial vlaue its 0 or false

```Go
    var (
        Debug bool
        LogLevel = "info"
        startUpTime time.Time = time.now
    )
```

But the go compiler isn't a know all, cause depending of what you need you'll have to specify the type on it.

```Go
    var seed = 1234456789
    rand.NewSource(seed)
```

This will throw an error like this ``./main.go:19:17: cannot use seed (variable of type int) as int64 value in argument to rand.NewSource`` this happens cause the ``rand.NewSource`` function need an ``int64`` and what it inference by default in ``seed`` its just an ``int`` since go its practically statically typed it will throw an error.

We have another short variable declaration type with the ``:=`` operator, this shorthand for the whole type inference that is needed in the var declaration, we can use the multiple var declaration example.

```Go
    Debug := false
    LogLevel := "info"
    startUpTime := time.Now()
```

One of the most

## Going in an out of go and go script structure

### The packages section

### Importing libraries

We first use the ``import()`` statement

### The main section

## Go cli with go commands

## Go environment variables
