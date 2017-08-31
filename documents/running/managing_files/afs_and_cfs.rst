.. index:: AFS and Klemming File Systems
.. _afs_and_cfs:

Guide: 1. File Systems at PDC
=============================

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

* The **Andrew File System (AFS)** is a distributed file system which uses a set of trusted servers to present a homogeneous, location-transparent file name space to all the client workstations. Proceed to Guide 2. AFS	   
* The **Klemming** system is based on Lustre - a parallel file system optimized for handling data from many clients at the same time. Proceed to Guide 3. Klemming

   
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
   | Storage size                |   default 5GB in home directory                    |   total 5 PB shared with all user                |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | File access speed           |   Slow                                             |   Fast                                           |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Access from Beskow          |   No (accessed only from the login node)           |   Yes                                            |
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
   | Backup                      |   files in home directory are backed up            |   files are not backed up                        |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Contents                    |   1. user home directory (with backup)             |   1. cluster scratch (no backup)                 |
   |                             |   2. project volumes (backup optional)             |   2. program code                                |
   |                             |   3. installation/configuration of PDC environment |   3. nobackup area (input/output) of running jobs|
   |                             |   4. source code packages                          |                                                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
 
