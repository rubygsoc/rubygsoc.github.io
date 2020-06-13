---
layout: post
title: "Allowing Type Checking in Method Signatures"
image: '/assets/img/'
main-class: 'ruby'
tags:
- ruby
- rbs
introduction: 'We are working to provide optional _static_ type checking for Ruby, but also open for optional _runtime_ type checking too. This idea is to implement a runtime type checking library which cooperates with RBS type definitions.'
---

We are working to provide optional _static_ type checking for Ruby, but also open for optional _runtime_ type checking too. This idea is to implement a runtime type checking library which cooperates with RBS type definitions.

* This is not to extend the Ruby language itself.
* Type definitions are given as RBS files, and the library does not assume any change to Ruby code.
* The library loads the type definitions and install hooks for each method to type check given arguments and return values.

The runtime checker will provide another option for type checking for Ruby, which gives another opportunity to Ruby developers to work with types. You can find a prototype of runtime type checker in [ruby/ruby-signature repo](https://github.com/ruby/ruby-signature/blob/master/lib/ruby/signature/test/hook.rb).

The goal of this idea is:

* To provide a type check library for Ruby program which type checks Ruby program with respect to RBS type definitions.
* It type checks method arguments and return values and applies the same checks to blocks.
* It should provide good performance. (The prototype makes Ruby code about 2x slower; this is the baseline.)
* It should be more compatible with Ruby programs. (The prototype uses `Module#prepend` to install hooks, but more compatible implementation is expected.)

This is really experimental idea. The goal is subject to change as we work for the idea.

* **Recommendation**: We have been working for type checking support for Ruby for years. These projects will help making our type checking solution much more beneficial.
* **Prerequisites**: Ruby
* **Programming areas include**: Data structure, Ruby runtime APIs
* **Estimated difficulty level**: Medium/Hard
* **Student**: Afront
* **Mentors**: @soutaro