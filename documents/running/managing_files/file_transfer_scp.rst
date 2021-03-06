.. index:: File transfer_scp
.. _file_transfer_scp:
     
Using SCP/RSYNC
===============

Transfer nodes
--------------

At PDC we have a number of transfer nodes setup to transfer large amount of data so to transfer data
and not bog down the login node, here are a couple of rules to abide by

================= ====================== =======================================
Name              Type                   Intended for...
================= ====================== =======================================
t04n27.pdc.kth.se Dedicated tranfer node Large/many file(s) transfer
t04n28.pdc.kth.se Dedicated tranfer node Large/many file(s) transfer
tegner.pdc.kth.se login node             Submitting jobs and small file transfer
beskow.pdc.kth.se login node             Submitting jobs and small file transfer
================= ====================== =======================================

.. _scp_ubuntu:

Using SCP/RSYNC from Ubuntu (Linux):
------------------------------------

SCP: (secure copy) copies files between hosts on a network.
It uses SSH for data transfer, and uses the same authentication and provides the same security as ``ssh``. Before using ``scp``,
make sure you have valid forwardable Kerberos tickets on your local machine and a working SSH setup. 

Transferring from your local machine to PDC
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Standing in a directory on your local computer containing the file ``localfile``, you can copy it to the ``Private``
directory on your PDC home directory ``~`` using the command:
::  

  scp ./localfile username@t04n28.pdc.kth.se:~/Private/

where ``username`` is your username at PDC. 

Transferring from PDC to your local machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Standing in a directory on your local computer where you want to put the file pdcfile located in
``/cfs/klemming/nobackup/u/username/`` you can transfer it using the command:
::

  scp username@t04n28.pdc.kth.se:/cfs/klemming/scratch/u/username/pdcfile .

where ``username`` is your username at PDC. 

.. note:: Avoid overloading the login nodes

   The login nodes of most clusters can be weak, so it is important not to over load these nodes.
   The currently recommended machines for transferring large amounts of data in and out of the
   Lustre filesystem are the two transfer nodes: ``t04n27.pdc.kth.se`` and ``t04n28.pdc.kth.se``.

.. note::

   If your ``.bashrc`` or other shell configuration files produce **ANY** output, then ``scp`` can fail.
   You can test this with the command below. If the command produces output,
   then you need to fix your shell configuration files so that they do not produce output.
   ::
   
     ssh pdcusername@t04n28.pdc.kth.se /bin/true

.. _scp_windows:      

Using SCP/PSFTP from Windows:
-----------------------------

If you're using *putty* to login to PDC clusters, you can use **PSFTP** or **PSCP** that follows the putty installation.

Using PSCP
^^^^^^^^^^

To use PSCP, open up the command prompt, i.e run cmd. Use PSCP to transfer the files using the
Saved Session you previously added in PuTTY. 
The syntax is similar to scp (ie. -r for recursive etc).

To transfer a file from your local computer to Lustre
::

  "C:\Program Files\PuTTY\pscp.exe" C:\[file to transfer] t04n28.pdc.kth.se:/cfs/klemming/nobackup/[u]/[username]

To transfer a file from AFS to your local computer
::

  "C:\Program Files\PuTTY\pscp.exe" t04n28.pdc.kth.se:/afs/pdc.kth.se/home/[u]/[username]/[file] C:\[folder to transfer to]

Using PSFTP
^^^^^^^^^^^

Simply go to the folder putty is installed, or search for *PSFTP* on windows main menu. Note that just like putty, you need kerberos ticket to use PSFTP.

if you start PSFTP, a new terminal will open. Here, you first have to connect to the cluster. You can do this by typing
::
   
  open <username>@t04n28.pdc.kth.se

This is a designated transfer node. If you have followed the step from :ref:`Windows Login <windows_login>`
and saved a login session (example: Beskow) you can also type `` open <session_name> `` instead.

Now you have logged in to the cluster and you're in your *AFS Home Directory*.
You can change your **remote** directory location to your cfs directory with
::

  cd /cfs/klemming/nobackup/u/user/file_location

You can also change your **local** directory location with
::

  lcd c:\Users\username\folder_to_save_file

Keep in mind that the location should be specified in the same way you change directory on a windows terminal, for ``lcd``.

You can transfer files by using **get** or **put**. *get* will transfer files specified from remote location to current local directory,
and *put* will transfer files from current local directory to the current remote directory.
::

  get <filename>

For more information about PSFTP utility and commands, please look at `Putty Documentation <http://the.earth.li/~sgtatham/putty/0.63/htmldoc/>`

Using SCP/RSYNC from Mac OS:
----------------------------

TODO
