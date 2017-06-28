.. index:: File transfer
.. _file_transfer:

File transfer
=============

With SCP/RSYNC
############################

SCP: ``scp`` (secure copy) copies files between hosts on a network. It uses SSH for data transfer, and uses the same authentication and provides the same security as ``ssh``. Before using ``scp``, make sure you have valid forwardable Kerberos tickets on your local machine and a working SSH setup. 

.. rubric:: Transferring from your local machine to PDC

Standing in a directory on your local computer containing the file ``localfile``, you can copy it to the ``Private`` directory on your PDC home directory ``~`` using the command:

.. code-block:: bash
  
   scp ./localfile username@t04n28.pdc.kth.se:~/Private/

where ``username`` is your username at PDC. 

.. rubric:: Transferring from PDC to your local machine

Standing in a directory on your local computer where you want to put the file pdcfile located in ``/cfs/klemming/nobackup/u/username/`` you can transfer it using the command:

.. code-block:: bash  

   scp username@t04n28.pdc.kth.se:/cfs/klemming/scratch/u/username/pdcfile .

where ``username`` is your username at PDC. 

.. note:: Avoid overloading the login nodes

   The login nodes of most clusters can be weak, so it is important not to over load these nodes. The currently recommended machines for transferring large amounts of data in and out of the Klemming filesystem are the two transfer nodes: ``t04n27.pdc.kth.se`` and ``t04n28.pdc.kth.se``.


.. note::

   If your ``.bashrc`` or other shell configuration files produce **ANY** output, then ``scp`` can fail. You can test this with the command below. If the command produces output, then you need to fix your shell configuration files so that they do not produce output.

   .. code-block:: bash  
	   
      ssh pdcusername@t04n28.pdc.kth.se /bin/true

.. note::

   There are some problems trying to transfer files bigger than 1GB using a certain version of openssh (e.g. openssh v72.p1 on MacOs x10.11). You can try to downgrade openssh to an older version, or else, use ``rsync`` to re-establish communication and continue like:

   .. code-block:: bash  

      rsync -avHP pdcusername@t04n28.pdc.kth.se:/cfs/klemming/scratch/u/username/pdcfile .

With AFS
######################
