---
title: Meetup
tags:
  - boston
  - asp.net core
date: 2016-06-01 23:33:59
---

Yesterday I attended a meetup at the Microsoft New England Research and
Development Center in Cambridge!  Despite being in a different city, it was
only a few short miles from my overpriced apartment in Boston.

##Networking and Pizza
This meetup was more organized than most, and included an actual schedule.
The first order of business was eating pizza and networking with other
developers.  I chatted with a developer who works remotely for StackOverflow,
and another dev who is currently looking for a C++ gig.

Being my first meetup in the area, I didn't know anybody, so it was good to
talk to a few people at least.  During the networking portion I was mainly
distracted/bemused by the sights of Shawn Wildermuth and Miguel de Icaza
just...hanging out with everybody.  It feels stupid to admit, but I guess I
didn't realize that developers who have attained a "rock star" type reputation
are still only rock stars in the relatively small world of software
development.  They don't have handlers.  They don't appear from backstage all
of a sudden when the lights dim.  They enjoy the free pizza just as much as
you do.

##Hello World
The primary objective of this meetup was to record an episode of Shawn's
[Hello World Podcast](https://wildermuth.com/hwpod), which is currently
[on tour](http://www.hwroadtrip.com/) visiting a bunch of cities across
America along with a handful of international stops.  The podcast uses an
interview format where Shawn talks with developers who speak about their roots
and history in the development field.  In this instance, the subject of the
episode was [Miguel de Icaza](https://en.wikipedia.org/wiki/Miguel_de_Icaza).

Miguel talked about his roots in open source, and how contributed as a hardcore
OSS developer for a long time.  He eventually moved into the world of closed
source software, only to be bought out by Microsoft, who then proceeded to
open source his product and give it away for free in an exercise of ridiculous
irony.

An interesting tidbit from the podcast was that Miguel considers
[Gnumeric](https://en.wikipedia.org/wiki/Gnumeric), a spreadsheet application,
to be the most beautiful code he has ever written, and he's not above 
admitting it.  On programming forums, you'll often see people asking for
examples of beautiful code that they can learn from.  Maybe this could be a
good example.

The podcast was recorded live at the event, but based on the
upload schedule, it should be available on Shawn's site within the next few
weeks.  I highly recommend giving it a listen once it's available.

##ASP.NET Core
After the podcast, Shawn did about an hour-long demo/introduction to
[ASP.NET Core](https://docs.asp.net/en/latest/conceptual-overview/aspnet.html).
If you've seen any of his
[Pluralsight courses](https://www.pluralsight.com/authors/shawn-wildermuth),
you'll know that he is somewhat of a subject matter expert when it comes to
web development on the Microsoft stack, so I was very excited for this part.

After seeing Shawn's presentation, it has never been more clear to me that
ASP.NET Core is effectively Microsoft's response to the development style
of [Node.js](https://nodejs.org/en/) with [Express](http://expressjs.com/).
**This is not a bad thing**. In fact it's great!  C# is a beautiful language,
and JavaScript...isn't.  Bringing the design ideology behind Express to
ASP.NET is a great thing in my opinion.

With the standard ASP.NET MVC project template, you're given a massive pile
of included features that you don't even know what they do, and virtually
every resource for learning the framework kind of just rolls with it.  It
reminds me of people starting with Java as their first programming language,
and being told to just ignore most of the language features you're required
to use just to get a simple "Hello, world!" printed to the console.

So Shawn started his demo from basically nothing.  All he had was a console
application which listened to web requests.  During the talk, he slowly added
and configured pieces of middleware from Nuget, demonstrating the flexibility
of the new framework. Even fundamental things that you'd assume are included
by default were actually added to the base web app:

   * Application configuration
   * Support for serving static files
   * The .NET Framework itself
   
These were all included as Nuget packages and tied into the web application
as middleware.  It was a pretty compelling demo, and like the podcast, the
code should be available in the coming weeks at Shawn's
[github repo](https://github.com/shawnwildermuth/HWRoadTripDemos) for the
tour.

***

Overall, this was a fun and interesting event.  I definitely hope to go to
more like this in the Boston area.  I met other local developers, I learned
new things, and I even got some free pizza out of it.  What more is there to
ask for?

[Delta Sleep - Lake Sprinkle Sprankle](https://www.youtube.com/watch?v=QHLWGRJwA28)