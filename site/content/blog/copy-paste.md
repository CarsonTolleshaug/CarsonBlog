---
title: My Love-Hate Relationship with Copy & Paste
date: 2021-04-29T11:00:00-07:00
tags: 
- Opinion
- Pair Programming
image: images/blog/post-copy-paste.jpg
feature_image: images/blog/details-copy-paste.jpg
tldr: next time you go to copy a big piece of code, maybe consider not doing that.
---

This may come as a shock to my fellow developers, but I'm not a big fan of copying and pasting code.

Hot takes aside, I recognise that the copy-paste functionality is a useful tool, which no developer 
should have to live without, but I've noticed a trend among my peers that concerns me. You know how 
since the advent of smart phones, no one remembers phone numbers anymore? Well the same
thing is happening with code. 

### My Experience

Tell me if this sounds familiar: a while back a pairing partner and I were tasked with creating a very simple C# class
to process a string property of a POCO and throw an exception if it was invalid. My partner immediately
started scowering the project for an example of code that did something similar to copy. When I explained that they
wouldn't find anything because this was new functionality, they breifly shot me a look of terror, as if I had just told a 
drug addict that their stash had run dry. They then proceded to go to stackoverflow in search of their next fix.

The coworker in question was a decent developer, perfectly capable of writing the code from scratch.
The problem is that they began to rely on copying and pasting code to the point where writing new code felt
wrong. This is not an isolated incident either. I've seen this happen several times over my relatively short career.

### So what? Who Cares?

I care. I care because it creates five major issues for me as a pairing partner:

1) It slows down our speed as a pairing team, if you *have to* copy-paste *everything*.

2) It's sloppy, and often leads to vestigial peices of code, or worse, creates unstable code.

3) It reduces code readibility.

4) It leads to code duplication, which ultimately makes code harder to maintain.

5) It reduces our understanding of the code. 

That last one might need some clarification. When I see people copy and paste a big chunk of code from Stack Overflow or 
another project, the next thing I see them do is run the code to see if it works. If it does, the next step is to 
completely forget we ever added it to our code in the first place. I could watch someone copy and paste `X` into our code and then later ask them about some attribute of `X` only for them to stare at me like a deer in the headlights because they've never even heard of `X`, despite **literally just adding `X` to the code**.

### So you want everyone to stop using copy-paste then?

No. I wouldn't have titled this article "My **Love-Hate** Relationship with Copy & Paste" if I didn't also have some
good things to say about copying and/or pasting:

- Spellign Erros. I spell bad, but I want to spell good, and copy-paste helps me spell things gooder.
- Copying and pasting can prevent trivial mistakes and syntax errors.
- It can save time when writing boilerplate code (but I think many people underestimate the cognitive benefits of repetition)

I'm not saying don't copy and paste. But next time you go to copy a big piece of code, maybe consider not doing that. 