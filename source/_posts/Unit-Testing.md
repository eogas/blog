---
title: Unit Testing
tags: code unit-testing
date: 2020-05-10 12:14:49
---

Over the past few years, I have had a few opportunities to get some hands on experience in unit testing. I'm still learning and improving my understanding of the topic, but I figure I can put together a quick post about the most important things I've learned.

## Unit Testing is Primarily an Architecture Problem
Writing a single unit test against a small, pure function is an easy task. Throw some inputs at it, then test the expected output, right? If only all parts of our applications were this simple. Alas, as software engineers in 2020, we tend to write complicated, object-oriented code that is quite hard to test if it isn't expressly designed to be modular in the right ways.

Are you calling out to a database? Well unfortunately that's untestable. Communicating with a web API? Untestable. Writing to the filesystem? You better believe *that's* untestable. Don't get me wrong, we can certainly write tests that invoke the filesystem, the registry, and so on. But these are not unit tests. They're exercising far more than a single 'unit' of functionality in our software system. In a true unit test, all we want to test is a single business need and nothing more.

Because of this constraint, we as developers must concoct an architecture that decouples our core business logic from these implemetation details. This is what enables unit testing. Fortunately, it just so happens that architecting for unit testing tends to align with good design practices in general. Most developers have probably heard of the [SOLID prinicples](https://en.wikipedia.org/wiki/SOLID) of OOP. Nearly all of these principles apply directly to code that is easy to unit test as well.

## Testing Legacy Code
So let's say I *haven't* been applying these architectural concepts to my codebase. In fact, let's say that somebody (not me, *definitely* not me) has failed to modularize and apply any real architectural rigor to my codebase whatsoever...for the past 20 years of development...

We'll then we're in a bit of a pickle aren't we? How can I prove that if I do A, then B will happen? There's no way to test A, because in order to even do A, I have to first do C, D, E, F, G...etc until I have exhausted the alphabet analogy several times over. A legacy application that is not architected to be modular will be impossible to unit test without a lot of refactoring.

The guidance for this situation tends to be that we should refactor this code into something that *is* testable. But this reveals the fundamental contradicton of unit testing legacy code. We can't refactor the untestable code into something testable without potentially introducing regressions. To avoid regressions, we need to have tests in place. Uhhhh, what?

Most of the resources I have seen suggest adding tests at a higher level first to verify that we aren't breaking important business logic as we refactor toward an architecture that supports unit testing. This may mean system level tests, or full integration tests. At any rate, we will need to temporarily make our code (and tests) less maintainable as a means of refactoring toward something that is testable.

## Unit Testing Greenfield Code
This topic is where I am currently still struggling. It's extremely easy to succumb to [analysis paralysis](https://www.hanselman.com/blog/AnalysisParalysisOverthinkingAndKnowingTooMuchToJustCODE.aspx) when you're thinking a lot about about testability.

>Oh fuck! That class I just wrote can't really be tested at all can it? But...do I even care about testing that?

Maybe not. The first struggle I ran into after learning about all this unit testing stuff was that I didn't understand which portions of the code even needed unit tests, versus those that are essentially an implementation detail. The crux of the matter seems to be that you want to be testing core business logic. Anything that deals with the specific implementation of this logic, and how it works with other systems, should be decoupled and made as thin as possible.

Beyond this point, I am still having trouble iterating on untestable code. I'm not doing TDD, so I'm writing the code before I write tests for it. But do I need to write beautifully testable code from day 1? Probably not. I think I have just been burned so many times on 'prototypes' that eventually shipped with no further refinement that I fear greenfield code written in a way that is expressly not testable. Maybe TDD is the only true way forward. I guess I'll find out eventually.

## Resources
These are the resources I have come across in my unit testing journey:

#### [Starting to Unit Test: Not as Hard as You Think](https://daedtech.com/starting-to-unit-test-not-as-hard-as-youd-think/) by Erik Dietrich
This is a very short book, which seems to be comprised of a handful of posts published in the author's blog. If I'm honest, the quality is not great. It does seem like a direct transcription of the blog posts (with references to hyperlinks and all). However, it is a quick overview of unit testing and the eventual complications that will come. This book won't make you a unit testing expert, but it does a great job of giving the reader the lay of the land on the topic as quickly as possible.

#### [The Art of Unit Testing, 2nd Ed](https://www.manning.com/books/the-art-of-unit-testing-second-edition) by Roy Osherove
This book is exactly what it says on the tin. It's heavily focused on unit testing specifically. While the author does cover some architectural concerns, writing testable code is not the primary focus of the book. The value in this book is primarily around good habits and practices surrounding your unit test suite. Specific unit test and mocking frameworks are covered, as are the various tradeoffs between them. Most of the book assumes the reader is using a statically typed language, similar to C#. At a few points, the author briefly discusses the fundamental differences of testing in a language like C# vs something like Python, Ruby, or JavaScript. Interstingly, the upcoming new edition of this book does target JavaScript. I'm excited to see what that looks like.

#### [Dependency Injection Principles, Practices, and Patterns](https://www.manning.com/books/dependency-injection-principles-practices-patterns) by Steven van Deursen and Mark Seemann
I covered this book extensively in [my previous post](/2019/05/06/Dependency-Injection-Principles-Practices-and-Patterns/). This is not a book about unit testing. However, the architectural techniques described in the book are *essential* to crafting code that is easily unit testable. Nearly all in-depth resources I have found on unit testing mention dependency injection as a core concept. I think this book does an amazing job at tying the two concepts together, along with other general software design guidelines.

[Covet - Nero](https://www.youtube.com/watch?v=8a-GGIQlBns)