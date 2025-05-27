# Code Archeology

Status: Under development

*Note: Code or Software Archeology may not be the best term as it specificly refers to working with undocmumented legacy code.  But sometimes that describes an open source project. :-)*

## Meeting notes

Topics to cover

* Focus on tools and techniques for code investigation
* How is a feature implemented
* How and where should this new feature be implemented
* High-level understanding of architecture and design (including rationale)
* Necessary domain knowledge

## JS NOTES

Thanks for the draft Tom. Here are some initial thoughts and/or questions.

* Would it make sense to talk about learning programming languages and frameworks in this context? Or would that be better in its own module? Of course it is hard to understand a code base if you don't understand the programming languages, key frameworks, et.

* One thing I was thinking about (that may be worth considering as we refine this topic) is that code archeology is a fairly general term and it may be worth considering thinking about more specific versions. So for example ...

  * Questions based vs. task based vs. general familiarization vs. design rationale ...
  * Static structure vs. control flow vs. data flow

* Also, would it help to refine the exercise perhaps by giving the students a couple questions to answer or tasks to perform or ?

* Consider adding: how to ask good questions (of project participants, say)

## Learning outcomes
By discussing code archeology, our aim is to:

1. Learn how to explore a code base to understand how it works
2. Explore tools that will allow us to examine unfamiliar code bases.
3. Understand the need to communicate with others (developers, users, etc.) in order to fully understand issues and the code being studied.

## Reading
Some possible readings. Not all of them are necessarily for the students.
* [Software Archeology Wikipidea article](https://en.wikipedia.org/wiki/Software_archaeology)
* [The Code Archeololgist](https://www.profocustechnology.com/software-development/the-code-archaeologist/) - More about the need to be able to dive into old code bases and the challenges you might face
* [Code archeology. A study of how the code got to its present state.](https://craiglrock.com/code-archeology/) - Practices to get up to speed on a code base.  It is in the context of learning how the code got to where it is but applies to just understanding the code as well.
* [CMU lecture on Code Archeology](https://cmu-313.github.io/_old/F22/assets/pdfs/04-code-archaeology.pdf) - Not necessarily a student reading but useful for lecture/discussion points.
* [How to learn a code base quickly (reddit post)](https://www.reddit.com/r/learnprogramming/comments/89pjdy/how_to_learn_a_new_codebase_quickly/)
* [How to Approach a New Codebase(blogpost)](https://amberwilson.co.uk/blog/how-to-approach-a-new-codebase/)
* [How to understand an existing code-base(blogpost)](https://medium.com/the-curious-coder/how-to-understand-an-existing-code-base-65989642baae)
* [How to Get Familiar with an Existing Codebase(blogpost)](https://dev.to/isaactony/how-to-get-familiar-with-an-existing-codebase-49k5)


## Class discussion
Questions to start class:
* What does it mean to you when you hear the phrase "code archeology?"
* Have you ever had to dive into and use or edit code you didn't write?  
  * What was the context?
  * What problems/challenges/hurdles did you have to overcome?
  * What tool/techniques did you use to get up to speed?

Before you can start making changes to code, you need to understand it.  There are a number of things to look at when you are trying to understand a new code base:
* **Context** - Why was the code written? What is its purpose? What expectations are there about its use?
* **Design & Architecture** - How is the project organized?  Are there patterns?  What external dependencies exist?  What internal dependencies?
* **Documentation** - How is the code documented?  Is external documentation up-to-date?  Where can you find it?  Is the code commented cleanly?
* **Personnel** - Are the original developers still part of the project?  How do you reach out to them with questions?
* **Build Process** - How do you build the code?  What technologies does it use?

As you start to learn the code, how do you effectively navigate it and generate understanding?
* **Evaluate your Assumptions** - Were the things you assumed about the code correct?  What did you learn that was different?
* **Use your IDE's tools** - "Go to Definitions" and "Go to Uses" are goint to be your friend.
* **Run the code** - See how it behaves, run it through profilers to see what classes/functions are heavily used, run it in the debugger and step through to the program flow.
* **Look at the tests** - these will often indicate what the developers felt were the most important aspects, especially if the project lacks 100% test coverage.
* **Take copious notes** - Record the things you learn.


## Exercise
The purpose here is to actually spend some time in a large, unfamiliar codebase.  All the students will be in the same codebase but working in small groups of 2-3 people.  

Spend 15-20 minutes exploring the code to see what you can learn about it.  In your group, identify questions you have about the code and try to find the answers.

## Post exercise discussion
After everyone has spent some time in the codebase, the groups should compare notes.  Some possible questions that may prompt discussion are:
* What did you learn about the codebase?  What was clear?  What was confusing?
* What patterns do you see?
* Can you determine any dependencies for the code?
* How is it organized?  Why do you think it is organized that way?
* Did you look at documentation?  Was it clear? Was it up-to-date?
* Were you able to build and run the code?
* What do you think you need to learn to make progress?
* Could you identify people you might ask about the code?


## Assignment and reflection
Spend a couple of hours exploring the code for the project you've selected.  Submit a one-page reflection that addresses the following questions:
* What did you do to explore the code base?
* What are two (or more) things you learned about the project?
* How are you documenting what you learned?
* What next steps are you planning to increase your understanding? 
