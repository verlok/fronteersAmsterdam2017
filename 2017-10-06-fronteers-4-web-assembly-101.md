---
layout: post
title: WebAssembly 101 - Ash Kyd - Fronteers Amsterdam 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

Javascript has become a compile target. That compiles to other javascript.

Running in the browser, here's what happens:

- download
- unzip
- parse JS
- optimize (to run quicker, browser devs did good)
- compile to machine code (this is device-aware)
- run on CPU

Parse times for 1mb bundle of js have different speed depending on the device (fastest shown: macbook pro w/ safari 10, slowest: iPhone 6s). But if performance aren't good you'd start losing users.

What if we could skip all that? Webassembly (or wasm) webassembly.org. It's portable, binary, size and load time efficient. 

Webassembly precompiled workflow

1. write code (c, c++, rust)
2. compile to wasm
3. (lost it)

Run in the browser: 

- download binary
- unzip
- NO parse
- NO optimize
- compile to machine code (device-aware)
- run on CPU

Wasm is NOT a language. It's a compile target. It runs in the wasm stack machine, a VM that runs in the browser.
Oh, and it's FAST. Sometimes, we must check.

It's a MVP today. Wasm format, modules, stack machine, no DOM access and no APIs.
The DOM access and WebAPIs we have in JS though. So the two can work together. Wasm should be kept for the (_lost it, it's in the slides_).

Wasm concepts in code. (see slides)

Data types support: Integer, float, both in 32 and 64 bit. We don't have strings. We don't have objects.

Wasm memory it's separate from your system, has an ArrayBuffer, we import & export them to share data to JS.

What can we do? Binary data, audio and video, gaming, everything else with binary data!

Here's webassembly explorer (google it), we can write code and compile it and download it. Then we can load them using the dev tools (he's using Firefox ones) and `WebAssembly.compile()` them. -- He's showing a set of videos of how to do all this in the slides. Actually it doesn't return the "Hello world" test but a pointer in memory (_?_). So we need to get the memory area (see slides videos) and transform it using TextDecoder. Wow.

Raw wasm power!

- data types
- imports and exports
- isolated memory

Enscripten

This involves a lot of reinventing the wheel. It's good for playing around and tickering, we probably need some framework to do this. That's where enscripten comes to place. 

It compiles C and C++ into JS. You can port *everything* to the browser.

What was ported to the web: Unity, Unreal and other game engines; Languages, including lua, ruby, python, .NET runtime; sqlite, ffmpeg, qemu. Recently also old games, including Street Fighter II, Prince of Persia, etc. :)

(live demo)

What can we do today?

- hack stuff
- build games
- migrate existing stuff
- write modules

It's kinda like a playground at the moment. The future looks like this: 

- spec will evolve
- the tools will improve (e.g. webpack)
- many languages for the web

@ashkyd