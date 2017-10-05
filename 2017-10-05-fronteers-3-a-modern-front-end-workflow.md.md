---
layout: post
title: A modern front-end workflow - Umar Hansa - Fronteers Amsterdam 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

Recent Updates in the elements panel.

- Screenshot: Cmd + Shift + P > capture screenshot
- Color contrast: it can say that is the contrast ratio, acceptable vs unacceptable. It's reachable from a color rule in the CSS panel.
- Inspecting a grid, you get dashlines to know exactly where the CSS grid is
- Smart console: you can wrap code using the return key. It now features multi-cursor selection and edit with the mouse or Cmd + D.
- Top-level AWAIT: you can do await (await (...)) - _?_
- Cleaner logs with console.context() to use 3rd party loggers and log in different "tabs" of console
- Coverage panel: reload the page and know how many "lines" of code is unused in your project. U can also open a file and see it line by line what's unused. You can record the page and know the result in real time to monitor optimization progress. Recording also useful for page evolutions, like async stuff.
- Snippets: you can have your own snippets, e.g. "add jQuery to this page"

Performance

In the past it was all about the network. We could investigate only in the network panel. We need to take in consideration more things, like Scrolling smoothness, etc. We have many tools to do that now.

Qualitative vs quantitative. Turn "It feels sluggish" into metrics.

- Page smoothness with the FPS meter in the rendering pane. 
- Javascript execution cost - you can throttle the CPU, find the resource in sources, see the metrics at the side of the lines of code, like how much time took to execute.
- Enable verbose logging to see what violations you did like what took tog long, what caused a reflow, etc.
- Audits panel now features Lighthouse, which does a lot of audits over accessibility etc. like best practice - lighthouse is now featured also in the webpagetest.org website

## A 2 minutes performance workflow

Quantify damage from third-party scripts - like how much tracking scripts cost to our users
Profile the page reload, _(lost it, a colleague was chatting to me, damn Slack)_

Performance monitor - Open the performance monitor tab next to the console. Navigate your website, the visualization will keep track of everything, and you'll have a general understanding of your web performs. Why? It's a quicker introduction to render performance, it captures your complete website usage,you can drill down into what you care about.

## Development workflows

Animations. Animation recorder, animation inspector, modify animation timing.
Open the animations pane, it will record all animations and transitions, break it down to the properties that changed, draw a curve that you can edit with (crazy) cursors.

Authoring. Terminal + sources diff + changes drawer + workspaces. I can open the terminal in Chrome (experimental) e.g. to run `gulp serve`. I can also save back edits to CSS that I did in the devtools, go to the "filesystem" pane, link the folder, go back to the elements panel, cmd + click on the line of CSS code, sends me to the .scss file, and when I save it, it's saved to the FS. (The transformation to CSS is still done from Gulp in the background)

The changes panel also allows me to see what I've changed, like in `git diff`, and I'm able to revert the changes like in git. Cmd + S to save.

Workspaces. _?_

