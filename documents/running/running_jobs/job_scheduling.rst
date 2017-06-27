.. index:: Job scheduling
.. _job_scheduling:

Job scheduling
==============
Many researchers run their program on PDC's computer system, often simultaneously. The computer systems need a workload management and job scheduling. For Job scheduling PDC uses `Slurm Worlkload Manager <https://slurm.schedmd.com/>`_ . 

The queue system use two main methods *fair-share* and *Backfill* to decide which jobs are run. It might be a good idea to check how the queue system work to get your jobs a better priority, see more at [LINK TO STANDALONE PAGE ABOUT QUEUE DETAIL].


You can either put your code/program to be run on the queueing system, or book an interactive node where you can run your code interactively.

Queueing jobs
#############

* You can submit a job script to the Slurm queue system from the login node with
	.. code-block:: bash


		sbatch ./jobscript.sh

	more information on how to create an job script can be found in :ref:`job-scripts`.

* You can remove your job from queue with
	.. code-block:: bash
	
		scancel jobid

* Information about the jobs running in the queue can be obtained with
	.. code-block:: bash
		
		squeue

	you can also see your job in the queue by adding the flag **-u <username>** to *squeue*.


These commands are the basic commands for submit, cancel, check jobs to the queue system.

.. _job-scripts: 

Job scripts
*****************

To submit a job to the queue system one have to specify few details, such as the time allocation the user belong to and the number of nodes required. This is done by adding option in the job script with **#SBATCH** flag.

.. container:: toggle

	.. container:: header
		
		**Job scripts ( Tegner )**
		
	
	stuff, you know
	dont forget GPU flag and specifications
	and maybe link to example code?

.. container:: toggle

	.. container:: header

		**Job scripts (Beskow)**
		


	stuff
		...

Run interactively
#################


How are jobs scheduled
######################
