---
title: Boston Code Camp 31
tags: boston
date: 2019-04-11 22:45:39
---


Last weekend I attended a local developer event called [Boston Code Camp](https://www.bostoncodecamp.com/). BCC is an informal gathering of Boston area software developers full of cool technical talks. It's free, and pretty convenient to get to, so I try to attend whenever my schedule allows.

Here's a quick rundown of the talks I attended:

---

### [Xamarin Forms Challenge](https://www.bostoncodecamp.com/CC31/sessions/details/16745) - [Carl Barton](https://twitter.com/cbartonnh)

This talk was more of an exhibition of the flexibility of Xamarin Forms. The speaker aimed to build, deploy, and run a Xamarin Forms application on every supported platform. Aside from a couple of platforms skipped due to technical problems, he was actually able to build and run on nearly every platform.

The main point of the talk seemed to be to highlight the idea that a single (mostly) shared codebase can be deployed to many platforms, with only differing UI layers. He did explain that it is possible to detect which platform is being used at runtime and switch sections of code on and off based on this, but I gather that this is meant to be avoided whenever possible.

Because he had some extra time toward the end of the talk, the speaker also demoed targeting [a UI library for the web called Ooui](https://github.com/praeclarum/Ooui), which is absolute insanity.

This was a pretty cool talk, although I'd love to see a followup talk that delves a bit more into the architecture of a nontrivial application targeting many platforms. The powerpoint and all of the demos for the talk are available on github at: [https://github.com/JarleySoft/XFChallenge](https://github.com/JarleySoft/XFChallenge)

### [Creating Docker Images with .NET Core Debugging](https://www.bostoncodecamp.com/CC31/sessions/details/16743) - [James Pansarasa](https://twitter.com/Mill5James)
I'm not particularly experienced with containers, so I didn't get a ton out of this talk, but it was certainly interesting.

After some initial discussion, the speaker kicked off with his main assertion that the automatically scaffolded Docker setup from Visual Studio should not be used. For various reasons, he recommends creating everything from scratch on the command line instead.

>If you're going to use Docker, get used to the command line

The key to his alternate design is that instead of building the application normally and deploying it into the contianer, you should instead deploy the source code, then build and run it inside the container.

The speaker, a developer at Mill5 in Boston, mentioned that he will soon be putting up a full technical post with some more info on [the Mill5 blog](https://www.mill5.com/innovation/), so stay tuned for that if this sounds interesting.

### [How to Interview Your Future Coworkers](https://www.bostoncodecamp.com/CC31/sessions/details/16740) - [Jen Weber](https://twitter.com/jwwweber)
I won't go too in depth on this one as the speaker has made the whole presentation freely available online here: [http://tinyurl.com/hiring-boscc](http://tinyurl.com/hiring-boscc)

This talk contained some great hiring tips, beyond just interviewing practices. Near the end was a great list of resources about avoiding bias, and hiring in general. I highly recommend checking out the slide deck.

  * [Facebook - Managing Unconscious Bias](https://managingbias.fb.com/)
  * [Textio - The Augmented Writing Platform](https://textio.com/)
  * [Jen Weber - Medium](https://medium.com/@jenweber)
  * [Compassionate Coding](https://compassionatecoding.com/)

### [The Promise of an Async Future Awaits](https://www.bostoncodecamp.com/CC31/sessions/details/16723) - [Bill Wagner](https://twitter.com/billwagner)
Again, I won't say too much about this talk, as the entire thing has recently been made available for free on YouTube. The main points were about the basics of async/await in C#, some common pitfalls, and a quick demo of the new [async streams](https://www.infoq.com/articles/Async-Streams) feature of C# 8.
{% youtube lw3HTm5EYuk %}

### [Going Independent](https://www.bostoncodecamp.com/CC31/sessions/details/16750) - [Jason Haley](https://twitter.com/haleyjason)
This was a pretty interesting talk. The speaker, Jason Haley, is an independent consultant, and the talk went over over many of the special considerations that need to be taken when going into business for yourself. This included general financial advice, legal advice, information on how to find clients, how to deal with clients, and much more.

If I'm honest, before attending this talk, "Going Independent" sounded like a pretty appealing concept to me. Jason did a great job of disabusing the audience of this belief. He makes it clear that going independent requires shifting a significant portion of a developer's time away from strict technical work onto the actual logistics of running a business.

This talk got me thinking about alternative ways of working as a software developer. A while back, I picked up a copy of Erik Dietrich's [Developer Hegemony](https://leanpub.com/developerhegemony). I haven't gotten around to reading it yet, but from what I understand, it talks about a model of software development where programmers work in a co-op type situation, similar to a law firm.

**Update** (4.13.19): Jason has since posted a nice summary, along with the full slides [on his own blog](http://www.jasonhaley.com/post/Going-Independent-from-Boston-Code-Camp-31). If this topic sounds interesting, definitely go check those out.

### [Building Fast, and almost free apps with Azure Functions](https://www.bostoncodecamp.com/CC31/sessions/details/16720) - [Tommy Parnell](https://blog.terrible.dev/)
This talk was all about Azure functions and serverless applications. A lot of this went way over my head, becuase I don't have any experience in this area, but it was fairly interesting nonetheless. 

The speaker presents the combination of Azure functions and Cloudflare's free tier to build serverless applications that cost very little to run. His prime example of this was [Troy Hunt's PwnedPasswords tool](https://haveibeenpwned.com/Passwords). Hunt wrote a [thorough post](https://www.troyhunt.com/serverless-to-the-max-doing-big-things-for-small-dollars-with-cloudflare-workers-and-azure-functions/) about a similar setup works, and how he is able to run the service very cheaply.

Beyond this, I came away with a handy list of links to check out on serverless development:

* [The Serverless Application Framework](https://serverless.com/)
* [Serverless DevOps - Free eBook](https://www.serverlessops.io/download-the-serverless-devops-ebook)
* [Troy Hunt - Breaking Azure Functions with Too Many Connections](https://www.troyhunt.com/breaking-azure-functions-with-too-many-connections/)
* [Martin Fowler - Serverless Architectures](https://martinfowler.com/articles/serverless.html)
