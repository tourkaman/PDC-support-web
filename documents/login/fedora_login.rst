.. index:: Fedora Login
.. _fedora_login:

How to login from Fedora/CentOs/RHEL
====================================

This section describes how to acquire kerberos tickets and login

Installing Kerberos
-------------------

For Fedora packages krb5-workstation and openssh-clients are needed.
Install these packages with your favorite package manager or by executing **as root**
::

  yum install krb5-workstation openssh-cliensudo apt-get install openssh-client

These packages may already be installed. If there are updates available, we recommend you to update it (yum will ask you for it).

Be aware that the MIT kinit shipped with Fedora differs from the Heimdal kinit and that the MIT kerberos library does not
have as many features to break out of firewalls as Heimdal's library.

For additional information goto :ref:`configuration`
