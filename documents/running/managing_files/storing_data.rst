.. index:: Storing data
.. _storing_data:

.. _storing_begineer:

Where to store my data (begineer)
=================================

As the speed of CPU computations keep increasing, the relatively slow rate of input/output (I/O) or
data accessing operations can create bottlenecks and cause programs to slow down significantly.
Therefore it is very important to pay attention to how your programs are doing I/O and accessing data
as that can have a huge impact on the run time of your jobs. Here, you will find a quick guide to storing data,
ideal if you have just started to use PDC resources. 

.. rubric:: What are AFS and Klemming?

The **Andrew File System (AFS)** is a *distributed* file system which uses a set of trusted servers to present a homogeneous,
location-transparent file name space to all the client workstations.
The **Klemming** system is based on Lustre - a *parallel* file system optimized for handling data from many clients at the same time.

.. rubric:: Why is there more than one file system?

The AFS and Klemming file systems offer different and often complementary functionality.
AFS allows a huge number of computers all over the world to share files between each other.
Users can define custom groups and control access-rights effortlessly, suitable for project groups.
But, AFS has a small storage volume and slow access speed, making it unsuitable for directly access with computational processes.
On the contrary, Klemming is accessible only to PDC systems, but provides large storage and,
is highly optimized for fast access with computational processes. 

.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFSnNJYVZmUWE1bHM
   :height: 200px
   :width: 300 px
   :scale: 100 %
   :alt: alternate text
   :align: center
	
.. topic:: Where do I find it?
  
   | You can find AFS at ``/afs/pdc.kth.se``
   | You can find Klemming at ``/cfs/klemming``

   
.. rubric:: Before running your processes
   
* All files for Beskow computations must go on **Klemming**
* Big data files for Tegner computations should be put on **Klemming**
* Small data files for Tegner computations can be put on **AFS**

.. rubric:: Things to remember when using all types of files

*  Minimize I/O operations: larger input/output (I/O) operations are more efficient than small ones
   – if possible aggregate reads/writes into larger blocks.
*  Avoid creating too many files – post-processing a large number of files can be very hard on the file system.
*  Avoid creating directories with very large numbers of files – instead create directory hierarchies, which also improves interactiveness.

.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFN1lySG1zUFRBSTg
   :height: 400px
   :width: 600 px
   :scale: 100 %
   :alt: alternate text
   :align: center

.. rubric:: Things to remember when using Klemming

* Avoid all unnecessary metadata operations - once a file is opened, do as much as possible before closing it again.
  Do not check the existence of files or ``stat()`` files too often.
* Open files as read-only if possible – read-only files require less locking and therefore put less load on the file system.
* Avoid using ``ls`` with flags like ``-l`` , ``-F``, or ``--color``  as this requires ``ls`` to ``stat()``
  every file to determine its type, which puts an unnecessary load on the file system. Use such flags only
  when the extra information is really needed and do not have them as default.

  .. table:: Comparison summary of AFS and Klemming
   :widths: auto
   :align: center
	
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+
   |                             |                                                    |                                                  |
   |  File system                |  AFS                                               |   Klemming                                       |
   |                             |                                                    |                                                  |
   +=============================+====================================================+==================================================+
   |                             |                                                    |                                                  |
   | Suggested usage             |   1. small files that needs backup                 |   1. large files                                 |
   |                             |   2. unsuited for files accessed by computation    |   2. program code                                |   
   |                             |                                                    |   3. files accessed for computation              |   
   |                             |                                                    |                                                  |
   +-----------------------------+----------------------------------------------------+--------------------------------------------------+     

.. rubric:: After running your processes

* Move important data files to your own departmental storage systems after performing computations at PDC.
  Remember, space on Klemming is currently limited, and are not backed up
* Smaller data files can be moved to AFS 

.. _storing_advanced:

Where to store my data (advanced)
=================================  

Finding a good storage solution may be essential for the success of your application.
This guide will help you to choose a storage option that suits your problem. To find the most suitable storage option for your data set,
please consider the following aspects of your data.

* the amount of data you need to store, and
* how you will be using or accessing the data.
* Life time - Is your data temporary, i.e. can it be deleted after your job finishes?
* Back up - Can your data be regenerated if lost, or do you require safety mechanisms to keep it safe?
* Locality - Does your data need to be accessed only by a single node (locally) or by more processes?
* Input size - What size is the input data you need?
* Output size - What amount of data do you generate? How often do you generate this data (number of consequetive or simultaneous jobs)?
* Data structure - What organization does your data have? How many files/folders? How are these organized?
* I/O pattern - How does your program access disk during its runs?
		
