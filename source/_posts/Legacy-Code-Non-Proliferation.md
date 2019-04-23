---
title: Legacy Code Non-Proliferation
tags:
  - code
date: 2017-03-04 23:46:48
---


At work, one of the projects that my team maintains is a legacy Perl codebase. This project originally contained both the client and server elements of a homegrown build system, as well as a homegrown SCM system, among other things. This project was initially written by a sole developer in the 90s, and over the years it has been maintained by probably 10 or so developers, none of whom likely knew Perl before working on this project.

Obviously, this is not an ideal situation for code quality. And indeed, this project has some pretty bad code. I'm talking single letter identifier names, global variables, no use of OOP whatsoever, massive subroutines, and very minimal use of the module system. In short, it's a mess.

---

#### Fortunately, a lot of this code is not actually used anymore.

It isn't uncommon to come across a file that was last modified over 10 years ago. In certain source files, if you grab the name of a function from its definition, there's a decent chance that a grep won't return any other results for that name in the entire codebase. 

For this reason, I have proposed a policy of **legacy code non-proliferation** to my teammates. The gist of this policy is that any time a developer is tinkering in a specific area of this project, any clearly redundant or unused functionality should be dropped along with any other changes that are occurring. The goal here is not to go out of our way to weed out unused code, but if we happen to notice any "dead branches" in the area we're working in, we will prune them.

When dropping this old code, we will segregate the removal into its own submission, and it will be tagged with a standard bug number. That way, if some legacy functionality that we've dropped actually turns out to be super important, it's a simple process to restore it. After ripping out the old code, we can continue working in this area of the project with less of a mental burden.

---

#### So how did we even get into this situation?

There are a few specific styles of unused legacy code that I have come across:

* One thing I have noticed a few times is instances where someone refactored a piece of commonly used code into its own function in a module, but the developer failed to update all of the instances of this functionality to reference the module. Or perhaps they did do the refactoring, but they left the old implementation commented out, presumably for the sake of posterity. The fix here is simple. Replace the redundant code with the generalized implementation that someone has already written for us.

* Another thing I've noticed is the use of boolean flags to toggle between new and old functionality. This practice is fine when actually testing out a new way of doing things, but once you actually make the switch for good, it is important to remove the dead code path. Again, fixing this is fairly straightforward. Find every branching structure where we toggle between the old and new functionality, and simply remove the old branch and any code that is exclusive to it.

* The last scenario is simply code paths, or full scripts, that are no longer used. An example of this is a script I came across that used to be called by users directly, on the command line. There were several different ways that a user could call this script, with a handful of different arguments. Today, no one uses this script directly, rather it is called indirectly from a UI application in a fairly restricted manner. A large part of the original functionality is no longer required. Again, our task is relatively simple. Remove the unused script or code path.

By no means am I suggesting that we all go diving into our old legacy codebases and ripping out anything that seems unnecessary. However, if you are actively working in a legacy codebase, maybe employ some of these techniques to try to reduce the amount of cruft, with the goal of eventually honing down the codebase into a useful nugget of core functionality. Removing unused legacy code is the first step in making it easier to reason about the overall design of the application and facilitating future improvements.