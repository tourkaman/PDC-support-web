.. index:: Ubuntu Login
.. _ubuntu_login:

How to login from Ubuntu/Debian
===============================

This section describes how to acquire kerberos tickets and login

Installing Kerberos
-------------------

In Ubuntu, kinit and ssh are in the packages heimdal-clients and openssh-client. 
Install these packages with your favorite package manager or by executing
::

  sudo apt-get install heimdal-clients
  sudo apt-get install openssh-client

For additional information goto :ref:`configuration`

Installing AFS
--------------

In order to access your home directory from your local computer you need to install AFS
::

  sudo add-apt-repository ppa:openafs/stable
  sudo apt-get install openafs-client openafs-modules-dkms
  
The last step will take quite some time, so please be patient!
If asked about which AFS cell this workstation belongs to, answer **pdc.kth.se**.
Please note that the openafs-kernel-module will be rebuilt automatically for 
you with every new openafs version and with every kernel upgrade. 
You do not need to do any manual work! To start, stop and use your AFS client.

Then you need to start the AFS daemon
::

  sudo /etc/init.d/openafs-client start
  
After installing AFS you can access your home folder located at
::

  cd /afs/pdc.kth.se/home/u/username
