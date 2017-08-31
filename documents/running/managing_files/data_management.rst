.. index:: Data Management
.. _data_management:

Data management
===============

This section gives you information about PDC's storage solutions. Before following this section, make sure you can login to a PDC system.

Working with PDC would involves transferring data back and forth between your local machine and PDC, or between different systems at PDC. PDC offers two storage systems AFS and CFS(Klemming), and an efficient usage of PDC would involve knowing when to use what.

File transfer
-------------

We recommend two methods for this:

#. **SCP/rsync**: Secure Copy (SCP) and RSYNC copies files between hosts on a network. It uses SSH for data transfer, and uses the same authentication and provides the same security as SSH.
   
   .. toctree::
      :glob:
      :maxdepth: 2
      
      file_transfer_scp
     
#. **AFS client**: With an AFS client on your local machine transferring files between PDC and your local computer is as is as drag-and-drop, or, using a cp command. 

   .. toctree::
      :glob:
      :maxdepth: 2
      
      file_transfer_afs

Storing data
------------

Computations on PDC resources usually demands storage of files relating to computations, such as data files or program files. PDC has two file systems available: AFS and Klemming. To know more:
	    
.. toctree::
   :glob:
   :maxdepth: 2
  
   storing_data
    
Guide: File Systems at PDC
--------------------------

For storing files, PDC has two file systems available. They are known as AFS (which is based on Andrew File System) and Klemming (which is a Lustre-based system). For first-time users, it might be confusing knowing there are different file systems, and more so, when having to choose between them. We give a tutorial-style indtroduction to AFS and Klemming systems, that will hopefully help getting started.

.. toctree::
   :glob:
   :maxdepth: 2
      
   afs_and_cfs
   afs
   klemming
     
     
