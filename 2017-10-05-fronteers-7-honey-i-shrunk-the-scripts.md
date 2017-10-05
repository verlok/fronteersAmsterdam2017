---
layout: post
title: Honey, I Shrunk the Scripts - Flaki - Fronteers Amsterdam 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

A little history. 

He wrote "The Javascript World Domination" post. People kept commenting. _lost it_

Javacript and Hardware = Nodebots. Johnny 5 is a library to control HW with JS. At the time it was written they had to have a controller to control the hardware. They used node.js for that. 

Nodebots, nodeboats and nodecopters. At JSconf 2014 they came up with noderockets. North Korea would like it :)

At the time, a new JS engine started to emerge. And the ES6 / ES2015 spec. People were happy to use classes and arrow functions. 

Can you put JS on a microcontroller? 

- ESpruino, came from an educator in the UK, like Arduino but easily programmed. It's small as a thumb. It runs JS and you can create stuff easily with it. You can program it with a browser extension. It interpretes source code, it has a hand-written JS engine that was very bad handling modern JS (ES5 only), but basically it stores code as plain text, so if you put more spaces in your code it would run slower. :\ So a few other JS engines started to come out.
- JerryScript made a JS engine fit into 200kb. Opensourced by Samsung who made it in 2015. And they created a JS language to fit into it. _?_
- Microbit by BBC is built to be handled by kids, it fits in the palm of a small hand. Now it's given out for free to 7th grade students. It includes built-in sensors. And you an program it with JS. And with Blocks, if you don't know how to code. It appears as an external drive, so to flash code in, you just drag it to that drive.
- V7 was a JS engine you could use to put js into these devices. When you program for the browser you have the DOM, the Network to access, etc. So they created MJS, you can fit the whole js engine into 25 kb. (The Pebble uses Jerryscript, the controls are exposed to the JerryScript runtime) They made sure it was just as performant as the C version.
- Web bluetooth! It's only available on Chrome, but also in an experimental browser called Servo _?_. But coming next month Firefox Quantum will become much more performing. 

But to put your js on a microcontroller, ... Arduboy is a $12 mini gaming system, and tiny arcade to put JS in the game. It's basically JS code and it's translated into C. 

Try it: http://cld.by/mozillaid

