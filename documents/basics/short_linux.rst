.. index:: shortlinux
.. _shortlinux:

Short introduction to the UNIX shell
====================================

We are greeted with a command-line interface (CLI)

::
  
  $ ssh user@milner.pdc.kth.se
  Last login: Fri Aug 8 10:14:59 2014 from example.com
  user@milner-login1:~> _

Bash: Files and directories
---------------------------

* Command **pwd** tells me where I am. After login I am in the "home"directory::
  
    user@machine:~$ pwd
    /afs/pdc.kth.se/home/u/user
    
* I can change the directory with **cd**::
  
    user@machine:~$ cd tmp/talks
    user@machine:~/tmp/talks$ pwd
    /afs/pdc.kth.se/home/u/user/tmp/talks
    
* I can go one level up with **cd ..**
* List the contents with **ls -l**::
  
    user@machine:~/tmp/talks
    $ ls -ltotal 237
    drwx------ 3 user csc-users 2048 Aug 17 15:21 img
    -rw------- 1 user csc-users 18084 Aug 17 15:21 pdc-env.html
    -rw------- 1 user csc-users 222051 Aug 17 15:22 remark-latest.min.js
 
Bash: creating directories and files
------------------------------------

* We create a new directory called *results* and change to it::
  
    $ mkdir results
    $ cd results

* Creating and editing files

  * Textfiles can be edited on your local computer and then transferred
  * Textfiles can also be edited locally using vim
    http://http://www.fprintf.net/vimCheatSheet.html
    
Copying, moving renaming and deleting
-------------------------------------

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
--------------------------------

* history preserve commands used::

    $ history
    689  cd ..
    691  cd Documents/
    692  cp -r introduction_PDC /afs/pdc.kth.se/home/h/hzazzi/Documents/Presentations
    693  ssh beskow.pdc.kth.se
    694  cd introduction_PDC/
    695  ls -l
    696  pwd
    697  history

* If I want to repeat...::

    $ !696
    pwd
    ~/Documents/introduction_PDC

* Use also the **TAB** key for completion
* **CTRL/R** to search for previous commands
* Arrows up/down to scroll for earlier commands

Bash: finding things
--------------------

* Extract lines which contain an expression with **grep**::

    # extract all lines that contain searchme
    $ grep searchme draft.txt
    
* If you do not know what a UNIX command does, examine it with **man**::

    $ man [command]

* Find files with **find**::

    $ find ~ | grep lostfile.txt
    
 * We can pipe commands and filter results with |::
 
    $ grep energy results.out | sort | uniq

Bash: Redirecting output
------------------------

* Print content of a file to screen::

    $ cat test.out

* Redirect output to a file::

    $ cat test.out > myfile.txt
  
* Append output to a file::

    $ cat test.out >> myfile.txt
  
Bash: Writing shell scripts
---------------------------

::

  #!/bin/bash
  # here we loop over all files that end with *.out
  for file in *.out; do
    echo $file
    cat $file
  done
    
We make the script executable and then run it::

  # Make it executable
  $ chmod u+x my_script
  # run it
  ./my_script

Arguments to script can be passed by using **$**
------------------------------------------------

::
  
  #!/bin/bash
  echo "Hi" $1 $2

::

  $ ./myscript Nils Nilsson
  Hi Nils Nilsson
    
:$1..$X: First...Xth argument
