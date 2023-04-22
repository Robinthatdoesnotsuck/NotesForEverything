# The technique, what you need to know first

## What is a game computational speaking?

+ It is just a glorified loop, What do I mean by that?
    + This means that a game is a program that just loops but it is looking for updates as many times it can per second .
+ So knowing this we can add the starting point of a game

### The Game LOOP and Game Class

+ The Game loop is a loop that controls the principal flow of the program, this loop executes code on every iteration(that is where the magic happens)
    + Its quit condition is well the player quitting the game or a crash
+ But ) ) the game loop it is something else that everyone knows a **|F R A M E|** this means the games runs periodically at intervals of FPS or Frame per Seconds, just like a movie a game is just a bunch of code that runs 60 times per second

+ A **|F R A M E|** processes each time it well runs
    + It processes the inputs
        + Inputs means everything, from controll/keyboard inputs, to internet ports, gps tracking, etc. It is used in the broader definition ofa system input
    + It updates the game according to the inputs
        + This means that a game updates everything it has on sight on the scene or level and that is everything, but only updates it as neededand also this is why a game is such a complex endeavour when it comes to the scope of the project and programming wise
    + Generates the output according to the inputs
        + Just like Inputs, output is used on the broader definition, from rumble on your controller, graphics or even data going to the internet


