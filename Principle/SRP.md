## Single Responsibility Principle (单一职责原则)

### Motivation

In this context, a responsibility is considered to be one reason to change. This principle states that if we have 2 reasons to change for a class, we have to split the functionality in two classes. Each class will handle only one responsibility and if in the future we need to make one change we are going to make it in the class which handles it. When we need to make a change in a class having more responsibilities the change might affect the other functionality related to the other responsibility of the class.

> **The Single Responsibility Principle is a simple and intuitive principle, but in practice it is sometimes hard to get it right.**

### Intent

> A class should have only one reason to change

