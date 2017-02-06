---
layout: post
title: "Add new kinds of Gem dependencies"
image: '/assets/img/'
main-class: 'rubygems'
tags:
- ruby
- rubygems
introduction: 'There have been a number of requests over the years to add in additional gem dependency categories. A full summer would probably mean implementing 2 or more of these new types of dependencies.'
---

There have been a number of requests over the years to add in additional gem dependency categories. A full summer would probably mean implementing 2 or more of these new types of dependencies.

* Optional Dependencies - these are dependencies that do not need to be
  satisified and are possibly recommended during install.
    * https://github.com/rubygems/rubygems/issues/1404
    * https://github.com/rubygems/rubygems/issues/1266
    * https://github.com/rubygems/rubygems/issues/346
* Or dependencies - Where any number of gems can be listed in the dependency and
  at least one of them must be installed. This may overlap with at optional
  dependencies
    * https://github.com/rubygems/rubygems/issues/934
* Exclusion dependencies - This is where gem A dependes on gem B and some of the
  functionality of gem B dependeds on gem C. The author of gem A doesn't need
  what is in gem C in forder for gem C to work, and so doesn't want C to be
  installed.
    * https://github.com/rubygems/rubygems/issues/835
* Build/install dependencies - these are dependencies that are necessary for the
  correct instalation of the gem itself. The main reason for this on is for gems
  with C extensions that use ruby tools to do the build of the extension. Once
  the gem is installed, the build dependency is not necessary
    * https://github.com/rubygems/rubygems/issues/624
* Platform Dependencies - In the case of a gem with a dependency that was
  satisfied on linux by one gem, and on java by another and yet a third on
  windowws this would allow the gem author to specify independt platform level
  dependencies. This is effectively forking the dependency tree based upon
  RUBY_PLATFORM
    * https://github.com/rubygems/rubygems/issues/628
* Engine Dependencies - Currently this has high overlap with Platform
  dependencies, this is where the implementation of ruby makes a difference and
  not the operating system that is the differentiator. This is effectively
  allowing branching of the dependency tree based upon RUBY_ENGINE
    * https://github.com/rubygems/rubygems/issues/722

Related, although not an entire summer project by itself, there is also:

* Ruby Engine Version - this is the case requires a minimum ruby version in
  order to perform. This is different than a gem dependency, it is more a
  generalization of required_ruby_version.
    * https://github.com/rubygems/rubygems/pull/1468
    * https://github.com/rubygems/rubygems/issues/1263

* **Prerequisites**: Familiarity with Ruby and RubyGems
* **Programming areas include**: Ruby
* **Estimated difficulty level**: medium to hard
* **Potential mentors**: @indirect, @copiousfreetime
