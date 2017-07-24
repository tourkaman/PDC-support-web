.. index:: Glossary of terms
.. _glossary:

Glossary
========

Here you will find the basic terminologies and quick reference materials.

.. glossary::
   
   cluster
     Computer cluster is in the broad sense terminology for a supercomputer, consisting of a set of connected computers working together so that they can be viewed as a single system. Currently PDC have two clusters, **Tegner** and **Beskow**.
     
   node
     Nodes are component of a cluster and analogus to computer we use everyday. A supercomputer consist of a number of nodes that perform computations and runs its own instance of an operating system.
   
   prosessor
     component of each node. Each node have a number of processors that is analogus to the CPU(Central processing unit) in a personal computer.

   core
     component of each processor. The actual computing entities. 

   Time Allocation
     Time Allocation is the technical term for "Project" that users need to be a part of to use the supercomputer. Time allocation contains information about the project and how much resources the project have been allocated. There are different types of time allocation depending on how one applied for one, but for runtime instruction there is no difference.

   Principal Investigator (PI)
     Principal Investigator is the "Project manager" of a time allocation. This user can add/remove users from the project, and usually the one that applied for the time allocation. All project related utilities is managed through SUPR.
   CAC
     CAC or Charge Account Category is a deprecated term referring to allocations for a project. It is now replaced by Time Allocation.

   node-hours
     Node hours(n) equals the core hours(c) divided by the number of cores per node(cpn): `n = c/cpn`. 
     PDC allocate time on our systems in node hours. SNAC, allocates time in kilo-core hours. 

   core-hours
     Core hours(c) can be calculated with Node hours (n) you have requested on a particular system, by knowing cores per node(cpn): `c = n*cpn` 

   SNIC
     SNIC or Swedish National Infrastructure for Computing is a national research infrastructure.

   SUPR
     SUPR or SNIC User and Project Repository is the SNIC database used to keep track of persons, projects, project proposals and more. 

   SNAC
     SNAC or Swedish National Allocations Committee handles all the applications and allocations of SNIC.

   SLURM
     SLURM or Simple Linux Utility for Resource Management is an open-source cluster management and job scheduling system extensively used by PDC.

   Beskow
     Beskow is the name of cluster currently deployed in PDC designed for running large parallel jobs.

   Tegner
     Tegner is the name of cluster currently deployed in PDC designed for pre/post processing.

   Kerberos
     Kerberos is a computer network authentication protocol. It works on the basis of creating a *ticket* that is used for secure communication. You need to create a kerberos ticket to login to the clusters, run program and get access to the home directory and transfer files.
   AFS
     Andrew File System (AFS) is a distributed file system. This file system can be accessed without logging in to the clusters, and this is also the system where users home directory reside. To get access to AFS, one needs to use Kerberos.

   CFS/Klemming
     TODO
   
