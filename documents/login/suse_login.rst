.. index:: SUSE Login
.. _suse_login:

How to login from SUSE
======================

This section describes how to acquire kerberos tickets and login.

Installing Kerberos
-------------------

For SUSE you need to install heimdal and a patched ssh to get GSSAPI-keyExchange to work.
Download and install a suitable rpm from ftp://ftp.pdc.kth.se/pub/krb/contrib/opensuse/

Follow instruction for :ref:`configuration`

You might also need to run the command
::

  /sbin/ldconfig
