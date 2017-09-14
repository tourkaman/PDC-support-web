.. index:: Mac Login
.. _mac_login:

How to login from Mac OS
========================

This section describes how to acquire Kerberos tickets and
log in from different versions of Mac OS X.


Mac OS X 10.7 to 10.10
----------------------

These versions of Mac OS come with Heimdal and kerberized ssh, so you only have 
to modify your Kerberos and SSH configuration files.

For additional information goto :ref:`configuration`

Mac OS X 10.11 to 10.12
------------------------

The native ssh which comes with recent Mac OS X versions (El Capitan 10.11 and Sierra 10.12) does not support 
GSSAPI key exchange, which is required for authenticating to PDC systems 
using Kerberos.  
Two options are available for setting up the connection to PDC. The 
first option listed below is easier if you don't have macports installed on your machine, 
but both methods are described below.

(Method 1) Mac Installer
^^^^^^^^^^^^^^^^^^^^^^^^

Start by downloading `the OSX installer <https://drive.google.com/file/d/0B3KTk17tdgqDY2xCMWJxMXNvQWs/view?usp=sharing/>`_.

Start the installer and click through the steps.

To avoid interfering with the default binaries in /usr/bin, the installer will place the ssh, scp and sftp binaries in /usr/local/bin, 
and it will adjust your path to make sure this directory is 
listed before the system location in your PATH variable (by adding a line your 
.profile file).

(Method 2) Install openssh via macports
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Another option is to install openssh via macports.  
First, install Xcode through the App Store.  
Open Xcode and choose in the menu:  

*Xcode > Open Developer Tool > More Developer Tools*

A browser will open with a list.  Download and install:

*Command Line Tools for Xcode*

Then install macports from https://www.macports.org.

Finally install openssh through macports with the command
::

  sudo port install openssh +gsskex

You can now restart the computer and continue with the setup of the 
Kerberos file and .ssh/config described above for Mac OS X 10.7 to 10.10.

Installing AFS
--------------

https://www.pdc.kth.se/resources/software/file-transfer/file-transfer-with-afs/mac
