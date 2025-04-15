# Operating systems overview

A simple overview of the main computer components is given in picture below. Here we see
the hardware at the bottom. The hardware consists of chips, boards, Flash drives, disks,
a keyboard, a monitor and similar physical objects. On top of the hardware is the
software.

Most computers have two models of operation:

* __kernel mode__ or (__supervisor mode__) and
* __user mode__;

The operating system runs in kernel mode (for at least some of its functionality). In
this mode it has complete access to all the hardware and can execute any instruction the
machine is capable of executing.

The rest of the software runs in user mode, in which only a subset of the machine
instructions is available.

In particular, those instructions that affect control of the machine, determine the
security boundaries, or do I/O (Input/Output) are forbidden to user-mode programs.

![OS](/operating_systems/images/os.png)

The program that users interact with, usually called the __shell__ and the __GUI__ (
Graphical User Interface). The shell or GUI is the lowest level of user-mode software,
and allows user to start other programs.

The operating system runs on the bare hardware and provides the base for all the other
software.
