.. index:: Run interactively
.. _Run_interactively:
		
Run interactively
#################

Compute nodes can be booked from the queue system for interactive use. This means that you can run your program similar to how you run it on a local computer through terminal.

Booking an interactive node can be useful when you want to test, verify or debug your code in a parallell environment. It's also suitable when the program is not time consuming but is in need of frequent adjustment. For a large scale program we recommend :ref:`Queueing jobs <Queueing_jobs>` instead, since waiting for an interactive node booked with large amount of run time can take a lot of time.

 The command to book an interactive node is `salloc`

.. code-block:: bash
		
   salloc --nodes=2 -t 1:00:00 -A <project>

The above command would then book two nodes for one hour. The `-A <project>` should be the time allocation you are a part of. You can check the time allocations you are a member of with

.. code-block:: bash
		
   projinfo

The ``-A`` flag must be specified, or the command will give an error. If you do not type ``-t`` or the amount of nodes, the standard value is used. (This is cluster specific. More information can be found below)

Depending on how busy the supercomputer is, it might take a while before the interactive node is booked. The terminal would then be loading while it waits in the queue. When an node is ready you will recieve a message like

.. code-block:: bash
   
   salloc: Granted job allocation <jobid>

For Tegner the name of the node booked, usually something like *t01n08* is also printed in the terminal. 

When a node is booked, the program must be run with *cluster specific commands* specified below. If you're running a specific software, please see the :ref:`Accessing software <software>`.  

.. Note::
  
   Keep in mind that after *salloc* you're still in the Login Node! if you execute a program without the specific commands the program will be running in the login node! 


Keep in mind that the node is booked as long as you have not shut down the terminal you typed salloc, or typing the ``exit`` command, or the time runs out.

 

Beskow
*******
.. Note::

   The standard value of ``-t`` and ``--nodes`` for ``salloc`` in Beskow is 1 hour and 4 nodes.


For beskow a job can be started using `aprun`.

.. code-block:: bash

   aprun -n 64 ./program

check the manual page of aprun for more details about flags and options with

.. code-block:: bash

   man aprun


Tegner
*******

.. Note::

   The standard value of ``-t`` and ``--nodes`` for ``salloc`` in Tegner is (loosely speaking) **Infinity** and 1 node. Since the queueing system prioritise smaller running time, this usually means that you will never get an interactive node. Therefore **always** specify the ``-t`` flag.


For tegner, the jobs can be started using mpirun or srun.

.. code-block:: bash

   module add intelmpi/5.0.3
   mpirun -np 48 ./program

.. code-block:: bash

   srun -n 1 ./program


