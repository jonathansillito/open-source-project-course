# Investigating Code

## Learning outcomes
By discussing code investigation, our aim is to:

1. Learn how to explore a code base to understand how it works
2. Explore tools that will allow us to examine unfamiliar code bases.
3. Understand the need and how to communicate with others (developers, users, etc.) in order to fully understand issues and the code being studied.

## Reading

* [The Code Archeololgist](https://www.profocustechnology.com/software-development/the-code-archaeologist/) - The need to be able to dive into old code bases and the challenges you might face
* [How to Approach a New Codebase(blogpost)](https://amberwilson.co.uk/blog/how-to-approach-a-new-codebase/)
* [How to Get Familiar with an Existing Codebase(blogpost)](https://dev.to/isaactony/how-to-get-familiar-with-an-existing-codebase-49k5)


## Discussing

Questions to start class:
* What does it mean to you when you hear the phrase "code archeology?"
* Have you ever had to dive into and use or edit code you didn't write?  
  * What was the context?
  * What problems/challenges/hurdles did you have to overcome?
  * What tool/techniques did you use to get up to speed?

When we start looking at existing code we may be doing so for a number of different reasons:
1. To figure out how to get it to build and run
1. To understand the overall architecture/design
1. To identify the location and cause of a bug
1. To identify how to implement a desired new feature or modify an existing one

Before you can start making changes to code, you need to understand it.  There are a number of things to look at when you are trying to understand a new code base:
* **Context** - Why was the code written? What is its purpose? What expectations are there about its use?
* **Design & Architecture** - How is the project organized?  Are there patterns?  What external dependencies exist?  What internal dependencies?
* **Documentation** - How is the code documented?  Is external documentation up-to-date?  Where can you find it?  Is the code commented cleanly?
* **Personnel** - Are the original developers still part of the project?  How do you reach out to them with questions?
* **Build Process** - How do you build the code?  What technologies does it use?
* **Domain Knowledge** - Is there specialized domain knowledge the code relies on or assumes the developer/user understands?

As you start to learn the code, how do you effectively navigate it and generate understanding?
* **Evaluate your Assumptions** - Were the things you assumed about the code correct?  What did you learn that was different?
* **Use your IDE's tools** - "Go to Definitions" and "Go to Uses" are going to be your friends.
* **Run the code** - See how it behaves, run it through profilers to see what classes/functions are heavily used, run it in the debugger and step through to understand the program flow.
* **Look at the tests** - These can often indicate what the developers felt were the most important aspects or the things they struggled with, especially if the project lacks 100% test coverage. (Or they might just be what was easiest to test.)
* **Take copious notes** - Record the things you learn.
* **Ask Questions** - Reach out to the user who reported the bug/requested the feature. Reach out to the original developers.

### An Example

This is an example of a focused investigation looking for the source of an error reported by a user and trying to identify how to fix it.

A user reported this bug in the science analysis software distributed by NASA's Fermi Gamma-ray Space Telescope mission: [Memory use and delete_local_fixed](https://github.com/fermi-lat/Likelihood/issues/90).  I'd never worked with this particular part of the codebase before and had to dive in to figure out what was happening.  Here are my [notes from tracing the program flow](../docs/likelihood-90.notes.txt).  Let's walk through the entire process.  These notes were made between the 8th (Aug 25, 2020) and 9th (Sep 24, 2020) comments on the issue thread.

### Tools

There are a number of various tools you can use to help understand your codebase:
* Your IDE - view and navigate through the code
* Memory profilers - the [Valgrind](https://valgrind.org/) suite on Linux, [leaks](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/ManagingMemory/Articles/FindingLeaks.html) on Mac
* AI - analyze, interpret, & summarize code
  * [Cursor](https://www.cursor.com/en)
  * [Claude](https://claude.ai/)
  * [Warp](https://www.warp.dev/code)
 
## Practicing

*The following is to be completed in groups of two or three students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

Our goal is to investigate the parts of the Ruby programming language that are implemented in the C programming language. In the process we will get some practice with a few tools.

### Preparation (could be done before class)

At least one member of the group, but ideally all members of the group should follow the following steps:

1. Download the latest release of the Ruby code base. At the moment the latest release is [3.3.9](https://www.ruby-lang.org/en/news/2025/07/24/ruby-3-3-9-released/). 
2. Starting with the README.md, follow the build instructions.

### Generating questions

Generate a list of questions about the Ruby code base. And consider how you would answer each of those questions (including what tools might be helpful). Questions about *why something is the way it is* can be some of the most interesting and difficult to answer. These are sometimes called *design rationale* questions. This is partially filled out, but please fill in the blanks as a group. Feel free to think creatively, and consider approaches and tools not discussed so far in today's class.

Here are a few examples to get you thinking creatively...

<table>
    <tr>
        <th>
            #
        </th>
        <th>
            Question
        </th>
        <th>
            Possible approach/tools?
        </th>
    </tr>
    <tr>
        <td>
        1
        </td>
        <td>
            At the C level how are classes and objects implemented? 
        </td>
        <td>
            In an IDE investigate the relationships between RBasic, RObject and RClass. In debugger inspect values of the structs for different classes/objects.
        </td>
    </tr>
    <tr>
        <td>
        1
        </td>
        <td>
            How are methods stored in Ruby classes/objects?
        </td>
        <td>
            Start with Init_Hash to see how methods are added (rb_define_method). Statically/dynamically trace from there (warning this gets a bit complicated ...).
        </td>
    </tr>
    <tr>
        <td>
        2
        </td>
        <td>
            What are the performance characteristics of method dispatch? What optimizations are in place?
        </td>
        <td>
            Identify relevant C functions, create test code, run in (platform specific) profiler. Say Instruments in macOS.
        </td>
    </tr>
    <tr>
        <td>
        3
        </td>
        <td>
            What would be the memory layout of a simple object (at the C level)? 
        </td>
        <td>
            &nbsp;
        </td>
    </tr>
    <tr>
        <td>
        4
        </td>
        <td>
            &nbsp;
        </td>
        <td>
            &nbsp;
        </td>
    </tr>
    <tr>
        <td>
        5
        </td>
        <td>
            &nbsp;
        </td>
        <td>
            &nbsp;
        </td>
    </tr>
</table>

### Investigating in an IDE

Integrated development environments (IDEs) such as VS Code provide various tools for exploring a code base (navigating, searching, documentation hints, etc.). Open the Ruby code in an IDE of you choice and use its features to answer the following questions or carry out the following tasks. Don't be afraid to read documentation to help!

1. What is the relationship between the following C structs `RBasic`, `RObject` and `RClass`? 

2. What role do they play in providing an implementation for objects and classes in the Ruby programming language? (See also the `rb_classext_struct`.)

3. How are builtin classes created and setup with the methods, instance variables, etc. needed? Consider using the Hash type as an example to investigate (see `Init_Hash`, `rb_define_class` and `rb_define_method` functions).

### Investigating in a debugger

This will require recompiling the Ruby C code to include the debug information and also properly setting up C/C++ debugging for your IDE of choice. Some partial instructions for VS Code are included at the end of this file. Once debugging is setup, please use the debugger to answer the following questions.

1. What are some of the builtin classes that are created during the initialization of the Ruby VM? (Hint: start by putting a break point in the `Init_Hash` function to see where it is called from and then what else is called.

Note that due to the use of C macros, it may not be so easy to use the IDE--without the debugger--to find some calls. We will spend more time working in a debugger later in the course (see the [Capable/Debugging tools and techniques](../capable/debugging.md) module).

### Investigating with AI

For the following, you can use an AI tool integrated with your IDE (say Copilot in VS Code) or a command line tool such as Warp. With your choice of tool try prompts such as the following (and any others you are interested in).

1. `Give me an overview of this code`

2. `Explain to me how Ruby classes and objects are implemented in C`

3. `Explain the VALUE type use in this code base`

### Post-practice discussion

Now that the exercise is complete, let's discuss the results as a class.

* What did you learn about how Ruby classes and objects are implemented? 
* Is there anything that remains unclear?
* What role did the tools you used play in helping you understand the code?

## Applying

Complete the following tasks to develop a better understanding of an open source code base. For this you can use any tools you find helpful (including, but not limited to, the tools discussed above).

1. Build the source code, learning about the build tools as needed. 
2. Run the code in a debugger, learning about the relevant debugging tools as needed.
3. Develop an understanding of the overall structure of the code base. What are the major components or modules and how do they fit together? 
4. Pick one component to investigate in detail. What are the core types and functions or methods? How are errors handled in the component? 
5. Generate a list of questions you have about the code base (and related tools). For each question plan how you might answer that question.

Note: in the above we are using the term "component" generically. In any particular code base components maybe captured as packages, subdirectories, etc.

## Reflecting

Submit a (about one page) reflection on the following questions and the result of your investigation. 

1. What tools helped you in your investigation and in what way?
2. How did you document what you learned?
3. What else would you like to learn about the code? What next steps will you take? (You're answer to this can be based on the list of questions you were asked to generate above)

Please also submit a diagram capturing the overall structure of the code base--with a particular focus on what you have investigated/learned. We are not interested in a diagram that captures all the types, functions, classes ... of the entire code base.

## Appendix

### Compiling for debugging

Follow the usual build steps (including creating a build subdirectory), but use the following options when running the configuration command. This will enable various debug-related environment variables when building (`--enable-debug-env`), include source-level debugging information (`-g`), and make sure functions are not being optimized away (`-O0`).

```
> cd build
> ../configure CFLAGS='-g -O0' --enable-debug-env --disable-install-doc
> make
```

It will also be helpful to create a simple Ruby program to execute during debugging, which conventionally is called `test.rb`. Start with something simple, like the following and add code as needed.

```
puts "hello world"
```

### Configuring a C debugger in VS Code

Install an appropriate debugger extension. I'm running VS Code on macOS and chose the CodeLLDB extension.

Next, create a build task in `.vscode/tasks.rb`. Something like this should work:

```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "command": "make -j",
            "options": {
                "cwd": "${workspaceFolder}/build"
            },
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```

Finally, create a launch configuration in `.vscode/launch.json`. Here are a couple notes: (1) This references to build task defined above, and (2) Will run a file `test.rb` by passing it as an argument to the ruby executable.

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "lldb",
            "name": "Debug ruby with lldb",
            "request": "launch",
            "program": "${workspaceFolder}/build/ruby",
            "args": ["test.rb"],
            "preLaunchTask": "build"
        }
    ]
}
```

Now you an create breakpoints in VS Code and run ruby in the lldb debugger.
