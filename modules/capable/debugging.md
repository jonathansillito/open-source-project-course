# Debugging tools and techniques

Status: Overview with many details missing. We need to find some code for the students to use in the debugging exercise, and we need to decide what to discuss as a class.

## Learning outcomes

By discussing and practicing debugging in the context of analytical thinking our aim is to:

1. Improve our ability to systematically investigate (using appropriate information gathering) complex system problems.
2. Use logical reasoning to identify defects and propose fixes.

## Reading

* Chapter from the pragmatic programer or similar resource
* Instructions for setting up a debugger for the exercise below

## Class discussion

Think about difficult debugging problems you have faced in the past. What made them difficult? What approach did you try (possibly an approach that was not effective)? How did you (or the TA or whoever) ultimately find the defect?

Possible discussion topics:

* Gathering and evaluating information critically
* Recognizing patterns, relationships, or inconsistencies
* Making reasoned judgments based on evidence
* Breaking problems into components to tackle them systematically
* Tooling and information sources
* Practical strategies and tips

## Exercise

*The following are to be completed in groups of two or three students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

Given a small system with one or more defects illustrated by some failure, do the following in a loop (you do not need to follow a strict order).

1. Generate one or more hypotheses (read code, ...)
2. Test and investigate methodically (vary inputs, use debugger, write test cases)
3. Review results and (newly) available information

Continue with the above activities until you can (1) isolate the defect, (2) explain the circumstances under which it is activated, and (3) propose a fix. Time permitting you can make the fix and test

## Post exercise discussion

Once the exercise is complete, as a class we will discuss questions such as:

* What tooling was most helpful in this case? What is it about this case that made those the most valuable?
* What hypotheses were considered? 
* What strategies did you use to narrow down the issue?

## Assignment and reflection

Individually complete the following tasks to deepen your understanding of how to debug issues in the OSS project you have selected for this course. 

* Build the software and execute it in a debugger, setting breakpoints and exploring the code.
* Explore the logging configuration and logging used by the software.
* Identify the key (top level) error handling strategies used by the software.

**Submit:** A one page reflection on the following topics. TODO...