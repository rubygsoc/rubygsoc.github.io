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

## RubyGSOC 2020 Final Report

(Add your final report here)

## Status Updates

### Week 10 (08/11/2020)

1. What did you accomplish this past week?
   - Continued to implement `rbs subtract` in topic branch

1. What will you do this upcoming week?
   - Investigate and add codes for subtract

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No

### Week 9 (08/04/2020)

1. What did you accomplish this past week?
    - Changed some behavior of [soutaro/steep#173](https://github.com/soutaro/steep/pull/173)
    - Investigated and began to [implement `rbs subtract`](https://github.com/ruby/rbs/compare/master...tadd:add-subcommand-subtract)

1. What will you do this upcoming week?
    - Continue to implement `rbs subtract` in above topic branch

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No

### Week 8 (07/28/2020)

1. What did you accomplish this past week?
    - Investigated some problems of `steep check`
    - Investigated a problem and [created PR](https://github.com/soutaro/steep/pull/173) about `steep watch`

1. What will you do this upcoming week?
    - Improve above PR
    - Check RBS codes to implement `rbs subtract`
        - This would be helpful to merge machine-generated RBS with hand-written RBS

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No

### Week 7 (07/21/2020)

1. What did you accomplish this past week?
    - Updated to follow new syntax of RBS in [Mastodon](https://github.com/tadd/mastodon/commit/33b212af13209124ea7fccf538258cebe414858f?w=1#diff-0a902584bfa6f640041ae92a3a17a50e)
    - Tried to improve speed on interrupting `steep watch`
    - Tried to fix Steep's problem about `::String | false`
    - Setup LSP package on local Emacs and check behavior of Steep

1. What will you do this upcoming week?
    - Create an issue of `::String | false`
    - Create a PR about `steep watch`

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No

### Week 6 (07/10/2020)

1. What did you accomplish this past week?
    - Improved RBS Rails to auto-generate more signatures about DB columns [pocke/rbs_rails#32](https://github.com/pocke/rbs_rails/pull/32)
        - `boolean_attr?` (end with `?`), `anyattr_changed?` (`_changed?` suffix), etc
    - Finished to [annotate User model of Mastodon](https://github.com/tootsuite/mastodon/compare/master...tadd:typed#diff-3cd343654abee8aa661035eb36d68fd5)
        - Used the improved RBS Rails with pocke/rbs_rails#32
        - 2 errors remain. One seems to be a problem of Steep, another seems a dead-code of implementation
    - Tried to fix the above issue of Steep (not completed)

1. What will you do this upcoming week?
    - Investigate the issue of Steep
    - Investigate and improve `steep watch`

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No

### Week 5 (07/03/2020)

1. What did you accomplish this past week?
    - Created some issues and PRs: [steep#158](https://github.com/soutaro/steep/issues/158), [rbs_rails#28](https://github.com/pocke/rbs_rails/pull/28), [rbs_rails#29](https://github.com/pocke/rbs_rails/pull/29), [rbs_rails#30](https://github.com/pocke/rbs_rails/pull/30)
    - Almost completed to [type User model of Mastodon](https://github.com/tootsuite/mastodon/compare/master...tadd:typed#diff-3cd343654abee8aa661035eb36d68fd5)
    - Looked over the new RBS syntax

1. What will you do this upcoming week?
    - Continue to type (write signatures) of Mastodon's User model
    - Improve some behavior of `steep watch`
    - Auto-generate additional signatures with RBS Rails for some Rails model convention
        - `foo?` method for a boolean column `foo`
        - `foo_changed?` method for a column `foo`

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No for now, but I'll continue to communicate

### Week 4 (06/26/2020)

1. What did you accomplish this past week?
    - Made a [bugfix PR for Ruby CI](https://github.com/ruby/rubyci/pull/196) (This is found by static analysis)
    - Continued typing Ruby CI
    - [Began typing](https://github.com/tootsuite/mastodon/compare/master...tadd:typed) (huge) [User model](https://github.com/tootsuite/mastodon/blob/master/app/models/user.rb) of [Mastodon](https://github.com/tootsuite/mastodon) as an example of larger practical Rails app

1. What will you do this upcoming week?
   - Improve and (hopefully) complete typing of Mastodon's User model
   - Create a PR for some lacked signatures in RBS Rails
   - Catch up for a [new syntax of RBS](https://hackmd.io/BuYUsK9IRLqRehlu6_62gg) and [its PR](https://github.com/ruby/rbs/pull/307)

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentors for this task?
    - No

### Week 3 (06/19/2020)

1. What did you accomplish this past week?
    - Fixed an issue of RBS about anonymous modules / classes: [ruby/rbs#302](https://github.com/ruby/rbs/pull/302)
    - Typing [Ruby CI](https://github.com/ruby/rubyci), a small but practical Rails app, is [mostly completed](https://github.com/ruby/rubyci/compare/master...tadd:typed)
        - Some bugs found with RBS!
    - With typing of Ruby CI, many bugs and features found to be improved in RBS / Steep

1. What will you do this upcoming week?
   - Just report or fix some of the found bugs
   - Type some parts of larger Rails apps than Ruby CI (e.g [Discourse](https://github.com/discourse/discourse) or [Mastodon](https://github.com/tootsuite/mastodon) or some other)

1. What obstacles are impeding your progress?
    - Nothing!

1. Would you like help from some mentor for this task?
    - No for now

### Week 2 (06/12/2020)

1. What did you accomplish this past week?
    - Run `rbs prototype runtime` for Rails app
    - Created a [PR to fix `rbs prototype runtime --require-relative`](https://github.com/ruby/rbs/pull/299)
    - Another PR to [fix old name of RBS](https://github.com/ruby/rbs/pull/300)
    - Reported [an issue about anonymous modules](https://github.com/ruby/rbs/pull/301)

1. What will you do this upcoming week?
   - Mostly complete to add signatures of RubyCI
   - Fix `ruby/rbs#301`
   - Fix RBS Rails with adding signatures of `ActiveRecord::Base` methods

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No

### Week 1 (06/07/2020)

1. What did you accomplish this past week?
    - Revised project's description in https://summerofcode.withgoogle.com/
    - Created small fix PRs for [RBS](https://github.com/ruby/rbs/pull/294) and [RBS Rails](https://github.com/pocke/rbs_rails/pull/12)
    - Tried to work with `steep langserver`
    - Add some signatures of [RubyCI](https://github.com/ruby/rubyci)

1. What will you do this upcoming week?
    - Continue to add signatures of RubyCI
    - Try `rbs prototype runtime` for Rails apps
        - `eager_load!` would be needed

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No
