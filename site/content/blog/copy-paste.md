---
title: My Love-Hate Relationship with Copy & Paste
date: 2021-05-29T11:00:00-07:00
tags: 
- Opinion
- Pair Programming
image: images/blog/post-copy-paste.jpg
feature_image: images/blog/details-copy-paste.jpg
tldr: next time you go to copy a big piece of code, maybe consider not doing that.
---

This may come as a shock to my fellow developers, but I'm not a big fan of copying and pasting code.

Hot takes aside, I recognize that the copy-paste functionality is a useful tool, which no developer 
should have to live without, but I've noticed a trend among my peers that concerns me. You know how 
since the advent of smart phones, no one remembers phone numbers anymore? Well the same
thing is happening with code. 

### My Experience

Tell me if this sounds familiar: a while back a pairing partner and I were tasked with creating a very simple C# class
to process a string property of a POCO and throw an exception if it was invalid. My partner immediately
started scouring the project for an example of code that did something similar to copy. When I explained that they
wouldn't find anything because this was new functionality, they briefly shot me a look of terror, as if I had just told a 
drug addict that their stash had run dry. They then proceeded to go to StackOverflow in search of their next fix.

The coworker in question was a decent developer, perfectly capable of writing the code from scratch.
The problem was they felt they *needed* copying and pasting to write *any* code. For some developers it can get to the 
point where writing new code feels wrong. This is not an isolated incident either. I've seen this happen several times 
over my (so far) relatively short career.

### So what? Who Cares?

I care. I care because it creates issues for me as a pairing partner:

1) It slows down our speed as a pairing team, if you *have to* copy-paste *everything*.

2) It's sloppy, and often leads to vestigial pieces of code, or worse, creates unstable code.

3) It reduces code readability.

4) It leads to code duplication, which ultimately makes code harder to maintain.

5) It reduces your understanding of the code. You may understand what you think the code does in a "black box" sense, 
but you miss out on the deeper understanding you get from mechanically typing it out.

Even if you're copying line for line from StackOverflow, you'd be surprised how much of a better understanding you
get from actually typing it out yourself. You want to be a better developer? Don't copy / paste code.

### So... everyone should just stop using copy-paste then?

Well... I wouldn't have titled this article "My **Love-Hate** Relationship with Copy & Paste" if I didn't also have some
good things to say about copying and/or pasting:

- Spellign Erros. I spell bad, but I want to spell good, and copy-paste helps me spell things gooder. I have also found a 
spell-checker IDE plugin to an essential part of the developer toolkit.
- Copying and pasting *can* prevent trivial mistakes and syntax errors.
- It can save time when writing boilerplate code (but I think many people underestimate the cognitive benefits of repetition)

I'm not saying don't ever copy and paste. But next time you go to copy a big piece of code, maybe consider not doing that. 