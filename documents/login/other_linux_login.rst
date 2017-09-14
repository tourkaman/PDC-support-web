.. index:: Other Linux Login
.. _other_linux_login:

How to login from other Linux distributions
===========================================

This section describes how to acquire kerberos tickets and login

Installing Kerberos
-------------------

In order to access the computers at PDC in a secure way you have to install some variant of Kerberos binaries.

* Gentoo: Install app-crypt/heimdal and net-misc/openssh
* FreeBSD: generally comes with Kerberos pre-installed (in ports).
* Archlinux: Patch for OpenSSH needed (January 2011). Cf: http://www.sxw.org.uk/computing/patches/openssh.html
* Solaris: At NADA/CSC: module add heimdal/latest, otherwise use the ssh shipped with Solaris.

If you need support for a Unix dialect that is missing, you have to compile
the latest heimdal release yourself from scratch which can be downloaded from
http://www.h5l.org/

For additional information goto :ref:`configuration`
