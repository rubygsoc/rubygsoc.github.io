---
layout: post
title: "Add gem owner add and remove in web UI of rubygems.org"
image: '/assets/img/'
main-class: 'rubygems'
tags:
- rubygems
- rubygems.org
- rails
introduction: 'We will add options for adding/removing gem owners via Web UI. Additionally, we will make owner add/remove events notifiable. We will also add a new flow for ownership transfers.'
---

`gem owner -a/r` [command](https://guides.rubygems.org/command-reference/#gem-owner) is used to add or remove owners by an email. This method requires that the user has the `gem` CLI configures on a host.
Option of adding and removing owners through the web UI would facilitate friction-less transfer of gem ownership. To avoid spamming, adding a new owner would require a confirmation from the user being added. We will update the existing [`POST - /api/v1/gems/[GEM NAME]/owners`](https://guides.rubygems.org/rubygems-org-api/) to follow the same process where a confirmation is required. Additionally,
We will make owner add/remove events notifiable, ie users can opt-in to receive email notification about ownership changes of a gem.

We are also hoping to add a new flow for ownership transfers, where users can make `ownership request` for any gem with less than 100_000 downloads and older than 12 months updated at time. When a gem owner approves an ownership request, the requester would be added as an owner to the gem. Gem owners who are looking for new maintainers/owners would be able to request `ownership application`. These application will be searchable and listed on a site wide link.

* **Related**: [#2044](https://github.com/rubygems/rubygems.org/issues/2044), [#725](https://github.com/rubygems/rubygems.org/issues/725), [#1842](https://github.com/rubygems/rubygems.org/pull/1842)
* **Prerequisites**: Familiarity with rails
* **Programming areas include**: ruby, rails
* **Estimated difficulty level**: medium
* **Student**: Pavan Vachhani
* **Mentors**: @sonalkr132

## RubyGSOC 2020 Final Report

[https://vachhanihpavan.github.io/2020-08-21-gsoc-2020-final-report/](https://vachhanihpavan.github.io/2020-08-21-gsoc-2020-final-report/)

## Status Updates

### Week 12 (08/21/2020)

1. What did you accomplish this past week?
    - Rework on rack-attack rate limiting configuration.
    - Finished final report

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No
    
### Week 11 (08/14/2020)

1. What did you accomplish this past week?
    - Resolve review comments on [ownership confirmation PR](https://github.com/rubygems/rubygems.org/pull/2357)
    - Changed notification from all owners to only removed user on owner removal.

1. What will you do this upcoming week?
    - Get reviews on the PR and resolve the review comments if any.
    - Work on drafting final GSoC report.

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No
    
### Week 10 (08/07/2020)

1. What did you accomplish this past week?
    - Finished all tests for [ownership transfer PR](https://github.com/vachhanihpavan/rubygems.org/pull/22)

1. What will you do this upcoming week?
    - Get review on the PR and resolve the review comments if any.

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No
    
### Week 9 (07/31/2020)

1. What did you accomplish this past week?
    - Finished implementation of ownership requests feature

1. What will you do this upcoming week?
    - Start writing tests for ownership calls and requests
    - I18nize strings, add mailers and other improvements

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No

### Week 8 (07/24/2020)

1. What did you accomplish this past week?
    - Started with implementing ownership call controller and model

1. What will you do this upcoming week?
    - Finish ownership calls UI
    - Start working on ownership requests features

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No

### Week 7 (07/17/2020)

1. What did you accomplish this past week?
    - Added Rack Attack configuration with tests for rate limiting to prevent abuse of email service.
    - Resolve review comments on [Ownership confirmation PR](https://github.com/rubygems/rubygems.org/pull/2357)
    - Rename a few terms in [Ownership RFC](https://github.com/rubygems/rfcs/pull/25) based on community suggestions 

1. What will you do this upcoming week?
    - Start working on the ownership transfer part of the project.
    - Will work on writing model, controller and views for ownership calls.

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No

### Week 6 (07/10/2020)

1. What did you accomplish this past week?
    - UI improvements and code quality improvements [rubygems/rubygems.org#2357](https://github.com/rubygems/rubygems.org/pull/2357)

1. What will you do this upcoming week?
    - Add rate limiting with Rack Attack on newly added endpoints

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No

### Week 5 (07/03/2020)

1. What did you accomplish this past week?
    - Resolve the comments by mentor on the PR [rubygems/rubygems.org#2357](https://github.com/rubygems/rubygems.org/pull/2357)

1. What will you do this upcoming week?
    - Get PR [rubygems/rubygems.org#2357](https://github.com/rubygems/rubygems.org/pull/2357) ready for merge.

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No
    
### Week 4 (06/26/2020)

1. What did you accomplish this past week?
    - Added unit, functional and UI tests for new features
    - Resolve the comments by mentor on the PR [rubygems/rubygems.org#2357](https://github.com/rubygems/rubygems.org/pull/2357)
    - Refactor existing mailers to make them DRY [rubygems/rubygems.org#2421](https://github.com/rubygems/rubygems.org/pull/2421)

1. What will you do this upcoming week?
    - Fix the issues pointed on the PR
    - Work on improving code quality and minimise the changes in existing code.

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No

### Week 3 (06/19/2020)

1. What did you accomplish this past week?
    - Fixed failing test due to new changes in ownership flow
    - Resolve the comments by mentor on the PR [rubygems/rubygems.org#2357](https://github.com/rubygems/rubygems.org/pull/2357)

1. What will you do this upcoming week?
    - Fix the issues pointed on the PR
    - Add tests for the new code

1. What obstacles are impeding your progress?
    - None

1. Would you like help from some mentor for this task?
    - No
