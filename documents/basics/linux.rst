.. index:: Introductin to Linux
.. _linux:

Tutorial: Linux 
========================

.. Refer to http://www.ee.surrey.ac.uk/Teaching/Unix/unix1.html

.. rubric:: Starting with UNIX

Working with PDC resources requires a basic understanding of Linux systems. Some of our users are new to using Linux-based systems and have asked for introductory materials. We give a simple tutorial with basic command-line operations needed to get started with PDC.

The **shell** is the program from which the user control all things interesting. When you login to a system remotely, you are already in the shell window of the system. If you login to your own system, you are in the graphical screen. From there, search for terminal or Ctrl+Alt+T to enter the shell terminal.

In the shell, you can start typing commands to perform some action. Most commands are quite intuitive acronums and are easy to remember once you start using them. Start with ``pwd``  to print the address of directory your shell is currently in (**p**\ rint **w**\ orking **d**\ irectory). The **ls** command prints the files and directories present in the directory. It is also important to know how to navigate around the directories in your system: the **cd** (**c**\ hange **d**\ irectory) can be used for that. Unlike the previous commands, **cd** requires more attributes to tell which directory to go to. In UNIX, . and .. means current and parent directories. Type **cd .** or **cd ..** to go to the same or the parent directory.

.. table:: Basic UNIX commands
   :widths: auto
   :align: center

   ========================  ====================================
      Command                  Description
   ========================  ====================================
      ``pwd``                  print working directory
      ``cd <path>``            change directory
      ``ls``                   list files in the working directory
      ``mkdir <name>``         make directory named <name>
      ``cp <src> <dst>``       copy file from <src> to <dst>
      ``mv <src> <dst>``       move file from <src> to <dst>
      ``rm <name>``            remove file <file>

   ========================  ====================================

For additional explanations, have a look at the command manual by typing ``man <cmd>``. 

.. seealso:: 
 
 The Linux Command Line by William E. Shotts, Jr.
   This book introduces the linux command line from the basics, and moves on to customizing the working environment and then finally to shell scripting. The entire book is available for free from the authors web page, and if you would like a paper copy you can order one from the publisher.

 UNIX / Linux Tutorial for Beginners
   The University of Surrey has an online tutorial that introduces the linux command line. The web page also has links to other recommended linux books.

Tutorial: Scripting and text-editors
====================================

Now that we can use Linux commands on the shell, we can move on to executing a bunch of commands together. This is usually executing a file called **script** that contains the list of commands to be executed sequentially.

.. code-block:: scipt
		
   #!/bin/bash
   # here we loop over all files that end with *.out
   for file in *.out; do
     echo $file
     cat $file
   done

To starting executing such scripts, you would need to start with a text-editor. Choosing a text-editor is a matter of personal choice, the most popular ones being Vim and Emacs. But there are a lot more new and interesting ones. Open your favorite text-editor and copy-paste the above code and save with file as <script>. Then run the script by typing ``./<script>``. 
