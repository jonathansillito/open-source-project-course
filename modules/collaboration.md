# Collaboration

Status: Initial draft

> "You have your agency to choose contention or reconciliation. I urge you to choose to be a peacemaker, now and always." [*Peacemakers Needed* By President Russell M. Nelson]

## Learning outcomes

1. Effectively use (project-specific) collaboration tools and processes
2. Identify Gospel principles that are relevant in our professional interactions

## Reading

* [Peacemakers Needed](https://www.churchofjesuschrist.org/study/general-conference/2023/04/47nelson?lang=eng)

We will base some of our discussion today on tools and processes used by the Linux project. It is a large complex project and they have correspondingly complex processes. It is very possible that the open source project you are contributing to will have less overhead. As you read, focus on principles, not every (minor) detail.

* [Become a Linux kernel contributor - Part 1](https://hackerbikepacker.com/kernel-contributor-1)
* [Become a Linux kernel contributor - Part 2](https://hackerbikepacker.com/kernel-contributor-2)
* [Become a Linux kernel contributor - Part 3](https://hackerbikepacker.com/kernel-contributor-3)

Ruby

* [Contributing to Ruby](https://docs.ruby-lang.org/en/master/contributing/contributing_md.html)
* [Making changes to Ruby](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_ruby_md.html)
* [Making Changes To Ruby Standard Libraries](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_stdlibs_md.html)
* [Reporting Ruby bugs](https://docs.ruby-lang.org/en/master/contributing/reporting_issues_md.html)
* [Ruby pull requests](https://github.com/ruby/ruby/pulls)

## Discussing

TODO: PEP mechanisms, "what does it take to change Python"

For those of you with software engineering work experience (through internships or part-time jobs, maybe), it may be interesting to compare the way collaboration and coordination happen at a typical company vs. in a typical open source project. Both the similarities and differences may be interesting. One thing that I have seen personally, is that often (not always, of course) many companies use processes to quite closely track and coordinate work (say sprint planning, daily stand up meetings, burn-down charts, etc.). Such mechanisms would be quite rare in the open source world, I suppose.

### Collaboration/coordination tools

* Communication tools: Email list(s) and/or discussion list(s)
* Issue or bug tracking systems such as Jira (at a company). Later in the course we will talk more about [writing effective bug reports](bug-reports.md).
* Source code management systems such as Git, CI tooling, etc. The role of branches is worth paying attention to in many projects. (E.g., long lived [Ruby branches](https://www.ruby-lang.org/en/downloads/branches/))
* Code review tools. Later in the course we will discuss code review further, including how to engage constructively with feedback.

### Example contributions

**Example 1:** The following is an example of a contribution to the Ruby project (ZJIT, in particular) that was not accepted. Though it was called a "good PR", the maintainer (reviewer) decided that it introduced too much complexity. Instead the submitter was directed to the [issue tracker](https://github.com/Shopify/ruby/issues) and recommended the reviewer get some feedback before starting on an issue. Note that this is not the general ruby issue tracker but the ZJIT project specifically. Note: many larger projects have smaller sub-projects with separate maintainers. A key comment from the maintainer was: 

> "We're tracking our current issues at this [issue tracker](https://github.com/Shopify/ruby/issues). If you are interested, feel free to comment on some issue listed there and I can tell you if I think it's a good fit."

* Pull request: [ZJIT - Add SmallBitSet and LargeBitSet](https://github.com/ruby/ruby/pull/14029)
* Originated as a project TODO
* Decision: close without merge

**Example 2:** Despite some initial concerns from @matz (the creator of ruby), this was approved and merged after discussion in a dev meeting. Note the use of temporary branches to test and then merge changes into the mainline.

* Pull request: [Support cause: in Thread#raise and Fiber#raise](https://github.com/ruby/ruby/pull/13967)
* Reported as bug: https://bugs.ruby-lang.org/issues/21360 and the related: https://bugs.ruby-lang.org/issues/21359 (which @matz commented on)
* Discussed and approved here https://github.com/ruby/dev-meeting-log/blob/master/2025/DevMeeting-2025-07-10.md#bug-21360-inconsistent-support-for-exceptioncause-in-fiberraise-and-threadraise-ioquatix (by matz during a dev meeting)
* Decision: merge

### Soft skills

Your ability to contribute to an open source project, will be influenced by how well you connect with people in the project, and how well you understand the culture and follow the processes used by the team. Over time your ability to contribute will be enhanced as you further develop relationships and your reputation. Here are a couple additional thoughts:

* Not all processes are written down in sufficient detail. You learn by being involved. This might especially be true of the importance of **socializing a (coming) change**. This is true in open source projects and closed source projects too. By socializing a change we mean ...

* Developing a **reputation** as someone who cares about the project, makes quality contributions and will be around to maintain those contribution overtime will enhance your influence and ability to contribute. *How can you build or hurt your reputation?*

### Gospel principles

Before getting in to the practice section, let's discuss insights from President Nelson's conference talk *Peacemakers Needed* and other gospel principles that would ...

## Practicing

*The following is to be completed in groups of two or three students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

Work through the the following activities using Git and GitHub.

* Branch, build, test locally 
* Create and submit pull request; revise and update pull request
* Review other's pull request (including testing locally) and merge when ready

## Applying

* Read docs
* Trace a successful contribution
* Trace a (un|less)successful contribution

## Reflecting

