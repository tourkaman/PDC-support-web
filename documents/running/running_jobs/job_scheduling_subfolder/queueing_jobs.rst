.. index:: Queue jobs
.. _Queueing_jobs:

Queueing jobs
#############

* You can submit a job script to the Slurm queue system from the login node with
	.. code-block:: bash


		sbatch ./jobscript.sh

	more information on how to create an job script can be found in :ref:`job-scripts`.

	.. Warning::

	   Note that programs should **ONLY** be run with `sbatch` above or following the instruction in :ref:`Run_interactively` ! Running programs in other way will result in the program running in the login node and not the super computer. 
* You can remove your job from queue with
	.. code-block:: bash
	
		scancel jobid

* Information about the jobs running in the queue can be obtained with
	.. code-block:: bash
		
		squeue

	you can also see your job in the queue by adding the flag **-u <username>** to *squeue*.


These commands are the basic commands for submit, cancel, check jobs to the queue system.

.. Note::
   
   Beskow & Tegner clusters work a bit differently. This is pointed out in the below section. A major difference is that Beskow computing nodes *DO NOT* have access to AFS file system. Therefore, all files and scripts must recide in the CFS file system. All Beskow users have a space in the CFS file system located in:

   .. code-block:: bash
		
	   /cfs/klemming/nobackup/y/yourUsername


	   
For information about how a job script is written look at:
     * :ref:`Job scripts <job-scripts>`
