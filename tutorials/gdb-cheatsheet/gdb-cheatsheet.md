GDB Cheatsheet
===

###Starting GDB

After you finish up your sweet program, you should generally compile it with your standard flags, but also with the `-g` flag. The `-g` flag lets gdb debug our executable and gives us a bunch of helpful feedback. Without it, gdb will still run your program, but it won't allow you to step through to see if there's any errors, and where they occur. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ g++ -g -Werror -Wall -ansi -pedantic moo.cpp `

After compilation, you want to run it in the following format:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb a.out <flags>`

You can also just run `gdb` and start your program within gdb like so:

```
  $ gdb <flags>
  (gdb) file <executable>
```

`file` is the command that tells gdb that the following argument is the program to be debugged.

###GDB Flags

There are many GDB flags, but most of them aren't too useful. The most useful so far in this class are :<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb --args <program> <arguments>`

This allows us to pass command line arguments into our program which is run through gdb. This is like program-ception.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb -quiet <program>` or `$ gdb -q <program>`

If you don't want your terminal to be flooded with nonsensemoo, then you can use this flag.

You can also chain flags together. 

###Running GDB

All gdb commands can be shortened to the shortest recognizable command (usually a single letter).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) breakpoint <line number>` or `(gdb) breakpoint <function name>`

`breakpoint` can be replaced with `b`.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) run` or `(gdb) r`

`run` runs the program until it ends, accepts input, or until it reaches a breakpoint.

###Using GDB

After using `run` and reaching a line with input or a breakpoint, there are many commands that you can use.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) watch <variable name>` or `(gdb) wa <variable name>`

`watch` will cause the program to pause at wherever the variable changes.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) continue` or `(gdb) cont`

`continue` continues running the program from wherever it stopped at, such as a breakpoint, a watchpoint, or a conditional breakpoint.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) step` or `(gdb) s`

`step` steps through your code line by line and also lets you walk through any function calls line by line.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) next` or `(gdb) n`

`next` steps through your code line by line, but will run function calls automatically.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) print <variable name>` or `(gdb) p <variable name>`

`print` prints out the value in any variable once.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) display <variable name>` or `(gdb) disp <variable name>`

`display` prints out `<variable name>` after every `step` or `next` so you can see what value is contained in the variable. You can use `display` to keep track of multiple variables and only have to declare it once within gdb, unlike `print`.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) record` or `(gdb) rec` after `(gdb) run`.

`record` will enable the `reverse-step` and `reverse-next` commands so the user can step backwards through their program.

*Note: Using `record` will cause your program to run much slower because it requires a lot of memory to keep track of previous actions.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) reverse-step` or `(gdb) rs` and `(gdb) reverse-next` or `(gdb) rn`

These commands allow you to move one line backwards in your code.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) kill` or `(gdb) k`

`kill` kills the current program being run through gdb, but does not close gdb itself. This allows you to restart the debugging process with all breakpoints intact.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) quit` or `(gdb) q`

`quit` does what it sounds like; it quits gdb!
