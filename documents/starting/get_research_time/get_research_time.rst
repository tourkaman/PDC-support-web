.. index:: get_research_time
.. _get_research_time:

Step 1: Getting research time
=============================

.. centered::
   *It is easy to become a user at PDC, just follow these instructions.*

Before running on PDC, users must belong to at least one Time Allocation. 


.. rubric:: Are you a student taking a course requiring PDC resource?

If you're a participant of a course at KTH that requires using PDC resources, you don't have to bother with Time Allocation.

* If you already have a PDC account (maybe you used PDC for other courses), 
  all you have to do is send us a mail at ``support@pdc.kth.se``. 
  Include your...
  
  #. Username at PDC
  #. The course code that requires PDC. 
     You also need to make sure you are included in the participant list managed by your course responsible.

* If you don't have a PDC account, go directly to :ref:`Step 2: Account Creation -> Course account <course_account>` 
  and fill in the form. Do not forget to specify the course code and the name of the course responsible. 
  You also need to make sure you are included in the participant list managed by your course responsible.

.. rubric:: Are you a student (Bachelor or Master level) requiring PDC resources for your thesis?

In general, we do not accept applications directly from students below PhD level. However, your supervisor can apply on your behalf.

#. Request your supervisor to :ref:`apply for a new Time Allocation <Apply_for_a_new_time_allocation>`. 
#. You can :ref:`join that Time allocation <joining_a_existing_time_allocation>` as a project member. 

We recommend applying for *small allocation* (see more info in the link) for thesis work.

.. rubric:: Are you a researcher (PhD or higher) requiring PDC resources?

