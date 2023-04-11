# Everything in Ruby is an object

## Objects

### Variables

### Numbers

#### Integers

#### Floats

### Strings

### Arrays

+ An array is an array, it is indexed by integer values

### Hashes

+ Hashes are KEY/VALUE paired but the key can be an object of all sorts of nature
+ They are unordered
+ Found by key that are unique
+ They are practically a dictionary from python(even the syntax is practically the same exceptuating that you separate the value with =>)
+ Example
    + ```car = {'brand' => 'Ford', 'model' => 'Mustang'} ```
    + ```puts car['model']``` so we just like python have the variable with the key in the [] to access that key value
    + ```car['color'] = 'blue'``` this is done to just add a new key/value pair 
    + ```car.keys ``` to access the keys on the hash 
    + ```car.value ``` to access the values on the hash 
    + ```car.size ``` to access the size of the hash
    + ```car.to_a ``` to convert the hash into an array 

### Symbols

+ They are goddamn atoms from erlang
+ So they are strings that are not modifiable
+ They start with a colon :
+ Not delimited by quotes
+ And like atoms they are lowercase and use underscores to separate them
+ Example
    + ```:first_name```
+ They are practically lables
+ So they can be used in hashes just like how erlang makes us manage tuples and maps
+ This enables us to be able to write hashes like this
    + ``` scores = {low: 2, high: 8, avg: 6} ``` Ruby Automatically kknow that it is a label instead of a string so it is simplier to write down hashes this way

### Booleans

#### Comparison and logic Operators

+ Equal ==
+ Less than <
+ Greater than >
+ Less than or equal to <=
+ Greater than or equal to >=
+ Not !
+ Not equal !=
+ And &&
+ Or ||

### Ruby conventions

+ If a method ends with a ? it returns a boolean

### Ranges

+ Inclusive Range
    + 1..10
+ Exclusive Range
    + 1...10
+ Good practice is if I use a method on the range class, to wrap it up in a ()
    + ```(1..10).class ```

### Constants

+ They are UPPERCASE like everything
+ Ruby can change the value of constants
+ But you only have to capitalize the first letter of the variable to make it a constant

## Control Structures

### Conditionals

+ IF 
    ``` 
    if boolean
        # Code block 
    end
    ```
+ ELSE
    ``` 
    if boolean
        # Code block 
    else
        # Code block
    end
    ```

+ ELSIF
    ``` 
    if boolean
        # Code block 
    elsif boolean
        # code block
    else
        # Code block
    end
    ```
+ UNLESS
    + It is the negation of the condition that we have in the boolean section
   ```
    unless boolean
        # code block
    end
    ```
+ CASE
    + A normal case
    ```
    case
    when boolean
        # code block
    else
        # code block
    end
    ```
+ SHORTHAND operators
    + ternary operator
    ```
    boolean ? result1 : result2
    ```
    + or operator
    ```
    x = y || z

    # same as
    if y
        x = y
    else
        x = z
    end
    ```
    + or equals operator
    ```
    x ||=y

    # same as
    unless x
        x = y
    end
    ```
    + Statement modifiers
    ```
    puts "Hello" if greeting_enabled
    score += 10  unless score >= MAX_SCORE
    ```
### Loops

### Iterators

