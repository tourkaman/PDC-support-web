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

The flag option depend on the cluster you are intending to run the program on. Below are the cluster specific instructions:

.. container:: toggle

	.. container:: header
		
		**Job scripts ( Tegner )**
		
	In a job script option the following sbatch command can be defined:
	
		* **#SBATCH -A project_name** - the name of the project(time allocation) to be charged for this run. Note the name should not normally contain PDC or SNIC, so PDC-2015-1 is just 2015-1 and SNIC 2015/1-1 is just 2015-1-1	


		* **#SBATCH -t hh:mm:ss** - maximum job elapsed time should be indicated whenever possible: this allows slurm to determine best scheduling startegy.


		* **#SBATCH -n n** - Number of processes (MPI ranks) that will be reserved for the given job. Each node supports up to 48 MPI processes with hyperthreading. It is recommended to use 24 cores per node though in most cases.


		*  **#SBATCH --nodes=X** - Number of Nodes to reserve


		* **#SBATCH --ntasks-per-node=X** - Set the number of tasks per node. The default is 48, to allow the use of hyperthreading. In most cases, using 24 (the number of physical cores) is better.


		* **#SBATCH --gres=gpu:X** - for Tegner you can book nodes with GPU. note that the following command is needed for program to recognize the GPU. the *X* option can either be **K80:2** or **K420:1**
		* **#SBATCH -J job_name** - the job name is used to determine the name of job output and error files


		* **#SBATCH -e error_file.e** - job error file


		* **#SBATCH -o output_file.o** - job output file


		* **#SBATCH --mail-type=ALL** - request a mail when the job starts and ends

	dont forget GPU flag and specifications
	and maybe link to example code?

.. container:: toggle

	.. container:: header

		**Job script examples (Tegner)**
		
	Arr, here yer exaples code be!

	software specific examples can be found at <software link>
.. container:: toggle

	.. container:: header

		**Job scripts (Beskow)**
		


	stuff
		...

Run interactively
#################


How are jobs scheduled
######################
