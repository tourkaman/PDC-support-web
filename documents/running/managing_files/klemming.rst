.. index:: Klemming File System
.. _klemming:

Guide: Klemming
===============

Guidelines on the usage of Klemming - PDCs high-performance file system.

.. topic:: What is Klemming?:

   Klemming is a parallel file system based on Lustre optimized for handling data from many clients at the same time.

Klemming is divided into two parts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^	     

Note that the two parts currently reside in the same file system and therefore share resources. This means that if one part gets overloaded or fills up, so does that other part too. This also means that you can move files between the two parts, with e.g. 'mv', rather than having to copy the data over.

.. rubric:: Scratch

Use for most files that are used by jobs running at PDC (but does not fall into the nobackup-category). This branch will be automatically cleaned by removing files that has not been changed within a certain time. This time will be adjusted when needed so that:

* The files are available while a job is running on the cluster
* After the job has run there is a reasonable chance to move the files to some other storage.
* There is a low likelihood of jobs failing due to a full file system

Currently all files older than 30 days are eligible for being deleted during cleaning. The cleaning is usually done at least once a week, but will be done as frequently as deemed necessary to fulfill the above goals.

If your username is "user" is located under /cfs/klemming/scratch/[first letter of username]/username or::

/cfs/klemming/scratch/u/user

.. rubric:: Nobackup

Use for files that - while needed as input by jobs frequently running on PDC - is not of a transient nature. Examples of this could be large in-data sets that are used by several jobs running over several months. In other words nobackup is a cache for frequently used data and exists to alleviate staging problems. PDC will manually monitor the usage of this branch and it will be cleaned if need arises. If frequent misuse proves it necessary, PDC can and will monitor this branch for files that more properly belongs in scratch.

Similar to scratch, your nobackup directory is under::

/cfs/klemming/nobackup/u/user

.. warning:: All files on Klemming are **NOT** backed up!	     

Disk usage and quota
^^^^^^^^^^^^^^^^^^^^

You can see how much data and how many files you currently have stored in Klemming using the command:

.. code-block:: bash

   lfs quota -u $USER /cfs/klemming

There are currently no disk quotas enforced on Klemming, but remember that Klemming is only intended for **temporary storage**, and should not be used for long term storage. And while it can handle large amounts of data well, it can not handle too many files, so please keep the number of files down. Only files needed by, or were recently produced by, jobs running on PDC compute resources should be on Klemming.

Tranfer nodes
^^^^^^^^^^^^^

For more information on how to transfer files to, from and between PDC's resources please check here. There are dedicated machines for moving data in and out of Klemming. The recommended way is to use Tegner for this to not overload other resources, e.g. the login node of Beskow.

Characteristics of a Lustre file system
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Lustre file systems such as Klemming perform quite differently to local disks that are common on other machines. Lustre was developed for providing fast access to the large data files needed for large parallel applications. They are particularly bad at dealing with small files and with doing many small operations on these files and those cases should be avoided as much as possible.

.. rubric:: Good practice on a Lustre system

To get the best performance out of a Lustre system you should use as small a number of files as possible and each time you access a file you should read/write as much data at a time as you can. An ideal program using Lustre would read in a single data file using parallel IO (e.g. MPI IO), process the data and then at the end write out a single file again using parallel IO, with no intermediate use of the disk.

.. rubric:: Bad practice on a Lustre system

As Lustre is designed for reading a small number of large files quickly, certain IO patterns that are perfectly fine on other systems cause very high load on a Lustre system e.g.

* Small reads
* Opening many files
* Seeking within a file to read a small piece of data

These practices are very common in applications that were designed to run on systems where each node has its own local scratch disk.

Many software packages (e.g. Quantum Espresso) have input options that reduce the disk IO

File locking
^^^^^^^^^^^^

We recommend not using file locking since it can have negative impacts on performance.

If you need help in converting your code to better use the Lustre file system contact support.
