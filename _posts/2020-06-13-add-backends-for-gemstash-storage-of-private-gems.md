---
layout: post
title: "Add backends for Gemstash storage of private gems"
image: '/assets/img/'
main-class: 'rubygems'
tags:
- rubygems
- gemstash
introduction: 'Implement a cloud-storage system to Gemstash that will allow gems to be shared, and used across internal machines effectively.'
---

Today, Gemstash is only able to store private gems directly on disk. That's fine for relatively small setups, but becomes a problem when users want to run multiple web servers for redundancy, or need to store more gems than easily fit on a small server's hard disk.

This project would include extending Gemstash to support storing gems in other places. At a minimum, that would mean building a system for multiple backends and implementing the existing local disk storage as one of those backends. Ideally, it would also include implementing a backend for storing private gems in S3, to demonstrate that the backends system works for different kinds of backends.

* **Prerequisites**: Familiarity with Ruby, familiarity with RubyGems or AWS S3 a bonus
* **Programming areas include**: Ruby, AWS S3
* **Estimated difficulty level**: easy to medium
* **Student**: Hac Duy Quang Nguyen
* **Mentors**: @bronzdoc

## Status Updates

### Week 3 (06/19/2020)

1. What did you accomplish this past week?
    - I published a PR that composed of the full S3 functionality. The implementation I made proved to be successful in pushing, and yanking various gems.

1. What will you do this upcoming week?
    - Continue fixing bugs, and improving code style, as well as formulizing a wrapper class for abstractualization between storage backends.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - My mentor and I are working well in our discussions. One problem I face is having difficulty managing the spec environment for my tests, which uses default configurations that raise some errors. If anyone have any experience with that, it'd be great if I can hear some advice.
