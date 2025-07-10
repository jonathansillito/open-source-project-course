# Creativity

Status: Complete first draft

> "The more you trust and rely upon the Spirit, the greater your capacity to create." [Happiness, Your Heritage By President Dieter F. Uchtdorf]

## Learning outcomes

The focus of this module is creativity and problem solving, with an emphasis on solving problems in the context of project priorities and constraints. The expected learning outcomes are:

1. Describe the four (or six) stages of the Osborn-Parnes CPS process 
2. Understand and apply **divergent** thinking while defining and solving problems
3. Understand and apply **convergent** thinking while defining and solving problems

## Reading

Please read the following article before class:

* [Osborn-Parnes Creative Problem Solving Process](https://brdo.berkeley.edu/sites/default/files/cps_handbook.pdf)
* [Channeling Your Creativity](https://www.churchofjesuschrist.org/study/new-era/2004/02/channeling-your-creativity?lang=eng) By Elder Robert D. Hales

## Discussing

Solving problems is an important part of software engineering. Various structured processes exist which aim to help people *creatively* solve problems. *Creative* solutions are those with an element of newness or innovation to them. For the sake of time, we will focus on just one process: the *Osborn-Parnes Creative Problem Solving Process* or *CPS*. For reference, other examples include: Design Thinking and TRIZ (Theory of Inventive Problem Solving).

As we discuss CPS, it may help to have in the back of your mind a problem you would like to solve or an opportunity you would like to pursue. This could be personal problem, a relationship you would like to strengthen, church calling related, a struggle with a class, or work related.

### Steps in the process

The CPS process has four (sometimes written out as six) stages as follows:

*#1 Clarification:* Explore the problem space, collect data and facts, and generate problems (or questions). Select the most intriguing or fruitful problem(s) to address. By *problem space* we mean the current (or initial) state that presents some opportunities. Some important breakthroughs come from reframing the problem, and certainly the framing of the problem can affect the stages that follow.

*#2 Ideation:* Generate ideas by deferring judgement, prefer quantity to quality, look for unusual ideas, build on ideas. The output from this stage is a list of ideas, with no ranking ("every idea is equal"). 

*#3 Development:* Develop ideas by applying affirmative judgement, keeping novelty alive and staying focused on your objectives. In the SE context during the clarification phase and the development phase, project priorities and constraints become important, though they can be in tension with the novelty.

*#4. Implementation:* Planning for implementation and action. Be flexible when needed. Note that in many organizations the effort involved in "socializing" an idea is important part of having a contribution accepted. This is true for both open and closed source projects.

### Ways of thinking

All four phases can include a certain amount of both *divergent* and *convergent* thinking, and the distinction is central to the CPS process. Naturally step 2 (ideation) may be particularly divergent and step 3 (development) may be particularly convergent.

* *Divergent thinking:* Divergent thinking is the process of generating many different ideas or solutions to a problem. It emphasizes creativity, open-mindedness, and exploration.
* *Convergent thinking:* Convergent thinking is the process of narrowing down multiple ideas into a single, correct, or best solution. It focuses on logic, accuracy, and decision-making.

An illustration of the value of generating many ideas before picking an idea to develop further can be found in this research paper where the creative activities were the egg drop and writing advertising copy. Participants were divided into two groups (see below). What do you think they found?

* Simultaneous Evaluation Group: Generated and evaluated ideas concurrently.
* Delayed Evaluation Group: Generated multiple ideas before evaluating any.

### Tools

The pre-class reading describes various (potentially) useful tools for applying divergent or convergent thinking in various contexts related to CPS. The following are a few examples. Where do you see divergent/convergent thinking in these?

<table>
    <tr>
        <th>
        Tool
        </th>
        <th>
        Description
        </th>
    </tr>
    <tr>
        <td>
        Webbing (Ladder of Abstraction)
        </td>
        <td>
        Using questions to make an idea more specific or bigger picture. What's stopping you? Why is this important? 
        </td>
    </tr>
    <tr>
        <td>
        Post-It Brainstorming
        </td>
        <td>
        For generating and recording creative ideas. Aims for many ideas.
        </td>
    </tr>
    <tr>
        <td>
        Brainwriting
        </td>
        <td>
        Generate ideas (on a worksheet) and build on other's ideas (by swapping worksheets).
        </td>
    </tr>
    <tr>
        <td>
        PPPC/O
        </td>
        <td>
        Identify pluses, potentials, concerns with ideas. Brainstorm ways to overcome concerns.
        </td>
    </tr>
    <tr>
        <td>
        Value vs. Do-ability
        </td>
        <td>
        Evaluate many ideas by comparing them along two dimensions. Ideas can be refined to improve them along those dimensions.
        </td>
    </tr>
</table>

## Practicing

*The following is to be completed in groups of three or four students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

We want to build a mechanism for protecting an egg from being dropped at (gradually increasing usually) various heights. Work through the problem, explicitly following each of the stages of the CPS process. The following has some suggestions and questions to help you work through the stages. Feel free to pick one student to be the facilitator.

### Stage 1: Clarification

THeh objective of this stage is to make sure the problem is clearly defined and understood.

* What is the (real) goal? 
* What are the constraints?
* Who is the user/stakeholder?

### Stage 2: Ideation

The objective is to brainstorm many possible ways to protect the egg *without judgment*. Encourage wild ideas and aim for quantity over quality. Here are a few questions that may help.

* What are all the different designs or materials we could use?
* How could we absorb the impact? Slow the fall? Protect the shell?
* How could some already suggested ideas be built on?
* Which of the tools in the table above could be helpful?

### Stage 3: Development

The objective is to evaluate and improve the best ideas from brainstorming. Consider using sketches, thought exercises, discussion about why it might work, etc.

* Which ideas seem most feasible with available materials?
* Can we combine parts of different ideas?
* What might go wrong? How can we improve it?
* Which of the tools above could be helpful??
* Which of the tools in the table above could be helpful?

### Stage 4: Implementation

The objective of this stage is to build and test the solution. We don't have time in this class to prototype and test out the ideas, but if we did we could be guided by questions such as:

* What worked? 
* What didn't? 
* How could you improve it?

### Post exercise discussion

Now that the exercise is complete, let's discuss the results as a class.

* What tooling was most helpful in this case? What is it about this case that made those the most valuable?
* What were the wildest ideas considered? How did those contribute to the final option considered?
* How did you employ divergent and convergent thinking?
* How can we apply these ideas to SE projects?

## Applying

Complete the following tasks to (1) solidify your understanding of how the ideas discussed above related to software engineering work, and (2) hopefully improve your contribution(s) to an open source project.

* Identify a (first) contribution to make and apply the principles of stage 1 of the CPS process. Note that this will almost certainly involve discussing the problem or opportunity with other project members.
* Apply the principles of stage 2 of the CPS process and one or more of the tools described in the pre-class reading (some of which are listed in the table above) to help you explore possible solutions. Please consider many solutions before moving on to the next task.
* Apply the principles of stage 3 of the CPS process and one or more of the tools described in the pre-class reading (again, some of which are listed in the table above) to help you develop the most promising solution(s). A deep understanding of project priorities, constraints, culture, etc. may help.
* Share what you consider the most promising solution(s) with project members, including your views on the pros and concerns.

## Reflecting

Submit a one page reflection on the following questions. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* What tools did you use when applying CPS to an open source project? What effect did that have on the outcomes? 
* What did you lear from communicating with project members during the process?
* What role do you see divergent and convergent thinking playing in software engineering work.
* What areas of your person, church or professional life could benefit from creative problem solving?

## Conclusion

The proponents of processes like CPS are fundamentally arguing the creativity is a skill that can be developed and how we approach problems can affect the probability of creative breakthroughs. While we wanted to cover (at some level of detail) a comprehensive creative problem solving process, you will likely only apply some of the ideas we've discussed in an open source project during this course. Here are two final questions for discussion and personal reflection:

* What does the article by Elder Hales (see the pre-class reading list above) suggest, over and above the CPS process? What difference might his ideas make?
* As a final thought, I would like to invite you to consider what might be limiting your ability to do deep work in your life? Distractions?

## Notes

* Here is an interesting problem framing story. Inspired by burrs sticking to clothing, George de Mestral wondered if this natural sticking mechanism could be replicated. The result was his invention of Velcro https://www.invent.org/blog/inventors/walk-in-the-woods-velcro

* Is the right opportunity to refine and existing phone keyboard or rethink user input more generally? The iPhone (and the Android phones) are an example of this. Calory counting apps use the phone camera for input. I wonder how that came to be?