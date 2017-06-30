.. index:: AFS and Klemming File Systems
.. _afs_and_cfs:

AFS and Klemming File Systems
=============================

.. centered::   
   *Survival tricks when using AFS and Klemming at PDC!*
   
[**TODO**: attach funnel picture from poster]

Researchers using PDC's facilities need different types of storage:

* massive storage for archiving large volumes of research data
* somewhere to store files relating to calculation being performed on PDC's systems (such as data files or program files)

For storing the latter type of files, PDC has two file systems available. They are known as AFS (which is based on Andrew File System) and Klemming (which is a Lustre-based system). Which system you should use to store your files depends on:

* the amount of data you need to store, and
* how you will be using or accessing the data  


.. topic:: **What is AFS and Klemming?**:

   The Andrew File System (AFS) is a distributed file system which uses a set of trusted servers to present a homogeneous, location-transparent file name space to all the client workstations. Klemming is based on Lustre - a parallel file system optimized for handling data from many clients at the same time

The following describes the main differences between AFS and CFS.

* **AFS file access differs from CFS**
    The access right to a file is controlled by so called Access Control Lists (ACL) describing what you (or anyone else) can do in that directory. Subdirectories inherit the ACL of the parent directory when created. More about this in "Access Control List".

     
* **The command ls does not show AFS file permissions**
    Only the three first of the nine file protection codes you see when you type ls -al are used by AFS. These would normally describe the owners rights to these files, but shows in AFS if the file is read- write- or executable for all those who have access to the file.

     
* **Problems with your home directory**
    Since the the access to a file is based on directories rather than files, you might have problems with directories that should contain both public and private files. This is typical for your home directory, certain init files must be public readable, but you do not want all your files in your home directory to be public readable. A solution to this is presented in Protecting your init files.

     
* **You need Kerberos tickets**
    To access your AFS-files you need a valid ticket in the authentication system Kerberos. We assume here that you have forwarded a valid ticket from your workstation when you logged in, see Kerberos for details.

     
* **Quota for your disk space**
    Each AFS-directory has a limit for the space it may use on disks. The command fs listquota or fs lq for short will show the disk quota in the current directory. The default quota at PDC is 500 MB. Contact PDC if you need more disk space.

     
* **AFS is global**
    Anybody anywhere in the world using AFS can access your files if your files are not protected by ACL. This has some advantages: you can access your files without logging in to a PDC computer, but has also some risks: if you are not aware of this you might make your files readable for anyone. You should read the section on Access Control list below thoroughly.

  
.. rubric:: AFS ``/afs/pdc.kth.se``

* **Storage size**:small volume of storage (around 50 TB total)
* **File access speed**: relatively slow access to files (not good for files being accessed by parallel computation)
* **Backup**: all files on AFS are backed up
* **Access**: files stored on AFS can be directly accessed from any computer connected to the internet - it is not neccessary to log in to a PDC computer over the internet first
* **Access from Beskow**: files on AFS are not accessible from Beskow's compute nodes (so any data or program files that you need for running pograms ob Beskow must be stored Klemming)
* **Access from Tegner**: files on AFS can be accessed from Tegner's compute nodes - so small amounts of data for Tegner computations can be stored on AFS (any large amount of data should be stored on Klemming for reasons of speed of access)
* good for storing small files that need to be backed up
* home directories are on AFS (so you will be in AFS when you first log in to PDC's systems)
* **Access Control List**: AFS has its own implementation of Access Control Lists (ACLs), where users can define new groups (Note: In AFS access is set per directory and not on individual files)
* secure access - uses Kerberos for authentication and is designed for security and robustness
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
* Lustre supports standard (POSIX) Access Control Lists
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
