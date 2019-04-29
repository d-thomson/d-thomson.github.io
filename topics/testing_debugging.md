# Debugging and Testing

## Introduction
Debugging allows you to run a program interactively while watching the source code and the variables during the execution.

A breakpoint in the source code specifies where the execution of the program should stop during debugging. Once the program is stopped you can investigate variables, change their content, etc

## Tutorial
In this tutorial, we will be using the Intellij Java IDE. Debugging is supported in the almost any modern IDE so these steps may be replicated on other software platforms as well. Intellij is free for students and can be downloaded [here](https://www.jetbrains.com/student/) 

#### Setting a breakpoint
To define a breakpoint in your source code, click on the line in the gutter on the left side. The line of code will highlight red. 

[IMAGE]

We want to choose our breakpoint wisely, if we know that our code is breaking at a line, set the breakpoint prior to that so we can analyze variables and control flow. Now that we have a breakpoint, we can run our program in debug mode by clicking the debug button.

[IMAGE]

Once we click this, you'll notice that the execution halts when hitting our breakpoint we set. In the debug window you'll see some stepping options as well as some variable information that we'll touch on shortly. The stepping options help us navigate through our code that's now executing line by line.

[IMAGE]

The first button is Step Over (F8). An action to take in the debugger that will step over a given line. If the line contains a function the function will be executed and the result returned without debugging each line.

[IMAGE]

The next button is step into. If the line does not contain a function it behaves the same as “step over” but if it does the debugger will enter the called function and continue line-by-line debugging there. There is also a force step into that will enter the called function regardless.

[IMAGE]

Step out can be used to return to the line where the current function was called.

There is also a live stack trace. This is useful to see where the current program is and where it's heading next. The most useful piece of the debugger, in my opinion, is the variables view. This shows a list of current variables and their values at the time of execution.

[IMAGE]


## Example
Here is a worked example.

## Tips, Tricks and Interview Questions
Here are some tips, tricks and common interview questions.
