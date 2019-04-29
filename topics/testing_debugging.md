# Debugging and Testing

## Introduction
Debugging allows you to run a program interactively while watching the source code and the variables during the execution.

A breakpoint in the source code specifies where the execution of the program should stop during debugging. Once the program is stopped you can investigate variables, change their content, etc

## Tutorial
In this tutorial, we will be using the Intellij Java IDE. Debugging is supported in the almost any modern IDE so these steps may be replicated on other software platforms as well. Intellij is free for students and can be downloaded [here](https://www.jetbrains.com/student/) 

#### Setting a breakpoint
To define a breakpoint in your source code, click on the line in the gutter on the left side. The line of code will highlight red. 

![](../img/breakpoint.PNG?raw=true)

We want to choose our breakpoint wisely, if we know that our code is breaking at a line, set the breakpoint prior to that so we can analyze variables and control flow. Now that we have a breakpoint, we can run our program in debug mode by clicking the debug button.

![](../img/run.PNG?raw=true)

Once we click this, you'll notice that the execution halts when hitting our breakpoint we set. In the debug window you'll see some stepping options as well as some variable information that we'll touch on shortly. The stepping options help us navigate through our code that's now executing line by line.

![](../img/toolbar.PNG?raw=true)

The first button is Step Over (F8). An action to take in the debugger that will step over a given line. If the line contains a function the function will be executed and the result returned without debugging each line.

The next button is step into. If the line does not contain a function it behaves the same as “step over” but if it does the debugger will enter the called function and continue line-by-line debugging there. There is also a force step into that will enter the called function regardless. Step out can be used to return to the line where the current function was called.

There is also a live stack trace. This is useful to see where the current program is and where it's heading next. 

![](../img/stack.PNG?raw=true)

The most useful piece of the debugger, in my opinion, is the variables view. This shows a list of current variables and their values at the time of execution. 

![](../img/vars.PNG?raw=true)

## Example
First, create the following java classes. Ensure they are in a package named sample.

```java
package sample;

public class Calculator {

  public int add(int a, int b) {
    return a + b;
  }
  
  public int multiply(int a, int b) {
    return a + b;
  }
  
  public void loop() {
    for(int i=0; i<50; i++){
      System.out.println("i = "+i);
    }
  }

}

package sample;

public class Main {

  public static void main(String[] args) {
	  int a = 5;
	  int b = 10;
    Calculator c = new Calculator();
	
    int addition = c.add(a, b);
    int product = c.multiply(a, b);
    
    c.loop();
	
    System.out.println(a + " + " + b + " = " + addition);
    System.out.println(a + " * " + b + " = " + product);
  }
}
```
Complete the following tasks:

1. Set a breakpoint on the calculator constructor.
2. Step into the constructor methods.
3. Step out of the constructor methods.
4. View the addition, product, and a/b integer values in the Variables window.
5. Practice stepping into and out of the add and multiply methods.
6. Step over the loop method.
7. Rerun the program and step over the add and multiply methods functions.
8. Step into the loop method.
9. Step through the loop and attempt to step out back to Main.main.


## Tips, Tricks and Interview Questions
You can set certain properties for a breakpoint and be very selecting with your triggers. By right clicking the breakpoint and going to the properties window. For example, you can set a property that the breakpoint shall only trigger if the value of a variable is greater than something.

* What is a breakpoint?

A breakpoint in the source code specifies where the execution of the program should stop during debugging

* What's the difference between step over and step into?

Step over will gloss over a line of code if it is a method where as step into will enter the method.
