.. index:: HPC/PDC Preliminaries
.. _preliminaries:

Introduction
============

Here, you will find the basic terminologies needed to get started with PDC.

Clusters, nodes, processors, and cores
--------------------------------------

.. About basic HPC architecture

Like most high-performance computing facilities, PDC mainly features **clusters**. 
A computer cluster is in the broad sense terminology for a supercomputer, 
consisting of a set of connected computers working together so that they can be viewed as a single system.
Currently PDC has two clusters: Tegner and Beskow.

A **node** is the individual computer part of each cluster. Nodes are analogous to the computers we use everyday.

And each node in turn has **processors** made up of computing entities called **cores**.

.. seealso::
   For a more technical overview, please visit the `Resources <https://www.pdc.kth.se/resources>`_ page.

.. Old image: https://drive.google.com/uc?id=0B7GAinAyrwFFR0p5ZU1vREFwWWM

.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFOVFxQ0NCRTl3czg
   :height: 220px
   :width: 800 px
   :scale: 100 %
   :alt: alternate text
   :align: center

.. TODO: Maybe remove the title 'Supercomputer anatomy'.
.. TODO: Picture does not match well with the text. Explain racks, blades, CPU,..

Deciding whether you need PDC for your work
-------------------------------------------
	    
.. https://www.hpc2n.umu.se/documentation/guides/beginner-guide
   
The key feature of PDC systems (or most HPC resources in general) is large-scale parallelization of computations. 
PDC resources are used in a wide-range of scientific disciplines. 
If you want to find out if you work could benefit from PDC resources, check if:

* your application required large computional resources
* your application can be parallelized 
* your application does not require dynamic user interaction

.. anything else?  

If you decide to use PDC resources, welcome on board! PDC provides you with:
   
* supercomputer systems for large simulations and calculations
* systems for processing data before and after simulations or calculations
* software for simulation and modelling
* short term storage for large volumes of data
* assistance with using PDC's computing and storage resources
* experts in different research fields to assist you with using and/or scaling software	    
	    
Account and Time Allocation
---------------------------

.. You need account. And time allocation.
.. Refer to https://www.pdc.kth.se/support/getting-started-at-pdc
.. Refer to https://www.pdc.kth.se/support/time-allocations/
.. USE EITHER time allocation or CAC consistently.

PDC receives national funds and is free for all Swedish academic users and their collaborators.
Before starting using PDC resources, you will need to get an account.
Each user account must belong to one or more **Time Allocations**, since we allocate resources and manage job queueing based on 
the Time Allocation you belong to and not based on your individual user account. Each Time Allocation includes the following information:

#. list of users belonging to that Time Allocation
#. number of corehours allocated per month (for all members of the Time Allocation put together)
#. an expiration date for the Time Allocation
#. list of clusters available for running jobs

When you submit jobs in a cluster, you should belong to at least one Time Allocation, or the submission will fail.
Using Time Allocations allows us to:

#. Prioritize your submitted jobs compared to other user's jobs.
#. Keep track of compute-time used each month by users and projects.

How much resources will be needed: core-hours
---------------------------------------------

At PDC, we allocate compute-time on our systems in corehours and you are granted an
amount of corehours on a particular system.
Corehours equals the number of cores used in how many hours.
A time allocation gives you a certain amount of corehours per month.
