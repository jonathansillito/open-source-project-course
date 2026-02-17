# Collaboration

> "You have your agency to choose contention or reconciliation. I urge you to choose to be a peacemaker, now and always." [*Peacemakers Needed* By President Russell M. Nelson]

## Learning outcomes

1. Effectively use (project-specific) collaboration tools and processes
2. Communicate clearly and persuasively about technical topics, while engaging constructively with feedback 

> *Be an uplifting influence and an example of a believer in professional and personal relationships and collaborations*

## Reading

* [Peacemakers Needed](https://www.churchofjesuschrist.org/study/general-conference/2023/04/47nelson?lang=eng) by President Nelson

We will base our class discussion and practice examples on the Ruby project, and so here are some documents to read before class. These are short documents. Should be a very quick read.

* [Contributing to Ruby](https://docs.ruby-lang.org/en/master/contributing/contributing_md.html)
* [Making changes to Ruby](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_ruby_md.html)
* [Making Changes To Ruby Standard Libraries](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_stdlibs_md.html)

## Discussing

For those of you with software engineering work experience (through internships or part-time jobs, say), it may be interesting to compare the way collaboration and coordination happen at a typical company vs. in a typical open source project. Both the similarities and differences may be interesting. One thing that I have seen personally, is that often (not always, of course) many companies use processes to quite closely track and coordinate work (say sprint planning, daily stand up meetings, burn-down charts, etc.). Such mechanisms would be quite rare in the open source world, I suppose. *However, many collaboration related skills, tools and processes apply equally to open and closed source projects.*

For some context on collaboration, let's consider a couple example contributions to the Ruby project.

**Example 1:** The following is an example of a contribution to the Ruby project (ZJIT, in particular) that was not accepted. Though it was called a "good PR", the maintainer (reviewer) decided that it introduced too much complexity. Instead the submitter was directed to the [issue tracker](https://github.com/Shopify/ruby/issues) and recommended the reviewer get some feedback before starting on an issue. Note that this is not the general ruby issue tracker but the ZJIT project specifically. A key comment from the maintainer was: 

> "We're tracking our current issues at this [issue tracker](https://github.com/Shopify/ruby/issues). If you are interested, feel free to comment on some issue listed there and I can tell you if I think it's a good fit."

* Pull request: [ZJIT - Add SmallBitSet and LargeBitSet](https://github.com/ruby/ruby/pull/14023)
* Originated as a project TODO
* Decision: close without merge

Note: many larger projects have smaller sub-projects with separate maintainers.

**Example 2:** Despite some initial concerns from @matz (the creator of Ruby), this was approved and merged after discussion in a dev meeting. Note the use of temporary branches to test and then merge changes into the mainline.

* Pull request: [Support cause: in Thread#raise and Fiber#raise](https://github.com/ruby/ruby/pull/13967)
* Reported as bug: [https://bugs.ruby-lang.org/issues/21360](https://bugs.ruby-lang.org/issues/21360) and the related: [https://bugs.ruby-lang.org/issues/21359](https://bugs.ruby-lang.org/issues/21359) (which @matz commented on)
* Discussed and approved here: [https://github.com/ruby/dev-meeting-log/blob/master/2025/DevMeeting-2025-07-10.md#bug-21360-inconsistent-support-for-exceptioncause-in-fiberraise-and-threadraise-ioquatix](https://github.com/ruby/dev-meeting-log/blob/master/2025/DevMeeting-2025-07-10.md#bug-21360-inconsistent-support-for-exceptioncause-in-fiberraise-and-threadraise-ioquatix) (by matz during a dev meeting)
* Decision: merge

We will not discuss this now, but just for reference, here is an example of a more significant (language level change).

* [https://bugs.ruby-lang.org/issues/12912](https://bugs.ruby-lang.org/issues/12912) (adding endless range)
* [https://ruby-doc.org/core-2.6/Range.html#class-Range-label-Endless+Ranges](https://ruby-doc.org/core-2.6/Range.html#class-Range-label-Endless+Ranges)

### Tools and processes

Naturally there is significant and interesting variation in the ways that even different open source projects manage collaboration, though for many projects, the collaboration revolves around tool types (and associated processes) such as:

1. A discussion tool such as an email list
2. An issue or bug tracking systems for features requests and bug reports
3. A source code management system and repository
4. Code review tool (e.g., GitHub pull requests)

We will discuss concrete tools and processes in two submodules:

* <course-link type="page" id="P_Issues">Bugs, bug reporting and triage</course-link>
* <course-link type="page" id="P_CodeReview">Managing code and participating in code review</course-link>

However, before we do we will discuss some *soft skills* and Gospel principles that can shape how you collaborate in professional settings, including open source projects.

### Soft skills

Your ability to contribute to an open source project, will be influenced by how well you connect with people in the project, and how well you understand the culture and follow the processes used by the team. Over time your ability to contribute will be enhanced as you further develop relationships and build your reputation. Here are a couple additional thoughts:

* Not all processes are written down in sufficient detail. You learn by being involved. This might especially be true of the importance of **socializing a (coming) change**. This is true in open source projects and closed source projects too. *What does it mean to socialize a change?*

* Developing a **reputation** as someone who cares about the project, makes quality contributions and will be around to maintain those contribution overtime will enhance your influence and ability to contribute. *How can you build or hurt your reputation?*

### Gospel principles

Let's discuss insights from President Nelson's conference talk *Peacemakers Needed* and other gospel principles that would how you collaborate with others. Here are a few that came to my mind:

* "One of the easiest ways to identify a true follower of Jesus Christ is how compassionately that person treats other people."
* "His true disciples build, lift, encourage, persuade, and inspire-—no matter how difficult the situation. True disciples of Jesus Christ are peacemakers."
* "How we speak to and about others at home, at church, at work, and online really matters. Today, I am asking us to interact with others in a higher, holier way. Please listen carefully. 'If there is anything virtuous, lovely, or of good report or praiseworthy'"
* When we humble ourselves before God and pray with all the energy of our hearts, God will grant us charity.

> "My dear brothers and sisters, the best is yet to come for those who spend their lives building up others. Today I invite you to examine your discipleship within the context of the way you treat others. I bless you to make any adjustments that may be needed so that your behavior is ennobling, respectful, and representative of a true follower of Jesus Christ."

## Appendix 

As another example, consider the Linux project. It is a large complex project and they have correspondingly complex processes. It is very possible that the open source project you are contributing to will have less overhead. As you read, focus on principles, not every (minor) detail.

* [Become a Linux kernel contributor - Part 1](https://hackerbikepacker.com/kernel-contributor-1)
* [Become a Linux kernel contributor - Part 2](https://hackerbikepacker.com/kernel-contributor-2)
* [Become a Linux kernel contributor - Part 3](https://hackerbikepacker.com/kernel-contributor-3)