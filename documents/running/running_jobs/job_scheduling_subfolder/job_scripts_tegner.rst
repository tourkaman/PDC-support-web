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
		  
	and maybe link to example code?

	
Job script examples
*******************	
	   
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

Job scripts (Beskow)
===================	

	In the job script,  The following option can be defined:
   
	 * `#SBATCH -A allocation` - set the time allocation to be charged. This is required for all jobs, even if you only belong to a single allocation.
	 * `#SBATCH -J job_name` - the job name is used to determine the name of job output and error files
	 * `#SBATCH -t hh:mm:ss` - maximum job elapsed time should be indicated whenever possible: this allows slurm to determine best scheduling startegy. Current maximum is 24 hours.
	 * `#SBATCH -n n` - Number of processes (MPI ranks) that will be reserved for the given job. Each node supports up to 32 MPI processes. Note the actual number started with the aprun command can be different. Either use -N or -n to reserve nodes/tasks and always ask for full nodes
	 * `#SBATCH -N (--nodes)` - Number of nodes that will be reserved for a given job (we recommend that the option always is explicitly set).
	 * `#SBATCH -e error_file.e` - job error file
	 * `#SBATCH -o output_file.o` - job output file
	 * `#SBATCH --mail-type=ALL` - request a mail when the job starts and ends


	   .. note::
	     Some flags in the `#SBATCH` might look the same as the one used in aprun, such as the `-N` flag. But those two might point to different configuration. for aprun, `-N` means number of cores per node, while `-N` for SLURM means number of nodes.
	      
Job examples (Beskow)
***********************
       Below are a job script example for MPI.
   
       **Example 1:**
		      
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
		      

       An example for a Hybrid MPI+OpenMP program. This example will place 4 MPI processes with 8 threads each on each compute node. Note that -N has a different meaning for SBATCH and aprun. When supplied to SBATCH, -N(--nodes)  sets the "number of nodes", whereas for aprun it sets the "number of MPI tasks/node".

       **Example 2:**
       
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
		       
		       # Number of Nodes
		       #SBATCH --nodes=256
		       # Number of MPI tasks.
		       #SBATCH -n 1024
		       
		       # Number of MPI tasks per node
		       #SBATCH --ntasks-per-node=4
		       
		       # Number of cores hosting OpenMP threads
		       #SBATCH -c 8
		       
		       #SBATCH -e error_file.e
		       #SBATCH -o output_file.o
		       
		       export OMP_NUM_THREADS=8
		       
		       # Run the executable named myexe 
		       # and write the output into my_output_file
		       aprun -n 1024 -N 4 -d 8 -cc none ./myexe > my_output_file 2>&1
				     

