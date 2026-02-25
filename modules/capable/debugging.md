# Debugging tools and techniques

## Learning outcomes

By discussing and practicing debugging in the context of analytical thinking our aim is to:

1. Improve our ability to systematically investigate (using appropriate information gathering) complex system problems.
2. Use logical reasoning to identify defects and propose fixes.

## Reading (class preparation)

* Before class, please download <file path="ruby-with-issues.zip"></file>, build it and run the code in a debugger of your choice. 
* Some instructions for running ruby in the VS code debugger can be found at the end of the [investigating code module](../curious/investigating-code.md).

## Discussing

Think about difficult debugging problems you have faced in the past. What made them difficult? What approach did you try (possibly an approach that was not effective)? How did you (or the TA or whoever) ultimately find the defect? What role did each of the following play?

* Gathering and evaluating information critically
* Recognizing patterns, relationships, or inconsistencies
* Making reasoned judgments based on evidence
* Breaking problems into components to tackle them systematically
* Tooling and information sources
* Practical strategies and tips

## Practicing

*The following are to be completed in groups of two (or three) students. While you are practicing, please feel free to ask questions and start impromptu class discussions. Also, please expect interruptions and be open to feedback!*

The <file path="ruby-with-issues.zip"></file> file contains a version of the c ruby code with (at least) two issues, described below (and also described in test.rb). For each issue, use the crash report (see below for one example), the code, the debugger, etc. and do the following in a loop (you do not need to follow a strict order).

1. Generate one or more hypotheses (read code, ...)
2. Test and investigate methodically (vary inputs, use debugger, write test cases)
3. Review results and (newly) available information

Continue with the above activities until you can (1) isolate the defect, (2) explain the circumstances under which it is activated, and (3) propose a fix. Time permitting, you can make the fix and test it.

### Issue #1

The following code leads to a segfault after the first successful read. The expected behavior is that it should throw an IOError instead.

```ruby
file = File.open("../test.rb")

file.each_byte do |byte|
  p byte
  file.close
end
```

### Issue #2

The following code leads to a segfault (depending on compiler settings):

```ruby
["a"*3070].pack("m4000")
["a"*(3072*3-2)].pack("m3072")
```

Some background: `Array#pack` takes an array of ruby objects and formats them into various representations suitable for storage or transmission in various contexts. The `m` directive in `Array#pack` is used for Base64 encoding. It takes the elements of the array, treats them as binary data, and encodes them into a Base64 string. In the above the `m` directive is followed by a number which specifies the line length for the encoded output.

### Post exercise discussion

Once the exercise is complete, as a class we will discuss questions such as:

* What tooling was most helpful in this case? What is it about this case that made those the most valuable?
* What hypotheses were considered? 
* What strategies did you use to narrow down the issue?

## Applying

Individually complete the following tasks to deepen your understanding of how to debug issues in the OSS project you have selected for this course. 

* Build the software and execute it in a debugger, setting breakpoints and exploring the code.
* Explore the logging configuration and logging used by the software.
* Identify the key (top level) error handling strategies used by the software.
* (Optionally) find a bug in the issue tracking system and identify defect and possible solutions.

## <course-link type="assignment" id="R_Debugging">Debugging Tools & Techniques Reflection</course-link>

Submit a one-page reflection on your experience applying analytical thinking to your project. There is no "right answer" here, but you will be graded on how insightful your answers are and the depth of understanding displayed.

* Explain the logging and error handling strategies you identified in your open source project.
* What aspects of analytical thinking are easier or more natural for you? Which are more difficult?
* (Optional) Tell us about the bug you investigated and what you learned.

## Appendix

Note that a **segmentation fault** occurs when a program accesses memory outside of the segment it owns. 

