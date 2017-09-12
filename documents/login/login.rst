.. index:: Login
.. _login:

How to login
============

This section covers the procedure for accessing PDC resources . Before following this section,
make sure you have a PDC account successfully created and you have recieved your creditionals.

PDC uses `Kerberos <http://web.mit.edu/kerberos/>`_ authentication protocol. 
This means that, irrespective of your operating system, logging in to PDC is a two stage process:

#.  obtain Kerberos tickets on your local machine once (requires a password)
#.  login to PDC machine (does not require a password)

.. image:: https://drive.google.com/uc?id=0B7GAinAyrwFFUEF5VGQydHAyZDA
   :height: 400px
   :width: 700 px
   :scale: 100 %
   :alt: alternate text
   :align: center

Kerberos tickets are stored on your local machine, and are then presented when you try to log in to the remote system. 
You'll need the following software (in versions that are appropriate for your operating system):
	   
*  Kerberos v5 software (from Heimdal or MIT) - which is necessary for getting a Kerberos ticket, and
*  SSH software supporting GSSAPI with KeyExchange (from modified OpenSSH).

For step-by-step tutorials on how to login, choose from below the operating system of your local computer
from which you want to access PDC resources. If you face any trouble logging in or need further help, feel free to contact PDC support.

.. toctree::
   :glob:
   :maxdepth: 2
		
   linux_login
   windows_login
   mac_login
