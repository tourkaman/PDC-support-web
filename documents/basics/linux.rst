.. index:: Introductin to Linux
.. _linux:

Basic Linux for new HPC users 
=============================

.. Refer to http://www.ee.surrey.ac.uk/Teaching/Unix/unix1.html
.. Refer to https://www.osc.edu/sites/osc.edu/files/documentation/Intro%20to%20Unix%202015.pdf

Working with PDC resources requires a basic understanding of Linux systems. 
Some of our users are new to using Linux-based systems and have asked for introductory materials. 
Here is a collection for the basic command-line operations needed to get started with PDC.

Using commands in the shell
---------------------------

The **shell** is the program from which the user controls everything in a text-interface. 
When you login to a PDC system remotely, you are already in the shell window of the system.
If you login to your own system, you are probably on a graphical screen. 
From there, search for terminal or Ctrl+Alt+T to enter the shell terminal.
In the shell, you can start typing commands to perform some action. 
The default shell on the PDC clusters is **bash**.

Useful Shell commands
---------------------

Upon login we are greeted with the shell
::
  
  $ ssh user@tegner.pdc.kth.se
  Last login: Fri Aug 8 10:14:59 2014 from example.com
  user@milner-login1:~> _

Bash: Files and directories
^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Command **pwd** tells me where I am. After login I am in the "home"directory
  ::
  
    user@machine:~$ pwd
    /afs/pdc.kth.se/home/u/user
    
* I can change the directory with **cd**
  ::
  
    user@machine:~$ cd tmp/talks
    user@machine:~/tmp/talks$ pwd
    /afs/pdc.kth.se/home/u/user/tmp/talks
    
* I can go one level up with **cd ..**
* I can return to my HOME folder with **cd**
* List the contents with **ls -l**
  ::
  
    user@machine:~/tmp/talks
    $ ls -ltotal 237
    drwx------ 3 user csc-users 2048 Aug 17 15:21 img
    -rw------- 1 user csc-users 18084 Aug 17 15:21 pdc-env.html
    -rw------- 1 user csc-users 222051 Aug 17 15:22 remark-latest.min.js
 
Bash: creating directories and files
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* We create a new directory called *results* and change to it
  ::
  
    $ mkdir results
    $ cd results

* Creating and editing files

  * Textfiles can be edited on your local computer and then transferred
  * Textfiles can also be edited locally using vim
    http://http://www.fprintf.net/vimCheatSheet.html
    
Copying, moving renaming and deleting
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::
  
  # copy file
  $ cp draft.txt backup.txt
  # recursively copy directory
  $ cp -r results backup
  # move/rename file
  $ mv draft.txt draft_2.txt
  # move/rename directory
  $ mv results backup
  # move directory one level up
  $ mv results ..
  # remove file
  $ rm draft.txt
  # remove directory and all its contents
  $ rm -r results

Bash: history and tab completion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* history preserve commands used
  ::

    $ history
    689  cd ..
    691  cd Documents/
    692  cp -r introduction_PDC /afs/pdc.kth.se/home/h/hzazzi/Documents/Presentations
    693  ssh beskow.pdc.kth.se
    694  cd introduction_PDC/
    695  ls -l
    696  pwd
    697  history

* If I want to repeat...
  ::

    $ !696
    pwd
    ~/Documents/introduction_PDC

* Use also the **TAB** key for completion
* **CTRL/R** to search for previous commands
* Arrows up/down to scroll for earlier commands

Bash: finding things
^^^^^^^^^^^^^^^^^^^^

* Extract lines which contain an expression with **grep**
  ::

    # extract all lines that contain searchme
    $ grep searchme draft.txt
    
* If you do not know what a UNIX command does, examine it with **man**
  ::

    $ man [command]

* Find files with **find**
  ::

    $ find ~ | grep lostfile.txt
    
* We can pipe commands and filter results with |
  ::

    $ grep energy results.out | sort | uniq
    
Bash: Redirecting output
^^^^^^^^^^^^^^^^^^^^^^^^

* Print content of a file to screen
  ::

    $ cat test.out

* Redirect output to a file
  ::

    $ cat test.out > myfile.txt
  
* Append output to a file
  ::

    $ cat test.out >> myfile.txt
  
Bash: Writing shell scripts
^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

  #!/bin/bash
  # here we loop over all files that end with *.out
  for file in *.out; do
    echo $file
    cat $file
  done
    
We make the script executable and then run it
::

  # Make it executable
  $ chmod u+x my_script
  # run it
  ./my_script

Arguments to script can be passed by using **$**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

File example
::
  
  #!/bin/bash
  echo "Hi" $1 $2

::

  $ ./myscript Nils Nilsson
  Hi Nils Nilsson
    
:$1..$X: First...Xth argument

To starting executing such scripts, you would need to start with a text-editor.
Choosing a text-editor is a matter of personal choice, the most popular ones being Vim and Emacs. 
But there are a lot more new and interesting ones. 
Open your favorite text-editor and copy-paste the file example above and save with file as <script>.
Then run the script by typing ``./<script>``.

Information about shell commands
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Information about a commands can be retrieved from the manual
::

  man <cmd>
  
Also you can get information about where the executable lies
::

  which <cmd>

Executing your software
^^^^^^^^^^^^^^^^^^^^^^^

Most commands are quite intuitive acronyms and are easy to remember once you start using them. 
The usual syntax is
::

  command -option1 arg1 -option2 arg2
  
where ``command`` is the name of the command, 
``-option1`` and ``-option2`` specifies the particulars of the command (they are optional, 
there can be as many options as the specific command permits), and ``arg1`` and ``arg2`` are 
the value of the corresponding options.
In general
::

  command -h
  
Prints information about what options and arguments you can enter.

Further information
^^^^^^^^^^^^^^^^^^^

.. seealso::
 
 The Linux Command Line by William E. Shotts, Jr.
   This book introduces the linux command line from the basics, and moves on to customizing the working environment and then finally to shell scripting. The entire book is available for free from the authors web page, and if you would like a paper copy you can order one from the publisher.

 UNIX / Linux Tutorial for Beginners
   The University of Surrey has an online tutorial that introduces the linux command line. The web page also has links to other recommended linux books.
