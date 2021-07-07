# Dashboard Design

As you might have read on my previous posts. I have a SaaS in mind and after reading Seth Godin and listening to Indie Hackers, I've desided to rise up to the challenge and build it on my freetime. 

This blog post is inspired by the following Youtube Video: [6 Tips to Improve Your Dashboard Design](https://www.youtube.com/watch?v=cTXt0FoRXMk).

## The Problem

> We need a dasboard that allows us to clearly see the current state of a website peformance, as well as a brief description of how it performs across time.

Here are two other ways to think about this:

* An answer to the question : *How do we know that our next release is better that the last one?*
* An score board that tells our dev team if it is winning or loosing the game after each release.

## Before 

Before I decided to see the video and write this post, this is what the app looked like:
![alt text](https://github.com/papaponmx/blog/blob/master/img/image.png "Previous dashboard design")


## Solution Outline

> A dashboard that lets you know at a glance, how your web app is performing according the most relevant metrics(this is not a fact, just my opinion) of your [Lighthouse](https://developers.google.com/web/tools/lighthouse/v3/scoring) report.


## Tip 1: Ditch the decor

There are not many borders or bright colors colors on the dasboard, other than the green/red wich is meant to indicate the build status.

## Tip 2: Choose charts wisely

3D Bar charts and Pie charts are not the best, since they are not easy to compare at a glance, so we will change it for a line chart later. We will define those in the after image.

## Tip 3: Kill useless data:

I'll remove most data on the next step.

## Tip 4: Make meaningful groups.

Instead of the groups defined by Ligthouse, (PWA, Accesibility, Best Practices, SEO, etc). We will run with 5 groups and 1 or 2 metrics for each group: 

* HTML. Number of nodes in the DOM:
* JavaScript/CSS. Specially coverage for both:
* Images: Average image size and loading time:
* Http: Number of requests and average load time:

## Tip 5: Stress what's important.

Now that we have groups and metrics, I'll use visual hierachy and size.
