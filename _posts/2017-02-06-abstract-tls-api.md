---
layout: post
title: "Abstract TLS API"
image: '/assets/img/'
main-class: 'krypt'
tags:
- ruby
- TLS
- OpenSSL
introduction: 'Krypt is a Ruby library that provides TLS services via backend adapters. Today, those adapters are all backed by some version of OpenSSL. This project would mean creating an API..'
---

Krypt is a Ruby library that provides TLS services via backend adapters. Today, those adapters are all backed by some version of OpenSSL. This project would mean creating an API for TLS clients and servers which abstractly supports multiple backend providers and isn't tied specifically to OpenSSL. At a minimum the project should provide a TLS implementation which works with Krypt's OpenSSL FFI backend. Ideally it should support one additional backend TLS provider to prove out whether the abstract API is leaky or solid.

* **Prerequisites**: Familiarity with Ruby, TLS, and OpenSSL
* **Programming areas include**: Ruby, security, C?, Java?
* **Estimated difficulty level**: hard
* **Potential mentors**: @digitalextremist
