---
layout: post
title: 	The Landscape of Front-End Testing - Alicia Sedlock - Fronteers Amsterdam 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

Metodologies like scrum don't allow us to stabilize our software, we're always running. How to make sure it doesn't crumble?

Front-end testing: a collection of techniques to hold devs accountable for writing and maintaining code and delivering functional experiences.

> Spoiler: not here to push a particular technology.

She's speaking of: Unit, integration and acceptance testing
But also about: Visual regression, performance and accessibility testing

Start with the first row.

## Unit testing 

ensures that small pieces of code, like functions, behave like we expect.
E.g. to test that calculator adds two numbers: `let result = Calculator.addNumners(7,3); expect(result).toBe(10);`
We can also use `spy`s to check that a function has been called, or called with specific arguments.

## Integration testing

Checks that different parts of the application work together. 
The test sets current step to 0, renders progress bar, checks that progress bar has not the _completed_ class, then sets current step to 1 and checks that the progress bar has the _completed_ class.

## Acceptance tests

Make sure we can accomplich major tasks. One level up.
Uses a page handler to set invalid data in a form, submit it, and chheck that a sign up error exists in the page.

Tools: Karma, Nightwatch, jasmine-integration, etc.

---

The descripted above you may already have heard of.
Now with the 2nd row mentioned below.

## Visual regression tests

It makes a screenshot before, a keyboard later, and compare it using Casper (it uses Phantom). 
You tell Casper to navigate to programmatically set URL, then take screenshots. 

The cool thing is to check visuall regression tests in the `/styleguide` so you don't have errors in every page if you slightly change 1 component.

About that responsive design thing... you can set viewport sizes when you set the options in Casper tests `phantomcss: { options: { viewportSize: [1280, 768 ] } }`, even as an array of viewports to test multiple.

To do the visual comparison, she found "Percy", which features an integration with Github and I can check each visual regression error and review them as "expected, not expected". 

Other tools to do visual regression tests mentioned in Alicia's slides.

## Accessibility tests

There's a tool for the command line called a11y, you pass a URL to it, and it tests the page. 
Other tools: a11y, Pa11y, there are also specific ones for angular, react, etc. And Chrome Accessibility Audit.

## Performance tests

Keep your project honest about performance. How fast pages are rendered, what is the size of the page, images, etc.
There's a tool called perfbudget, you can call it setting expectations about SpeedIndex, fullyLoaded, requests, etc.

Q: About performance testing, how do you deal with the fact that our users will navigate in a more performing environment (behind a CDN, a balancer, with a slower connection, etc.)
A: "There must be some option to do network throttling", Alicia said. (Ok but I want to test faster server response time, not only slower network conditions. Probably we need to set up a complete production-similar testing environment and network throttle there)

## Monkey testing

Use gremlins. `Gremlin.createHorde()` :)

## Lint

Linting everything makes you less error-prone reducing common error situations.

---

There's one thing to talk about and it's process and people behind this.
It's easy not to keep tests up to date, and turning those off when they fail. Don't do that. :)

And that's the "I can't get my colleagues to do it" problem. 
It's just another thing to do, like we did with "make it work across browsers", "build mobile-first", "build by progressive enhancement", etc.
Long story short: we can't find the ways to make it part of our process. 
Some tips:

- Require tests during code reviews
- Automate code coverage test (at least X% required to build pass)

Infrastructure time required... at least give it a try and find a way to people commit to this.
Someone has to be the champion, the one that pushes tests until others get up to speed and become champions themselves.

It's not easy. The testing road is a bumpy one. That's one of the reasons why they get abandoned over time. 

---

Wonderful talk about front-end testing by @aliciability here at #fronteers!