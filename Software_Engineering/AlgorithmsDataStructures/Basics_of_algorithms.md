# Starting with the good stuff Algorithms and Data Structures

## Basic Data Structures

### Collections

+ They don't have any kind of order
+ They have multiple types of objects in them
+ Data structures are the ones that decide any of this

### Lists

+ They are ordered
+ The objects in it are related
+ There is no fixed lenght

#### Arrays are the most basic type of lists available in programming languages

    + The power of arrays depends on the language you're using them
    + They have a fixed size but this depends on the language
    + Arrays  have indexes to tell the position of the elements inside them
    + Insertion is difficult in arrays if you want to insert something between elements also deleting has this problem

    #### Linked Lists
    + Is an extension of a list
    + It has order but it doesn't have indexes
    + They are related by its links not by index
    + They know what elements is next and behind them
    + It solves the problem of deleting and inserting elements
      + A linked list stores in a way that it doesn't used indexes with numbers
        + it actually saves a reference to the next or the element behind the element you are standing in
        + So it saves references or memory addresses of the elements beside it
        + You practically hop from element to the next
        + It takes constant time to insert cause you hop and jump between the pointers

    #### Stacks
    + Last In First OUT
    + Push is to put an element at the begining of the stack and pop to delete it

    #### Queue
    + FIFo first in, first out
    + First element is head, last element is tail
    + Dequeue is adding to the head
    + Enqueue is adding to the tail
    + Double ended Queue
      + It works as an stack and a queue
      + Priority Queue

## Searching and Sorting algorithms

### Binary Search

+ It checks the middle value of a sorted array
+ it checks if it is higher or smaller than this number so that it can skip a section of the array that wouln't have our number, so it does this until it finds it or it doesn't exists
+ Efficiency
  + O(log(n))

### Sorting algorithms

+ Bubble Sort, Naive approach
+ The algorithms bubbles up the biggest element to the top but this is iterative
  + We compare everything with everyone
  + The complexity is (n-1)^2
    + But it is also O(n-1)^2 or O(n^2)

### Merge Sort

+ You break up an array to sort it and then you build it up again
  + This is called divide and conquer
  + We divide the array in pairs or in single elements and compared them to sort this array
  + Then we combine the arrays in pairs and compare the arrays that are sorted
    + We put them in a new array and sort this arrays
  + Complexity is O(nlog(n))

### Quick Sort

+ You use a pivot at the lower sections of the array to swap
  + The pivot is a value from the array and usually you choose the last item
  + You need to make an in place sort so we need to move the n-1 in lenght of the element to move the number and swap it with the bigger one

## Maps or something

The maps are indexed by a key it can be well practicaly anything

+ A key only exists once that means that is there only once
+ For python maps are dictionaries
