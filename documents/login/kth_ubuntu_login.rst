.. index:: KTH Ubuntu login
.. _kth_ubuntu_login:

How to login from KTH UBUNTU computers
======================================

KTH Ubuntu already has the necessary software and configuration in place, but
the command are working a bit differently so that users can access both
their KTH and PDC home folder.

Most kerberos and ssh commands have a special script starting with *pdc-*

To acquire a Kerberos ticket
::

  pdc-kinit
  
To login into a cluster
::

  pdc-ssh cluster.pdc.kth.se
  
Other commands
::

  # List tickets
  pdc-klist
  # Destroy tickets
  pdc-destroy
  # Copy files
  pdc-scp [localfile] [username]@t04n28.pdc.kth.se:~/Private/

See more information at https://intra.kth.se/en/it/support/guider/kth-ubuntu/pdc-1.735552
