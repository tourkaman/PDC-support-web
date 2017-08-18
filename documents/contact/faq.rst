.. index:: faq

.. _faq:

FAQs
^^^^

**I got "kinit: krb5_get_init_creds: No ENC-TS found" error when trying to run kinit**

Write an e-mail asking PDC support to extend your Kerberos principal. When this has been done you can continue to login again using the same password as you did before. If we have not yet received the paperwork or time allocation information this will not be done until we do.

**When using the KTH Ubuntu computers I lose permission to access my documents after getting my kerberos ticket**

Both PDC systems and KTH Ubuntu systems use Kerberos authentication, but are in different realms. Replacing the login session's credentials with PDC credentials will destroy the access to your AFS home directory, typically causing applications or the entire login session to crash.

A workaround to the issue is to use pdc-* in front of the commands needed to access PDC systems. This includes: kinit, klist, kdestroy, ssh, scp... The new commands would then be *(pdc-kinit, pdc-klist, pdc-kdestroy, pdc-ssh, pdc-scp)*. These commands work in the same way as the original commands, but stores/looks for the kerberos ticket in a different location.

**I get chdir /afs/pdc.kth.se/home/u/username No such file or directory error on Beskow when running**

Beskow does not have access to the afs directory on runtime. Therefore you need to move your executables/scripts to your *cfs* home directory: /cfs/klemming/scratch/u/username and execute the codes/scripts from there.
