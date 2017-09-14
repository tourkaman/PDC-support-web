.. index:: Job scheduling
.. _job_scheduling:
   
Job scheduling
==============
Many researchers run their program on PDC's computer system, often simultaneously. For this, the computer systems need a workload management and job scheduling. For Job scheduling PDC uses `Slurm Workload Manager <https://slurm.schedmd.com/>`_ . 

When you login to the supercomputer with `ssh`, you will login to a designated **login node** in your *afs home directory*. Here you can modify your scripts and manage your file.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrdkY0UWJhTXgyQ2M
	   
To run your script/program on the supercomputer, you can do it in one of the following ways.

How are jobs scheduled
----------------------

The queue system use two main methods *fair-share* and *Backfill* to decide which jobs are run. It might be a good idea to check how the queue system work to get your jobs a better priority.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqraDM5UHg0WGdQUUk

How to submit jobs
------------------

Jobs can be submitted to PDC clusters in several ways. Both by send jobs to the job queue
or by booking and running a node interactively.

.. toctree::
   :glob:
   :maxdepth: 3

   queueing_jobs
   run_interactively
