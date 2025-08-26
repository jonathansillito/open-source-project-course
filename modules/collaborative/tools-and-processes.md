# Collaboration tools and processes

## Learning outcomes

1. Effectively use Git and GitHub as collaboration tools (this will involve somewhat advanced Git)
2. Prepare to follow the project-specific collaboration processes and tools of an open source project

## Reading

We will base our class discussion and practice examples on the Ruby project, and so here are the 

* [Contributing to Ruby](https://docs.ruby-lang.org/en/master/contributing/contributing_md.html)
* [Making changes to Ruby](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_ruby_md.html)
* [Making Changes To Ruby Standard Libraries](https://docs.ruby-lang.org/en/master/contributing/making_changes_to_stdlibs_md.html)
* [Reporting Ruby bugs](https://docs.ruby-lang.org/en/master/contributing/reporting_issues_md.html)
* [Ruby pull requests](https://github.com/ruby/ruby/pulls)

## Discussing

For those of you with software engineering work experience (through internships or part-time jobs, say), it may be interesting to compare the way collaboration and coordination happen at a typical company vs. in a typical open source project. Both the similarities and differences may be interesting. One thing that I have seen personally, is that often (not always, of course) many companies use processes to quite closely track and coordinate work (say sprint planning, daily stand up meetings, burn-down charts, etc.). Such mechanisms would be quite rare in the open source world, I suppose.

* What similarities and differences have you seen so far?

Here are some categories of tools that are often central to a project's collaborative processes.

    * Communication tools: Email list(s) and/or discussion list(s)
    * Issue or bug tracking systems such as Jira (at a company). Elsewhere in the course we will talk more about [writing effective bug reports](../capable/bug-reports.md).
    * Source code management systems such as Git, CI tooling, etc. The role of branches is worth paying attention to in many projects. (E.g., long lived [Ruby branches](https://www.ruby-lang.org/en/downloads/branches/))
    * Code review tools. Later in the course we will discuss code review further, including how to engage constructively with feedback.

### Example contributions

To illustrate a few things about the Ruby project and collaboration more generally, let's discuss a couple example contributions (the first of which was not accepted).

**Example 1:** The following is an example of a contribution to the Ruby project (ZJIT, in particular) that was not accepted. Though it was called a "good PR", the maintainer (reviewer) decided that it introduced too much complexity. Instead the submitter was directed to the [issue tracker](https://github.com/Shopify/ruby/issues) and recommended the reviewer get some feedback before starting on an issue. Note that this is not the general ruby issue tracker but the ZJIT project specifically. A key comment from the maintainer was: 

> "We're tracking our current issues at this [issue tracker](https://github.com/Shopify/ruby/issues). If you are interested, feel free to comment on some issue listed there and I can tell you if I think it's a good fit."

* Pull request: [ZJIT - Add SmallBitSet and LargeBitSet](https://github.com/ruby/ruby/pull/14029)
* Originated as a project TODO
* Decision: close without merge

Note: many larger projects have smaller sub-projects with separate maintainers.

**Example 2:** Despite some initial concerns from @matz (the creator of ruby), this was approved and merged after discussion in a dev meeting. Note the use of temporary branches to test and then merge changes into the mainline.

* Pull request: [Support cause: in Thread#raise and Fiber#raise](https://github.com/ruby/ruby/pull/13967)
* Reported as bug: https://bugs.ruby-lang.org/issues/21360 and the related: https://bugs.ruby-lang.org/issues/21359 (which @matz commented on)
* Discussed and approved here https://github.com/ruby/dev-meeting-log/blob/master/2025/DevMeeting-2025-07-10.md#bug-21360-inconsistent-support-for-exceptioncause-in-fiberraise-and-threadraise-ioquatix (by matz during a dev meeting)
* Decision: merge

**Example 3 (big change):** Next let's discuss a language level change (adding an endless range `(1..)`): https://bugs.ruby-lang.org/issues/12912 and https://ruby-doc.org/core-2.6/Range.html#class-Range-label-Endless+Ranges

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

This practice is continued in the [code review submodule](code-review.md)...

## Applying

Complete the following tasks to develop a deeper understanding of the collaborative processes used by an open source project.

1. Find and read the relevant documentation for the project. Examples of the type of documents we mean are listed below for the Ruby language project. The set of documents for your project will be different.
2. Find a recently merged contribution for the project. Review in detail how that contribution came to be accepted, by tracing it through the various parts of the process. For example, there might be a pull request with discussion, a bug report with discussion, an email/message thread, etc.
3. Repeat #2, but with an unsuccessful contribution. Say starting from a pull request that was closed without being merged.
4. Familiarize yourself with any tools used for collaboration.

## Reflecting

Submit a one page reflection on the following questions. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* What are the key parts of the collaboration processes used in your open source project? Why are they there?
* What might differentiate a proposed contribution that is successful (i.e., accepted) from one that would not be successful?

## Appendix 

As another example, consider the Linux project. It is a large complex project and they have correspondingly complex processes. It is very possible that the open source project you are contributing to will have less overhead. As you read, focus on principles, not every (minor) detail.

* [Become a Linux kernel contributor - Part 1](https://hackerbikepacker.com/kernel-contributor-1)
* [Become a Linux kernel contributor - Part 2](https://hackerbikepacker.com/kernel-contributor-2)
* [Become a Linux kernel contributor - Part 3](https://hackerbikepacker.com/kernel-contributor-3)
