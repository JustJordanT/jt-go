---
title: 'solid-principles-in-go'
date: 2024-04-01T13:43:53-06:00
draft: false
# image: brand_image.jpg
tags: ["go", "project"]
# series: "How to use poison"
---

# [solid-principles-in-go](https://github.com/JustJordanT/solid-principles-in-go/blob/master/README.md)
A playground for SOLID Principles in Go

![image](https://github.com/JustJordanT/object-oriented-go/assets/38886930/b4213c01-3fd3-4630-88f2-5c4885ca49a0)

"SOLID Principles In Go" would explore applying the SOLID principles in the context of Go, a programming language traditionally seen as procedural rather than object-oriented. Here's a summary of how each SOLID principle could be applied in Go:

1. **Single Responsibility Principle (SRP)**: In Go, this principle can be implemented by designing packages and types with a single, clear purpose. Go's emphasis on small, reusable packages naturally supports SRP.

2. **Open/Closed Principle (OCP)**: Go facilitates this principle through its interface system. Interfaces in Go are implicitly satisfied, allowing systems to be extended and modified without altering existing code. You can define an interface and have multiple types implement this interface, enabling the types to be extended with new functionality without modifying the existing implementations.

3. **Liskov Substitution Principle (LSP)**: This principle states that objects of a superclass should be replaceable with objects of its subclasses without altering the program's desirable properties. In Go, this is less about traditional class hierarchies and more about ensuring that types fulfilling an interface can replace each other without breaking the contract defined by the interface.

4. **Interface Segregation Principle (ISP)**: Go's small, focused interfaces (often single-method interfaces) align well with ISP. By designing small, specific interfaces, Go encourages developers to implement only the methods necessary for the application's functionality, thus avoiding the "fat interfaces" seen in other object-oriented languages.

5. **Dependency Inversion Principle (DIP)**: In Go, dependency inversion is achieved through interfaces to decouple high-level components from low-level components. This allows high-level modules to define the interfaces that low-level modules will implement, reducing the dependencies on specific implementations.


"Go is a profoundly object-oriented language." - Rob Pike (https://youtu.be/rKnDgT73v8s?t=750)

"Go is object-oriented, but it's not type oriented." - Russ Cox (https://youtu.be/jgVhBThJdXc?t=127)
