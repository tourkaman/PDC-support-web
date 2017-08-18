
.. index:: Job scheduling
.. _job_scheduling:
   
Job scheduling
==============
Many researchers run their program on PDC's computer system, often simultaneously. For this, the computer systems need a workload management and job scheduling. For Job scheduling PDC uses `Slurm Workload Manager <https://slurm.schedmd.com/>`_ . 

When you login to the supercomputer with `ssh`, you will login to a designated **login node** in your *afs home directory*. Here you can modify your scripts and manage your file.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrdkY0UWJhTXgyQ2M
	   
To run your script/program on the supercomputer, you can do it in one of the following ways.


Queue jobs
###############################################
Here's a simplified workflow of queueing jobs to the supercomputer.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqra2JSUnpYcUJtOGc

For running time counsuming large programs, sending the job to the queue system might be preferred. You can find more information about how to queue jobs at:
:ref:`send the code to the queueing system <Queueing_jobs>` `(sbatch)`


Run Interactively
######################################################

Here's a simplified workflow of booking a node.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrbTVybmJTZWRFRjA

Booking a node might be suitable if you want to test and verify your code in a parallell environment, or when the code is not time consuming but frequent adjustment is needed. You can find more information about how to run interatively at:
:ref:`book an interactive compute node where you can run your code. <Run_interactively>` `(salloc)`:

     
How are jobs scheduled
######################

The queue system use two main methods *fair-share* and *Backfill* to decide which jobs are run. It might be a good idea to check how the queue system work to get your jobs a better priority.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqraDM5UHg0WGdQUUk
