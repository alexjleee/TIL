# OOP vs. Functional Programming

> **Programming paradigms** are how you organise your code. JS is a multi-paradigm language, you can write _object-oriented_ or _functional_ code or even both. Both paradigms help you to write clear and understandable code that is easy to maintain and extend.

## Object-Oriented Programming

> **OOP** means that you organise your code in _logical entities_ (objects containing data in form of fields, logic in form of methods).

Core concepts of OOP

- **Encapsulation** : The data and logic that are related are bound together.
- **Abstraction** : When a method is called, the complexity and the implementation detail are hidden.
- **Inheritance** : A child class extends properties and methods from its parent class.
- **Polymorphism** : 
  - Overriding : If there are methods in the parent class and its child class with the same name, the one in the child class overrides the one of the parent class.
  - Overloading : There can be more than two methods with same name but with different number of argument or with different data type.

## Functional Programming

> **Functional Programming** means that you organise your in (pure) _functions_ with clearly defined tasks and pass data via parameters. The data and the behaviors(functions) should be kept separated.

- The function should perform single task.
- The function should be **pure**.
- The function should have `return` statement.
- The function should be immutable - should not change the original state.

### What is a _pure_ function? 
- If the input value is the same, it must return the same value.
- No side effects! - it does not modify its outer world.
