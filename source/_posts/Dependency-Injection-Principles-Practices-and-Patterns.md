---
title: 'Dependency Injection Principles, Practices, and Patterns'
tags:
  - code
  - architecture
  - .NET
date: 2019-05-06 09:41:18
---

I recently finished reading the book *[Dependency Injection Principles, Practices, and Patterns](https://www.manning.com/books/dependency-injection-principles-practices-patterns)* by [Mark Seemann](https://blog.ploeh.dk/) and [Steven van Deursen](https://blogs.cuttingedge.it/steven/). This is technically the 2nd edition of *[Dependency Injection in .NET](https://www.manning.com/books/dependency-injection-in-dot-net)*, but the title was changed to reflect less of a focus on .NET. This post will be a rough overview of the book, and what I got out of it.

## Core Concepts: Pure DI and Volatile Dependencies
Throughout most of the book, the authors present examples using what they refer to as "Pure DI". Pure DI is essentially just doing Dependency Injection without an [IoC container](https://martinfowler.com/articles/injection.html). Specific IoC containers aren't covered in depth until the last few chapters. Until then, everything is done from scratch.

This approach seems to work fine for instructional purposes. I wouldn't want to do it for anything but a trivial application, but it does show the core mechanisms behind all DI containers, and makes clear that they aren't doing anything particularly magical. Pure DI is covered in depth later on in the book.

Apart from Pure DI, the authors introduce the extremely important concept of [volatile dependencies](https://blogs.msdn.microsoft.com/ploeh/2006/08/24/volatile-dependencies/) early on. This concept is key for understanding the value of DI, proper unit testing, and clean software architecture in general. Page 27 contains a comprehensive definition of what constitutes a volatile dependency, but in short, it refers to any dependency that may be subject to change. This can mean a data access layer that hits the file system being reworked to target a database instead. It may refer to a module that is still undergoing development by a different team. It can even be as simple as a piece of logic that changes depending on [the current date and time](https://stackoverflow.com/a/2425739).

Whatever the situation may be, the goal of DI is to allow the developer to avoid depending directly on volatile dependencies, and to depend on abstractions instead.

## Architecture
After looking into DIPPP a bit deeper, I was delighted to find out that this is actually more of an architecture book than a basic introduction to Dependency Injection. The book kicks things off early in chapter 2 with a powerful example of a nontrivial, multi-layer application written in a tightly coupled manner. This example is then reworked in chapter 3 to invert the volatile dependencies, resulting in a loosely coupled version of the same application.

The reason this example is so powerful is that every developer has written the tightly coupled version of this application. When you're a beginner, and for many people for [the rest of their career](https://daedtech.com/how-developers-stop-learning-rise-of-the-expert-beginner/), this is just how you write software. I'm not too proud to admit that it wasn't immediately obvious to me how the loosely coupled version should be written. This example is great, because it clearly demonstrates the goals of Inversion of Control, and how to achieve them through DI.

{% blockquote DIPPP page 67, Dependency Inversion Principle %}
...abstractions should be owned by the module using the abstractions. In this context, "owned" means that the consuming module has control over the shape of the abstraction, and it's distributed with that module, rather than with the module that implements it. **The consuming module should be able to define the abstraction in a way that benefits itself the most.**
{% endblockquote %}

The book makes constant reference to the [SOLID principles](https://en.wikipedia.org/wiki/SOLID). One might think that [Dependency Inversion](https://en.wikipedia.org/wiki/Dependency_inversion_principle) is the only principle that comes into play with DI, but this couldn't be further from the truth. As I said, this is more of an architecture book. Most of the concepts demonstrated via DI are motivated by one or more of the SOLID principles, and the authors never miss an opportunity to point it out.

## DI Patterns/Anti-patterns/Code Smells
Once the book starts diving into proper DI patterns, four important concepts are introduced:

* Composition Root
* Constructor Injection
* Method Injection
* Property Injection

Your composition root is a centralized location, ideally near the entry point of the application, where the entire dependency graph is defined. This is a fundamental feature of DI. The other three concepts are different ways to provide a dependency to a consumer. The book makes it clear that Constructor Injection is preferred over the other techniques. Unless there is a good reason why it cannot be used, the authors make clear that Constructor Injection should be used by default whenever possible.

After covering DI patterns, the book moves on to what it refers to as "DI anti-patterns". This chapter title is a bit of a misnomer, because it covers both instances of DI being applied incorrectly, and coding practices that are effectively the antithesis of DI.

{% blockquote DIPPP Section 5.1, Control Freak %}
What’s the opposite of Inversion of Control? Originally the term Inversion of Control was coined to identify the opposite of the normal state of affairs, but we can’t talk about the “Business as Usual” anti-pattern. Instead, Control Freak describes a class that won’t relinquish control of its Volatile Dependencies.
{% endblockquote %}

The discussion around the control freak anti-pattern really hits home. Much like the tightly coupled application example from Chapter 2, everyone has written code like this. Prior to digging into some architecture books, I suspect that this is just what coding is for most developers.

This chapter, along with the one on code smells, should be a great reference for driving code reviews. Instead of saying "this is terrible code don't do this", you can say "this is considered an anti-pattern (or a code smell), and here's why".

## Object Lifetimes
Before reading this book, [object lifetimes](https://simpleinjector.readthedocs.io/en/latest/lifetimes.html) were just about the point where my understanding of DI started to dwindle. And if I'm honest, I'm still a little fuzzy on this topic after finishing it. An IoC container (or your Pure DI implementation) can create and release concrete object instances according to three different policies:

* Singleton
* Transient
* Scoped

Much like the types of injection, some general recommendations are given for which lifetime to use and when. Singleton is presented as a reasonable default, at least for thread safe code. In the singleton lifetime, a concrete instance is created immediately in the composition root, and that same instance is provided to any consumer that depends on the abstraction. The authors make it very clear that the singleton lifetime is in no way the same as the singleton design pattern (or rather, anti-pattern), and that it doesn't share the same downsides.

The use cases for the transient and scoped lifetimes mostly focused on thread safety and web request scope respectively. I feel that these lifetimes weren't really covered deeply enough, especially the scoped lifetime. But perhaps I just need to go back and give that section another read to really understand it.

## Interception and Aspect Oriented Programming
The next section covers what the authors refer to as 'interception', which is a way to implement [Cross Cutting Concerns](https://en.wikipedia.org/wiki/Cross-cutting_concern) in a codebase that already uses DI. The examples of this include adding logging, auditing, etc without having to modify any existing code. This is mostly achieved through various applications of the [Decorator](https://en.wikipedia.org/wiki/Decorator_pattern) pattern.

The interception idea is applied in increasingly generic ways, which eventually leads seamlessly into the next chapter on [Aspect Oriented Programming](https://en.wikipedia.org/wiki/Aspect-oriented_programming). I haven't read much about AOP before this book, and the book doesn't go particularly in-depth on the topic either. The information presented makes me wonder how/if it works in practice, or if this is purely a case of software architects taking their geekiness to the highest extremes possible.

AOP is complicated enough that there are texts dedicated solely to this topic, so I'm assuming the information we get in DIPPP just grazes the surface. The authors do a decent job of describing the natural progression from DI to AOP however.

## Specific IoC Libraries
The final chapters of the book cover three specific Inversion of Control libraries:

* [Autofac](https://autofac.org/)
* [SimpleInjector](https://simpleinjector.org/index.html) - maintained by co-author Steven van Deursen
* [Microsoft.Extensions.DependencyInjection](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.2) - abbreviated as MS.DI

Each one of these libraries is covered in the exact same way, with the exact same examples. This section is a reference of sorts, and a good way to show how the ideas presented in the book are handled in practice using an IoC container. I skimmed through these chapters, but the main takeaway I got is that MS.DI is not a recommended IoC container, because it lacks some key features like auto-registration and auto-wiring of decorators. There are also limitations in the support for composites.

There is one major miss in this section that I think is fairly regrettable. MS.DI may not have all of the features that the authors expect in a full fledged IoC container, but it is notable in that it is an official, built-in solution for anyone developing .NET Core and ASP.NET Core applications. And even more notable is the fact that it is designed as a generic interface that can be implemented by other IoC Container authors. The authors of Autofac have done [exactly that](https://autofaccn.readthedocs.io/en/latest/integration/netcore.html), creating an implementation that conforms to the standard MS.DI interface. .NET Core developers need not be immediately flummoxed by the use of an alternative IoC container.

I suspect that the reason this aspect isn't covered may be that one of the authors, Mark Seeman, considers this [Conforming Container](https://blog.ploeh.dk/2014/05/19/conforming-container/) idea to be a DI anti-pattern. When I first saw this article, it struck me as harmful dogmatism, especially in relation to MS.DI, but I'm certainly not experienced enough on this topic to say one way or the other. I also recognize that this article was published in May of 2014, about 2 years before version 1.0.0 of MS.DI was released. It's possible that the authors have softened their stance on this issue, but I still would like to have seen it covered in DIPPP.

## Problems and Potential Improvements
While the book was great overall, there is always room for improvement. After finishing the book, I don't feel like I totally understand how to use the scoped and transient lifetimes. Some more concrete examples may help here. Also, part of the idea behind the title change between the 1st and 2nd editions is that the book is no longer exclusive to .NET, and can be useful as a general DI reference for all developers. To me, this is a bit misleading. All of the examples are in C#, and all of the IoC libraries covered are .NET libraries. There is some brief mention of Spring, but beyond this there is almost no discussion of any concrete tech unrelated to .NET. It's still an amazing resource for DI in general, but I would hesitate to recommend it to someone who has no .NET experience at all.

On tone, the authors present their ideas in absolute terms, and at points this starts to sound like dogmatism. Service Locator isn't "considered" an anti-pattern. It's not that "some say" it's an anti-pattern. It just *is* an anti-pattern, [because Mark Seeman and Steven van Deursen said so](https://simple.wikiquote.org/wiki/Stone_Cold_Steve_Austin). I get that this makes the text clearer, and the reasoning is always explained, but the way things are presented as undeniable, subjective facts rubbed me the wrong way in many instances.

Finally, the most glaring problem with this book by a country mile is the complete lack of any discussion of the human aspect of writing software this way. If I want to write a new application architected using DI, there are several people who have to sign off on this: my boss for one, maybe even my boss' boss, and certainly my teammates who will be working on the project with me. I can't just go into a cave of DI goodness for several months and come out with a gleaming pile of perfection that no one else in the company knows how to maintain. I might have to change the way I interview potential candidates who might work on a project architected with DI. How am I supposed to convince my team that DI is the way to go when [well known developers](https://www.mergeconflict.fm/146) and even [godlike coding geniuses](https://twitter.com/migueldeicaza/status/1120660136794701824) are still skeptical about DI?

Due to the way that DI turns on its head the way most developers typically think about writing software, at least a chapter or two is desperately needed to cover questions like:

* How do I pitch DI to my team?
* How do I introduce new developers to a codebase that makes heavy use of DI?
* When is it appropriate to apply Pure DI vs using an IoC container? When it is appropriate to use DI at all?
* How do I refactor toward DI without completely fucking everything up?

Perhaps this would expand the scope of the book too much. But some supplementary material on the web, or maybe a companion book covering this side of DI would be awesome.

## Wrap Up
Despite these flaws, reading this book was a great experience. Even information in the earliest chapters will change the way I write software forever. Having finished it, I feel much more confident in my understanding of Dependency Injection, and in software architecture in general. The authors frequently cite high-quality sources in the footnotes, which will no doubt promote continued learning and deeper understanding of the underlying architectural concepts.

I expect to keep this book on my desk as a reference for quite a while, and I strongly recommend that any developers interested in DI or architecture in general pick up a copy. If you're like me, you will regret not doing it sooner.