All research projects are handled through the SUPR portal,
so applying/joining Time Allocation and applying for PDC account must be done on SUPR (https://supr.snic.se)
	    
* If you want to start a new Time Allocation, then :ref:`apply for a new Time Allocation <Apply_for_a_new_time_allocation>`
* If you are joining a research project that already has a Time Allocation at PDC, then :ref:`join the Time Allocation <joining_a_existing_time_allocation>`.


|
|

.. TODO: Make red arrows as hyperlinks to pages.
.. Shouldn't be here. Maybe in running research section. Acknowledge your SNAC/PDC time allocation https://drive.google.com/uc?id=0BxYU3X5kGVqrYW1xTkRnQXRqRU0

.. graphviz::

   digraph structs {
   
     subgraph cluster1 {
     style=invis; 
     color=white;
     edge [color=white];
    
     user_phd [shape=box,color=white,fixedsize=true,height=2,width=2,label=
     <
       <table border="0">
         <tr>
           <td fixedsize="true" width="100" height="100" border="0"><img src="documents/starting/get_research_time/icons/researcher.png"/></td>
         </tr>
         <tr>
           <td>Researcher <br /> (PhD)</td>
         </tr>
       </table>
     >];

     user_student [shape=record,color=white,fixedsize=true,height=2,width=2,label=
     <
       <table border="0">
         <tr>
           <td fixedsize="true" width="100" height="100" border="0"><img src="documents/starting/get_research_time/icons/student.png"/></td>
         </tr>
         <tr>
           <td>Student <br /> (MSc/Course)</td>
         </tr>
       </table>
     >];

     user_industry [shape=record,href="www.google.com",color=white,fixedsize=true,height=2,width=2,label=
     <
       <table border="0">
         <tr>
           <td fixedsize="true" width="100" height="100" border="0"><img src="documents/starting/get_research_time/icons/industry.png"/></td>
         </tr>
         <tr>
           <td>Special account <br /> (PRACE, Scania, ..)</td>
         </tr>
       </table>
     >];  
     
     user_phd -> user_student;
     user_student -> user_industry;
     }


     subgraph cluster0 {
     rank=same;
     style=invis; 
     node [shape=record];

     struct1 [border=0,shape=box,fixedsize=true,height=0.7,width=2.2,label=
     <
       <table border="0">
         <tr>
           <td fixedsize="true" width="150" height="30" border="0"><img src="documents/starting/get_research_time/icons/snic.png"/></td>
         </tr>
       </table>
     >];
     
     struct3 [shape=box,fontsize=20,fontsize=20,fixedsize=true,height=4,width=2.5,label=
     <
       <table border="0">
         <tr>
           <td> PDC Centre <br/><br/></td>
         </tr>
         <tr>
           <td fixedsize="true" width="75" height="75" border="0"><img src="documents/starting/get_research_time/icons/pdc.png"/></td>
         </tr>
         <tr>
           <td fixedsize="true" width="120" height="75" border="0"><img src="documents/starting/get_research_time/icons/pdc_cluster.png"/></td>
         </tr>
       </table>
     >, href="www.google.com"];

     struct2 [shape=box,fontsize=20,fixedsize=true,height=4,width=2.5,label=
     <
       <table border="0">
         <tr>
           <td> Other HPC Centres <br/><br/> </td>
         </tr>
         <tr>
           <td fixedsize="true" width="70" height="30" border="0"><img src="documents/starting/get_research_time/icons/nsc.png"/></td>
         </tr>
         <tr>
           <td fixedsize="true" width="100" height="30" border="0"><img src="documents/starting/get_research_time/icons/hpc2n.png"/></td>
         </tr>
         <tr>
           <td fixedsize="true" width="70" height="50" border="0"><img src="documents/starting/get_research_time/icons/lunarc.png"/></td>
         </tr>
         <tr>
           <td fixedsize="true" width="120" height="30" border="0"><img src="documents/starting/get_research_time/icons/UPPMAX.png"/></td>
         </tr>
         <tr>
           <td fixedsize="true" width="120" height="30" border="0"><img src="documents/starting/get_research_time/icons/C3SE.png"/></td>
         </tr>
       </table>
     >];

     }

     { rank=same; struct1; user_phd; }
     { rank=same; struct2; user_industry; }
     { rank=same; struct3; user_industry; }

     struct1 -> struct2 [penwidth=2];
     struct1 -> struct3 [penwidth=2];    

     edge[constraint=false];
     user_phd -> struct1 [penwidth=3, fontcolor=red, color=red, label="Apply via SUPR account"];
     user_student -> struct3 [penwidth=3, fontcolor=red, color=red, label="Apply for PDC account"];
     user_industry -> struct3 [penwidth=3, fontcolor=red, color=red, label="Contact PDC directly"];   
     
     }

.. _Apply_for_a_new_time_allocation:
     
Apply for a new Time Allocation
-------------------------------

All research projects are now handled at the national level in SNIC through the `SUPR <https://supr.snic.se/>`_ portal, 
so applying/joining Time Allocation, adding/removing users from Time Allocation,
and applying for PDC account must be done from your SUPR page.

If you are applying for a new Time Allocation, you will be the Principal Investigator (PI). As a PI,
you would have to decide on the...

#. Compute-time per month for running jobs
#. Clusters intended for usage
#. Duration of the project.

Please keep in mind that the PI will apply for a Time Allocation to cover the needs of all the members in the research project. 
You can decide what allocation would suit the best for your project with the help of the table below:

========================= ==================================== ==================================== ====================================
Description                          Small allocation                     Medium allocation                    Large allocation
========================= ==================================== ==================================== ====================================
Limit                     5000 corehours/month                 200 kcorehours/month                 Above 200 kcorehours/month
Applicant requirement     PhD student or higher                Senior scientist in Swedish academia Senior scientist in Swedish academia
Application evaluation    Only technical evaluation            Only technical evaluation            Scientific and technical evaluation
========================= ==================================== ==================================== ====================================

.. Add to large allocation, application evaluation: Evidence of successful work at a medium level needed. Performed by SNAC twice a year   


To know more on what cores or core-hours mean, please visit the Introduction page.


Once you decide on the details of your Time Allocation, you can go to :ref:`Step 2: Account Creation -> SUPR account <supr_account>`. 
You can then login/signup on SUPR and submit a proposal. You may then apply for a PDC account (if you do not have a PDC account)
directly from SUPR.

.. _joining_a_existing_time_allocation:

Joining an existing Time Allocation
-----------------------------------

Applying/joining Time Allocation, adding/removing users from Time Allocation, and applying for PDC account must be done from your SUPR page.
If you want to join an existing Time allocation, you have to login/signup on SUPR and send an Project Membership Request from SUPR web interface. 
You may then apply for a PDC account (if you do not have a PDC account) directly from SUPR. 
You can go :ref:`Step 2: Account Creation -> SUPR account <supr_account>`.


Check your existing Time Allocation
-----------------------------------

You can see what Time Allocations in two ways:

#. If you have a SUPR account, go to your SUPR page and click the Projects tab.
#. If you have a PDC account, you can login to Beskow/Tegner and use the ``projinfo`` command.
   It will print the information of all the allocations you belong to and information on the recent usage of the allocation.

Note that medium allocations normally have an extra m, at the start, e.g. SNIC 2015/1-1 is m.2015-1-1 on our system.

