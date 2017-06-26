.. index:: Getting research time at PDC
.. _get_time:

Step 1: Getting research time
=============================

.. rubric:: Are you applying for a new Time Allocation or joining an exisiting one?

Before running on PDC, users must belong to at least one Time Allocation. If you are joining a project in a research group that already has a Time Allocation, then jump to [joining an existing time allocation].


.. rubric:: Are you applying for PDC resources for a course?

If you're a participant of a course at KTH that uses the super computers, you can jump to the step [STEP 2: account creation for course account]. Do not forget to specify the course ID, and the name of the course administrator for the course. You also need to be a part of a participant list managed by the course administrator.


Applying for a New Time Allocation
############################

If you are applying for a new Time Allocation, you are the Principal Investigator (PI). Since the Time Allocation is so limited, both in time per month for running jobs, and in duration, many projects have applied for more time on a certain computer/cluster. For instance, a PI apply for a time allocation that will cover the needs for all people in a certain research project. You would have to find what allocation would suit the best for your project with the help of the table below:

.. table::
   :widths: auto
   :align: center

   ========================= ==================================== ==================================== ====================================
   Description                          Small allocation                     Medium allocation                    Large allocation
   ========================= ==================================== ==================================== ====================================
   Limit                     5000 corehours/month                 200 kcorehours/month                 None
   Applicant requirement     PhD student or higher                Senior scientist in Swedish academia Senior scientist in Swedish academia
   Application evaluation    Only technical evaluation            Only technical evaluation            Scientific and technical evaluation
   ========================= ==================================== ==================================== ====================================

.. Add to large allocation, application evaluation: Evidence of successful work at a medium level needed. Performed by SNAC twice a year   

All time allocations are now managed through SUPR, so users can be added or removed from the allocation directly using the SUPR web interface. The changes are then automatically applied overnight by various scripts. All allocations are handled on a national level through SNAC (Swedish National Allocations Committee), and the SUPR system. regardless of the size of the requested allocation.

To know more on what cores or core-hours mean, please visit the Preliminaries page.

Joining a existing Time Allocation
##################################

Check your existing Time Allocation
###################################

You can see what time allocations you belong to via the SUPR web page. Note that medium allocations normally have an extra m, at the start, e.g. SNIC 2015/1-1 is m.2015-1-1 on our system. You can see which time allocation you are a member of using the ``projinfo`` command. It will print the information of all the allocations you belong to and information on the recent usage of the allocation.

.. Shouldn't be here. Maybe in running research section. Acknowledge your SNAC/PDC time allocation
