.. index:: Login
.. _login:


How to login
============

This section covers the procedure for accessing PDC resources . Before following this section, make sure you have a PDC account successfully created and you have recieved your creditionals.

PDC uses `Kerberos <http://web.mit.edu/kerberos/>`_ authentication protocol. This means that, irrespective of your operating system, logging in to PDC is a two stage process:

1.  obtain Kerberos tickets on your local machine once (requires a password)
2.  login to PDC machine (does not require a password)

Kerberos tickets are stored on your local machine, and are then presented when you try to log in to the remote system. This means that in order to log in you need the following software (in versions that are appropriate for the operating system on your local computer):

.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFUEF5VGQydHAyZDA
   :height: 400px
   :width: 700 px
   :scale: 100 %
   :alt: alternate text
   :align: center

*  Kerberos v5 software (from Heimdal or MIT) - which is necessary for getting a Kerberos ticket, and
*  SSH software supporting GSSAPI with KeyExchange (from modified OpenSSH).

Choose the operating system of your local computer from which you want to access PDC resources. If you face any trouble logging in or need further help, feel free to contact PDC support.


Windows
#######

:ref:`Login from Windows <windows_login>`

Linux
#####

:ref:`Login from Linux <linux_login>`

Mac OS
#######

:ref:`Login from Mac <mac_login>`
