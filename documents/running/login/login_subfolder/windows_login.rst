.. index:: Windows Login
.. _windows_login:

How to login from Windows
=========================

This section describes how to acquire kerberos tickets in Windows

Installing Kerberos
-------------------

#. Download the newest Heimdal Kerberos for Windows
   (32-bit or 64-bit depending on your computer's architecture).
   The latest version can be found at https://www.secure-endpoints.com/heimdal/

   In case if this link is temporarily down, please use one of the following...
   
   | 64 bits: https://www.pdc.kth.se/resources/software/login-1/windows/heimdal-kerberos/downloads/64-bit-heimdal
   | 32 bits: https://www.pdc.kth.se/resources/software/login-1/windows/heimdal-kerberos/downloads/32-bit-heimdal

#. Run the downloaded installer for Heimdal.
#. Choose to install a complete installation of Heimdal following this series of pictures

Configure Kerberos
------------------

Next you need to configure **Kerberos** so we are able to find the PDC domain.
The kerberos file should located at::

  C:\ProgramData\krb5.conf

If windows is not installed as default under **C:** then replace
this with were windows is installed. Also the folder **ProgramData**
is hidden by default in windows, so just write the path in the file manager.

**krb5.conf** should be defined with the following entries::

  [domain_realm]
    .pdc.kth.se = NADA.KTH.SE
  [appdefaults]
    forwardable = yes
    forward = yes
    krb4_get_tickets = no
  [libdefaults]
    default_realm = NADA.KTH.SE
    dns_lookup_realm = true
    dns_lookup_kdc = true

.. _acquire_kerberos:

Acquire kerberos tickets
------------------------

In order to get a kerberos ticket you need to open command shell *cmd* and
enter the following::

  kinit Username@NADA.KTH.SE

You will be asked for your kerberos password and then you have acquired your ticket.
More information about kerberos can be found at ...

If you intend to use OpenAFS(see :ref:`file_transfer` ), you also need to obtain an AFS token with the following command::
	
    aklog

After you have obtained an kerberos ticket.


Installing PuTTY
----------------

In order to login you need to install PuTTY with GSSAPI and heimdal support.

#. Installation files for windows can be found at https://marcussundberg.com/putty/
   If the external site is not reachable, here are copies of the Windows installers, PuTTY version 0.67, kex version 1.0

   | 64 bits windows: https://www.pdc.kth.se/resources/software/login-1/windows/putty/putty-0.67-kex-1.0-installer64.exe
   | 32 bits windows: https://www.pdc.kth.se/resources/software/login-1/windows/putty/putty-0.67-kex-1.0-installer32.exe

#. Run the installer. If you get a warning from Windows that it prevented an unrecognized app from starting, click on "More info" and then "Run anyway".
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrQm0xa2VwazV1NVE

#. If you get a User Account Control popup, click 'Yes' to allow it to make changes.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrMkhKUXBlYm43Yk0
#. On the first screen, click Next.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrbUtoSWtQWWlqakU
#. Select where you want to install PuTTY. The default is probably fine. Click Next
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrY3BtM3RZM1RuRTQ
#. Select a start menu folder name, then click Next.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrczB2bjcwY09LT3c
#. If you want, check "Create a desktop icon" and/or a quick launch icon, then click Next.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrNmNId0JLN05SM3c
#. Click Install.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrNXVqTlZmb291OGM
#. Click Finish (view the readme if you wish).

Configuring PuTTY
-----------------

#. Start PuTTY with the shortcut you created or from the location you installed it. 
   The first step is to create what is called a Session in PuTTY. 
   A session is basically a collection of settings for a connection to a machine. 
   In this case, we will assume that the machine we are connecting to is **Beskow**
   (with hostname beskow.pdc.kth.se), with username "user". 
   You can substitute these values for some other cluster at PDC (eg tegner.pdc.kth.se, etc) and of course your own username respectively.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrLWVmdVh3VURnWnc
#. In the field Host Name at the top, we enter ``user@beskow.pdc.kth.se``. 
   Again, substitute the username and the cluster as needed. Make sure the port is 22 and that SSH is selected underneath.
	.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrTzloaUxMWmU0eG8
#. In the menu to the left, navigate to Connection > SSH > Auth > GSSAPI  and check the box "Allow GSSAPI credential delegation".

#. Make sure to move the Heimdal Kerberos GSSAPI.DLL library to the top of the list by using the up key.

#. In the menu to the left again, navigate back to the screen where we started by clicking Session at the very top.
		.. image:: https://drive.google.com/uc?id=0BxYU3X5kGVqrLWVmdVh3VURnWnc 
#. In the field Saved Sessions, we will enter a name for this session. In this case, we will call it "Beskow", 
   but the name can of course be anything descriptive.

#. Click the Save button to the right.

#. Now, click Open. If you have valid Kerberos tickets like
   explained in :ref:`acquire_kerberos` you will now login to the cluster
