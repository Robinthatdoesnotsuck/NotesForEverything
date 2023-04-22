
## References
+ It is just that, a reference to a variable that aleady exists. To declare a variable reference you must use the type sufix of **&** 
    + Example
    ```
    int i = 20;
    int& r = i; //
    ```
    + This r variable will give you the direction in memory of the i variable in an standard way(in hexadecimal)

+ Pass-by-value
    + This is general programming knowledge, this is not exclusive of C++
    + So when you call a function the parameters inside of it will be copies of the input ones, meaning if you modify anything on the input 
    parameters, it will not show the changes of it
        + This is the code like you would imagine would swap to variables but it doesn't do that cause of what we explained previously
        ```
        void Swap(int a, int b) {
            int temp = a;
            a = b;
            b = temp;
        }
        ```
        + To change this we will pass it by reference, instead of just by value
        ```
        void Swap(int& a, int& b) {
            int temp = a;
            a = b;
            b = temp;
        }
        ```
    + But ] ], Why does this happens? cause as a default when you use a function in C++(and many more C-like languages) it will pass by value making a temporary copy of the variables that you use as parameters and the compiler will destroy this temp variables once it is done with executing the function
    + This leaves you with some work arounds
        + Since you are now passing by reference you need to use existing variables with a direction on memory, this means that your function now only works with variables instead of variables and values

+ If you are using a C-like language read the reference on how it defaults on the pass-by-x when you use functions cause depending on the language it will be pass-by-reference or by-value
## Pointers

+ THE BREAD AND BUTTER OF C++

+ What the hell is a pointer?
    + Nobody knows, bye

+ Useful know hows of pointers
    + When we declare a pointer
        ```
        int y = 100;
        int* p = &y;
        ```
        + We just store the direction on memory of that variable and well, how would anyone modify the value of a pointer variable?
          we will ned to use the power of dereferencing the pointer to do this we would just use ```*p = 42;``` this is done to modify the value of the thing we are pointing to directly instead of been a silly billy to try and change an hexadecimal value on memory
    + Also unlike references pointers can point to well whatever the hell we want since these things are just memory directions

## Arrays
+ Arrays you know the drill
    + To initialize an array is simplier than you think
    ```
    int a[10];
    a[0] = 50;
    ```
    + To initialize it with values you can use the {} notation
    ```
    int fib[5] = {0, 1, 1, 2, 3};
    ```
    + Also if we want to access elments of an array via pointers c++ has something for us, the elements of an array are store contiguously

## Dynamic Memory allocation
+ This is the dread of using this god forsaken/given thing of c++

+ But like why do we have this?
    + In like programming and such, we have a limited space where we can store all of our shit this is the **|STACK|** and that memory space it's very limited, like ridicously limited(also depends on the compiler in usage, so there's that)
    + So we will use something called the **|HEAP|** so that we can have full control of the allocation and deallocation of variables in memory
    + All Dynamic allocations go into the heap
