---
title: 'Dependency Injection Principles, Practices, and Patterns'
tags: ['code', 'architecture', '.NET']
---
A couple of years ago, I signed up for early access to the 2nd edition of *[Dependency Injection in .NET](https://www.manning.com/books/dependency-injection-in-dot-net)* by [Mark Seemann](https://blog.ploeh.dk/). Since then, a second author, [Steven van Deursen](https://blogs.cuttingedge.it/steven/), joined the effort, and the title was changed to *[Dependency Injection Principles, Practices, and Patterns](https://www.manning.com/books/dependency-injection-principles-practices-patterns)*.

I had heard good things about the first edition of this book, and I was very excited to dig into the latest edition when it was released in its final form last month. This post will be a rough overview of the book, and what I got out of it.

## Core Concepts: Pure DI and Volatile Dependencies
Throughout most of the book, the authors present examples using what they refer to as "Pure DI". Pure DI is essentially just doing Dependency Injection without a DI container. Specific DI containers aren't covered in depth until the last few chapters. Until then, everything is done from scratch.

This approach seems to work fine for instructional purposes. I wouldn't want to do it for anything but a trivial application, but it does show the core mechanisms behind all DI containers, and makes clear that they aren't doing anything particularly magical. Pure DI is covered in depth later on in the book.

Apart from Pure DI, the authors introduce the extremely important concept of volatile dependencies early on. This concept is key for understanding the value of DI and clean software architecture in general. Page 27 contains a comprehensive definition of what constitues a volatile dependency, but in short, it refers to any dependency that is liable to change. This may mean a data access layer that hits the file system being reworked to target a database instead. It may mean swapping out calls to network resources during a test for a mocked version of the resource. It may refer to a module that is still undergoing development by a different team.

Whatever the situation may be, the goal of DI is to allow the developer to avoid depending directly on volatile dependencies, and to depend on abstractions instead.

## Architecture
After looking into DIPPP a bit deeper, I was delighted to find out that this is actually more of an architecture book than a basic introduction to Dependency Injection. This does make sense, since it shouldn't really take 500 pages to convey the concept of DI.

No, this book kicks things off early in chapter 2 with a powerful example of a nontrivial, multi-layer application written in a tightly coupled manner. This example is then reworked in chapter 3 to invert the volatile dependencies, resulting in a loosely coupled version of the same application.

The reason this example is so powerful is that every developer has written the tightly coupled version of this application. When you're a beginner, and for many people for the rest of your career, this is just how you write software. I'm not too proud to admit that it wasn't immediately obvious to me how the loosely coupled version should be written. This example is great, because it clearly demonstrates the goals of Inversion of Control, and how to achieve them through DI.

Beyond these two chapters, the book makes constant reference to the [SOLID principles](https://en.wikipedia.org/wiki/SOLID). One might think that [Dependency Inversion](https://en.wikipedia.org/wiki/Dependency_inversion_principle) is the only principle that comes into play with DI, but this couldn't be further from the truth. As I said, this is more of an architecture book. Most of the concepts demonstrated via DI are directly applicable to maintaining one or more of the SOLID principles, and the authors never miss an opportunity to point it out.

## DI Patterns/Anti-patterns/Code Smells
Once the book starts diving into proper DI pattners, three important concepts are introduced:

* Composition Root
* Constructor Injection
* Method Injection
* Property Injection

Your composition root is a centralized location, ideally near the entry point of the application, where the entire dependency graph is defined. This is a fundamental feature of DI. The other three concepts are different ways to inject a dependency. The book makes it clear that Constructor Injection is preferred over the other techniques. Unless there is a good reason why it cannot be used, the authors make clear that Constructor Injection should be used by default whenever possible.

After covering DI patterns, the book moves on to what it refers to as "DI anti-patterns". This chapter title is a bit of a misnomer, because it covers both instances of DI being applied incorrectly, and coding practices that are effectively the antithesis of DI. This chapter, along with the one on code smells, seems to be a great reference for driving code reviews. Instead of saying "this is terrible code don't do this", you can say "this is considered an anti-pattern, and here's why".

## Object Lifetimes
Lifetimes
* Singleton
* Transient
* Scoped

## Interception and AOP
Cross cutting concerns
Decorator pattern -> AOP

Specific DI libraries
* Autofac, SimpleInjector, MS.DI
* MS.DI is not recommended due to lack of features for Decorators, Composites

Wrap up
* Wished there were more scoped examples
* .NET still kind of assumed in content
* Great reference material in footnotes
* Authors speak in absolute terms, uncompromising
