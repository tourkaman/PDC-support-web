.. index:: Queue jobs
.. _Queueing_jobs:

Queueing jobs
=============

* You can submit a job script to the Slurm queue system from the login node with
  ::

    sbatch ./jobscript.sh

  more information on how to create an job script can be found in :ref:`job-scripts_tegner`.

.. Warning::

   Note that programs should **ONLY** be run with `sbatch` above or following the instruction in :ref:`Run_interactively`
   Running programs in other way will result in the program running in the login node and not the super computer. 
     
* You can remove your job from queue with
  ::
    
    scancel jobid

* Information about the jobs running in the queue can be obtained with
  ::
    squeue

	you can also see your job in the queue by adding the flag **-u <username>** to *squeue*.


These commands are the basic commands for submit, cancel, check jobs to the queue system.

.. Note::
   
   Beskow & Tegner clusters work a bit differently. This is pointed out in the below section.
   A major difference is that Beskow computing nodes *DO NOT* have access to AFS file system.
   Therefore, all files and scripts must recide in the CFS file system.
   All Beskow users have a space in the CFS file system located in
   ::
   
     /cfs/klemming/nobackup/y/yourUsername

Job scripts
-----------

To submit a job to the queue system one have to specify few details, 
such as the time allocation the user belong to and the number of nodes required.
This is done by adding option in the job script with **#SBATCH** flag. This option are then given to the SLURM.
   
The flag option specified in `#SBATCH` is for **SLURM** (the queue system). 
This have nothing to do with the `aprun` option, and both needed to be configured properly for the job to make sense. 
Below are the cluster specific instructions:

.. toctree::
   :glob:
   :maxdepth: 2
      
   job_scripts_tegner
   job_scripts_beskow
