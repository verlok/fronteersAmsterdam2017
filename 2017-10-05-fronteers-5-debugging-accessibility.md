---
layout: post
title: Debugging Accessibility - Alice Boxall - Fronteers Amsterdam 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

This is not an a11y 101. If you need that, video-course on accessibility: bit.ly/a11y-fundamentals

How do people with disabilities use the web? It depends on the disability. Disability is an interaction: if someone is deaf, purely visible interaction isn't disabling. 

Basically every UI requires some ability. Interfaces made on "mouse-over" are disabling for most. The less an interface requires of its users, the more accessible is is.

WCAG 2.0 are the guidelines for accessibility. Content must be perceivable, operable, understandable and robust. Who are your interface excluding?

Perceivable: enough contrast.
Operable: must support keyboard and all common key and mouse interaction
Understandable: easy to read and to understand
Robust: compatibility with current and future UA (user agents) including AT (assitive technologies)

How do people without disabilities use the web? Application sends a UI, the user visually scans the UI, they click with mouse or touchscreen. The affordances on a UI are buttons etc. common UI patterns have a button, a drop-down, etc. A drop down list is a combination of a button, a list, other affordances, and some of them control other ones. I don't usually think about this, I just take it for granted. 

How do people wit disabilities use the web? The user uses an AT. The application is not visible and it sends data to the AT, like "Reload button". The user then tells the AT to press it, and the AT sends the event to the application. (she demoes how AT works on a blacked-out website). The application have an "Accessibility tree", a collection of information used by the AT via an a11y API. 

It's difficult to think about all this, because we usually think about the visible interface as we perceive it. So it's also expensive. So let's make it simpler. 

On Chrome Canary the a11y tree is inspectable. We need to turn "experimental devtools" flag on. Then we can open the a11y tab. It gives the ability to inspect the a11y tree. Semantic HTML5 tags really help in defining the a11y tree!

How CSS affects semantics? `Display: none` and `aria-hidden` remove content from the a11y tree. List items can be read differently by different AT, which have bugs of their own.

How do we compute names? `aria-label` is useful to change the way things are read by AT. 

ARIA is used to modify the semantics of an HTML document (when HTML 5 is not enough).

Experimenting with AOM (Accessibility Object Model). _?_

Perform audits using Lighthouse to check contrast issues. There's also a Lea Verou's tool to find optimal contrast ratio. Use Chrome Devtools's panel to assess color contrast (press shift 6 times?) - Best used in Chrome Canary.

