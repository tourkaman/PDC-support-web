.. index:: faq

.. _faq:

FAQs
^^^^

**I got "kinit: krb5_get_init_creds: No ENC-TS found" error when trying to run kinit**

Write an e-mail asking PDC support to extend your Kerberos principal. When this has been done you can continue to login again using the same password as you did before. If we have not yet received the paperwork or time allocation information this will not be done until we do.

**When using the KTH Ubuntu computers I lose permission to access my documents after getting my kerberos ticket**

Both PDC systems and KTH Ubuntu systems use Kerberos authentication, but are in different realms. Replacing the login session's credentials with PDC credentials will destroy the access to your AFS home directory, typically causing applications or the entire login session to crash.

Use pdc-* to access PDC systems. PDC versions of most tools (kinit, klist, kdestroy, ssh, scp...) are available.

