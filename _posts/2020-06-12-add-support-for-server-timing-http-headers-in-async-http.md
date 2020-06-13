---
layout: post
title: "Add support for server timing HTTP headers in async-http"
image: '/assets/img/'
main-class: 'async'
tags:
- ruby
- async-http
introduction: 'This project aims to implement support for server timing headers in async-http so that library users can utilize the server timing performance diagnostics when making async requests and retrieving responses. async-http, at a glance, already supports trailers in both requests and responses when handling HTTP/2 streams.'
---

This project aims to implement support for server timing headers in async-http so that library users can utilize the server timing performance diagnostics when making async requests and retrieving responses. async-http, at a glance, already supports trailers in both requests and responses when handling HTTP/2 streams. The server timing specification mentions:

The user-agent MAY process Server-Timing header field communicated via a trailer field (see [RFC7230] section 4.1.2) using the same algorithm.
I intend to implement trailer handling for HTTP/1.1, handling for the server timing header and it's fields, and store the header field syntax such that it can be handled by the implementing developer in a helpful way.

* **Prerequisites**: Understand HTTP/1 and HTTP/2 protocol.
* **Programming areas include**: Ruby.
* **Estimated difficulty level**: medium-high
* **Student**: Mei Walker
* **Mentors**: @ioquatix