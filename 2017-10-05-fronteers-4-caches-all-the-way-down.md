---
layout: post
title: Caches all the way down - Yoav Weiss - Front-trends Warsaw 2017
date: 2017-10-05 18:00:00 +01:00
categories:
- conferences
tags: [fronteer, notes]
---

_These are my notes from Fronteers 2017 Amsterdam conference._

"I've seen a lot unproperly cached content". There's confusion about different browser caching. I'd like to reduce the confusion and the magic around it.

Why should we care?

2 hard things in computer science: naming things, cache invalidation. :)
Eviction means that the data inside the cache is valuable, and the old things are removed. Serve fresh content... cache invalidation requires to predict the future? 

We have caches everywere down to the CPU. Like cache -> RAM -> Disk. 
Shows a table with L1, L2, L3, RAM, SSD, HDD, Network. Network is 300.000.000 times slower than L1.
Latency is your biggest enemy. 

Browser and network caching. 

**MemoryCache** disappears when the page is rendered. It can be preloaded with a link preload. If something is not cachable it can be still stored in the MemoryCache. 

**Service workers** are powerful proxies to the browser's fetch. From the request perspective the SW is quite unpredictable, they can change request and responses by the web developers. If a resource is not matched by the SW logic, it's fetched from the network / or the next level of cache.

**HTTP cache** is then called to act. It evicts resource when it's full. Data is stored to disk that can be slower than from the MemoryCache. If it's not in the HTTP cache, we go to the next level.

**H2 push cache** AKA the unclaimed push stream container. Is where the H2 push resources are stored. They are swiped then the H2 connection is closed (5 mins in Chrome). On a different connection this doesn't exist. If it's not found, continues to the network.

**Network**: latency is unpredictable, packets can be lost, latency is high. Device -> ISP -> Edge servers -> Internet -> Reverse Proxy -> Origin. 4g has a theoretical latency of 400ms. 

What can we do to lower the latency? CDNs can allow you to serve content from next to your users ISP. If not found in the edge, the reverse proxy can have another cache used to reduce processing costs, then it's forwarded to the origin server.

--

## HTTP caching.

URL is the key of the cached resource. Freshness of the resource determines how long the cache can serve it without re-validating it. Like `cache-contro: max-age=3600` keep it for the next hour. What if we deployed a fix a minute later? Users can receive the buggy version for the next 59 mins. So there are other validators: `Last-modified: time; ETag: badbaaadbeef`. Coditional requests are made with `if-modified-since` and stuff. Response 304 Not Modified won't send anything. But still we have to wait a roundtrip to the network to know we can use the resource we already have.

`Cache-control: public | private`. Private means only in the browser.

`Cache-control: must-revalidate` (may not revalidate). It's refreshed only when the freshness runs out.

`Cache-Control: no-cache=set-cookie` - _?_

`Cache-Control: no-store` means don't store it, only in memory maybe. You can use it for your sensitive data, like banking data. 

`Cache-Control: stale-while-revalidate` the resource is stale and will be served from cache, but revalidated in parallel for the next time.

`Cache-Control: immutable` won't change ever, if I will change it, I will change the URL. 

`Age: ` is a response header used to tell how much time the resource is in cache.
`Vary: ` tells if a particular request header must be added in the cache key. Like `Vary: width` to use the width client-hint in the cache key.

`Key: ` to change the cache key. Like `Key: Width; partition: 300:600:1200`. Cool, but downside: not implemented in browser caches anywhere.

--

Pattern 1: If your scripts are versioned, use immutable + long max-age.
Pattern 2: always revalidate. `Cache-control: must-revalidate, max-age=5`.

Everything else is a gamble. 

Hold till told: immutable at the edge, until purged from the developer via an API call. 
Wouldn't it good if we could do this down to the browser?
- H2 push for invalidation? Because how it's architected, not realistic option.
- Another option is an hack called iframe reload: create an iframe and refresh it using JS: cool, but it forces you to put cache control in your app logic. 
- Service Workers to the rescue! It's not embedded in your app logic, you can have a SW to periodically check that resource.

--

Takeaways:

- Caching is important. 
- Browsers have lots of internal caches and networks too. 
- Common caching patterns: immutable and always revalitate.
- Service workers FTW - hold till told, in the browser.