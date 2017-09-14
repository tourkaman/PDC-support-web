
.. index:: Job scripts
.. _job-scripts: 
		
Job scripts
===========

To submit a job to the queue system one have to specify few details, 
such as the time allocation the user belong to and the number of nodes required.
This is done by adding option in the job script with **#SBATCH** flag. This option are then given to the SLURM.
   
The flag option specified in `#SBATCH` is for **SLURM** (the queue system). 
This have nothing to do with the `aprun` option, and both needed to be configured properly for the job to make sense. 		
In a job script option the following sbatch command can be defined:

.. glossary::

  #SBATCH -A project_name
    the name of the project(time allocation) to be charged for this run.
    Note the name should not normally contain PDC or SNIC, so PDC-2015-1 is just 2015-1 and SNIC 2015/1-1 is just 2015-1-1	
  
  #SBATCH -t hh:mm:ss
    maximum job elapsed time should be indicated whenever possible:
    this allows slurm to determine best scheduling startegy.

  #SBATCH -n n
    Number of processes (MPI ranks) that will be reserved for the given job.
    Each node supports up to 48 MPI processes with hyperthreading. It is recommended to use 24 cores per node though in most cases.

  #SBATCH --nodes=X
    Number of Nodes to reserve

  #SBATCH --ntasks-per-node=X
    Set the number of tasks per node. The default is 48, to allow the use of hyperthreading.
    In most cases, using 24 (the number of physical cores) is better.

  #SBATCH --gres=gpu:X
    for Tegner you can book nodes with GPU.
    note that the following command is needed for program to recognize the GPU.
    the *X* option can either be **K80:2** or **K420:1**
		  
  #SBATCH -J job_name
    the job name is used to determine the name of job output and error files
		  
  #SBATCH -e error_file.e
    job error file

  #SBATCH -o output_file.o
    job output file

  #SBATCH --mail-type=ALL
    request a mail when the job starts and ends

For job examples see information about specific clusters at...

.. toctree::
   :glob:
   :maxdepth: 2

   job_scripts_tegner
   job_scripts_beskow
