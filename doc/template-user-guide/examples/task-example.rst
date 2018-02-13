.. _task-example-ug:

==========================================================================
Migrate your email by using the Self-Service Migration Tool (task example)
==========================================================================

Use the Self-Service Migration Tool provided in the Cloud Office Control Panel
to copy email data from your current provider to Rackspace Email, Rackspace
Hosted Exchange, or Rackspace Office 365.

Prerequisites
~~~~~~~~~~~~~

To perform this task, you need access to the Cloud Office Control Panel and
Administrator access to the DNS host.

Before you begin your migration, you must create your mailboxes on the
Rackspace environment. The migration tool does not create your mailboxes for
you. Use the following resources to help you create your mailboxes:

- Rackspace Email: `Add Rackspace Email mailboxes <https://support.rackspace.com/how-to/add-rackspace-email-mailboxes/>`_
- Microsoft Exchange: `Add Microsoft Exchange mailboxes <https://support.rackspace.com/how-to/adding-microsoft-exchange-mailboxes-0>`_
- Rackspace Office 365:

  - `Add an Office 365 license <https://support.rackspace.com/how-to/add-an-office-365-license/>`_
  - `Add users individually or in bulk to Office 365 <https://support.office.com/en-US/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec>`_
    (Microsoft Support site)
  - `Create a shared mailbox <https://support.office.com/en-us/article/Create-shared-mailboxes-in-Office-365-871a246d-3acd-4bba-948e-5de8be0544c9>`_
    (Microsoft Support site)

Ensure that you meet the following migration requirements:

- Gather all email addresses, usernames, and passwords for mailboxes on both
  your source (current) and destination (Rackspace Email or Hosted Exchange)
  mail servers. This information is required for migrating email data with the
  Self-Service Migration Tool. For Office 365, you can use admin credentials to
  verify your migration.

- Ensure that you can update your email DNS records at your current DNS host.
  If you do not know where to update your email DNS records, read
  `Find your DNS host <https://support.rackspace.com/how-to/find-dns-host/>`_.

- Review the list of
  `items migrated during a Cloud Office migration <https://support.rackspace.com/how-to/items-migrated-during-a-cloud-office-migration/>`_.

- Ensure that the size of your source mailbox does not exceed 70 percent of
  your new mailbox's capacity.

- Copy email from the source server so that no data is lost. Some email
  messages might be corrupt and not migrate.

- Inform users to refrain from changing their passwords during the migration
  process.

.. warning::

  *Do not* cancel your source mail server service until you have confirmed with
  all users that they have their email data.

Migrate your email
~~~~~~~~~~~~~~~~~~

1. Log in to the `Cloud Office Control Panel <https://cp.rackspace.com/>`_.
#. In the **Domains** section at the bottom of the screen, click
   **Email Migrations**.
#. Click **Start Migration Now**.

   You are redirected to the MigrationWiz portal.

   You can follow the remaining instructions or follow a
   `MigrationWiz video tutorial <https://www.youtube.com/watch?v=AOvY0gOY1ao>`_.

#. In the **Email Address** box, enter a contact email address that will *not*
   be migrating. Then, agree to the User Agreement (BitTitan is MigrationWiz),
   and click **Login**.

   .. figure:: ../figures/MigWizSC1.png
      :alt: MigrationWiz portal

   A notification informs you that an email with a secure link has been sent to
   your email address. Follow the instructions in the email to log in to the
   MigrationWiz portal.

#. Find the server address for your existing email service:

   - IMAP: If you use Outlook, the incoming server address can be found under
     your account settings. It typically looks like **mail.domain.com** or
     **imap.domain.com**.
   - Webmail: Your server address is a portion of the webmail URL. For example,
     if your webmail address is **https://webmail.domain.com**, then your
     server address is **webmail.domain.com**.
   - Exchange: Your Outlook Web Access (OWA) address is the best way to
     connect. Check your mail via an Internet browser. It typically looks like
     **https://mail.domain.com/owa** or **https://mail.domain.com/exchange**.

   .. note::

      You can also use your server's IP address in place of any host names and
      server addresses.

#. Click **Next**.
#. Enter your source and destination server configuration settings:

    1. Select the source server system type and enter the server address. For
       IMAP, you must also enter a port number. IMAP ports are **993** (SSL)
       and **143** (non-SSL).
    2. For the destination server, select the service that you are migrating
       to, **Rackspace Email**, **Rackspace Exchange 2016**, or
       **Microsoft Office 365**.
    3. Click **Next**.

   .. note::

      If you are migrating to a hybrid solution (both Rackspace Email and
      Rackspace Exchange), you must create more than one migration project.
      Step 12 explains how to start a new project when the current one is
      completed.

#. Enter the email addresses, usernames, and passwords for the source and
   destination mailboxes. You can migrate multiple mailboxes by clicking the
   + symbol or by entering your mailbox information in the spreadsheet
   provided. Then, click **Next**.

   The next step is a trial migration to ensure that connectivity is successful
   to both the source and destination mailboxes based on the information that
   you entered.

#.  Click **Next** to begin the trial migration.

#. When the status changes to **Ready for migration**, click **Next**.

    .. note::

       If the status shows **Failed**, click the red button labeled
       **More info**. Next select **Solve Issue** for instructions on resolving
       the issue.

#. On the Ready to migrate page, click **Next** to begin the migration of your
   email data.

   Several factors influence how long your email takes to migrate. For a list
   of possible factors, see `Factors that affect the duration of email migrations <https://support.rackspace.com/how-to/factors-that-affect-the-duration-of-email-migrations>`_.

#. After your migration has completed, you can run the migration tool again
   by clicking **Migrate new items.**

   For more information about running additional migrations, see
   `Run additional passes with MigrationWiz <https://support.rackspace.com/how-to/running-additional-passes-with-migrationwiz>`_.
   Otherwise, click **Finish**.

#. To begin a new migration project, click **My Migrations** in the top-right
   corner of your migration portal. On the My Migrations page, click
   **Start new migration**.

   .. figure:: ../figures/15-2_0.png
      :alt: Start a new migration

Next step
~~~~~~~~~

After the migration is complete, users must reconfigure Outlook,
`mail clients <https://support.rackspace.com/how-to/cloud-office-support-terminology/>`_,
and mobile devices to connect to their mailbox at Rackspace. Users can visit
https://emailhelp.rackspace.com for configuration instructions.
