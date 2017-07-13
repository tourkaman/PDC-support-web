.. index:: HPC/PDC Preliminaries
.. _preliminaries:

Introduction
============

Here, you will find the basic terminologies needed to get started with PDC.

.. rubric:: Clusters, nodes, processors, and cores

.. About basic HPC architecture
.. Refer to https://www.pdc.kth.se/support/Presentations-about-using-PDC-resources/introduction-to-pdc-systems-course-material/introduction-to-pdc-systems-course-material-february-2016/introduction-to-the-pdc-environment-february-2016

Like most high-performance computing facilities, PDC mainly features **clusters** (currently, they are Beskow and Tegner). Each cluster has many individual computers called **nodes**, that are analogous to the computers we use everyday. And each node in turn has **processors** made up of actual computing entities called **cores**. To get some perspective, Beskow consists of 1676 nodes with 32 cores per node, and Tegner has 65 nodes with 48/24 cores per node. 

.. seealso::
   For a more technical overview, please visit the `Resources <https://www.pdc.kth.se/resources>`_.

.. Henric's presentation image: https://drive.google.com/uc?id=0B7GAinAyrwFFR0p5ZU1vREFwWWM

.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFOVFxQ0NCRTl3czg
   :height: 250px
   :width: 800 px
   :scale: 100 %
   :alt: alternate text
   :align: center

.. rubric:: Account and Time Allocation

.. You need account. And time allocation.
.. Refer to https://www.pdc.kth.se/support/getting-started-at-pdc
.. Refer to https://www.pdc.kth.se/support/time-allocations/
.. USE EITHER time allocation or CAC consistently.

PDC is funded centrally and is free for all Swedish academic users and their collaborators. Before you starting using PDC systems, you will need to get an account. Each user account must belong to one or more **Time Allocation**, since we allocate resources and manage job queueing based on the Time Allocation you belong (and not based on indivudal user account). Each Time Allocation includes the following information:

1. list of users belonging to that Time Allocation
2. number of node hours allocated per month (for all members of the Time Allocation put together)
3. an expiration date for the Time Allocation
4. list of clusters available for running jobs

When you submit jobs in a cluster, you should belong to at least one Time Allocation, or the submission will fail. Using Time Allocations allows us to:

1. Prioritize your submitted jobs compared to other user's jobs.
2. Keep track of compute-time used each month by users and user groups.

.. rubric:: Node-hours and core-hours

At PDC, we allocate compute-time on our systems in node-hours. Node hours (n) equal core-hours (c) divided by the number of cores per node (cpn), i.e., n = c/cpn. Conversely, core hours equal the number of cores per node times node hours: c = cpn*n. The queuing systems at PDC uses node hours, and you are charged according to the number of node hours you have requested on a particular system.

.. Course and SUPR accounts

.. Now that we know you need a Time Allocation to run on PDC, how can your account belong to a Time Allocation? You can either join an existing Time Allocation or apply for a new Time Allocation.

.. About methods for applying to an account. What is SUPR?

.. About software, only intro, no links

.. Apart for the hardware resources, PDC also offers software.
