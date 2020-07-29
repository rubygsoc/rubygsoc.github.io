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

### Week 6 (07/11/2020)

1. What did you accomplish this past week?
    - [My PR](https://github.com/ruby/rbs/pull/323) for adding the sampling option for arrays was approved and merged to the main repo

2. What will you do this upcoming week?
    - My next goal is to support mocks and stubs. My other goal is to continue optimizing the  runtime type checker since it's still really slow.

3. What obstacles are impeding your progress?
    - None

4. Would you like help from some mentor for this task?
    - None for now


### Week 7 (07/18/2020)

1. What did you accomplish this past week?
    - I added the `SAMPLE_SIZE` option to RBS, and my PR for that change is under review. I also worked on supporting mocks and stubs, and I found out that a particular [gem](https://github.com/benfalk/fetcher) that used RSpec Doubles had some issues with the RBS runtime type checker.

2. What will you do this upcoming week?
    - I have to get my PR approved and merged, and I also have to work on fixing the issues with RSpec Doubles.
3. What obstacles are impeding your progress?
    - None

4. Would you like help from some mentor for this task?
    - None for now



### Week 8 (07/22/2020)

1. What did you accomplish this past week?
    - My [second PR](https://github.com/ruby/rbs/pull/343) to improve the QoL of the `setup` Ruby file Was approved and merged. My PR to add the sample size option is still being reviewed

2. What will you do this upcoming week?
    - Like last week, I have to get my PR approved and merged, and I also have to work on fixing the issues with RSpec Doubles.
3. What obstacles are impeding your progress?
    - None

4. Would you like help from some mentor for this task?
    - None for now

### Week 9 (07/28/2020)

1. What did you accomplish this past week?
    - My [third PR](https://github.com/ruby/rbs/pull/336/commits/bcfc19991a93e41ce387145b687feaaeedd14ffd) was finally approved and merged. I also temporarily fixed the issue for RSpec Doubles. I also profiled the `writer_test`, which took a long time to finish.

2. What will you do this upcoming week?
    - I have to continue optimizing the runtime type checker based on the results from the profiler. I am also working on adding signature files to other projects to test the performance of RBS. I am also checking if there are any problems with running RBS alongside other Double suites.


3. What obstacles are impeding your progress?
    - None

4. Would you like help from some mentor for this task?
    - None for now
