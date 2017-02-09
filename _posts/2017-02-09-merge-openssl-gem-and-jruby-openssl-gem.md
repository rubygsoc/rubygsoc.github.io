---
layout: post
title: "Merge openssl gem and jruby-openssl gem"
image: '/assets/img/'
main-class: 'openssl'
tags:
- ruby
- openssl
- jruby
introduction: 'These two gems implement the same gem with the same functionality, but are separate gems that do not share a test suite. Because of..'
---

#### Merge openssl gem and jruby-openssl gem

These two gems implement the same gem with the same functionality, but are separate gems that do not share a test suite. Because of this, there is often inconsistent behavior between the two gems.

If merged, they could share a test suite across both platforms, and also ensure that `gem 'openssl'` works everywhere on all Rubies.

* **Prerequisites**: Familiarity with Ruby, OpenSSL, and JRuby
* **Programming areas include**: Ruby, C, Java
* **Estimated difficulty level**: medium to hard
* **Potential mentors**: @digitalextremist, @bascule, @headius
