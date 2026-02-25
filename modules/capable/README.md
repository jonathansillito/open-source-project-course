# Capable

## Learning outcomes

The capabilities we are focusing on our this module are analytical thinking and writing. The goal is to help us all get better at solving complex technical problems and communicating about technical topics. More specifically, we hope that students will be able to:

1. Apply the principles of analytical thinking in the context of debugging and troubleshooting
2. Communicate technical ideas through effective writing

* *Develop talents with diligence, faith, resilience, humility, and a desire to grow*

## Reading

* ["Do Your Part with All Your Heart"](https://www.churchofjesuschrist.org/study/general-conference/2025/10/16uchtdorf?lang=eng) by Elder Dieter F. Uchtdorf
* [Slack incident: Everyone back to work](https://slack.engineering/slacks-outage-on-january-4th-2021/)

The following is **optional** reading you may find interesting:

* [Details of the Cloudflare outage on July 2, 2019](https://blog.cloudflare.com/details-of-the-cloudflare-outage-on-july-2-2019/)
* [GitHub October 21 post-incident analysis](https://github.blog/news-insights/company-news/oct21-post-incident-analysis/)
* [Roblox Return to Service](https://corp.roblox.com/newsroom/2022/01/roblox-return-to-service-10-28-10-31-2021)

## Class discussion (analytical thinking)

Analytical thinking is the ability to break down complex information or problems into smaller, more manageable parts in order to understand them, identify patterns, draw logical conclusions, and solve problems effectively. In general, analytical thinking may involve steps such as: 

1. Observation – Gathering relevant data and identifying key details.
2. Decomposition – Breaking a problem into smaller components.
3. Pattern Recognition – Finding trends, anomalies, or relationships.
4. Logical Reasoning – Making inferences, identifying causes, and drawing conclusions.
5. Evaluation – Assessing evidence, arguments, and solutions objectively.

#### Troubleshooting at Slack

To introduce these ideas we will discuss the Slack incident linked above. This incident is an example of a collaborative troubleshooting activity or a collaborative analytical thinking activity. Here are some questions to loosely guide our discussion.

* What was the cause of the incident? Please think beyond a single root cause.
* How was it identified and mitigated? What tooling and information was used in the process?
* What aspects of analytical thinking are illustrated in this incident report? 

## Modules

In the following module we will discuss and practice analytical thinking in the context of debugging code:

* <course-link type="page" id="P_Debugging">Debugging tools and techniques</course-link>

Earlier in the semester we discussed communication:

* <course-link type="page" id="P_Communication">Technical communication and writing good documentation</course-link>

## Conclusion

Information gathering is central to developing and testing hypotheses. The information we need may come from a wide variety of tools. On that note, here are two important reminders:

* Master the tools available to you. Performance and profiling tools, debuggers, logging and tracing tools, memory tools, network debugging tools, monitoring and dashboard tools, testing tools, etc.
* Write your code so that logs are clean and well structured, with carefully considered logging levels. Noisy logs are your enemy.

It is unlikely that there is just one way a defect can be fixed, and I've noticed that mature engineers bring a certain *thoroughness* to the work of fixing. May I suggest that you:

* Resist the urge to just do a quick local fix. Consider systemic issues, and classes of problems represented by the defect discovered, and consider a fix that reflects your best design thinking.
* Sometimes quick fixes are necessary (such as when troubleshooting a system that is experiencing an outage), but in these cases a better fix should be proposed and put in the backlog (and perhaps you could advocate for prioritizing that fix).
* In addition to fixing the defect, consider changes that would prevent the defect (or similar defects) from being re-introduced, or help with detecting and diagnosing similar defects in the future.

In the talk "Do Your Part with All Your Heart", Elder Dieter F. Uchtdorf says that:

> My experience in the flight simulator was an important reminder that getting good at anything—whether it be flying, rowing, sowing, or knowing—takes consistent self-discipline and practice.

> You might spend years acquiring a skill or developing a talent. You might work so hard that it becomes second nature to you. But if you think that means you can stop practicing and studying, you’ll gradually lose the knowledge and abilities you once acquired at great cost.

This applies to engineering related skills, but "also applies to becoming a disciple of Christ."