---
title: Front End Development Automation with Puppeteer. Part 4
published: false
description: Connecting our tests to Git and Github.
tags: #webdev #javascript #nodejs #automation
---

# Front End Development Automation with Puppeteer. Part 4

## Intro

Hi everyone, sorry for taking so long to write this post. I'm developing a open source SaaS product out of these blog posts and figuring what the next logical step could be was not that easy for me.

## The problem

> ABC Corp has a `SPA` that is core to the business. It needs to perform great on mobile(we will define what great means later). As time goes by, releases become more frequent and there is a pressing need **to ensure that all new releases comply with the `performance budget` assigned to it**

## The solution

As developers, we must ensure each release must be in a deployable state. For us, deployable means that all tests are passing and new features work as expected in an production-like environment. On top of that, we need/would like to have a way to get instant feedback about the performance of our next release, there for the proposed solution:

> Create a system that runs performance tests each time a new release is made.

### Solution outline

Our soulition will be a NodeJS application that does X things:

1. Listen to all githooks

Within a [`git-flow`](https://danielkummer.github.io/git-flow-cheatsheet/) context, new releases happen in two ways, they come from either `release` or `hotfix` branches, both of them should point towards