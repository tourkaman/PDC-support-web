.. index:: Introductin to Linux
.. _linux:

Tutorials: Linux 
================

.. Refer to http://www.ee.surrey.ac.uk/Teaching/Unix/unix1.html
.. Refer to https://www.osc.edu/sites/osc.edu/files/documentation/Intro%20to%20Unix%202015.pdf

Working with PDC resources requires a basic understanding of Linux systems. Some of our users are new to using Linux-based systems and have asked for introductory materials. We give a simple tutorial with basic command-line operations needed to get started with PDC.

.. rubric:: Using commands in the shell

The **shell** is the program from which the user controls (almost) everything in a text-interface. When you login to a PDC system remotely, you are already in the shell window of the system. If you login to your own system, you are probably on a graphical screen. From there, search for terminal or Ctrl+Alt+T to enter the shell terminal.

In the shell, you can start typing commands to perform some action. Most commands are quite intuitive acronyms and are easy to remember once you start using them. The usual syntax is ``command -option1 arg1 -option2 arg2``, where ``command`` is the name of the command, ``-option1`` and ``-option2`` specifies the particulars of the command (they are optional, there can be as many options as the specific command permits), and ``arg1`` and ``arg2`` are the value of the corresponding options. Start by entering ``date`` to print the system date and time on the screen.

.. rubric:: Working with directories and file systems

Knowing how to navigate directories and handle files is very important when using PDC resources. The shell command you see is always active on some directory. Let's start with ``pwd`` (**p**\ rint **w**\ orking **d**\ irectory) to print the address of directory your shell is currently in.

File systems in Linux are organized as a tree structure. Each directory can have any number of files or more directories. What you see printed as your working directory (something like ``a/b/c/d``) is tracing your current directory from the root of the tree top-down. The ``ls`` command prints the files and directories present in the directory.

It is also important to know how to navigate around the directories in your system: the ``cd`` (**c**\ hange **d**\ irectory) can be used for that. Unlike the previous commands, ``cd`` requires more attributes to tell which directory to go to.

You can either enter any directory inside you current directory by entering ``cd <dir>``. You can also jump to any other directory if you know the complete path of the directory ``cd x/y/z``. UNIX also offers special symbols ``.`` and ``..`` meaning current and parent directories to your current directoryx. Type ``cd .`` or ``cd ..`` to go to the same or your parent directory. There are some more special symbols to denote directories: ``~`` refers to the user home directory. 

.. table:: 
   :widths: auto
   :align: center

   ================================  ====================================
      Command                          Description
   ================================  ====================================
      ``echo <arg>``                   prints <arg> to standard output
      ``cat <file1> <file2>``          concatenates and prints file content
      ``pwd``                          print working directory
      ``ls``                           list files in the working directory
      ``cd <path>``                    change directory
      ``mkdir <name>``                 make directory named <name>
      ``cp <src> <dst>``               copy file from <src> to <dst>
      ``mv <src> <dst>``               move file from <src> to <dst>
      ``rm <name>``                    remove file <file>
      
   ================================  ====================================
   
.. rubric:: Meta-commands

There is much more commands than the ones listed above. To know more about the new commands, some meta-commands are quite useful. For detailed explanation of some command, bash provides a **man**\ ual command which can by used by entering ``man <cmd>``. To know the directory where the command file resides, type ``which <cmd>``.


.. table:: 
   :widths: auto
   :align: center

   ========================  ====================================
      Command                  Description
   ========================  ====================================
      ``man <cmd>``            manual for the command <cmd>
      ``which <cmd>``          print the path name of the command <cmd> 

   ========================  ====================================
   
.. rubric:: Writing scripts

Now that we can use Linux commands on the shell, we can move on to executing a bunch of commands together. This is usually executing a file called **script** that contains the list of commands to be executed sequentially.

.. code-block:: bash
		
   #!/bin/bash
   # here we loop over all files that end with *.out
   for file in *.out; do
     echo $file
     cat $file
   done

.. TODO: add explanation for each script line: commenting, loops, $, echo, cat, ..

To starting executing such scripts, you would need to start with a text-editor. Choosing a text-editor is a matter of personal choice, the most popular ones being Vim and Emacs. But there are a lot more new and interesting ones. Open your favorite text-editor and copy-paste the above code and save with file as <script>. Then run the script by typing ``./<script>``.

.. seealso::
 
 The Linux Command Line by William E. Shotts, Jr.
   This book introduces the linux command line from the basics, and moves on to customizing the working environment and then finally to shell scripting. The entire book is available for free from the authors web page, and if you would like a paper copy you can order one from the publisher.

 UNIX / Linux Tutorial for Beginners
   The University of Surrey has an online tutorial that introduces the linux command line. The web page also has links to other recommended linux books.
