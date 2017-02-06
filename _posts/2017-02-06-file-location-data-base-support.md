---
layout: post
title: "File location data base support"
image: '/assets/img/'
main-class: 'ruby'
tags:
- c
- ruby
introduction: 'Loading libraries is overhead for invoking ruby interpreter. There are some bottoleneck. (a) finding file (b) read..'
---

Loading libraries is overhead for invoking ruby interpreter. There are some bottoleneck. (a) finding file (b) read and parsing file (c) compiling file (includes optimization).

This project aims to improve performance of (a) by making file location DB.

Pre-compilation for (b) and (c) is nice idea, but they are difficult because we need to know iseq data structure deeply and I believe that we need to modify it for this purpose.
