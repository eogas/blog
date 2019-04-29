---
title: 'Dependency Injection Principles, Practices, and Patterns'
tags: ['code', 'architecture', '.NET']
---
A couple of years ago, I signed up for early access to the 2nd edition of *[Dependency Injection in .NET](https://www.manning.com/books/dependency-injection-in-dot-net)* by [Mark Seemann](https://blog.ploeh.dk/). Since then, a second author, [Steven van Deursen](https://blogs.cuttingedge.it/steven/), joined the effort, and the title was changed to *[Dependency Injection Principles, Practices, and Patterns](https://www.manning.com/books/dependency-injection-principles-practices-patterns)*.

I had heard good things about the first edition of this book, and I was very excited to dig into the latest edition when it was released in its final form last month. This post will be a rough overview of the book, and what I got out of it.

## Core Concepts: Pure DI and Volatile Dependencies
Throughout most of the book, the authors present examples using what they refer to as "Pure DI". Pure DI is essentially just doing Dependency Injection without a DI container. Specific DI containers aren't covered in depth until the last few chapters. Until then, everything is done from scratch.

From what I understand, this wasn't the case in the first book. In a world where we all have unlimited time, I'd love to go back and read the first edition to see how it compares, but having only read the 2nd edition, all I can say is that this approach seems to work fine.

Apart from Pure DI, the authors introduce the extremely important concept of volatile dependencies early on. This concept is key for understanding the value of DI and clean software architecture in general. Page 27 contains a comprehensive definition of what constitues a volatile dependency, but in short, it refers to any dependency that is liable to change. This may mean a data access layer that hits the file system being reworked to target a database instead. It may mean swapping out calls to network resources during a test for a mocked version of the resource. It may refer to a module that is still undergoing development by a different team.

Whatever the situation may be, the goal of DI is to allow the developer to avoid depending directly on volatile dependencies, and to depend on abstractions instead.

## Architecture
After looking into DIPPP a bit deeper, I was delighted to find out that this is actually more of an architecture book than a basic introduction to Dependency Injection. This does make sense, since it shouldn't really take 500 pages to convey the concept of DI.

No, this book kicks things off early in chapter 2 with a powerful example of a nontrivial, multi-layer application written in a tightly coupled manner. This example is then reworked in chapter 3 to invert the volatile dependencies, resulting in a loosely coupled version of the same application.

The reason this example is so powerful is that every developer has written the tightly coupled version of this application. When you're a beginner, and for many people for the rest of your career, this is just how you write software. I'm not too proud to admit that it wasn't immediately obvious to me how the loosely coupled version should be written.

Tightly vs Loosely Coupled Example
* One of the most valuable parts of the book
* Demonstrates primary objectives of DI

Patterns/Antipatterns/Smells

Types of Injection
* Constructor injection
* Method injection
* Property injection

Lifetimes
* Singleton
* Transient
* Scoped

Decorator pattern -> AOP

Specific DI libraries
* Autofac, SimpleInjector, MS.DI
* MS.DI is not recommended due to lack of features for Decorators, Composites

Wrap up
* Wished there were more scoped examples
* .NET still kind of assumed in content
* Great reference material in footnotes
* Authors speak in absolute terms, uncompromising
