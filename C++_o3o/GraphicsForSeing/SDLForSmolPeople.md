# The good ol SDL library for c++

## Common methods for basic initializing

## The handling of Input

## 2D graphics basics

+ How dows the computer draws something in the screen?

## Other useful notes of the functionality of this thing

+ Subsystems in SDL
    + If you enable one this means that you will do something with either audio, Haptics, Video or controllers.
    + This is all thanks to the flags that you can use on SDL depending on the function that you are going to use
+ For SDL_Init()
    + SDL_INIT_AUDIO
    + SDL_INIT_VIDEO
    + SDL_INIT_HAPTIC
    + SDL_INIT_GAMECONTROLLER

+ For SDL_CreateWindos()
    + SDL_WINDOW_FULLSCREEN 
        + Full screen mode
    + SDL_WINDOW_FULLSCREEN_DESKTOP
        + Full screen mode at the current desktop resolution
    + SDL_WINDOW_OPENGL
        + Adds support for OPENGL 
    + SDL_WINDOW_RESIZABLE
        + Allows the user to resize the window
