# Managing code and participating in code review

## Learning outcomes

In this module we will discuss collaboration from the perspective of source code repositories and code review. Specifically, we have the following intended learning outcomes.

1. Effectively use Git and GitHub as collaboration tools (this will involve somewhat advanced Git)
2. Contribute effectively to a code review process (and similar review processes)

## Reading

* [Google code review guide](https://google.github.io/eng-practices/) (please read all linked documents)

## Discussing

Collaboration around code changes, generally revolves around a source code repository such as Git/GitHub. The specifics of the process for contributing code varies between projects, but often involves a code review process.

### The Git Workflow

Here is a simple example workflow for making a change to an open-source project. But remember, every project is different! We will diagram this workflow and discuss all the nuances in class.

1. Fork the repository
    * If you are not an owner or collaborator on the project, you will need to fork your own copy of the project before you can make changes.

2. Create a branch
    * It is good practice to put all of your related changes on a new branch to keep them organized.

3. Add your commits
    * You can put all of your changes in the same commit, or split them into logical chunks. This choice can be influenced by the merge strategy you plan to use (see the step 8). Also, the project community may have a preference -- if so, always defer to it.

4. Create a PR
    * Request to merge changes from your branch on your fork into the main branch in the parent repository.
    * Pay close attention to any requirements the project has for how to format your PR.
    * This is your chance to explain your changes -- the problem you're addressing, what you did, why you did it that way, etc.
    * You may wish to create a draft PR if your changes are not complete but you want others to take a look.

5. Deal with any new commits on main
    * While you've been developing, they may have been new commits on the main branch and your branch will be behind. There are multiple ways to address this:

    1. Ignore them
        * This is only possible if there are no merge conflicts. It's also risky -- [logical merge conflicts](https://medium.com/@elischleifer/what-is-a-logical-merge-conflict-c6525acead85) do not prevent merging, but still create bugs. Some projects require PRs to be up-to-date before merging. Even if not, it doesn't hurt to be safe.
    
    2. Merge main into your branch
        * This creates a new merge commit on your branch with all the commits from main. Your branch history will be a little messier now, which may interfere with reviewers who like to review changes by commit, but it avoids rewriting the commit history.
    
    3. Rebase your branch on main
        * Rebasing is like removing all of your commits from the branch, syncing the branch with main, and then placing the commits back on top. It makes it look like your branch was created from the latest version of main. This completely rewrites your branch history and requires force-pushing to your branch, which is potentially dangerous. However, your commit history will remain clean and clear.

6. Make sure status checks pass
    * Many projects will have automated status checks that must pass before merging. These include unit tests, linting, code security scanning, etc. A project with good status checks can help you identify issues with your PR and give you confidence that it is safe to merge.

7. Pass code review
    * There's a lot to say about code reviews. We've got a whole section on it -- see below.

8. Merge
    * This will often be done by a project maintainer (someone with permissions to merge) once they are satisfied with your PR.
    * There are multiple merge strategies and every project has a different preference. You should investigate what your project uses because it may affect the best way to organize your commits.
        1. Standard merge
            * This will create a merge commit on main and join the two branches together. This can result in a complicated, nonlinear commit history on main. Every commit on your branch will appear on the main branch of the project, so if the project uses this merge strategy, it may be advisable to put all of your changes into one commit (or only a few commits) to avoid cluttering main.
        2. Squash and merge
            * This will squash all of your commits together into one commit on main. A project that uses squash-and-merge will have a clean, linear commit history on main, with each commit representing a different PR / logical change (this has many benefits, such as auto-generating release changelogs, and making bisecting easier). If the project uses this merge strategy, you can organize your changes into as many commits as you want, knowing it'll all be squashed together in the end.

### Code Reviews

* Why do code reviews? What benefits do we gain?
* Are there any drawbacks/issues with doing code reviews?
* What experience do you have with code reviews?

There are many different types of code reviews.  The Google guide describes one of them, focused reviews on small changes.  But not everyone has a large codebase that they are making small changes on.  Sometimes you have a large collection of new code.  What might be different in that kind of situation?  What would be the same?

Sometimes code reviews are performed "live" with everyone in the room.  This probably doesn't happen as much today with all the collaboration tools available to us, but it does happen in some places.  How might this change the dynamic or the interaction?


Example project specific guide:

* [Ruby pull requests](https://github.com/ruby/ruby/pulls)

### Amazon leadership principles

* [Amazon Leadership Principles](https://www.amazon.jobs/content/en/our-workplace/leadership-principles)

At Amazon there are a set of leadership principles intended to shape how people work and collaborate. I believe that many companies have similar lists of principles, but it is worth noting that at Amazon they are used heavily (during interviews and promotion cases, for example) and there is a concerted effort to maintain a culture based on those principles. Which of the following are possibly relevant to collaboration in open source projects generally, and code-review specifically?

* Customer obsession
* Ownership
* Invent and simplify
* Are right, a lot
* Learn and be curious
* Hire and develop the best
* Insist on the highest standards
* Think big
* Bias for action
* Frugality
* Earn trust
* Dive deep
* Have backbone; disagree and commit
* Deliver results
* Strive to be earth's best employer (new)
* Success and scale bring broad responsibility (new)

## Practicing

*The following is to be completed in groups of two or three students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

There will be two different practice exercises for this module.

### git practice

Practice using the git workflow discussed in class by doing the following:
1. Clone/fork the [class repository](https://github.com/jonathansillito/open-source-project-course).
2. Create a new branch
3. Edit the [selected-mentors.md](../../mentoring/selected-mentors.md) file in your branch to include the information from the members of your group.
4. Create a pull request to merge your changes into the actual repository.

Once everyone has done that, we'll merge all the pull requests as a group.

### Code Review practice



## Applying

Complete the following tasks to develop a deeper understanding of the collaborative processes used by an open source project.

1. Find and read the relevant documentation for the project.
2. Find a recently merged contribution for the project. Review in detail how that contribution came to be accepted, by tracing it through the various parts of the process. For example, there might be a pull request with discussion, a bug report with discussion, an email/message thread, etc.
3. Repeat #2, but with an unsuccessful contribution. Say starting from a pull request that was closed without being merged.
4. Familiarize yourself with any tools used for collaboration.

## Reflecting

Submit a one page reflection on the following questions. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* What are the key parts of the collaboration processes used in your open source project? Why are they there?
* What might differentiate a proposed contribution that is successful (i.e., accepted) from one that would not be successful?

