# Creative problem solving and software engineering

## Learning outcomes

1. Apply a CPS process (or similar) in a software engineering context
2. Understand when such a process (or specific steps of the process) would be appropriate

## Case study

When executing ruby code, the C implementation of ruby compiles the code to a ruby specific bytecode--that is a series of instructions that can be executed by the underlying virtual machine. You can dump the bytecode using the `--dump=insns` argument, For example the following command dumps the output of the simple program: `2+3`.

```bash
ruby --dump=insns -e "2+3"
```

Below is the (slightly simplified) bytecode. The basic format is: an instruction offset (ex: `0002`), the instruction name (ex: `opt_plus`), followed by any arguments (ex: the int literal `2`).

```
== disasm: #<ISeq:<main>@-e:1 (1,0)-(1,3)>
0000 putobject 2 # put literal on stack
0002 putobject 3 # put literal on stack
0004 opt_plus    # an optimized addition
0006 leave       # exit block, etc.
```

Each instruction is defined in `insns.def` and compiled as part of the build process.`

### Switch statement

The switch statement in the Ruby programming language is powerful, but a naive implementation of that feature (in the interpreter) may be slow. Perhaps this poor performance is unavoidable for some switch statements, but should we need to pay that penalty in all cases? To explain what we mean, consider the following switch statement.

```ruby
# ...
def foo(state)
  case state
  when :wait_readable
    # do something
  when :closed
    # do something
  else
    # do something
  end
end
```

Our goal here is to design an improvement to the ruby implementation (not the language) that would improve the (runtime) performance of the case statement. A naive performance the performance is `O(n)` where `n` is the number of `when` conditions and of course related to the costs of checking for equality.

Before starting, let's invest some time together as a class on the *clarification* step of the CPS process. Then we will break into groups for *ideation* and *development* steps of the process. Please be sure you consider those separate steps. Recall that:

* *Clarification* involves exploring the problem space, understanding constraints, etc.

* *Ideation* involves generating ideas while deferring judgement. 

* *Development* involves developing ideas by applying affirmative judgement, while keeping novelty alive. 

### Discussion

* What interesting and potentially useful ideas did you develop as a team?
* What aspects of the CPS process seem useful in this context? 
* How could you involve other project members in such a process?

## Appendix

For the solution used in Ruby today see:

* https://bugs.ruby-lang.org/issues/11769, and 
* The opt_case_dispatch bytecode instruction

The basic idea is to use a jump table (when the opt_case_dispatch instruction can be used) rather than the equivalent to a sequence of if/else statements (more specifically using checkmatch/branchunless instructions).