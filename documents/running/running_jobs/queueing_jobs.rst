.. index:: Queue jobs
.. _Queueing_jobs:

Queueing jobs
=============

Here's a simplified workflow of queueing jobs to the supercomputer.

.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqra2JSUnpYcUJtOGc

For running time counsuming large programs, sending the job to the queue system might be preferred.

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
   
   Our clusters work a bit differently. This is pointed out in the below section.
   A major difference is that some cluster computing nodes *DO NOT* have access to AFS file system.
   Therefore, all files and scripts must recide in the lustre file system.
   ::
   
     /cfs/klemming/nobackup/y/yourUsername
     
   But it is always good practice to run any type of job in the lustre file system

.. toctree::
   :glob:
   :maxdepth: 3
      
   job_scripts

