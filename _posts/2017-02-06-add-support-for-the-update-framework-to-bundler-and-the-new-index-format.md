---
layout: post
title: "Add support for The Update Framework to Bundler and the new index format"
image: '/assets/img/'
main-class: 'bundler'
tags:
- rubygems
- bundler
introduction: 'Building on the TUF project for Rubygems and Rubygems.org, add support to Bundler for TUF. This would include both testing integration..'
---

Building on the [TUF project for Rubygems and Rubygems.org](https://github.com/rubygsoc/rubygsoc/wiki/Ideas-for-RubyGems#support-the-update-framework-with-rubygems), add support to Bundler for TUF. This would include both testing integration (since Bundler uses Rubygems to download gems) and adding TUF metadata to the [new plaintext index format](https://gist.github.com/indirect/6305503) that has been implemented and is currently being integrated into Bundler, bundler.rubygems.org, and will soon be integrated into Rubygems and Rubygems.org.

* **Prerequisites**: Familiarity with Rubygems
* **Programming skills needed**: Competence in Ruby
* **Estimated difficulty level**: hard
* **Potential mentors**: @indirect, @bascule, @JustinCappos, @vladimir-v-diaz, @andremedeiros