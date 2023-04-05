# Defining Software Design Patterns

## Review of Terms

### SOLID

- #### S

  - Single responsibility: a class has a single responsibility

- #### O

  - Open/closed: code is open for extension and closed for changes

- #### L

  - Liskov substitution: objects are replaceable with their subtypes

- #### I

  - Interface segregation: interfaces should be single purpose

- #### D

  - Dependency inversion: code depends on an interface rather than on a class

### DRY

- Don't repeat yourself

### YAGNI

- You Ain't Gonna Need It

## OOP

### Encapsulation

- Keep information as local as possible
- Minimal Intefrace

### Abstraction

- Layers of understanding
- I don't need to write machine code for a webapp
- Smart encapsulation enables abstraction
- Ignore details that don't matter
- Avoiding good abstraction and encapsulation makes for brittle code that is hard to change and easy to break

### Inheritance

- I can extend existing code without changing it
- Understand where code is extensible
- Inheritance means that i can create something new with the starting point of something that already exist without changing it
- Building on what is there; start from more than zero
- Helps in reusing code without breaking code that is dependant on it

### Polymorphism

- Extended objects can be treated as the thing they are extending
- Follow-up of inheritance
- Subclasses can be treated as its parent-class

## No nos

- ### Procedural programming

  - Scripting
  - List of instructions
  - Execute instructions in an order

- ### Functional programming

  - Actions over objects
  - Inmmutability
  - Different design patterns

- ### Pretend OOP

  - Just because you create an utility class is not OOP
  - It needs to follow the principles of OOP

## OOP  and Design Patterns

- ### OOP is a design pattern?

  - OOP is a high-level abstraction/design pattern
  - Without its basis the design patterns won't work
  - It helps use in providing maintainability and reusability

- ### C\#

  - Is not purely OOP
  - OO at the core, with procedural and functional capabilities
  - Built with the .NET Framework that uses many design patterns
  - A lot of value types are not objects
  - Many common core of design patterns are already built on C#

## What are design patterns?

- A reusable solution framework to recurring problems, a way to understand recurring problems and the types of solutions effective for that problem
- Helps us building software but also helps us in making it more understandable and more maintainable over time
- Way to understand recurring problems and the types of solutions effective for that problem

- ### Pattern Languages

  - How a pattern is described and shared
    - Name
    - Motivation
    - Applicability
    - Structure diagram
    - Participating classes
    - Consequences
    - Examples
  - Are organized and ordered for consumption
  - Are a way to communicate ideas about software design
- Patterns are a Guide
- They are just tools

## Why do we need design patterns

- Know why you are making a choice
- Cause a problem maybe different from anything but it can have similiarities to different types of problems

## History of design patterns

- We stole them from architects
- The first wiki was made to share software design patterns
- Manny patterns are part of the language design, like C# this adds functionalities to the languages

## Categories of design patterns

- ### By purpose

- #### Creational

  - How and when objects are created
  - How the object is deferred to a subclass
    - How an interface is passed in
      - Factory Method
      - Abstract Factory
      - Builder
        - Prototype
        - Singleton

- #### Structural

  - How classes and objects relate
    - Adapter
    - Bridge
    - Composite
    - Flyweight
    - Decorator
    - Facade
    - Proxy

- #### Behavioral

  - How interactions are handled between classes or objects
    - Who is responsible for what?
    - Interpreter
    - Template Method
    - Chain of Responsibility
    - Command
    - Iterator
    - Mediator Memento
    - Observer
    - State
    - Strategy
    - Visitor

- #### Concurrency

  - Handling Concurrent Actions

- ### By Scope

  - Class
    - Operates at the type and class-level relationships between classes and sub-classes
  - Object
    - Deals with the relationships and structures between instantiated objects
- Patterns are related to themselves
  - Like MVC
    - That is a combination of different patters
    - View uses a composite pattern
    - Controller is a factory
