---
title: The Coding Sunk Cost Fallacy
tags: code
---
The [Sunk Cost Fallacy](https://en.wikipedia.org/wiki/Sunk_cost) is a fairly simple concept to grok. You're checking out at the grocery store, and the line is moving soooo slowly. Five minutes pass. Then ten minutes. There are still 2 customers in front of you, but you notice that the line a few registers over is down to the last customer. From a purely rational point of view, it makes sense to move over to the shorter line.

> But I've already spent 10 minutes waiting in this line! I don't that to be for nothing!

This internal monologue is the sunk cost fallacy rearing its ugly head. That 10 minutes is a sunk cost, and we only increase our losses by choosing to stay in the slow line.

I think this concept exists in software development too. How many times have you started working on a problem, you get stuck in, head down for hours while code flows seamlessly from your head to your hands to the editor. You feel super productive! But alas, after several hours of coding, it becomes plainly obvious that you've been going about this the wrong way the entire time.

What sorts of things can go wrong that require a lot of rework? I'm sure you have some in mind already. The first few that pop into my head are:

* Bad initial assumptions made about core functionality

* Limitations of tech stack, libraries, tools, integration points, etc

* Core design decisions that make it difficult or impossible to meet requirements for performance, modularity, testability, etc

## How to Move Forward
I have found that most problems like this can be worked around in pretty ugly ways. I'm not too proud to admit that I've definitely written some putrid code to try to get past this sort of situation. And I've certainly come across legacy code written by other developers that carries the same stench. "Hm...the author of this code definitely realized they screwed up about halfway through writing this feature, and instead of starting over, they tried to hastily paper over their mistake to save time."

But it doesn't really save time. Maybe it felt like it was saving time that day. Or even for a week or so. But eventually, the bad design decision will make it slower to work in that area of the code.

## A Flawed Analogy
Of course, software development is slightly more complicated than standing in line at the grocery store. For one, the cost of changing lines at the grocery store is effectively zero. Whereas in a software project, if we dig ourselves into a sufficiently deep hole, going back to the drawing board may be more costly than staying the course.

However, it might not be quite as costly as we think either. It's up to us as developers to make the judgement call for whether the rework will save more time in the long run than living with the kludge.

## It's Okay to Throw Away Code
Despite the imperfect analogy, I think in the simple case of a poor design decision, it should be easy for us to make the choice to cut our losses and go back to the drawing board. My underlying reasoning here is that typing isn't the hard part about writing code.

If you spend some time coding up a feature and you eventually realize "aaah shit...I should have done it *this* way instead", you must be able to give yourself permission to go back and do it the better way. During the coding process, we learn so much about the problems we're solving. Starting over from scratch means throwing away the raw bytes in a text file, but the knowledge of how to solve the problem is all still in your head. A second attempt should be much quicker to execute than the first time around. Anyone who has ever lost a nontrivial amount of code ("hm...I thought I pushed that") will know this. Writing something a second time is *way* faster, because you already know all of the edge cases, tricky spots, and so on.

I don't mean to suggest that we should always [write everything twice](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself#DRY_vs_WET_solutions). But the next time you start to get that gross feeling of "ugh, this could have been done better", maybe go back and take another stab at it. You might be surprised at how little time it takes to write up a better version. And future-you will thank you for the work you did up front to make things a little better.