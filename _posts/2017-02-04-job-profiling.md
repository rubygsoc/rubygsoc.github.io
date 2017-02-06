---
layout: post
title: "Job Profiling"
image: '/assets/img/'
main-class: 'sidekiq'
tags:
- ruby
- sidekiq
introduction: 'Profile jobs running in production.
Can we profile a single job executing on a specific thread while other jobs execute normally on other threads?..'
---

Profile jobs running in production.

* Can we profile a single job executing on a specific thread while other jobs execute normally on other threads?
* Can we get thread-specific CPU info?
* Can we get thread-specific memory allocation info?
* Would statistical profiling (where we profile X% of all executed jobs) be useful?  How would we aggregate and present that data to the developer in a useful form?

Ruby's not known for having simple, easy to use profiling tools, anything we can do to improve this situation will help.

* **Prerequisites**: Familiarity with Ruby and Sidekiq
* **Programming areas include**: Ruby, concurrency
* **Estimated difficulty level**: medium to hard
* **Potential mentors**: @mperham
