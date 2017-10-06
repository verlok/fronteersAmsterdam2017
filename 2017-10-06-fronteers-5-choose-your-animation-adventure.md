---
layout: post
title: Choose Your Animation Adventure - Val Head - Fronteers Amsterdam 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

"What animation type should I use to achieve a certain result?" It depends.

## CSS 

They are good at defining states. You can have transitions from A to B or animations.

Pros: 
- no external lib needed
- great potential for performance without much effort
- keyframes are reusable
- can adjust props in MQs for responsive animations

Cons:
- Access to limited mouse/keyboard events
- Defined entirely ahead of time
- Can't separate transform properties* (*proposal coming in canary behind a flag)

#### CSS + JS = Yay!

(demo video) -> Long running things driven by JS, animating using CSS (transitions, mostly)

It shines in animated interactions and simple interactive animations. Nearly effortless perfs, no additional request.

CSS is good but you should move to JS if:

- you're chaining more than 3 animations in a sequence
- the animation needs to change dynamically at runtime
- need to animate tranform properties separately
- physics or other complex easings structures are required

## Javascript

Use it if

- Complex animated interactions - like showing data animating graphics
- Narrative or immersive animation 
- Dynamic state transitions

(demo video of the Stripe main menu)
(demo of animated 3d lion following mouse)
(demo of repeated timelines for animations - CLIMBER website)

Vanilla or framework?

- Vanilla should use `requestAnimationFrame` -> _see example code on slides_
- Most JS animation libraries already do this things so you don't need to do it yourself

#### Comparing JS anim libraries

- GreenSock, aka gsap.js. Pretty stable, around for a while, very active.
- Velocity.js, API like jQuery, active agin
- Anime

How do we compare the three?

In common: They all have a really similar syntax and do similar things. (comparison of the 3 API on a slide)

Differences:
- file size. Gsap is 7 to 29 kb depending on what you want to use. Velocity is 14.4 kb, Anime is 4.7 kb
- browser support. Gsap back to IE8, velocity too, Anime back to IE10.
- documentation and forums. GSAP docs + forums. Velocity docs + SO. Anime docs only.
- features: Gsap: drawSVG, morphSVG, Draggable; Velocity drop-in velocity replacement for jQuery; Anime: very lightweight
- licensing: Gsap is free but some features require $, the others are MIT licence
- performance: do some performance assessment yourself in your specific case

Summary of JS:

- complex UI animations, dynamic states, immersive animations, can animate DOM

## SVG

It's code and graphics at the same time, cool! :D

Good for:
- animated illustrations and icons
- infographics and data visualization
- fluidly scaling, responsive animation

(demo of animated quiz/svg)
(demo of animated logos, icons)
(demo of storytelling)
(demo of high interaction and full screen transitions)

Animating SVG
- We have SMIL which is tag-based animation within SVG, no IE or Edge support, being deprecated in Chrome
- CSS can do transitions and animations applied to SVG elements, limited number of properties are exposet do CSS, transforms not supported in IE or Edge.
- JS can access/animate native SVG properties, can do motion along path, shape morphing, more like SMIL

SVG in summary

- Animated illustrations
- shape morphine
- motion along path

- responsive by nature
- potential for tiny fily size

---

uianimationnewsletter.com
@vlh