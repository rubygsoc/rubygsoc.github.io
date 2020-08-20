---
layout: post
title: "Add backends for Gemstash storage of private gems"
image: '/assets/img/'
main-class: 'rubygems'
tags:
- rubygems
- gemstash
introduction: 'Implement a cloud-storage system to Gemstash that will allow gems to be shared, and used across internal machines effectively.'
---

Today, Gemstash is only able to store private gems directly on disk. That's fine for relatively small setups, but becomes a problem when users want to run multiple web servers for redundancy, or need to store more gems than easily fit on a small server's hard disk.

This project would include extending Gemstash to support storing gems in other places. At a minimum, that would mean building a system for multiple backends and implementing the existing local disk storage as one of those backends. Ideally, it would also include implementing a backend for storing private gems in S3, to demonstrate that the backends system works for different kinds of backends.

* **Prerequisites**: Familiarity with Ruby, familiarity with RubyGems or AWS S3 a bonus
* **Programming areas include**: Ruby, AWS S3
* **Estimated difficulty level**: easy to medium
* **Student**: Hac Duy Quang Nguyen
* **Mentors**: @bronzdoc

## RubyGSOC 2020 Final Report

(Add your final report here)

## Status Updates

### Week 3 (06/19/2020)

1. What did you accomplish this past week?
    - I published a PR that composed of the full S3 functionality. The implementation I made proved to be successful in pushing, and yanking various gems.

1. What will you do this upcoming week?
    - Continue fixing bugs, and improving code style, as well as formulizing a wrapper class for abstractualization between storage backends.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - My mentor and I are working well in our discussions. One problem I face is having difficulty managing the spec environment for my tests, which uses default configurations that raise some errors. If anyone have any experience with that, it'd be great if I can hear some advice.
    
### Week 4 (06/28/2020)

1. What did you accomplish this past week?
    - I wrote a simple storage abstractualization, and was waiting for review by my mentor. 

1. What will you do this upcoming week?
    - I'll continue to improve the wrapper class, as well as investigate the bug mentioned in Week 3's update.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope. He resolved most of my confusion recently.

### Week 5 (07/06/2020)


1. What did you accomplish this past week?
    - Fixed some errors on the storage unit. Improved testing infrastructures, and configure VCR to hide security credentials.

1. What will you do this upcoming week?
    - I'll proceed on working on a GCP implementation while waiting for further review on my PR.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope.

### Week 6 (07/13/2020)


1. What did you accomplish this past week?
    - Get started on making a Google Cloud Platform client. 

1. What will you do this upcoming week?
    - I'll keep working on that while waiting for my code to be reviewed.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope.


### Week 7 (07/20/2020)

1. What did you accomplish this past week?
    - GCP is completed. Mostly functional, but I'll leave it untested for now, since the S3 code hasn't been merged yet, it'll be inefficient to work on this.

1. What will you do this upcoming week?
    - Explore a new functionality idea that display configurations.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope.

### Week 8 (07/27/2020)

1. What did you accomplish this past week?
    - Wrote and created a PR for a simple functionality called gemstash info that displays the current config. Resolved issues regarding my S3 push request.

1. What will you do this upcoming week?
    - Work on writing tests for the gemstash config command.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope.

### Week 9 (08/03/2020)

1. What did you accomplish this past week?
    - Finished tests for simple config file. It turns out to be a bit more difficult to test outputs but it's was done.

1. What will you do this upcoming week?
    - Investigate on a bug with S3 storage. 

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope.

### Week 10 (08/10/2020)

1. What did you accomplish this past week?
    - The new changes caused an error to the current rspec tests. So I updated the tests, and include all the necessary changes to vcr files for it to work.

1. What will you do this upcoming week?
    - Spend sometime on documentation for the final project evaluation.

1. What obstacles are impeding your progress?
    - None so far.

1. Would you like help from some mentor for this task?
    - Nope.

