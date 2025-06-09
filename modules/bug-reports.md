# Bugs, Bug Reporting and Triage

Status: Complete first draft

## Learning outcomes

By discussing these topics in the context of analytical thinking our aim is to:

1. Strengthen our ability to reason about and report on bugs in software systems.
2. Build some relevant communication and collaborative problem-solving skills.

## Reading

* Mozilla project documents (you will also want to read relevant documents from your OSS project)
    * [Contributors guide for writing a good bug](https://support.mozilla.org/en-US/kb/contributors-guide-writing-good-bug) for the Mozilla project
    * [Bug Writing Guidelines](https://bugzilla.mozilla.org/page.cgi?id=bug-writing.html) for the Mozilla project
    * [Bugzilla Etiquette](https://bugzilla.mozilla.org/page.cgi?id=etiquette.html)
    * [Triage for Bugzilla](https://firefox-source-docs.mozilla.org/bug-mgmt/policies/triage-bugzilla.html)
* IEEE Std 1044-2009, specifically the parts defining the terms *failure*, *fault* and *defect*.

## Class discussion

#### Terminology

We will begin our brief class discussion by reviewing some definitions so that we can be more precise in our thinking and in our discussion. This precision can help with the analytic thinking involved in "bug" reporting, debugging, fixing and troubleshooting, in part because these terms remind us of the chain of reasoning often involved in understanding a problem well enough to address it effectively.

* **Error:** A human action that produces an incorrect result. That is, a human makes a mistake, such as misunderstanding the specification while writing code.

* **Defect (or bug):** An imperfection or deficiency in a work product. For us this most often will be a flaw in the software causing it to behave incorrectly. Example defect types:

    * Memory leak or corruption defects
    * Performance or resource utilization defects
    * UI or functional defects (maybe logic related)
    * Security defects
    * Compatibility defects
    * Usability defects
    * Regression defects
    * Data defects
    * Configuration defects

* **Fault:** A manifestation of a *defect* (introduced in *error*) in software. In other words what happens internally as a result of the defect.

* **Failure:** The observable incorrect behavior of the system during execution. That is, the way the system is not meeting its specification.

* **Triage:** The process of reviewing, categorizing, prioritizing and assigning bug reports. The goal is to improve communication, ensure effort is well spent.

An example from the IEEE standard

> Problem 1: Sue calls service desk and reports she cannot log in to timesheet system because the password
field is missing from the login screen. *In this example, Sue has a problem in that she cannot log in, caused by a failure wherein the password field did not appear on the login screen, which was in turn caused by a defect inserted during coding of the Login.tsx artifact.*

Spot the *error*, *defect* and *fault* and *failure* in the following example. What type of defect is this?

> A software developer misunderstands a requirement and puts the wrong condition in an if statement for a compound interest calculation website. In a particular situation the wrong code is executed (due to the faulty logic in the conditional) and so the wrong calculation is performed. As a result of that incorrect calculation by the software the output displayed to the user is incorrect.

#### Writing bug reports

Next let's discuss together the Mozilla documents linked above. Some of the details in those documents are specific to the Mozilla project but many of the principles are generally applicable. We do not have time to discuss all of the details, but here are a few key ideas worth highlighting.

* Some guidelines are to avoid wasting triage and development time. For example, before filing check for duplicate reports and confirm bug in latest version.
* For the developer who is assigned to fix the bug report, sufficient detail to reproduce the failure is important. Many defects are only activated in fairly specific circumstances (particular settings, platform, ...). Carefully narrowing this down will be appreciated.
* The information needed will vary based on the type of defect, which may require some careful thought when filing. 
* Etiquette specifics may vary between projects, but generally "vibrant debate" is good, and it is appropriate to "criticize things" but "not people".

#### Student emails

Consider the following emails from CS 340 students. Recall that the 340 Tweeter project has multiple parts (a frontend implemented using a layered architecture, an API defined in Amazon API Gateway, AWS Lambda's running the layered backend code, DynamoDB tables, and SQS queues to support asynchronous handling of feed updates).

> "Hello professor. I have an api gateway issue that I have been trying to debug for a while now. All of the TA's who have tried to help me are sending me to you, so here I am. Sometimes my api gateway works, other times it doesn't. I've made some test gates with test lambdas, and have tried to use postman to hit my endpoints. 30% of the time is a 200, the rest are 500's. That goes for all of my endpoints"

> "I am currently working on Milestone 3, but it seems like there's an issue with my AWS setup. Even though I've followed all the instructions, I keep getting a message saying that it can't find the Lambda function. I've tried asking TAs and others about this problem, but I haven't made any progress for two days, so I decided to meet with the professor."

Naturally these emails themselves do not reflect good bug reports and so it may be hard to develop good hypotheses for the source of the problem. *But what are some possible hypotheses given just what we know from those emails?*

If you were the professor in these cases what other information would be helpful? Or if you were a developer assigned to work on these problems, what information would help you with debugging? Here are some examples:

* Detailed steps to reproduce, along with verbatim error message, comparing expected and actual behavior.
* AWS configuration information, version information, etc.
* Relevant system logs. This may include client logs, API GW logs, and Lambda logs.
* Images of CloudWatch metric graphs.
* Previous debugging/fixing attempts and their results.

(PS In the first case the issue was with insufficient reserved capacity and a couple inefficiencies. In the second case the issue was that the Lambda Handler was not configured correctly. And interestingly sometimes by trying to answer my questions students identify the defect on their own.)

## Exercise

*The following are to be completed in groups of two or three students. While you are practicing, please feel free to ask questions and start impromptu class discussions.*

Read each of the following firefox bug reports, including the attachments and discussion comments, then answer the questions below. (TODO: this is a **random** list. Something more thoughtful would be better, including a range of bug types and report quality.)

Bug reports:

* [Memory corruption issue - Access violation reading address](https://bugzilla.mozilla.org/show_bug.cgi?id=1397642)
* [worker.postMessage with a WebAssembly.Memory followed by 2 typed arrays doesn't work](https://bugzilla.mozilla.org/show_bug.cgi?id=1821582)
* [Bugzilla::Bug->depends_on_obj and Bugzilla::Bug->blocks_obj leak memory (circular reference)](https://bugzilla.mozilla.org/show_bug.cgi?id=1189374)

Questions:

* How well can you distinguish the defect, fault and failure?
* What type of defect is described?
* How effective is this report? What might improve it?
* What triage work has been done so far?

## Assignment and reflection

Individually complete the following tasks to deepen your understanding of how bugs are handled in the OSS project you have selected for this course. Reporting, discussing, reproducing and fixing bugs is one important way you may be able to contribute to that project.

* Find and review any documented policies around how to write good bug reports. Review several open and/or recently closed defects. 
* Begin helping with *triage* or *bug fixing* work in the project. This is optional as you may decide to select other ways to contribute.

Note there can be important differences between documented procedures and actual project practice. Some procedures may not be documented but can be "discovered" through observation. By reading existing bug reports and discussions, for example.

**Submit:** A one page reflection on the following questions. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* In what way is analytical thinking relevant to bug reporting and triage?
* Briefly summarize how bug reporting and fixing is handled in your OSS project. Provide some reflection on *why* things are done the way they are.
* What (if any) opportunities do you see for contributing to bug reporting and handling in your OSS project?

## Appendix

Additional email conversation with 340 student. Instructor questions in bold.

> **Is that post duplicated in the UI AND the story table or just the UI?**

> It was just in the UI but I found someone had a similar issue in slack and it was a rendering issue that needed to be resolved.

> **Not updating correctly or not updating at all? I guess the feed table can’t be updated properly without the followers/followees table being updated correctly? Right? Though I guess maybe only the “followers” are needed. I get the two mixed up ... **

> This actually ended up being an issue similar to one I had before. I noticed the request was sending a user object instead of a UserDto object so I fixed that in the front end. This fixed a lot of the issues I was having.

> **Great idea. Does the followees and feed also get updated correctly when you call the appropriate services from main.ts on your laptop?**

> **Do you mean this is what is returned from the server when you look at the responses in the network tab of your browser dev tools? Or just that the UI shows a list of undefined users and empty feed page?**

> **When you say “payloads" do you mean both the request and the response? Like, is the server returning the right json object in the response? This should help us figure out if it is a client issue or a server issue.**

> I forgot to check the actual requests and responses which helped me figure out that it was a data type issue between the client and server. After checking the requests, I was able to resolve the issue for the followees list. Once I got that working, I was able to figure out some of the logic issues I had with the feed table never getting updated with each post status.

> This should work as long as you are looking at the correct “log group”. That is, you need to find the log group for the particular lambda function that was called. Is that not what you are finding. 
Though as always, if you can debug by running the server (services, say) on your laptop that’s easiest. 

> In addition to the cloud watch logs, I would also consider checking the monitoring tab for your DynamoDB tables and lambdas. I’m not sure that is relevant in this case, but can be useful in general. For example, you can see if DB reads or writes are being “throttled”.

> In some cases, I was throwing an error before the console.log statement which meant the program stopped before it reached the print code. I'll try using the monitor tab as well in DynamoDB. Eventually, I was able to find the console.log statements — I was checking the wrong lambda function at times as well so that helped to double check that! It also really helped to be reminded to check the requests and responses for each lambda call. I was able to work out most of the bugs.

> I just have a little more to work out with the feed (it displays the logged in user's alias rather than the alias of the user who posted the status) but everything else seems to be working now for Milestone 4a. This helped a lot, thank you so much!