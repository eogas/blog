---
title: Intern Interviews
tags: interviewing
date: 2017-03-18 11:00:36
---


Over the past week or so, my teammates and I have been interviewing potential candidates for a summer intern position. It's a development role, so of course, we have been asking some basic coding questions. We have also asked the candidates to solve a couple of simple programming challenges, both before and during the interview.

If you've ever been in an interview for a programming position before, the idea of coding as part of an interview probably sounds pretty normal. It is quite common to ask these sorts of questions, even to programmers applying to much more high level positions, strictly due to the small amount of "phony" programmers applying to highly skilled positions who actually cannot code their way out of a wet paper bag. We've all read the horror stories.

But that's not what this post is about. This post is about what we do *after* we have concluded that the candidate actually knows how to solve very trivial programming problems. In of our current batch of interviews, as the last question, we have been presenting a coding problem which consists of three phases:

### The First Phase

The first phase is just a simple text processing problem that we expect the candidate to solve in a specific manner. So far, no one has strayed outside of our assumptions, and no one has failed to solve this portion. Even so, this first part actually provides a smidgen of useful information. The main thing we have taken notice of is the candidate's choice of programming language.

Due to the disconnected bubble of CS academia, all of these candidates know at least C and Java. And without fail, these are the languages that they claim to be the strongest in. **A handful of our candidates chose to do the text processing problem in C**, which is an immediate handicap. And indeed, all of the candidates who tried to solve the problem in C have had issues with pointer manipulation. It's not so much the problems with pointers that concern me, rather it is the default choice of C to solve a problem that would be much easier in a language like Java (or Python, or C#, or whatever). For every candidate, we specified that they are allowed to use any language, even pseudocode, to solve this problem. So why would anyone choose C?

### The Second Phase

The second phase of our question is just a test that the candidates understands and can apply a basic CS concept. In this case, the concept is [recursion][1]. I have begun asking this question in two steps, first by simply saying something like "can you solve this problem without using any looping keywords, like 'for', or 'while'?" If the candidate seems stumped by this, we will connect the dots for them and mention that the concept they will need to use is called "recursion", and so far everyone has been on board from at least this point.

[1]: https://en.wikipedia.org/wiki/Recursion_(computer_science)

I don't believe that you can get even a year into a CS degree without being introduced to the concept of recursion, so I'm not too worried that asking this question is potentially alienating anybody. It's somewhat arbitrary, but I think general algorithms that can be solved recursively introduce themselves in the real world much more frequently than anything involving sorting algorithms or red-black trees, for example.

### The Third Phase (a.k.a, The Perl Phase)

Early on in the interviewing process, one of the guys on the team suggested a *new* type of coding question. As I mentioned in my last post, a large part of what my teammates and I deal with is a messy, legacy Perl codebase. So my teammate suggested, in not so many words:

{% blockquote %}
Why don't we have them try to write some Perl? Just say, "here you go, you have the full power of the internet", and let them try to figure out how to solve a simple problem in a programming language that they've never used before?
{% endblockquote %}

This actually turned out to be a stroke of genius. It's not a bad language by any stretch, but Perl is not exactly en vogue right now, so needless to say, nobody we interviewed knew even the first thing about Perl. **This is a good thing.** Remember, these are intern candidates we're interviewing. A major part of being an intern is learning new things. If all you know is C and Java, you better believe you're going to be learning some new languages if you're going to work on our team.

Chris Shaver summed up [in a recent post](http://chrisshaver64.ddns.net/bl0026):

{% blockquote %}
To find out what the candidate knows, ask them about something they know...
{% endblockquote %}

In a similar vein, **to find out how a candidate *learns*, ask them to code something in a language that they don't know**. For anyone who made it through the first two stages with no major issues, we presented this exact scenario to them. We gave them a clean browser opened to google, a text editor with Perl syntax highlighting enabled, and a terminal. Then we instructed them to do whatever they needed to do to write the same program as before in Perl.

Don't get me wrong, we're not cruel. For every candidate, we clarified that we weren't really looking for a working solution at the end of it, rather we were just interested in how the candidate tries to solve a new problem. Let's be fair here, the majority of what a developer does in day to day work is "advanced googling". We wanted to find out how good these candidates were at searching for information and learning from it. There are a few things that I learned from this experiment:

1. Anyone capable of writing a basic computer program must also have some basic googling chops, and can come to some useful pages without too much trouble. Surprisingly, this did not turn out to be a particularly enlightening part of the process. No one really struggled to come up with good sources.

2. The way a developer consumes the information seems to be much more pertinent than actually being able to find it. One candidate in particular was skimming through many pages very quickly. While he may have come across some good sources, they were rendered useless by the candidate skipping over large portions of important information in favor of quick, small code samples. On the other hand, the only candidate who actually ended up with a working solution worked through the sources slowly, with an apparent goal of understanding the information.

3. This process can give insight into how a candidate works through problems. One candidate in particular, with a bit of prodding, showed that he was able to segregate the different pieces of logic in his program and test the correctness of each portion to find out where an issue may be present. One flaw in this approach was exposed by the sole candidate who was able to produce a working solution. She actually came to a working solution before ever running the application. This gave great insight into her ability to search for and process information on the internet, but it didn't give any insight into the way she worked through problems.

All in all, I think this was a useful experiment in interviewing. During technical interviews, we are expected to do some very unnatural things, and this was a way to see how a candidate works in a more realistic environment. When is the last time you wrote a program longhand on a whiteboard, without consulting any sort of documentation, and without being able to run the code? It was probably while interviewing for your current job.