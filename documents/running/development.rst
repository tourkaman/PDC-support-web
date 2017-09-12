.. index:: developing_software
.. _development:

How to develop software
=======================

Compilers and libraries on Beskow
---------------------------------

This cluster uses compiler wrappers so that the source code is compiled
with the compiler module currently loaded.
Also, wrappers automatically link with math libraries if their modules are loaded.

Commands
^^^^^^^^

Command for using these compiler wrapper are as follows...

======== ======================
Language Command
======== ======================
C        cc [flags] source.c
C++      CC [flags] source.cpp
Fortran  ftn [flags] source.f90
======== ======================

Type of compiler
^^^^^^^^^^^^^^^^

By default the cray compiler is loaded into your environment.
In order to use another compiler you have to swap compiler modules::

  module swap PrgEnv-cray PrgEnv-other

======== ============  
Compiler Module
======== ============  
Cray     PrgEnv-cray
Intel    PrgEnv-Intel
GNU      PrgEnv-gnu
======== ============  

Libraries
^^^^^^^^^

By default normal libraries are wrapped within the compiler, but
there are others. If you would like additional libraries
they can be requested via modules and will automatically
link to the wrappers

Example::

  module load cray-libsci fftw
  
See http://pdc-software-web.readthedocs.io/en/latest/#libraries
For more libraries that can be added.

Examples
^^^^^^^^

Compiling serial and MPI code::

  # Fortran
  ftn [flags] source.f90
  # C
  cc [flags] source.c
  # C++
  CC [flags] source.cpp
  
Compiling OpenMP code::

  # Intel
  ftn -openmp source.f90
  cc -openmp source.c
  CC -openmp source.cpp
  # Cray
  ftn -h omp source.f90
  cc -h omp source.c
  CC -h omp source.cpp
  # GNU
  ftn -fopenmp source.f90
  cc -fopenmp source.c
  CC -fopenmp source.cpp

Compilers and libraries on Tegner
---------------------------------

This cluster does not use compiler wrappers so you must load the appropriate
modules and link to libraries yourself.
many versions of the different compilers do exist and the command does
differ depending on language and type of compiler.
Also on this cluster we only have the *Intel* and the *GNU* compiler.

Example of compiling serial code
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
::

  # GNU
  gfortran -o hello hello.f
  gcc -o hello hello.c
  g++ -o hello hello.cpp
  # Intel
  module add i-compilers
  ifort -FR -o hello hello.f
  icc -o hello hello.c
  icpc -o hello hello.cpp

Example of compiling OpenMP/MPI code
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
::

  # GNU
  module add gcc/5.1 openmpi/1.8-gcc-5.1 
  mpif90 -FR -fopenmp -o hello_mpi hello_mpi.f
  mpicc -fopenmp -o hello_mpi hello_mpi.c
  mpic++ -fopenmp -o hello_mpi hello_mpi.cpp
  # Intel
  module add i-compilers intelmpi
  mpiifort -openmp -o hello.f90 -o hello_mpi
  mpiicc -openmp -o hello_mpi hello_mpi.c
  mpiicpc  -openmp -o hello_mpi hello_mpi.cpp

Allinea forge
-------------

Allinea tools can be used for debugging and performance analysis.
More information at 
http://pdc-software-web.readthedocs.io/en/latest/software/allinea-forge/index.html
