---
layout: post
title: "Brush up RBS and related tools for practical Rails apps"
image: '/assets/img/'
main-class: 'ruby'
tags:
- ruby
- rbs
introduction: 'RBS is still a developing technology and its immediate applicability is somewhat unknown. In particular, it is an important task to verify and improve the practicality of RBS in Rails apps, where Ruby is typically used'
---

There are many chances to improve [RBS (the standard type signature for Ruby)](https://github.com/ruby/ruby-signature) toolchain. One of the major areas waiting for improvements is _generating RBS from other type definitions_, like RDB schema and schema for serialization formats.

The followings are examples of the projects:

* RBS generation from Rails database schema definition (`db/schema.rb` file).
* RBS generation from Rails ActiveRecord classes.
* RBS generation from Protocol Buffers data definition (`.proto` files).
* RBS generation from MessagePack formats.
* RBS generation from JSON schema.
* RBS generation from YARD docs.

You can propose any idea to improve the RBS toolchain. (You will find a missing piece easily if you try to use the tools. 💨)

* **Recommendation**: We have been working for type checking support for Ruby for years. These projects will help making our type checking solution much more practical.
* **Prerequisites**: Ruby
* **Programming areas include**: Data structure
* **Estimated difficulty level**: Easy/Medium
* **Student**: Tadashi Saito
* **Mentors**: @mame, @soutaro

## Status Updates

### Week 3 (06/19/2020)

1. What did you accomplish this past week?
    - (add your accomplishments)

1. What will you do this upcoming week?
    - (add your tasks for next week)

1. What obstacles are impeding your progress?
    - (list any obstacles)

1. Would you like help from some mentor for this task?
    - (list any help you need)
