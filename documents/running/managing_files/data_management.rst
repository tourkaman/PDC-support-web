.. index:: Data Management
.. _data_management:

Data management
===============

This section gives you information about PDC's storage solutions. Before following this section, make sure you can login to a PDC system.

Working with PDC would involves transferring data back and forth between your local machine and PDC, or between different systems at PDC. 
PDC offers two storage systems AFS and CFS(Lustre), and an efficient usage of PDC would involve knowing when to use what.

File transfer
-------------

We recommend two methods for this:

#. **SCP/rsync**: Secure Copy (SCP) and RSYNC copies files between hosts on a network.
   It uses SSH for data transfer, and uses the same authentication and provides the same security as SSH.
   
   .. toctree::
      :glob:
      :maxdepth: 2
      
      file_transfer_scp
     
#. **AFS client**: With an AFS client on your local machine transferring
   files between PDC and your local computer is as is as drag-and-drop, or, using a cp command. 

   .. toctree::
      :glob:
      :maxdepth: 2
      
      file_transfer_afs

Storing data
------------

Computations on PDC resources usually demands storage of files relating to computations, such as data files or program files.
PDC has two file systems available: AFS and Lustre. To know more:
	    
.. toctree::
   :glob:
   :maxdepth: 2
  
   storing_data
    
Guide: File Systems at PDC
--------------------------

For storing files, PDC has two file systems available. They are known as AFS (which is based on Andrew File System) and 
Lustre ( for normal users this correspond to `cfs/klemming` directories). 
For first-time users, it might be confusing knowing there are different file systems, and more so, 
when having to choose between them. We give a tutorial-style indtroduction to AFS and Lustre systems, 
that will hopefully help getting started.

.. centered::   
   *Survival guide when using AFS and Lustre at PDC!*

Researchers using PDC's facilities need different types of storage:

* massive storage for archiving large volumes of research data
* somewhere to store files relating to calculation being performed on PDC's systems (such as data files or program files)

For storing the latter type of files, PDC has two file systems available. They are known as AFS (which is based on Andrew File System) and
Lustre (with subfolders at `cfs/klemming` ). Which system you should use to store your files depends on:

* the amount of data you need to store, and
* how you will be using or accessing the data  
  
.. rubric:: What is AFS and Lustre?:

* The **Andrew File System (AFS)** is a distributed file system which uses a set of trusted servers to present a homogeneous,
location-transparent file name space to all the client workstations. Proceed to Guide 2. AFS	   
* The **Lustre** system is a parallel file system optimized for handling data from many clients at the same time. Proceed to Guide 3. Lustre

   
.. table:: Comparison summary of AFS and Lustre
   :widths: auto
   :align: center

   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |        Description          |                            AFS                     |                    Lustre                        |
   |                             |                                                    |                                                  |
   +=============================+====================================================+==================================================+
   |                             |                                                    |                                                  |
   | Location                    | ``/afs/pdc.kth.se``                                | ``/cfs/klemming``                                |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Storage size                | default 5GB in home directory                      | total 5 PB shared with all user                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | File access speed           | Slow                                               | Fast                                             |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Access from Beskow          | No (accessed only from the login node)             | Yes                                              |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Access from Tegner          | Yes                                                | Yes                                              |   
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+   
   |                             |                                                    |                                                  |
   | File access                 | #. own implementation of Access Control List       | #. supports standard POSIC ACLs                  |
   |                             | #. user can define own group                       |                                                  |
   |                             | #. access permissions per directory (not file)     |                                                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+   
   |                             |                                                    |                                                  |
   | Secure access               | uses Kerberos for authentication                   | ...                                              |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+   
   |                             |                                                    |                                                  |
   | Backup                      | files in home directory are backed up              | files are not backed up                          |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   | Contents                    | #. user home directory (with backup)               | #. cluster scratch (no backup)                   |
   |                             | #. project volumes (backup optional)               | #. program code                                  |
   |                             | #. installation/configuration of PDC environment   | #. nobackup area (input/output) of running jobs  |
   |                             | #. source code packages                            |                                                  |
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
 

.. toctree::
   :glob:
   :maxdepth: 2
      
   afs
   lustre
