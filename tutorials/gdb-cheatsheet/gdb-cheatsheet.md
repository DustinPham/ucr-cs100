GDB Cheatsheet
===


###GDB installation

If you already have gdb installed, you can skip this section! w00t!

Step 1: INSTALL LINUX

Step 2: Run these commands in the terminal

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a. `$ sudo apt-get update`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b. `$ sudo apt-get install gdb`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;c. `pat yourself on the back w000t`

###Starting GDB

After you finish up your sweet program, you should generally compile it with your standard flags, but also with the `-g` flag. The `-g` flag lets gdb debug our executable and gives us a bunch of helpful feedback. Without it, gdb will still run your program, but it won't allow you to step through to see if there's any errors, and where they occur. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ g++ -g -Werror -Wall -ansi -pedantic moo.cpp `

After compilation, you want to run it in the following format:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb a.out <flags>`

You can also just run `gdb` and start your program within gdb like so:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb a.out <flags>` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) a.out`



###GDB Flags

There are many GDB flags, but most of them aren't too useful. The most useful so far in this class are :<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb --args <program> <arguments>`

This allows us to pass command line arguments into our program which is run through gdb. This is like program-ception.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$ gdb -quiet <program>` or `$ gdb -q <program>`

If you don't want your terminal to be flooded with nonsensemoo, then you can use this flag.

You can also chain flags together. 

###Running GDB

The first thing you should do after running gdb is set a breakpoint(s). To set a breakpoint in your program simply type:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) breakpoint <line number>` or `(gdb) breakpoint <function name>`

`breakpoint` can be replaced with `b`.

In general, most gdb commands can be shortened.

The second thing to do is:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) run` or `(gdb) r`

`run` runs the program until it ends, accepts input, or until it reaches a breakpoint.

###Using GDB

After using `run` and reaching a line with input or a breakpoint, you can walk through your code line by line using:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) step` or `(gdb) s`

`step` or `s` steps through your code line by line and also lets you walk through any function calls line by line.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) next` or `(gdb) n`

`next` or `n` steps through your code line by line, but will run function calls automatically.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) print <variable name>` or `(gdb) p <variable name>`

`print` or `p` prints out the value in any variable.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) kill` or `(gdb) k`

`kill` or `k` kills the current program being run through gdb, but does not close gdb itself. This allows you to restart the debugging process with all breakpoints intact.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) reverse-step` or `(gdb) rs` or `(gdb) reverse-next` or `(gdb) rn`

These commands allow you to move one line backwards in your code. In order to enable this, you need to run:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`(gdb) record` after `(gdb) run`.



