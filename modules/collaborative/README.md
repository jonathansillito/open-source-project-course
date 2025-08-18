# Collaboration

Status: Initial draft

> "You have your agency to choose contention or reconciliation. I urge you to choose to be a peacemaker, now and always." [*Peacemakers Needed* By President Russell M. Nelson]

## Learning outcomes

1. Effectively use Git and GitHub as collaboration tools (this will involve somewhat advanced Git)
2. Prepare to follow the project-specific collaboration processes and tools of an open source project
3. Identify Gospel principles that are relevant in our professional interactions

## Reading

* [Peacemakers Needed](https://www.churchofjesuschrist.org/study/general-conference/2023/04/47nelson?lang=eng)

We will base some of our discussion today on tools and processes used by the Linux project. It is a large complex project and they have correspondingly complex processes. It is very possible that the open source project you are contributing to will have less overhead. As you read, focus on principles, not every (minor) detail.

* [Become a Linux kernel contributor - Part 1](https://hackerbikepacker.com/kernel-contributor-1)
* [Become a Linux kernel contributor - Part 2](https://hackerbikepacker.com/kernel-contributor-2)
* [Become a Linux kernel contributor - Part 3](https://hackerbikepacker.com/kernel-contributor-3)

Advanced Git commands

* Branching and keeping a branch up to date
* Cleaning up local Git history
* Submitting a GitHub pull request

## Discussing

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

**Example 3 (big change):** Naturally, the coordination effort for more significant changes would be, well more significant. (PEP or ...)

### Soft skills

Your ability to contribute to an open source project, will be influenced by how well you connect with people in the project, and how well you understand the culture and follow the processes used by the team. Over time your ability to contribute will be enhanced as you further develop relationships and your reputation. Here are a couple additional thoughts:

* Not all processes are written down in sufficient detail. You learn by being involved. This might especially be true of the importance of **socializing a (coming) change**. This is true in open source projects and closed source projects too. By socializing a change we mean ...

* Developing a **reputation** as someone who cares about the project, makes quality contributions and will be around to maintain those contribution overtime will enhance your influence and ability to contribute. *How can you build or hurt your reputation?*

### Gospel principles

Before getting in to the practice section, let's discuss insights from President Nelson's conference talk *Peacemakers Needed* and other gospel principles that would how you collaborate with others. Here are a few that came to my mind:

* "One of the easiest ways to identify a true follower of Jesus Christ is how compassionately that person treats other people."
* "His true disciples build, lift, encourage, persuade, and inspire-—no matter how difficult the situation. True disciples of Jesus Christ are peacemakers."
* "How we speak to and about others at home, at church, at work, and online really matters. Today, I am asking us to interact with others in a higher, holier way. Please listen carefully. 'If there is anything virtuous, lovely, or of good report or praiseworthy'"
* When we humble ourselves before God and pray with all the energy of our hearts, God will grant us charity.

> "My dear brothers and sisters, the best is yet to come for those who spend their lives building up others. Today I invite you to examine your discipleship within the context of the way you treat others. I bless you to make any adjustments that may be needed so that your behavior is ennobling, respectful, and representative of a true follower of Jesus Christ."

## Practicing

*The following is to be completed in groups of two or three students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

Work through the the following activities using Git and GitHub. These activities reflect a generic, but plausible workflow that considers the collaborative aspects of contributing to a project. Note that we will discuss more about authoring bug reports and working through code reviews later in the course.

### Step 1: Claim a task

* For this exercise we will all be working on the same issue ...

### Step 2: Work on a change 

* Create a branch based on the mainline of the project
* Follow project specific style guide and make changes (perhaps using multiple commits for the sake of having something to clean up in the next step)

To begin work clone the repository and create a *local* branch to use for your change. There are different approaches that used of course, but for various reasons (for example, you may have more than one change on the go) it can be convenient to make your changes in a separate branch until the are tested and reviewed and merged.

```
git clone ...
git branch issue-1234
```

As you work you can commit your work to the local branch and also synchronize your work from the master branch (as appropriate), which can limit the merge conflicts that can come if your local branch and the master branch diverge in important ways.

```
git commit -am "..."
git checkout master
git pull origin master
get checkout issue-1234
git merge master
```

Or if you want to keep your history more clean you can use rebase to make it look like your local commits are after the latest commit to master (so this is an alternative to merge). I assume that for many projects this would be appreciated for commits that have never been pushed to any shared repository.

```
git rebase master
```

### Step 3: Prepare and submit pull request

* Double check style guide and other project specific instructions
* Pull from main to make your change easier for reviewers to merge (this can be done as you go ...)
* Clean up you commit history to make the submission as clean as possible


### Step 4: Revise and update pull request

* Use the GitHub pull request tool as a discussion forum (find something to change)
* Revise and update pull request

### Step 5: Merge

* Find issue, discuss, take ownership, ...
* Branch, build, test locally 
* Create and submit pull request; revise and update pull request (clean up your history)
* Review other's pull request (including testing locally) and merge when ready

## Applying

Complete the following tasks to develop a deeper understanding of the collaborative processes used by an open source project.

1. Find and read the relevant documentation for the project. Examples of the type of documents we mean are listed below for the Ruby language project. The set of documents for your project will be different.
2. Find a recently merged contribution for the project. Review in detail how that contribution came to be accepted, by tracing it through the various parts of the process. For example, there might be a pull request with discussion, a bug report with discussion, an email/message thread, etc.
3. Repeat #2, but with an unsuccessful contribution. Say starting from a pull request that was closed without being merged.
4. Install and familiarize yourself with any tools used for collaboration.

## Reflecting

Submit a one page reflection on the following questions. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* What are the key parts of the collaboration processes used why are they there?
* What might differentiate a proposed contribution that is successful from one that would not be successful?

## Appendix

Ruby

* [Contributing to Ruby](https://docs.ruby-lang.org/en/master/contributing/contributing_md.html)
* [Making changes to Ruby](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_ruby_md.html)
* [Making Changes To Ruby Standard Libraries](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_stdlibs_md.html)
* [Reporting Ruby bugs](https://docs.ruby-lang.org/en/master/contributing/reporting_issues_md.html)
* [Ruby pull requests](https://github.com/ruby/ruby/pulls)
