---
title: "Why You Should Do CI/CD First"
date: 2021-07-12T11:00:00-07:00
tags: ["CI/CD", "Opinion"]
image: images/blog/post-ci-cd-first.jpg
feature_image: images/blog/details-ci-cd-first.jpg
tldr: You save yourself a lot of headaches by implementing your automation before your code.
---

If you're like me, when you start a new project it's tempting to want to dive right into the code. Writing code is 
the best part of being a developer after all. But if you can exercise a little self restraint you'll thank yourself 
in the long run.

When I start a new project the *very first* thing I try to do is get my automation in place. I've found this saves 
me a lot of time in the long run.

My pairing partners sometimes misconstrue my desire to start with CI/CD as a love for writing CI/CD. I'll be honest, 
I don't really enjoy writing automation which I think most developers can relate to. All the more reason to write it
first, because...

### 1. Writing Automation is easier when the code is simple

When there isn't much beyond boilerplate code, there are less things that can go wrong. Writing CI/CD is hard.
There's often no way to test things locally, so there may be a long time between when you make a change and when you
see if the change was successful or not. Don't make it harder on yourself by adding possible code failures to the mix.
Which brings me to...

### 2. Smaller code fails faster

"Cycle time" is what I call the time between when you make a change and when you see if the change was successful or 
not. I generally try to do everything in my power to keep cycle time as **low as possible**. Shorter cycle times mean
getting to the final solution faster, and smaller code means faster cycle times.

### 3. No one "forgets" to write the code

If you write the code first, you may put off automating the deployment in favor of manually deploying to save time.
You may then accidentally tell your product owner or Scrum master that you're "done" when your code is complete, forgetting
that you still need to write the automation. I've never seen this happen the other way around. No one "forgets" to
write the code.

### 4. Eat your meat, so you can have your pudding

I know this argument isn't very appealing, but the reality is that the sooner you finish the automation, the sooner
you can focus on the good part: writing code.

So those are my 4 reasons for writing CI/CD first when starting a new project. You save yourself a lot of headaches 
by implementing your automation before your code. Try this on your next greenfield project, you'll thank me later.
