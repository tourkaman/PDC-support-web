
.. index:: Job scripts(Tegner)
.. _job-scripts_tegner: 
		
Job scripts(Tegner)
===================
		
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

	
Job examples (Tegner)
*********************
	   
This is an an example of a job script for a MPI program. For other programs, you can find examples in the software page `Software <http://pdc-software-web.readthedocs.io/en/latest/>`_.
		
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
	      #SBATCH --nodes=2
	      # Number of MPI processes per node
	      #SBATCH --ntasks-per-node=24
	      
	      #SBATCH -e error_file.e
	      #SBATCH -o output_file.o
	      
              # Load the Intel MPI module
              module add intelmpi/17.0.1

	      # Run the executable named myexe with MPI-rank of 48
	      # and write the output into my_output_file
	      mpirun -n 48 ./myexe > my_output_file 2>&1
   
Cuda on Tegner
***************
The Tegner cluster have some GPU that can be used with CUDA (see more about hardware specification here). You can compile a code including CUDA the following way

.. code-block:: bash

   cd /cfs/klemming/nobackup/u/username
   module add cuda
   nvcc -arch=sm_37 hello.cu -o hello.out


and then excecuted with normally ( ./hello.out in a batch script, or with *srun* on interactive mode ). Remember to specify GPU nodes with 

.. code-block:: bash

   #SBATCH --gres=gpu:K80:2

for the K80 nodes or with **K420:1** for the K420 nodes.
