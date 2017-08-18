
.. index:: Job scheduling
.. _job_scheduling:
   
Job scheduling
==============
Many researchers run their program on PDC's computer system, often simultaneously. For this, the computer systems need a workload management and job scheduling. For Job scheduling PDC uses `Slurm Workload Manager <https://slurm.schedmd.com/>`_ . 

When you login to the supercomputer with `ssh`, you will login to a designated **login node** in your *afs home directory*. Here you can modify your scripts and manage your file.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrdkY0UWJhTXgyQ2M
	   
To run your script/program on the supercomputer, you need to use special commands to either:


:ref:`Queue jobs <Queueing_jobs>`
#################################
Here's a simplified workflow of queueing jobs to the supercomputer. [not sure if this picture should be here or next page].

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqra2JSUnpYcUJtOGc


:ref:`send the code to the queueing system <Queueing_jobs>` `(sbatch)`


:ref:`Run Interactively <Run_interactively>`
############################################
Here's a simplified workflow of booking a node.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrbTVybmJTZWRFRjA
     
:ref:`book an interactive compute node where you can run your code. <Run_interactively>` `(salloc)`:



The queue system use two main methods *fair-share* and *Backfill* to decide which jobs are run. It might be a good idea to check how the queue system work to get your jobs a better priority, see more at [LINK TO STANDALONE PAGE ABOUT QUEUE DETAIL].
   

Guide: SLURM scheduling
#######################

TODO: Explain how SLURM performs job scheduling and queueing
