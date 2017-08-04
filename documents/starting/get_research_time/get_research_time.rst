.. index:: Getting research time at PDC
.. _get_time:

Step 1: Getting research time
=============================

.. rubric:: Are you applying for a new Time Allocation or joining an exisiting one?

Before running on PDC, users must belong to at least one Time Allocation. If you are joining a project in a research group that already has a Time Allocation, then jump to :ref:`joining an existing time allocation <joining_a_existing_time_allocation>`.



.. rubric:: Are you applying for PDC resources for a course?

If you're a participant of a course at KTH that uses the super computers, you can jump to the step :ref:`STEP 2: account creation for course account <course_account>`. Do not forget to specify the course ID, and the name of the course administrator for the course. You also need to be a part of a participant list managed by the course administrator.

.. rubric:: Are you a Master student in need for PDC resources for thesis?

In general, we do not accept application from Master students. However, you can ask your supervisor to :ref:`Apply for a New Time Allocation <Apply_for_a_new_time_allocation>` and then join that Time allocation as an project member. We recommend to apply for *Small allocation* (see more info below) for thesis projects. 

.. _Apply_for_a_new_time_allocation:

Apply for a New Time Allocation
################################

If you are applying for a new Time Allocation, you are the Principal Investigator (PI). Time Allocation is limited both in time per month for running jobs, and in duration, so it is important to apply for the right amount of time. Keep in mind that a PI apply for a time allocation that will cover the needs for all people in a certain research project. You would have to find what allocation would suit the best for your project with the help of the table below:

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

All time allocations are now managed through `SUPR <https://supr.snic.se/>`_, handled by SNAC (Swedish National Allocations Committee) so users can be added or removed from the allocation directly using the SUPR web interface. If you do not have an SUPR account, you need to obtain one [go to step 2 SUPR account] and apply from my page in SUPR web interface.  The changes are then automatically applied to PDC clusters overnight by various scripts.

To know more on what cores or core-hours mean, please visit the Preliminaries page.

.. _joining_a_existing_time_allocation:

Joining a existing Time Allocation
##################################

If you want to join an existing Time allocation, you have to first create an SUPR account [go to step 2 SUPR account] and send an Project Membership Request from SUPR web interface, and then proceed to send an PDC account request through SUPR.


Check your existing Time Allocation
###################################

You can see what time allocations you belong to via the SUPR web page. Note that medium allocations normally have an extra m, at the start, e.g. SNIC 2015/1-1 is m.2015-1-1 on our system. You can see which time allocation you are a member of using the ``projinfo`` command. It will print the information of all the allocations you belong to and information on the recent usage of the allocation.


Graphic
#######

Placeholder for poster-like infographics for user

.. Shouldn't be here. Maybe in running research section. Acknowledge your SNAC/PDC time allocation https://drive.google.com/uc?id=0BxYU3X5kGVqrYW1xTkRnQXRqRU0

.. graphviz::

   digraph structs {
   
     subgraph cluster1 {
     style=invis; 
     color=white;
     edge [color=white];
    
     u0 [shape=box,color=white,fixedsize=true,height=2,width=2,label=
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

     u1 [shape=record,color=white,fixedsize=true,height=2,width=2,label=
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

     u2 [shape=record,href="www.google.com",color=white,fixedsize=true,height=2,width=2,label=
     <
       <table border="0">
         <tr>
           <td fixedsize="true" width="100" height="100" border="0"><img src="documents/starting/get_research_time/icons/industry.png"/></td>
         </tr>
         <tr>
           <td>Special account <br /> (PRACE, Scania)</td>
         </tr>
       </table>
     >];  
     
     u0 -> u1;
     u1 -> u2;
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

     { rank=same; struct1; u0; }
     { rank=same; struct2; u2; }
     { rank=same; struct3; u2; }

     struct1 -> struct2 [penwidth=2];
     struct1 -> struct3 [penwidth=2];    

     edge[constraint=false];
     u0 -> struct1 [penwidth=3, fontcolor=red, color=red, label="Apply for SUPR account"];
     u1 -> struct3 [penwidth=3, fontcolor=red, color=red, label="Apply for PDC account"];
     u2 -> struct3 [penwidth=3, fontcolor=red, color=red, label="Contact PDC directly"];   
     
     }
     
