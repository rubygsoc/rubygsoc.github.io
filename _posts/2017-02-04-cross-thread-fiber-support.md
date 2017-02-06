---
layout: post
title: "Cross-thread Fiber support"
image: '/assets/img/'
main-class: 'ruby'
tags:
- c
- concurrency
introduction: 'MRI supports coroutines through "Fibers", a lightweight cooperative concurrency context. However, Fibers are presently bound to a single thread..'
---

MRI supports coroutines through "Fibers", a lightweight cooperative concurrency context. However, Fibers are presently bound to a single thread, and cannot be resumed in a different thread from the one they were created in. This prevents scheduling runnable Fibers in a thread pool ala similar primitives like goroutines.

This project involves mapping out the semantic implications of resuming Fibers in a different thread from the one they're created in, paying attention to all of the potential problems e.g. holding a mutex while suspended, then making the corresponding changes to MRI. The resulting project should allow Fibers to be resumed between different Ruby threads in a way that is safe and won't corrupt memory.

* **Prerequisites**: C, concurrency
* **Programming areas include**: C, concurrency, multi-threaded programming. Ruby knowledge helpful
* **Estimated difficulty level**: Difficult
* **Potential mentors**: @bascule
