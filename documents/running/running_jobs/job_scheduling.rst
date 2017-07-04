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

.. _job-scripts: 

Job scripts
*****************

To submit a job to the queue system one have to specify few details, such as the time allocation the user belong to and the number of nodes required. This is done by adding option in the job script with **#SBATCH** flag.

.. note::
   The flag option and the procedure depend on the cluster you are intending to run the program on. Below are the cluster specific instructions:

.. container:: toggle

	.. container:: header
		
		**Job scripts ( Tegner )**
		
	In a job script option the following sbatch command can be defined:
	
		* ``#SBATCH -A project_name`` - the name of the project(time allocation) to be charged for this run. Note the name should not normally contain PDC or SNIC, so PDC-2015-1 is just 2015-1 and SNIC 2015/1-1 is just 2015-1-1	



	        * ``#SBATCH -t hh:mm:ss``  - maximum job elapsed time should be indicated whenever possible: this allows slurm to determine best scheduling startegy.



		* ``#SBATCH -n n`` - Number of processes (MPI ranks) that will be reserved for the given job. Each node supports up to 48 MPI processes with hyperthreading. It is recommended to use 24 cores per node though in most cases.



		*  ``#SBATCH --nodes=X`` - Number of Nodes to reserve



		* ``#SBATCH --ntasks-per-node=X`` - Set the number of tasks per node. The default is 48, to allow the use of hyperthreading. In most cases, using 24 (the number of physical cores) is better.


		  
		* ``#SBATCH --gres=gpu:X`` - for Tegner you can book nodes with GPU. note that the following command is needed for program to recognize the GPU. the *X* option can either be **K80:2** or **K420:1**
		  
		* ``#SBATCH -J job_name`` - the job name is used to determine the name of job output and error files
		  

		* ``#SBATCH -e error_file.e`` - job error file


		* ``#SBATCH -o output_file.o`` - job output file

		  
		* ``#SBATCH --mail-type=ALL`` - request a mail when the job starts and ends
		  
	and maybe link to example code?

	
.. container:: toggle

	.. container:: header
		
	   **Job script examples (Tegner)**
	   
	This is an an example of a job script for a MPI program. For other program, you can find an example in the software page <HYPERLINK SOFTWARE>.
		
        .. code-block:: bash
	      
	      #!/bin/bash -l
	      # The -l above is required to get the full environment with modules

	      # Set the allocation to be charged for this job
	      # not required if you have set a default allocation
	      #SBATCH -A 201X-X-XX
	      
	      # The name of the script is myjob
	      #SBATCH -J myjob
	      
	      # Only 1 hour wall-clock time will be given to this job
	      #SBATCH -t 1:00:00
	      
	      # Number of nodes
	      #SBATCH --nodes=4
	      # Number of MPI processes per node (the following is actually the default)
	      #SBATCH --ntasks-per-node=32
	      
	      #SBATCH -e error_file.e
	      #SBATCH -o output_file.o
	      
	      # Run the executable named myexe 
	      # and write the output into my_output_file
	      aprun -n 128 ./myexe > my_output_file 2>&1
   
	software specific examples can be found at <software link>. Note that the command `aprun` have to be used to run the code in parallel!


.. container:: toggle

	.. container:: header

		       **Job scripts (Beskow)**

	In the job script,  The following option can be defined:
   
	 * `#SBATCH -A allocation` - set the time allocation to be charged. This is required for all jobs, even if you only belong to a single allocation.
	 * `#SBATCH -J job_name` - the job name is used to determine the name of job output and error files
	 * `#SBATCH -t hh:mm:ss` - maximum job elapsed time should be indicated whenever possible: this allows slurm to determine best scheduling startegy. Current maximum is 24 hours.
	 * `#SBATCH -n n` - Number of processes (MPI ranks) that will be reserved for the given job. Each node supports up to 32 MPI processes. Note the actual number started with the aprun command can be different. Either use -N or -n to reserve nodes/tasks and always ask for full nodes
	 * `#SBATCH -N (--nodes)` - Number of nodes that will be reserved for a given job (we recommend that the option always is explicitly set).
	 * `#SBATCH -e error_file.e` - job error file
	 * `#SBATCH -o output_file.o` - job output file
	 * `#SBATCH --mail-type=ALL` - request a mail when the job starts and ends


		   stuff
		...



.. _Run_interactively:
		
Run interactively
#################
Compute nodes can be booked using the queue system for interactive use. The command to do this is `salloc`

.. code-block:: bash
		
   salloc --nodes=2 -t 1:00:00 -A <project>

The above command would then book two nodes for one hour. The `-A <project>` should be the time allocation you are a part of. You can check the time allocations you are a member of with

.. code-block:: bash
		
   projinfo
   



How are jobs scheduled
######################
