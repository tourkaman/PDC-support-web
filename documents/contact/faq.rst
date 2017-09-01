.. index:: faq

.. _faq:

FAQs
====

**I got "kinit: krb5_get_init_creds: No ENC-TS found" error when trying to run kinit**

Write an e-mail asking PDC support to extend your Kerberos principal. When this has been done you can continue to login again using the same password as you did before. If we have not yet received the paperwork or time allocation information this will not be done until we do.

**I cannot start my job**

Usually this depends on user not adding time allocation, or adding it wrongfully. on *salloc* you should *-A <allocationid>* and for batch files:

.. code-block:: bash
   
   #SBATCH -A <allocationid>

you can see what your time allocation is called (the value of *<allocationid>*) with the command ``projinfo``.

**When using the KTH Ubuntu computers I lose permission to access my documents after getting my kerberos ticket**

Both PDC systems and KTH Ubuntu systems use Kerberos authentication, but are in different realms. Replacing the login session's credentials with PDC credentials will destroy the access to your AFS home directory, typically causing applications or the entire login session to crash.

A workaround to the issue is to use pdc-* in front of the commands needed to access PDC systems. This includes: kinit, klist, kdestroy, ssh, scp... The new commands would then be *(pdc-kinit, pdc-klist, pdc-kdestroy, pdc-ssh, pdc-scp)*. These commands work in the same way as the original commands, but stores/looks for the kerberos ticket in a different location.

**I get chdir /afs/pdc.kth.se/home/u/username No such file or directory error on Beskow when running**

Beskow does not have access to the afs directory on runtime. Therefore you need to move your executables/scripts to your *cfs* home directory: /cfs/klemming/scratch/u/username and execute the codes/scripts from there.

**I want to test PDC resources and check if it suits my needs**

If you want to try out PDC resources to make sure it suits your needs, you will need to apply for a PDC account and choose time allocation: pdc-test-xxxx , the last one being the current year. By doing that you will be able to submit your jobs for an specific period of time and check if it fits your needs. If you decide to run using PDC resources you will then need to apply for a time allocation for yourself.

**I forgot my password, how can I get a new one?**

There are three methods by which you can get a new PDC password

	* Visit PDC (requires making an appointment, and valid ID card or passport)

	* Get a new password posted to you by paper mail. (requires your PDC username, postal adress and scanned copy of your passport if the address is different from the account application)

	* Get a new password sent to you by SMS (requires your PDC username, mobile phonenumber, a scanned copy of your passport)

For the last two method, you need to send us the detail via mail. see more about contacting pdc <HYPERLINK>
