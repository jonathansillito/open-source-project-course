# Managing code and participating in code review

## Learning outcomes

1. Effectively use Git and GitHub as collaboration tools (this will involve somewhat advanced Git)
2. Contribute effectively to a code review process (and similar review processes)

## Reading
 
* [Ruby pull requests](https://github.com/ruby/ruby/pulls)

## Discussing

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

### Step 4: Revise and update pull request

* Use the GitHub pull request tool as a discussion forum (find something to change)
* Revise and update pull request

### Step 5: Merge

* Find issue, discuss, take ownership, ...
* Branch, build, test locally 
* Create and submit pull request; revise and update pull request (clean up your history)
* Review other's pull request (including testing locally) and merge when ready

## Applying [TODO]

Complete the following tasks to develop a deeper understanding of the collaborative processes used by an open source project.

1. Find and read the relevant documentation for the project. Examples of the type of documents we mean are listed below for the Ruby language project. The set of documents for your project will be different.
2. Find a recently merged contribution for the project. Review in detail how that contribution came to be accepted, by tracing it through the various parts of the process. For example, there might be a pull request with discussion, a bug report with discussion, an email/message thread, etc.
3. Repeat #2, but with an unsuccessful contribution. Say starting from a pull request that was closed without being merged.
4. Familiarize yourself with any tools used for collaboration.

## Reflecting [TODO]

Submit a one page reflection on the following questions. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* What are the key parts of the collaboration processes used in your open source project? Why are they there?
* What might differentiate a proposed contribution that is successful (i.e., accepted) from one that would not be successful?

