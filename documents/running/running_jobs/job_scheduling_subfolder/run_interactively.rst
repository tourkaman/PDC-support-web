.. index:: Run interactively
.. _Run_interactively:
		
Run interactively
#################
Compute nodes can be booked using the queue system for interactive use. The command to do this is `salloc`

.. code-block:: bash
		
   salloc --nodes=2 -t 1:00:00 -A <project>

The above command would then book two nodes for one hour. The `-A <project>` should be the time allocation you are a part of. You can check the time allocations you are a member of with

.. code-block:: bash
		
   projinfo

Depending on how busy the supercomputer is, it might take a while before the interactive node is booked. The terminal would then be loading while it waits in the queue. When an node is ready you will recieve a message like

.. code_block:: bash
   
   salloc: Granted job allocation <jobid>

For Tegner the name of the node booked, usually something like *t01n08* is also printed in the terminal. Keep in mind that the node is booked as long as you have not shut down the terminal you typed salloc, or typing the ``exit`` command, or the time runs out

When a node is booked, the program must be run with a *cluster specific commands* specified below.  

Beskow
*******
For beskow a job can be started using `aprun`.

.. code-block:: bash
   aprun -n 64 ./program

   check the manual page of aprun for more details about flags and options with

.. code-block:: bash
   man aprun



Tegner
*******
For tegner, the jobs can then be started using mpirun or srun e.g.

.. code-block:: bash
   module add intelmpi/5.0.3
   mpirun -np 48 ./program

.. code-block:: bash
   srun -n 1 ./program
or other softwares available in <SOFTWARE PAGE>. the Module add command is how you add a software to your working environment, see here for more detail.
