# Get Started with Design Patterns

## Drawbacks

- Patterns cost
- Implementing a design pattern is not free
- They are not the fastest way to develop software
- Technical debt
- Don't save a little now to spend a lot later

## Overview of the creational patterns for C\#

- These patterns focus on the lifetime and creation of objects

- ### Factory Method

  - Separate using an object form creating it
  - Use dynamic context to decide what to build

- ### Abstract Factory

  - The interface for a factory so that the correct factory can be provided for in a dynamic situation
  - Create a family of related dependent objects

- ### Builder

  - Separates constructing an object form the object itself
  - Means that a different object is responsible for the construction of other object
  - Helps with flexibility

- ### Prototype

  - Create an object by cloning an existing concrete object
  - Flexibility of creating object dynamically
  - Prototype is an instance than a type

- ### Singleton

  - Most used and the most dangerous
  - Instad of any number of objects there is only one
  - Concurrent access and lack of clarity make it dangerous

## Structural Pattern Overview

- ### Adapter

  - Convert from one interface to another
  - Can be used at class level adapting typer or at the object level
  - Data mapper are common uses

- ### Bridge

  - Independently changed an abstraction and its concrete implementetion
  - It allows for a future state where an abstract class can use an implementation that is decoupled from it
  - Allows to compose objects without adding inheritance

- ### Compositve

  - Lets you treat a set of objects in the same way that a single object is treated
  - MVC uses Composite pattern

- ### Decorator

  - Extends additional functionality to an object without necessarily affecting other objects of the same type
  - Doesn't require subclassing

- ### Facade

  - Create an interface for a specific purpose
  - Makes a complex interface simpler by reducing it in some way
  - Simplify a single interface, or group a set of interfaces together
  - Several more complicate interfaces can be combined into a facade

- ### Flyweight

  - Create a representational versions of an object
  - Save memory by keeping fewer physical copies
  - It can store its own data and is a way to access some external data as its own

- ### Proxy

  - Is a gateway object to control access to another object or source
  - Concurrency check
  - It provides a placeholder for another object and controls access to it
  - Permission check on wrapping data access

## Behavioral Pattern Overview

- ### Interpreter

  - A Context-specific language
  - Compose sentences that can be interpreted

- ### Template

  - Crate places where subclasses can plug in part of an algorithm

- ### Chain of responsibility

  - Allow any number of object in an order to handle the request until handling is completed

- ### Command

  - Encapsulate an action as its own object
  - By thinking of a business level action as an object in its own  right

- ### Iterator

  - WalkThorugh a set of like object without neeeding to know what type they are

- ### Visitor

  - Is an operation that happens on each element of a set
  - Adds an operation to an object without altering the object

- ### Mediator

  - Encapsulates how a given set of objects interacts with one another
  - The objects don't have to know anything about the other and only know about the mediator
  - Reduces class coupling

- ### Memento

  - Is an object that allows another object to go back to the way it was
  - It helps in storing state for an object
  - Serialization helps to fill this role

- ### Observer

  - 1 to n relationships
  - Objects can subscribe to something and be notified when it changes
  - It allows decoupling from the observer group from the observed one

- ### State

  - Separete states of an object from the object itself
  - An object using this pattern doesn't need to be altered when new states are added. The states themselves are defined and can change independently of the object

- ### Strategy

  - By grouping algorithms into a similarly typed object, it is posiible to switch out the action taken on an object dynamically
