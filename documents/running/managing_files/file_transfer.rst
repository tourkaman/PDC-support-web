.. index:: File transfer
.. _file_transfer:
     
Using SCP/RSYNC
###############

.. _scp_ubuntu:

Using SCP/RSYNC from Ubuntu (Linux) and Mac OS:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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

.. _scp_windows:      

Using SCP/RSYNC from Windows:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you're using *putty* to login to PDC clusters, you can use **PSFTP** that follows the putty installation. Simply go to the folder putty is installed, or search for *PSFTP* on windows main menu. Note that just like putty, you need kerberos ticket to use PSFTP.

if you start PSFTP, a new terminal will open. Here, you first have to connect to the cluster. You can do this by typing

.. code-block::
   
   open <username>@t04n28.pdc.kth.se

This is a designated transfer node. If you have followed the step from :ref:`Windows Login <windows_login>` and saved a login session (example: Beskow) you can also type `` open <session_name> `` instead.

Now you have logged in to the cluster and you're in your *AFS Home Directory*. You can change your **remote** directory location to your cfs directory with

.. code-block::

   cd /cfs/klemming/nobackup/u/user/file_location

You can also change your **local** diectory location with

.. code-block::

   lcd c:\Users\username\folder_to_save_file

Keep in mind that the location should be specified in the same way you change directory on a windows terminal, for ``lcd``.

You can transfer files by using **get** or **put**. *get* will transfer files specified from remote location to current local directory, and *put* will transfer files from current local directory to the current remote directory.

.. code-block::

   get <filename>

For more information about PSFTP utility and commands, please look at `Putty Documentation <http://the.earth.li/~sgtatham/putty/0.63/htmldoc/>`

With AFS client
###############

With an AFS client on your local machine, transferring files between PDC and your local computer is as is as drag-and-drop, or, using a ``cp`` command. Follow the below instruction based on your OS to install an AFS client.

.. _afs_client_ubuntu:

Ubuntu (Linux):
^^^^^^^^^^^^^^^

.. rubric:: Method 1

Install the AFS client this way:

.. code-block:: bash  
	   
   sudo add-apt-repository ppa:openafs/stable
   sudo apt-get install openafs-client openafs-modules-dkms

The last step will take quite some time, so please be patient! If asked about which AFS cell this workstation belongs to, answer pdc.kth.se. Please note that the openafs-kernel-module will be rebuilt automatically for you with every new openafs version and with every kernel upgrade. You do not need to do any manual work! To start, stop and use your AFS client, see instructions below.

.. rubric:: Method 2

Using the Synaptic Package Manager's graphical user interface (GUI) to install these packages:

* module-assistant
* openafs-client
* openafs-modules-source

This can also be done without the GUI:

.. code-block:: bash  
	   
   sudo apt-get install module-assistant openafs-client openafs-modules-source

If asked about which AFS cell this workstation belongs to, answer pdc.kth.se

Then, in a shell run:

.. code-block:: bash  
	   
   sudo module-assistant

and do the following:

1.    Choose SELECT
2.    scroll down to and select openafs-modules (mark with space)
3.    Choose OK
4.    Choose GET
5.    Choose BUILD
6.    If asked - select YES to INSTALL the AFS kernel module
7.    If not asked - choose INSTALL
8.    Then, elect EXIT to exit the program.

An AFS client for your Ubuntu kernel is now installed on your computer.

Please note, the AFS client kernel module has do be rebuild every time a new openafs version is installed and every time the Ubuntu kernel is upgraded. This involves starting the module-assistant and following the steps 1 through 8 above.

Now, see instructions below on how to start, stop and use the AFS client.

Starting and using the installed AFS client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Start the AFS client on your local machine::

  sudo /etc/init.d/openafs-client start

Make sure that you have Kerberos installed, then get Kerberos tickets on your local machine::

  kinit --forwardable username@NADA.KTH.SE

Check that you have gotten Kerberos tickets and AFS tokens on your local computer::

  klist -Tf

The output should look like::

  Credentials cache: FILE:/tmp/krb5cc_1000
       Principal: username@NADA.KTH.SE
  Issued           Expires        Flags    Principal
  Dec  8 10:56:11  Dec  8 20:56:11  FPI    krbtgt/NADA.KTH.SE@NADA.KTH.SE
  Dec  8 10:56:12  Dec  8 20:56:11         afs/pdc.kth.se@NADA.KTH.SE

  Dec  8 10:56:12  Dec  8 20:56:11  User's (AFS ID 1000) tokens for pdc.kth.se

Now you should be able to go to your PDC home directory. On your local computer, simply do::

  cd /afs/pdc.kth.se/home/u/username
  
.. _afs_client_windows:
.. _afs_client_mac:
.. _afs_client_freebsd:
