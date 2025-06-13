# Analytical Thinking in Software Engineering

Status: Nearly complete first draft (but see linked modules for their status)

## Learning outcomes

By discussing analytical thinking our aim is to:

1. Develop our understanding of the role of analytical thinking in software engineering.
2. Improve our ability to apply the principles of analytical thinking in the context of bug reporting and debugging.

## Reading

* TODO: find a nice analytical thinking overview article or book chapter
* [Slack incident: Everyone back to work](https://slack.engineering/slacks-outage-on-january-4th-2021/) OR other?

## Class discussion

Analytical thinking is the ability to break down complex information or problems into smaller, more manageable parts in order to understand them, identify patterns, draw logical conclusions, and solve problems effectively. In general, analytical thinking may involve steps such as: 

1. Observation – Gathering relevant data and identifying key details.
2. Decomposition – Breaking a problem into smaller components.
3. Pattern Recognition – Finding trends, anomalies, or relationships.
4. Logical Reasoning – Making inferences, identifying causes, and drawing conclusions.
5. Evaluation – Assessing evidence, arguments, and solutions objectively.

#### Troubleshooting

To introduce these ideas we will discuss the Slack incident linked above, which is a collaborative troubleshooting activity or really a collaborative analytical thinking activity. Here are some questions to loosely guide our discussion.

* What was the cause of the incident? Please think beyond a single root cause.
* How was it identified and mitigated? What tooling and information was used in the process?
* What aspects of analytical thinking are illustrated in this incident report? Here is what I noticed (TODO):
    1. Observation – 
    2. Decomposition – 
    3. Pattern Recognition – 
    4. Logical Reasoning – 
    5. Evaluation – 

#### NASA bug report and debugging example

* Likelihood issue #90

## Modules

In software engineering, analytical thinking is needed when debugging code, assessing pros and cons of a design decision, troubleshooting a system (as just discussed), and in other contexts. In this course we will discuss the following activities more specifically.

1. [Bugs, Bug Reporting and Triage](bug-reports.md)
2. [Debugging tools and techniques](debugging.md)

## Conclusion

Information gathering is central to developing and testing hypotheses. The information we need may come from a wide variety of tools. On that note, here are two important reminders:

* Master the tools available to you. Performance and profiling tools, debuggers, logging and tracing tools, memory tools, network debugging tools, monitoring and dashboard tools, testing tools, etc.
* Write your code so that logs are clean and well structured, with carefully considered logging levels. Noisy logs are your enemy.

It is unlikely that there is just one way a defect can be fixed, and I've noticed that mature engineers bring a certain *thoroughness* to the work of fixing. May we suggest that you:

* Resist the urge to just do a quick local fix. Consider systemic issues, and classes of problems represented by the defect discovered, and consider a fix that reflects your best design thinking.
* Sometimes quick fixes are necessary (such as when troubleshooting a system that is experiencing an outage), but in these cases a better fix should be proposed and put in the backlog (and perhaps you could advocate for prioritizing that fix).
* In addition to fixing the defect, consider changes that would prevent the defect (or similar defects) from being re-introduced, or help with detecting and diagnosing similar defects in the future.

TODO: Make sure the above are well captured in the material we cover.