.. index:: File transfer_afs
.. _file_transfer_afs:

With AFS client
===============

With an AFS client on your local machine, transferring files between PDC and your local computer is as is as drag-and-drop, or,
using a ``cp`` command. Follow the below instruction based on your OS to install an AFS client.

.. _afs_client_ubuntu:

Ubuntu (Linux):
---------------

Method 1
^^^^^^^^

Install the AFS client this way:
::

  sudo add-apt-repository ppa:openafs/stable
  sudo apt-get install openafs-client openafs-modules-dkms

The last step will take quite some time, so please be patient! If asked about which AFS cell this workstation belongs to,
answer **pdc.kth.se**. Please note that the openafs-kernel-module will be rebuilt automatically
for you with every new openafs version and with every kernel upgrade. You do not need to do any manual work!
To start, stop and use your AFS client, see instructions below.

Method 2
^^^^^^^^

Using the Synaptic Package Manager's graphical user interface (GUI) to install these packages:

* module-assistant
* openafs-client
* openafs-modules-source

This can also be done without the GUI:
::
	   
  sudo apt-get install module-assistant openafs-client openafs-modules-source

If asked about which AFS cell this workstation belongs to, answer pdc.kth.se

Then, in a shell run:
::
   
  sudo module-assistant

and do the following:

#.    Choose SELECT
#.    scroll down to and select openafs-modules (mark with space)
#.    Choose OK
#.    Choose GET
#.    Choose BUILD
#.    If asked - select YES to INSTALL the AFS kernel module
#.    If not asked - choose INSTALL
#.    Then, elect EXIT to exit the program.

An AFS client for your Ubuntu kernel is now installed on your computer.

Please note, the AFS client kernel module has do be rebuild every time a new openafs
version is installed and every time the Ubuntu kernel is upgraded.
This involves starting the module-assistant and following the steps 1 through 8 above.

Now, see instructions below on how to start, stop and use the AFS client.

Starting and using the installed AFS client
-------------------------------------------

Start the AFS client on your local machine
::

  sudo /etc/init.d/openafs-client start

Make sure that you have Kerberos installed, then get Kerberos tickets on your local machine
::

  kinit --forwardable username@NADA.KTH.SE

Check that you have gotten Kerberos tickets and AFS tokens on your local computer
::

  klist -Tf

The output should look like
::

  Credentials cache: FILE:/tmp/krb5cc_1000
       Principal: username@NADA.KTH.SE
  Issued           Expires        Flags    Principal
  Dec  8 10:56:11  Dec  8 20:56:11  FPI    krbtgt/NADA.KTH.SE@NADA.KTH.SE
  Dec  8 10:56:12  Dec  8 20:56:11         afs/pdc.kth.se@NADA.KTH.SE

  Dec  8 10:56:12  Dec  8 20:56:11  User's (AFS ID 1000) tokens for pdc.kth.se

Now you should be able to go to your PDC home directory. On your local computer, simply do
::

  cd /afs/pdc.kth.se/home/u/username
