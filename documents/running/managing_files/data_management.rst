.. index:: Data Management
.. _data_management:

Data management
===============

Working with PDC would involves transferring data back and forth between your local machine and PDC, or between different systems at PDC. PDC offers two storage systems AFS and CFS(Klemming), and an efficient usage of PDC would involve knowing when to use what.

File transfer
#############

We recommend two methods for this:

1. **scp/rsync**: Secure Copy (SCP) and RSYNC copies files between hosts on a network. It uses SSH for data transfer, and uses the same authentication and provides the same security as SSH.
   
   * :ref:`with Ubuntu (Linux) <scp_ubuntu>`
   * :ref:`with Windows <scp_windows>`
  
2. **AFS client**: With an AFS client on your local machine transferring files between PDC and your local computer is as is as drag-and-drop, or, using a cp command. 
	
   * :ref:`Using AFS client from Ubuntu (Linux) <afs_client_ubuntu>`
   * :ref:`Using AFS client from Windows <afs_client_windows>`
   * :ref:`Using AFS client from Mac <afs_client_mac>`
   * :ref:`Using AFS client from FreeBSD <afs_client_freebsd>`

Storing data
############

Computations on PDC resources usually demands storage of files relating to computations, such as data files or program files. PDC has two file systems available: AFS and Klemming. To know more:
	    
* :ref:`Where to store my data (begineer) <storing_begineer>`	   
* :ref:`Where to store my data (advanced) <storing_advanced>`	   

Guide: File Systems at PDC
##########################

For storing files, PDC has two file systems available. They are known as AFS (which is based on Andrew File System) and Klemming (which is a Lustre-based system). For first-time users, it might be confusing knowing there are different file systems, and more so, when having to choose between them. We give a tutorial-style indtroduction to AFS and Klemming systems, that will hopefully help getting started.

* :ref:`Guide: 1. File Systems at PDC <afs_and_cfs>`
* :ref:`Guide: 2. AFS <afs>`
* :ref:`Guide: 3. Klemming <klemming>`

