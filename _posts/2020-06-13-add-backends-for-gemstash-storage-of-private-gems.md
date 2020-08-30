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

Hello everyone, my name is Quang, or you can call me James. I’m a sophomore at the University of Massachusetts Amherst. This summer I had the incredible opportunity to participate in Google’s 2020 Summer of Code program. Below is a short report on what I’ve accomplished during the months from May - August, 2020.

Project Description:
Develop an Amazon S3 cloud storage backend that would allow users to store gems seamlessly across machines for the gemstash application.

My 2020 Summer of Code can be broken into three phases, the planning, building, and finalizing. The general work timeline is based on the timeline proposed in my accepted proposal, which can be found [here](https://summerofcode.withgoogle.com/dashboard/project/4662895368994816/details/).

### The Planning Stage:

First, I spent a lot of my time familiarizing with the codebase. Gemstash is one of the smaller repositories, but it was filled with gems and codes that I haven’t seen before. From the setup commands to how each gem is pushed and yanked, I carefully dissected the code to make sure I knew how each component interacts with each other.

Then, I spent a fair bit of time researching and reading on the AWS SDK Documentation. It was important to read most of all of the methods it provided, and how each of them work.

I set out to build a small sample S3 Client to test out the various uploading and deleting functions. And I managed to upload small text files using a free student membership I registered with Amazon S3 Storage.

During this stage, my goals were:

- Familiarize with the AWS S3 Ruby SDK
- Build a functioning S3 Client that features uploading and downloading of various files.
- Gain a deep understanding of the gemstash code base and all of its related functions and features.

### The Building Stage:

The S3 Storage concept is no new idea to [Gemstash](https://github.com/rubygems/gemstash). A cloud storage implementation was a topic of discussion years ago but wasn’t consistently worked on. It was mentioned in previous pull requests such as [#159](https://github.com/rubygems/gemstash/pull/159) and [#242](https://github.com/rubygems/gemstash/pull/242) on the Gemstash repository. As with the nature of most open source contributions, those pull requests are unfinished and have been inactive for months, if not years. So I opened a new pull request for my [S3 backend implementation](https://github.com/rubygems/gemstash/pull/270) and dive into work.

This stage is when I discovered the most important process of building any software, debugging. I’ve never had the experience of debugging a large codebase like this before, and it was certainly an arduous process to learn from. Sometimes the hardest problems have the easiest solutions that you simply didn’t notice. It is easy to get a simple client running but working with other parts of a larger program is certainly difficult. Many of the issues took days to figure out, and fixed. One of the error trace, for example was this.

![](https://user-images.githubusercontent.com/52845974/91579435-ce4fc080-e975-11ea-829c-0615148dacbf.png)

Originally, my code had successfully initialize a storage component given the correct credentials. However, the module was failing afterwards because it couldn't seem to locate the a certain method called 'gemstash_env' , in which I imported from another module. After following the error trace, I figured out that the storage client had relied on a method that rebuilds the storage instance by calling a previous storage instance to append a new folder name. This little interaction meant that the code needed to not just extend but include the Gemstash::Env module. As a developing engineer, it was an important lesson on recognizing the importance of correctly importing module code.

```jsx
class S3
    extend Gemstash::Env::Helper
    include Gemstash::Env::Helper
```

Once I had the component running without immediate breakage, I knew I was heading towards the right direction. The next target was to manually upload, delete, and download gems from the cloud storage without major errors. During this process, it really shows how easily software can break from just the littlest of mistakes.

![](https://user-images.githubusercontent.com/52845974/91579174-6a2cfc80-e975-11ea-97e4-9239dec9ed8b.png)

Here's a photo of another bug I encountered. Previously, my code was trying to fetch a gem file that was uploaded to AWS and compare it to the original gem file content that was saved on my disk. Despite the code running correctly, the comparison was failing. Upon closer inspection, and manually inspecting each element, it turns out that the content fetched from AWS are automatically encoded in UTF-8, while the content is encoded in ASCII-8BIT. This resulted for me to simply add a small adjustment to the read file method to include a method called .b, like so.

```ruby
def read_file(filename)
      @s3resource.object(filename).get.body.read.b
end
```

By June 18, I successfully surpassed my Phase 1 Milestones.

- [ ]  **Phase 1 Evaluation milestones:**
    - [x]  S3 Client with a working connection and core functionalities:
    - [x]  Upload a gem
    - [x]  Download a gem
    - [x]  Delete a gem
    - [x]  S3 service that can manually upload and download a gem from an S3 bucket

The next few weeks were spent on a key step in building any robust code, writing tests.

Working with an external API proved to be a challenge because I was faced with a design decision to either try to stub all of the methods associated with AWS S3 or to add integration tests and utilize HTTP interactions recording to run these tests offline. After a few days of personal research and tinkering, I consulted this decision with other Ruby mentors -  [@bronzdoc](https://github.com/bronzdoc), [@hiren](https://github.com/hmistry), [@ioquatix](https://github.com/ioquatix), [@aditya](https://github.com/sonalkr132) - about what is appropriate. I decided to settle with VCR, and Webmock, a pair of gems that would allow HTTPs recording on all external API calls made to AWS.

After a week or two writing all of the tests, running them, debugging, and then testing them, another piece of my Phase 2 milestone was checked off.

- [ ]  **Phase 2 Milestones**
    - [x]  Unit Tests
    - [x]  Gemstash's core functionality works with S3

Once that was done, all that was left before it was ready was to add the S3 to the existing CLI setup process for gemstash and prepare a storage wrapper class for dynamic switching between the local storage and S3 storage.

- [ ]  **Phase 2 Milestones**
    - [x]  Unit Tests
    - [x]  Gemstash's core functionality works with S3
    - [x]  Basic CLI for Setup
    - [x]  Complete wrapper class with configuration to choose between S3 and local storage

### The Finalizing Stage:

The next month or so was spent answering and fixing all the necessary code reviews from my mentor [@bronzdoc](https://github.com/bronzdoc) and  [@indirect](https://github.com/indirect) . Eventually I had some extra time to work on other stretch goal achievements that was, develop the Google Cloud Platform implementation. Currently, a functional [GCP implementation](https://github.com/rubygems/gemstash/pull/275) is posted as a pull request in the Gemstash repository. It will need some extra work writing tests for the storage and a bit more minor fixes. This pull request couldn’t be finished because the S3 pull request took longer than expected to be reviewed and merge.

Another stretch goal I attempted was to create a new command for Gemstash called

```ruby
$ gemstash info
```

The aim of the command is simply to print out the current configuration setup which would improve the user experience overall.

Towards of the end of the GSOC experience, I spent time writing this final report and some documentation for the work I’ve done. I also spent a little bit of time writing a bit of documentation for the Rubygems guides, which added Gemstash as an option for hosting your own gem server.

All in all, I’m glad that I was able to reach my personal milestones and complete my goals. I’d like to say that I’m really glad to be participating in the 2020 Summer of Code program. I would like to thank my mentor [@bronzdoc](https://github.com/bronzdoc) for mentoring me throughout this journey, and [@indirect](https://github.com/indirect) for providing us with this opportunity to work for the Rubygems organization.  And to everyone who have also helped me [@hiren](https://github.com/hmistry), [@ioquatix](https://github.com/ioquatix), [@aditya](https://github.com/sonalkr132), I appreciate your support very much.

Most importantly, thank you to Google for hosting this program and providing me with this opportunity. In the three months of the program, I felt like I've learn a lot of things that helped me grow as a developer. The program taught me how to work in a professional environment, and how to communicate my code with another engineer. It also taught me the fundamentals of software backend design, integration testings, and external API utilization. After this program, I hope I can take what I've learned to inspire others to contribute to open source and also keep contributing to the open-source community myself, whether it is through the Gemstash repository or many more.

### **Status of Work:**

- (Project Goal) S3 pull request is ready to be merged, all tests are passing, and it is waiting for the codebase to fix an internal issue before it can be approved and merged by maintainers.
- (Stretch Goal) Google Cloud Platform pull request needs more work on tests, and minor fixes.
- (Stretch Goal) Gemstash Info Command was merged.
- (Stretch Goal) RubyGems documentation is awaiting for approval by maintainers.

### Important links to my work:

- Gemstash repository
[https://github.com/rubygems/gemstash](https://github.com/rubygems/gemstash)
- Amazon S3 Storage Backend Implementation
[https://github.com/rubygems/gemstash/pull/270](https://github.com/rubygems/gemstash/pull/270)
- Google Cloud Backend Implementation
[https://github.com/rubygems/gemstash/pull/275](https://github.com/rubygems/gemstash/pull/275)
- Gemstash Info Command
[https://github.com/rubygems/gemstash/pull/274](https://github.com/rubygems/gemstash/pull/274)
- RubyGems Guide documentation
[https://github.com/rubygems/guides/pull/266](https://github.com/rubygems/guides/pull/266)
- My GSOC Project Proposal
[https://summerofcode.withgoogle.com/dashboard/project/4662895368994816/details/](https://summerofcode.withgoogle.com/dashboard/project/4662895368994816/details/)


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

