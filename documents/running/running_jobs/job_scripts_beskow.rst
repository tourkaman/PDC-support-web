
.. index:: Job scripts(Beskow)
.. _job-scripts_beskow: 

Job scripts (Beskow)
======================

Job examples (Beskow)
---------------------
   
Below are a job script example for MPI. For other programs, you can find examples in the software page `Software <http://pdc-software-web.readthedocs.io/en/latest/>`_.
   
**Example 1:**
::
   
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
		      
Below is another example for a Hybrid MPI+OpenMP program. This example will place 4 MPI processes with 8 threads each on each compute node. Note that -N has a different meaning for SBATCH and aprun. When supplied to SBATCH, -N(--nodes)  sets the "number of nodes", whereas for aprun it sets the "number of MPI tasks/node".

**Example 2:**
:: 

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