For reference, here is the crash report from the first segfault. Note which ruby level method call is the source of the segfault. Also, note which c function (and file and line number) is the source of the segfault. Hint: look just after the `_sigtramp` line, which shows the signal trampoline (that's the crash site and the connection between the CPU SIGSEGV and the ruby code to handle those events).

```
-- Crash Report log information --------------------------------------------
   See Crash Report log file in one of the following locations:             
     * ~/Library/Logs/DiagnosticReports                                     
     * /Library/Logs/DiagnosticReports                                      
   for more details.                                                        
Don't forget to include the above Crash Report log file in bug reports.     

-- Control frame information -----------------------------------------------
c:0003 p:---- s:0011 e:000010 CFUNC  :each_byte
c:0002 p:0013 s:0007 E:002408 EVAL   ../test.rb:8 [FINISH]
c:0001 p:0000 s:0003 E:001f50 DUMMY  [FINISH]

-- Ruby level backtrace information ----------------------------------------
../test.rb:8:in '<main>'
../test.rb:8:in 'each_byte'

-- Threading information ---------------------------------------------------
Total ractor count: 1
Ruby thread count for this ractor: 1

-- Machine register context ------------------------------------------------
  x0: 0x00000001f059216c  x1: 0x0000000128028078  x2: 0x0000000000000004
  x3: 0x0000000000000002  x4: 0x0000000128028080  x5: 0x0000000128028078
  x6: 0x0000000000000035  x7: 0x0000000000000000 x18: 0x0000000000000000
 x19: 0x0000000102f573c0 x20: 0x000000012388b720 x21: 0x0000000000000001
 x22: 0x0000000128127f90 x23: 0x0000000000000000 x24: 0x0000000128028040
 x25: 0x0000000128028038 x26: 0x0000000055550083 x27: 0x000000012264ae50
 x28: 0x0000000128127fa9  lr: 0x00000001029aaf40  fp: 0x000000016d5524f0
  sp: 0x000000016d5524d0

-- C level backtrace information -------------------------------------------
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_vm_bugreport+0xb7c) [0x102b309c8] /Users/jsillito/tmp/CS301R-Ruby/build/../vm_dump.c:1178
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_vm_bugreport) (null):0
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_bug_for_fatal_signal+0x10c) [0x102960db8] /Users/jsillito/tmp/CS301R-Ruby/build/../error.c:1130
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(sigsegv+0x90) [0x102a8ca04] /Users/jsillito/tmp/CS301R-Ruby/build/../signal.c:948
/usr/lib/system/libsystem_platform.dylib(_sigtramp+0x38) [0x1826396a4]
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_io_each_byte+0x98) [0x1029aaf40] /Users/jsillito/tmp/CS301R-Ruby/build/../io.c:4721
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(vm_call_cfunc_with_frame_+0xf0) [0x102b21a84] ../vm_insnhelper.c:3918
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(vm_sendish+0x10) [0x102b078c8] ../vm_insnhelper.c:6111
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(vm_exec_core) /Users/jsillito/tmp/CS301R-Ruby/build/vm.inc:0
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(vm_exec_loop+0x0) [0x102b02138] /Users/jsillito/tmp/CS301R-Ruby/build/../vm.c:2710
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_vm_exec) /Users/jsillito/tmp/CS301R-Ruby/build/../vm.c:2713
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_ec_exec_node+0x8c) [0x10296bd80] /Users/jsillito/tmp/CS301R-Ruby/build/../eval.c:283
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(ruby_run_node+0x4c) [0x10296bca0] /Users/jsillito/tmp/CS301R-Ruby/build/../eval.c:321
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(rb_main+0x1c) [0x1028ac890] /Users/jsillito/tmp/CS301R-Ruby/build/../main.c:42
/Users/jsillito/tmp/CS301R-Ruby/build/ruby(main) /Users/jsillito/tmp/CS301R-Ruby/build/../main.c:62

-- Other runtime information -----------------------------------------------

* Loaded script: ../test.rb

* Namespace: disabled
* Loaded features:

    0 enumerator.so
    1 thread.rb
    2 fiber.so
    3 rational.so
    4 complex.so
    5 pathname.so
    6 ruby2_keywords.rb
    7 set.rb

* Process memory map:

1028ac000-102c90000 r-x /Users/jsillito/tmp/CS301R-Ruby/build/ruby
102c90000-102c9c000 r-- /Users/jsillito/tmp/CS301R-Ruby/build/ruby
102c9c000-102ca0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby
102ca0000-102cb0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby
102cb0000-102dc8000 r-- /Users/jsillito/tmp/CS301R-Ruby/build/ruby
102dc8000-102dd0000 rw- /usr/lib/dyld
102dd0000-102dd8000 r-- /usr/lib/dyld
102dd8000-102ddc000 r-- /usr/lib/dyld
102ddc000-102de0000 rw- /usr/lib/dyld
102de0000-102de4000 --- /usr/lib/dyld
102de4000-102df0000 rw- /usr/lib/dyld
102df0000-102df4000 --- /usr/lib/dyld
102df4000-102df8000 --- /usr/lib/dyld
102df8000-102e04000 rw- /usr/lib/dyld
102e04000-102e08000 --- /usr/lib/dyld
102e08000-102e0c000 --- /usr/lib/dyld
102e0c000-102e18000 rw- /usr/lib/dyld
102e18000-102e1c000 --- /usr/lib/dyld
102e1c000-102e20000 r-- /usr/lib/dyld
102e30000-102e40000 rw- /usr/lib/dyld
102e50000-102e60000 rw- /usr/lib/dyld
102e70000-102e80000 rw- /usr/lib/dyld
102e90000-102ea0000 rw- /usr/lib/dyld
102eb0000-102ec0000 rw- /usr/lib/dyld
102ed0000-102ee0000 rw- /usr/lib/dyld
102ef0000-102f00000 rw- /usr/lib/dyld
102f10000-102f20000 rw- /usr/lib/dyld
102f30000-102f40000 rw- /usr/lib/dyld
102f50000-102f60000 rw- /usr/lib/dyld
103228000-103288000 --- /usr/lib/dyld
103288000-104688000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
104688000-10c688000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
10c688000-114688000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
114688000-11c688000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c688000-11c68c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c68c000-11c730000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c730000-11c734000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c734000-11c7d8000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c7d8000-11c7dc000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c7dc000-11c880000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c880000-11c884000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c884000-11c928000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c928000-11c92c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c92c000-11c9d0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c9d0000-11c9d4000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11c9d4000-11ca78000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11ca78000-11ca7c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11ca7c000-11cb20000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cb20000-11cb24000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cb24000-11cbc8000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cbc8000-11cbcc000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cbcc000-11cc70000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cc70000-11cc74000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cc74000-11cd18000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cd18000-11cd1c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cd1c000-11cdc0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cdc0000-11cdc4000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cdc4000-11ce68000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11ce68000-11ce6c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11ce6c000-11cf10000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cf10000-11cf14000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cf14000-11cfb8000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cfb8000-11cfbc000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11cfbc000-11d060000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d060000-11d064000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d064000-11d108000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d108000-11d10c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d10c000-11d1b0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d1b0000-11d1b4000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d1b4000-11d258000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d258000-11d25c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d25c000-11d300000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d300000-11d304000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d304000-11d3a8000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d3a8000-11d3ac000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d3ac000-11d450000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d450000-11d454000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d454000-11d4f8000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d4f8000-11d4fc000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d4fc000-11d5a0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d5a0000-11d5a4000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d5a4000-11d648000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d648000-11d64c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d64c000-11d6f0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d6f0000-11d6f4000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d6f4000-11d798000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d798000-11d79c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d79c000-11d840000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d840000-11d844000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d844000-11d8e8000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d8e8000-11d8ec000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d8ec000-11d990000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d990000-11d994000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11d994000-11da38000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11da38000-11da3c000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11da3c000-11dae0000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11dae0000-11dae4000 --- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11dae4000-11db88000 rw- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11db88000-11e7b0000 r-- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
11e7b0000-11f3d8000 r-- /Users/jsillito/tmp/CS301R-Ruby/build/ruby.dSYM/Contents/Resources/DWARF/ruby
122600000-122700000 rw-
122700000-122800000 rw-
122800000-123000000 rw-
123000000-123800000 rw-
123800000-123900000 rw-
123900000-123a00000 rw-
124000000-124800000 rw-
128000000-130000000 rw-
169554000-16cd58000 ---
16cd58000-16d554000 rw-
16d554000-16d558000 ---
16d558000-16d5e0000 rw-
180000000-1ec000000 r--
1ec000000-1edf78000 r--
1edf78000-1edf9c000 rw-
1edf9c000-1ee000000 rw-
1ee000000-1f0000000 rw-
1f0000000-1f0314000 r--
1f0314000-1f0338000 r--
1f0338000-1f1538000 rw-
1f1538000-1f91fc000 r--
1f91fc000-1fa000000 r--
1fa000000-282000000 r--
282000000-283a18000 rw-
283a18000-2847a8000 rw-
2847a8000-288d7c000 r--
288d7c000-28a000000 r--
28a000000-300000000 r--
fc0000000-1000000000 ---
1000000000-7000000000 ---
[IMPORTANT]
Don't forget to include the Crash Report log file under
DiagnosticReports directory in bug reports.

zsh: segmentation fault  ./ruby ../test.rb
```