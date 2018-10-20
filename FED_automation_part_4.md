---
title: Front End Development Automation with Puppeteer. Part 4
published: false
description: Connecting our tests to Git and Github.
tags: #webdev #javascript #nodejs #automation
---

# Front End Development Automation with Puppeteer. Part 4

## Intro

<!-- Hi everyone, sorry for taking so long to write this post. I'm developing a open source SaaS product out of these blog posts and figuring what the next logical step could be was not that easy for me. -->

In this post **we will create part of a system that is part of a bigger one**. We will focus only on running performance test.

## The problem

> ABC Corp has a `SPA` that is core to the business. It needs to perform great on mobile(we will define what great means later). As time goes by, releases become more frequent and there is a pressing need **to ensure that all new releases comply with the `performance budget` assigned to it**

## The solution

As developers, we must ensure each release must be in a deployable state. For us, deployable means that all tests are passing and new features work as expected in an production-like environment. On top of that, we need/would like to have a way to get instant feedback about the performance of our next release, there for the proposed solution:

> Create a system that runs performance tests each time a new release is made.

### Application outline

Our solution will be a NodeJS application that does X things:

1. **Listen to relevant event using Github actions**. Within a [`git-flow`](https://danielkummer.github.io/git-flow-cheatsheet/) context, new releases come from `release` or `hotfix` branches, both of them should point towards. This will be covered in my next blog post.
2. **Run performance tests**. Once the request is recieved, an audit will run within a Docker container.
3. **Generate a report**. I'll design this an develop it in another post.
4. **Put a link on the README.md**. I'll design this an develop it in another post.

<!-- ### Running performance tests -->

## Developing our Analysis tool

Ideally, our next build should always either improve upon the last release or stay within an acceptable range. If things start to deviate, we want to get the relevant data as fast as posible.

This is the order in which things should start to happen:

1. **Get the app URL running in a testing/staging/local environment**. This should be read from a configuration file.
2. **Run an audit**.
3. **Filter information and send it somewhere it can persist.** This could be either a JSON saved using file system or a Database. As the app matures we'll define it somewhere else

### Dependencies

* [dotenv](https://www.npmjs.com/package/dotenv). A zero-dependency module that loads environment variables from a .env file into process.env
* [ShellJS](https://github.com/shelljs/shelljs). Unix shell commands on top of the Node.js API
* [Lightouse CLI](https://developers.google.com/web/tools/lighthouse/#cli). Audit our application and get the relevant data.

```javascript
/**
 * perfAudits.js
 */

require('dotenv').config();
const shell = require('shelljs');
const APP_URL = { proccess.env };

lighthouse


```