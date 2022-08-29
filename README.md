_Author:_ Nathaniel Thomas

_Assignment:_ Lab Exercise 1

_Class:_ CSCE 313 - 508

__Assignment Prompt:__

Lab exercise 1
Environment Setup, Debugging, and C++ Refresh
Due date
Sep 5, 2022
Introduction
The objective of this exercise is to help you get ready for the programming assignments by covering some introductory topics. Through this assignment, you will complete setting up your own development environment where you will work until the end of the semester, learn the use of debuggers to debug your programs, and recap the core concepts of C/C++ programming.
You are given a simple program, buggy.cpp, that computes the area of shapes that has several compile/syntax errors and bugs that you are going to discover, debug, and fix with the help of three different debugging methods. Once you have corrected the program and committed to the repository, we will use the auto-grader of GitHub Classroom to grade your project.

__Development Environment Setup__

Depending on your host system operating system, there are a few options for the development environment:
1. Windows 10/11 Only: WSL2 is the recommended development environment. The tutorial can be found here:

    a. [Microsoft official tutorial](https://docs.microsoft.com/en-us/windows/wsl/install)

    b. [Windows 10 YouTube tutorial](https://www.youtube.com/watch?v=n-J9438Mv-s)

    c. [Windows 11 YouTube tutorial](https://www.youtube.com/watch?v=FQ6ahcJOVz0)

2. Google Cloud Platform: If you do not have a local Linux system, you can create a virtual machine on Google Cloud. The tutorial is [here](https://docs.google.com/document/d/10r5wUHH8dCLi6237dx9DFazqxQJtxhPixr3Iqxbzqzw/edit?usp=sharing).

3. Other platforms: You are also welcomed to have a clean boot of Linux through dual boot, USB boot, or on a separate machine (remote or local). As long as it is a Linux environment, you should be good.

__Important note:__ Do not use the department Linux servers. You should have a dedicated environment, on which you have administrator privileges.

Once you have your environment set up, you can install relevant packages with sudo apt install or sudo apt-get install. The following packages need to be installed:
* g++, gcc, make, gdb, libasan5

The recommended code environment is VSCode (as it has support for GitHub Classroom). Once installed, the recommended extensions are:
* GitHub Classroom, C/C++ Extension Pack, Remote Development (for WSL2), Remote - SSH

__Debugging Methods__

There are three debugging methods presented in this lab. In this exercise, you can determine which one works best for moving forward with other programming assignments.

__GDB.__ The first method presented is GDB. In order to use this method, you must include __-g__ in your compile statement (e.g., __g++ -g -o buggy buggy.cpp__). Once compiled, you can run your program in gdb with __gdb buggy__. Once GDB is running, to run the executable, simply use the __run__ command. When/If the program stops due to some error, you can run __backtrace__ to see where the program stopped and the error it encountered. You can then use the __break__ command to set a breakpoint before the line the error occurs, and then use the __print__ command to check values at the breakpoint. You can use __continue/step__ to move past the break. GDB Documentation can be found through [sourceware.org](sourceware.org).

__AddressSanitizer.__ Another useful debugging tool is AddressSanitizer (aka ASan). In order to use ASan, you must include __-fsanitize=address,undefined__ in your compile statement (e.g. __g++ -fsanitize=address,undefined -o buggy buggy.cpp__). You can then run the executable as normal and the tool will print pertinent information about memory issues if an error occurs. The ASan tool is break-at-first-error, meaning multiple runs of AddressSanitizer may be necessary to catch all errors. Tutorials to ASan can be found [here](https://youtu.be/MB6NPkB4YVs), [here](https://youtu.be/nkxGxWo2THo), and [here](https://youtu.be/1CcuD7EwhOY) ([here is a longer video](https://youtu.be/wfk0K4tFHk4)) - focus on how ASan is used.

__IDE Debugging.__ The final debugging method is to use the in-built IDE debugging tool. It is required that the GDB package be installed if you are using the VSCode debugger. Debugging reference for VSCode can be found [here](https://code.visualstudio.com/docs/cpp/cpp-debug).

__The Buggy Program__

The buggy program starter code consists of the following:

* A struct __Point__, which defines a point on the coordinate plane by its x and y value.
* A class __Shape__, which defines a shape formed by a number of different points or vertices (created by the struct Point) on the coordinate plane.
* The function __main()__, which creates two shapes (a triangle and a quadrilateral) using the definitions above.

You are expected to complete the following tasks for the buggy program to be fully functional:

1. Shape’s __addPoints(...)__ function is expected to take in a single parameter – an unsized Point array called pts.

2. In Shape’s __area()__ function, the computation of variables __lhs__ and __rhs__ in their current state is faulty due to incorrect member access of pointers. There are two different methods to fix such member access; you are expected to use one method to fix __lhs__ and the other to fix __rhs__.

3. In __main()__, you are expected to create three Point structs (corresponding to tri1, tri2, and tri3) in three different ways. These points will help construct the Shape object, __tri__. You are also expected to create four Point structs (corresponding to quad1, quad2, quad3, and quad4) in any way you choose. These points will help construct the Shape object, __quad__. Finally, print out the area of the two shapes (tri and quad) created.

Note that your tasks may not just be limited to ones explicitly defined above. Ensure that all dynamically allocated memory is properly cleaned up.

__Rubric__

There are three tests that check the elements of the program which you have been asked to fix and grades will be assigned as the score you see on GitHub classrooms (under the Actions tab):
1. Compilation (34 pts)
2. Correct output (33 pts)
3. No leaking memory (33 pts)

Partial credit will not be assigned for this exercise; it is all-or-nothing.

__Getting started__

The assignment template is hosted on GitHub classroom. Complete the following steps to get started:
1. Go to the assignment’s GitHub classroom: https://classroom.github.com/a/RO-ib28S
2. Link your Github account to the classroom - If you cannot find your name, accidentally link the account to a wrong name, or want to change the account linked, please contact a TA
3. Clone your assignment repository on the Linux machine
  
    a. [Official SSH guide by GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
  
    b. [This is a tutorial on how to clone, edit, and commit changes to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
