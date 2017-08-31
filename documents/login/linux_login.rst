.. index:: Linux Login
.. _linux_login:

How to login from Linux (Ubuntu)
--------------------------------

This section describes how to acquire kerberos tickets and login in linux

Installing Kerberos
^^^^^^^^^^^^^^^^^^^

In Ubuntu, kinit and ssh are in the packages heimdal-clients and openssh-client. 
Install these packages with your favorite package manager or by executing::

  sudo apt-get install heimdal-clients
  sudo apt-get install openssh-client

If you are on a centrally managed computer at KTH, both packages are probably
installed by default.

Configure Kerberos
^^^^^^^^^^^^^^^^^^

Next you need to configure **Kerberos** so we are able to find the PDC domain.
The configuration file for kerberos that you need to edit is **/etc/krb5.conf** as root.
and should be changed by adding the following entries::

  [domain_realm]
    .pdc.kth.se = NADA.KTH.SE
  ...
  [appdefaults]
    forwardable = yes
    forward = yes
    krb4_get_tickets = no
  ...
  [libdefaults]
    default_realm = NADA.KTH.SE
    dns_lookup_realm = true
    dns_lookup_kdc = true

If you are not able to become root on your machines you can create a file in your home
directory called for example **~/pdckrb** with the changes shown above.
After this you need to set the path for kerberos like::

  # For bash
  export KRB5_CONFIG=~/pdckrb/krb5.conf
  # For tcsh
  setenv KRB5_CONFIG  ~/pdckrb/krb5.conf

Acquire kerberos tickets
^^^^^^^^^^^^^^^^^^^^^^^^

In order to get a kerberos ticket::

  kinit Username@NADA.KTH.SE

You will be asked for your kerberos password and then you have acquired your ticket.
You can see what active tickets you have using::

  klist

More information about kerberos can be found at ...

Configure SSH
^^^^^^^^^^^^^

OpenSSH can be configured with command line arguments or a configuration file.
The options in the configuration file are parsed in order.
Create or modify the file **~/.ssh/config**::

  # Hosts we want to authenticate to with Kerberos
  Host *.kth.se *.kth.se.
  # User authentication based on GSSAPI is allowed
  GSSAPIAuthentication yes
  # Key exchange based on GSSAPI may be used for server authentication
  GSSAPIKeyExchange yes
  # Hosts to which we want to delegate credentials. Try to limit this to
  # hosts you trust, and were you really have use for forwarded tickets.
  Host *.csc.kth.se *.csc.kth.se. *.nada.kth.se *.nada.kth.se. *.pdc.kth.se *.pdc.kth.se.
  # Forward (delegate) credentials (tickets) to the server.
  GSSAPIDelegateCredentials yes
  # Prefer GSSAPI key exchange
  PreferredAuthentications gssapi-keyex,gssapi-with-mic
  # All other hosts
  Host *

The file can be downloaded from :download:`here <config>`.

Do remember to set the right permission on the file::

  chmod 644 ~/.ssh/config

After this you can login by using::

  ssh UserName@Cluster.pdc.kth.se
  
SSH without configuration
^^^^^^^^^^^^^^^^^^^^^^^^^

As an alternative you can also supply these options directly to the ssh command in order to login::

  ssh -o GSSAPIDelegateCredentials=yes -o GSSAPIKeyExchange=yes -o GSSAPIAuthentication=yes UserName@Cluster.pdc.kth.se

Installing AFS
^^^^^^^^^^^^^^

In order to access your home directory you need to install AFS::

  sudo add-apt-repository ppa:openafs/stable
  sudo apt-get install openafs-client openafs-modules-dkms
  
The last step will take quite some time, so please be patient!
If asked about which AFS cell this workstation belongs to, answer **pdc.kth.se**.
Please note that the openafs-kernel-module will be rebuilt automatically for 
you with every new openafs version and with every kernel upgrade. 
You do not need to do any manual work! To start, stop and use your AFS client.

Then you need to start the AFS daemon::

  sudo /etc/init.d/openafs-client start
  
After installing AFS you can access your home folder located at::

  cd /afs/pdc.kth.se/home/u/username
