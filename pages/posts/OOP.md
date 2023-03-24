---
title: Objected Oriented Programming
date: 2023/3/23
description: Four key concepts behind OOP
tag: programming, OOP,
author: Andrew K
---

# Objected Oriented Programming (OOP)

Below are four main concepts that define OOP's ability to translate real-world problems into code. Let's explore these concepts in terms of OOP's key components: classes, objects, and methods.

## Inheritance

Creates a new class which is a derivative of an existing one. The original is called the parent or superclass, and its derivatives are subclass or child class.

```
class Engineer:
    def__init__(self, name):
        self.name = name
    def knows_programming():
        return True
```

```
class FrontendEngineer(Engineer):
    def enjoys_design(self):
        return True
```

```
fe_engineer = FrontendEngineer("James")
print(fe_engineer.name)   # prints "James"
print(fe_engineer.knows_programming())   # prints True
print(fe_engineer.enjoys_design())   # prints True
```

It is possible to access `name` and `knows_programming()` using `fe_engineer` because the subclass `FrontendEngineer` inherits all attributes and methods of the superclass `Engineer`.

## Polymorphism

In the context of programming, polymorphism means that a single entity can behave in multiple ways depending on the context.

```
class Shape:
    def render(self):
        print("renders shape")
```

```
class Square(Shape):
    def render(self):
        print("renders square")
```

```
class Circle(Shape):
    def render(self):
        print("renders circle")
```

Here, we have a parent class `Shape` and two child classes `Square` and `Circle`.\
The parent class establishes the method `render()` and the child classes inherit the method. However, the method is redefined in the child classes through a process known as "method overriding".
The `render()`method behaves differently in different classes, therefore`render()` is polymorphic.
\
\
One might ask - do we only find polymorphism in inherited classes? The answer is no.

```
class Square():
    def render(self):
        print("renders square")
```

```
class Circle():
    def render(self):
        print("renders circle")
```

```
square_1 = Square()
square_1.render()   # prints "renders square"
circle_1 = Circle()
circle_1.render()   # prints "renders circle"
```

The classes `Square` and `Circle` are independent of each other, both use the method `render()`, define the methods differently. Therefore, the outputs are different.

## Encapsulation

Limits acccess to methods and variables by encasing them in a single unit of scope, in the case of Python, a class. It helps prevent unwanted modifications and restrict different functionalities, reducing errors and outputs.

```
Class Account:
    def __init__(self):
        self.balance = 0

    def deposit(self):
        self.balance += 10
```

```
my_account = Account()   # create an instance of the Account class
my_account.deposit()   # call deposit method which will add 10 to balance
my_account.balance = -99999   # set the value of the balance to -99999 (oh no...)
```

Let's prevent the balance attribute from changing outside of the Account class using access modifiers represented by keywords **private** and **protected**.

```
Class Account:
    def __init__(self):
        self._balance = 100   # protected
        self.__balance = 100   # private

    ...
```

Protected attributes can be only accessible by the class and its subclasses.\
Private attributes can only be accessed from within the class.

```
# Private Attribute
my_proper_account = Account()
print(my_proper_account.__balance)   # Throws an error
print(my_proper_account._Account__balance)   # 100 (Name mangling allows access to private attributes)
```

```
# Protected Attribute
my_proper_account = Account()
print(my_proper_account._balance)   # 100
```

## Abstraction

Hides internal implementation details of a process or method from the user for data security. In this way, the user knows what he/she is doing but not how the work is being done.\
For example, we do not think of a car as a set of thousands of individual parts. Rather, we abstract that a car is a well-defined object and drive it without knowing the complexity of the parts that form the car.\
From the outside, a car is a single object, but once inside, it consists of complex subsystems: brakes, airbags, sound system, etc.

```
from abc import ABC, abstractmethod
class Absclass(ABC):
    def print(self, x):
        print("passed value: ", x)
    @abstractmethod
    def task(self):
        print("inside Absclass task")
```

The class `Absclass` is inherited from the ABC class, and an abstract method `task` is defined. The abstract method does not include any implementations - all the implementations are done inside the subclasses.

```
class Test_class(Absclass):
    def task(self):
        print("inside test_class task")
```

```
test_obj = Test_class()
test_obj.task()   # prints "inside test class task"
test_obj.print(100)   # prints 100
```
