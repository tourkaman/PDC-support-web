.. index:: AFS and Klemming File Systems
.. _afs_and_cfs:

Guide: AFS and Klemming File Systems
====================================

.. centered::   
   *Survival guide when using AFS and Klemming at PDC!*

   
.. rubric:: Introduction

Researchers using PDC's facilities need different types of storage:

* massive storage for archiving large volumes of research data
* somewhere to store files relating to calculation being performed on PDC's systems (such as data files or program files)

For storing the latter type of files, PDC has two file systems available. They are known as AFS (which is based on Andrew File System) and Klemming (which is a Lustre-based system). Which system you should use to store your files depends on:

* the amount of data you need to store, and
* how you will be using or accessing the data  

  
.. rubric:: What is AFS and Klemming?:

* The **Andrew File System (AFS)** is a distributed file system which uses a set of trusted servers to present a homogeneous, location-transparent file name space to all the client workstations.	   
* **Klemming** is based on Lustre - a parallel file system optimized for handling data from many clients at the same time

   
.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFSnNJYVZmUWE1bHM
   :height: 200px
   :width: 300 px
   :scale: 100 %
   :alt: alternate text
   :align: center

	   
.. rubric:: AFS ``/afs/pdc.kth.se``

* **Storage size**:small volume of storage (around 50 TB total)
* **File access speed**: relatively slow access to files (not good for files being accessed by parallel computation)
* **Backup**: all files on AFS are backed up
* **Access**: files stored on AFS can be directly accessed from any computer connected to the internet - it is not neccessary to log in to a PDC computer over the internet first
* **Access from Beskow**: files on AFS are not accessible from Beskow's compute nodes (so any data or program files that you need for running pograms ob Beskow must be stored Klemming)
* **Access from Tegner**: files on AFS can be accessed from Tegner's compute nodes - so small amounts of data for Tegner computations can be stored on AFS (any large amount of data should be stored on Klemming for reasons of speed of access)
* good for storing small files that need to be backed up
* home directories are on AFS (so you will be in AFS when you first log in to PDC's systems)
* **File access**: AFS has its own implementation of Access Control Lists (ACLs), where users can define new groups (Note: In AFS access is set per directory and not on individual files)
* **Secure access**: uses Kerberos for authentication and is designed for security and robustness. We assume that you have forwarded a valid ticket from your workstation when you logged in, see Kerberos for details.
* mainly used for:
  * users' home directory (with backup) - initially 500 MB (can be raised to 5 GB)
  * project volumes (backup optional) - typically 10-50 GB (time limited)
  * installation and configuration of the PDC environment, and
  * source code packages
   
.. rubric:: Klemming ``/cfs/klemming``

* **Storage size**: large volume of storage (total over 5 PB - so 100 times more than AFS)
* **File access speed**: fast access (good for files accessed for computation)
* **Backup**: files are not backed up
* **Accessibility**: not possible to access files stored on Klemming directly via the internet - need to login to a PDC computer to get acces to Klemming
* **Access from Tegner**: files on Klemming can be accessed from Beskow's compute nodes (any data or program files that you need for running programs on Beskow must be stored on Klemming)
* **Access from Beskow**: files on Klemming can be accessed from Tegner's compute nodes - so large amounts of data for egner computationa should be stored on Klemming (small amounts of data are also okay on Klemming)
* good for storing any large files and program code
* **File access**: Lustre supports standard (POSIX) Access Control Lists
* mainly used for:
  * cluster scratch - shard ara for temporary files - no  backup - old files will be deleted periofically by the system, and
  * nobackup area - shared area to be used for input/output for running jobs - no backup - users should move files elsewhere as soon as possible when they are not needed for jobs

  
.. table:: Comparison summary of AFS and Klemming
   :widths: auto
   :align: center

   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |        Description          |                            AFS                     |                    Klemming                      |
   |                             |                                                    |                                                  |
   +=============================+====================================================+==================================================+
   |                             |                                                    |                                                  |
   | Location                    |  ``/afs/pdc.kth.se``                               |       ``/cfs/klemming``                          |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Total storage size          |   Small (around 50 TB)                             |   Large (5 PB)                                   |
   |                             |   unsuited for files accessed by computation       |   suitable for files accessed for computation    |   
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | File access speed           |   Slow                                             |   Fast access                                    |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Accessibility               |   accessible by any computer with internet         |   need to log in to PDC to access                |
   |                             |   (not neccessary to log in to PDC)                |                                                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Access from Beskow          |   No                                               |   Yes                                            |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Access from Tegner          |   Yes                                              |   Yes                                            |   
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+   
   |                             |                                                    |                                                  |
   | File access                 |   1. own implementation of Access Control List     |   1. supports standard POSIC ACLs                |
   |                             |   2. user can define own group                     |                                                  |
   |                             |   3. access permissions per directory (not file)   |                                                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+   
   |                             |                                                    |                                                  |
   | Secure access               |   uses Kerberos for authentication                 |   ...                                            |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+   
   |                             |                                                    |                                                  |
   | Backup                      |   all files are backed up                          |   files are not backed up                        |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Contents                    |   1. user home directory (with backup)             |   1. cluster scratch (no backup)                 |
   |                             |   2. project volumes (backup optional)             |   2. program code                                |
   |                             |   3. installation/configuration of PDC environment |   3. nobackup area (input/output) of running jobs|
   |                             |   4. source code packages                          |                                                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Suggested usage             |   1. small files that needs backup                 |   1. large files                                 |
   |                             |                                                    |   2. program code                                |   
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+

   
.. topic:: **Things to remember when using all types of files**

   *  Larger input/output (I/O) operations are more efficient than small ones – if possible aggregate reads/writes into larger blocks.
   * Avoid creating too many files – post-processing a large number of files can be very hard on the file system.
   * Avoid creating directories with very large numbers of files – instead create directory hierarchies, which also improves interactiveness.

.. topic:: **Things to remember when using Klemming**

   * Avoid all unnecessary metadata operations - once a file is opened, do as much as possible before closing it again. Do not check the existence of files or stat() files too often.
   * Open files as read-only if possible – read-only files require less locking and therefore put less load on the file system.
   * TIP: Avoid flags such as ``-l`` , ``-F`` or ``--color`` with ``ls`` by default as this requires ``ls`` to ``stat()`` every file to determine its type, which puts an unnecessary load on the file system. Use such flags only when the extra information is really needed.
