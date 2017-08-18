.. index:: Accessing software
.. _software:

Accessing software
==================
At PDC, there is a variety of machines, operating systems, projects and different versions of the same code that all have their special set of programs to run. This means that different users or different programs might have newer/older dependencies or preference of a specific software.

To be able to maintain and use this large set of programs we use `Modules <http://modules.sourceforge.net/index.html>`_. Below we present the needed commands to use these modules to your advantage.

Available softwares
##################
.. topic:: Available softwares
 
   You can find the softwares that are available in the different machines at

   `Available Software <http://pdc-software-web.readthedocs.io/en/latest/>`_

In the software page you can also find what versions is available. Each software have instructions on how to load and use the software. If you don't find the version or a specific software, you can either (temporary) create it in your `cfs` directory or :ref:`Contact PDC <contact_support>` and ask us to install it.

[More about Licence and policy etc should also be here?]


Using modules
#############

You can load/add a module from your terminal with the following command

.. code-block:: bash
   
   module add Programname/version

the *Programname*  can be found using

.. code-block:: bash

   module avail 

and the available versions can be found using

.. code-block:: bash

   module avail Programname

You can check the currently loaded modules with

.. code-block::

   module list

If you have an module you do not want, you can unload it with

.. code-block::

   module unload Programname

and you can also swap modules with

.. code-block::

   module swap loadedProgramname newProgramname

Make sure you haven't loaded multiple version of one program or forgot to load dependencies for certain software.


