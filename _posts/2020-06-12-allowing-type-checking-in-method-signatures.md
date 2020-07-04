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

## Status Updates

### Week 3 (06/19/2020)

1. What did you accomplish this past week?
	- This week, I tried integrating RBS to a type checker prototype I implemented.

2. What will you do this upcoming week?
    - My goal for next week is to write an RBS signature file for my old projects.

3. What obstacles are impeding your progress?
    - I had to work on my final projects and exams, but the exams are finally over.

4. Would you like help from some mentor for this task?
    - None for now

### Week 4 (06/24/2020)

1. What did you accomplish this past week?
    - I wrote the signature file for my old project, and I found out that running my Ruby code with RBS made it 20x slower.

2. What will you do this upcoming week?
    - My goal for next week is to use a profiler to see why the type checker is slow.

3. What obstacles are impeding your progress?
    - None

4. Would you like help from some mentor for this task?
    - None for now

### Week 5 (07/01/2020)

1. What did you accomplish this past week?
    - I used Stackprof to profile the RBS type checker, and I found out that it spent most of the time in the `Array` branch of a case statement in a method called `#value` .

2. What will you do this upcoming week?
    - My goal for the upcoming week is to optimize the type checker. I'm currently implementing a sampling option where only a selected amount of elements will be type-checked. I'm done with implementing it for `Array`, and I'm currently working on implementing the sampling functionality for all collections.

3. What obstacles are impeding your progress?
    - None

4. Would you like help from some mentor for this task?
    - None for now, but it would be interesting to know other approaches of optimizing the type checker.