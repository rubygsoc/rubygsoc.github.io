---
layout: post
title: "Bundler and gem metrics, statistics, and analytics"
image: '/assets/img/'
main-class: 'bundler'
tags:
- ruby
- bundler
introduction: 'Rubygems.org recently removed their download count analytics because they were too big of a maintenance burden for volunteers. A recent release..'
---

Rubygems.org recently removed their download count analytics because they were too big of a maintenance burden for volunteers. A recent release of Bundler includes some metric information when it makes requests to the server, but the server doesn't do anything with it. By capturing that information, it would be possible to build a public dashboard of the Ruby ecosystem, including Ruby version usage, Ruby platform and interpreter popularity, Gemfile sizes, and the popularity of individual gems.

In addition, Bundler itself is currently uninstrumented. We are very interested in adding (optional, opt-in) metrics directly to Bundler, allowing the Bundler team to see how Bundler is used "in the wild". That information is invaluable when making decisions about future deprecations and feature additions. The infrastructure needed for this project has already been donated by Heroku and Librato, so we need someone who can work to develop, refine, and iterate on the metrics and analytics provided by Bundler.

* **Prerequisites**: Familiarity with Ruby, possibly metrics or instrumentation systems
* **Programming areas include**: Ruby, Sinatra, web development
* **Estimated difficulty level**: easy to medium
* **Potential mentors**: @indirect, @andremedeiros
