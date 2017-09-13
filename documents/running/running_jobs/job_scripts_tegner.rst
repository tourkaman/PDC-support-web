
.. index:: Job scripts(Tegner)
.. _job-scripts_tegner: 
		
Job scripts(Tegner)
===================
			   
This is an an example of a job script for a MPI program. For other programs, you can find examples in the software page `Software <http://pdc-software-web.readthedocs.io/en/latest/>`_.
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
--------------

The Tegner cluster have some GPU that can be used with CUDA (see more about hardware specification here). You can compile a code including CUDA the following way

.. code-block:: bash

   cd /cfs/klemming/nobackup/u/username
   module add cuda
   nvcc -arch=sm_37 hello.cu -o hello.out


and then excecuted with normally ( ./hello.out in a batch script, or with *srun* on interactive mode ). Remember to specify GPU nodes with 

.. code-block:: bash

   #SBATCH --gres=gpu:K80:2

for the K80 nodes or with **K420:1** for the K420 nodes.
