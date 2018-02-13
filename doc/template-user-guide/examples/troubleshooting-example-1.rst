.. _troubleshooting-example-1-ug:

===========================================
Troubleshooting (example of several issues)
===========================================

If you encounter issues when working with Cloud Backup, use the information in
this section to help you troubleshoot.

.. contents::
   :depth: 1
   :local:
   :backlinks: none

Backup statuses
~~~~~~~~~~~~~~~

This section describes each of the backup statuses, why you might receive each
status, and actions that you can perform.

Skipped
-------

A status of Skipped indicates that the backup job was skipped because a backup
job was already queued. A single backup job can be queued only once.

This status likely occurs because the frequency of the backup job is set too
high (for example, hourly) and a single backup takes too long (longer than an
hour). The backup scheduler starts to skip backups that it can't meet.

Consider reducing the frequency of the job, or reducing the amount of data. If
this is the initial job, the subsequent jobs might finish faster.

Missed
------

A status of Missed indicates that the backup job was missed. The DriveClient
service was likely not running at the time of the scheduled backup, and the
agent was therefore offline.

Verify that the agent is running on the server. If the agent is not running,
start it. Then, check the logs to determine why the agent was not running.

An agent should never go offline by itself. If the agent did not respond, then
the agent could not reach one of the API endpoints, the agent was not running,
or the agent was manually stopped or terminated.

Completed with Errors
---------------------

A backup status of Completed with Errors indicates that the backup
completed but one or more files could not be backed up. The most common
issues that cause this status are as follows:

- The file was deleted between the time the index of files completed and the
  copy of that specific file was attempted. This issue is common with any
  temporary files, such as PHP session files, and is almost always harmless.
  If it is possible and practical for you to exclude these files from the
  backup definition, this kind of error goes away.

- The file was exclusively locked (Windows), so that no other process could
  read it. This issue is common with database binary files. Do not back up
  binary files; instead, dump the contents of the database to a flat file
  (such as an SQL file), and back up that flat file. Doing so allows for
  quicker backup and easier restore.

- Non-UTF-8 characters were used in the path of the file in the operating
  system. The current version of Cloud Backup supports only UTF-8 characters.
  When non-UTF-8 characters are used, a ``Path Not Found`` message is
  displayed.

Error
-----

Many issues might cause a backup status of Error to occur, such as cloud
account permissions for the user who configured that agent or the DriveClient
not being able to connect to the agent APIs.

Rackspace Support must review the **driveclient.log** file to determine the
cause. If the agent is not connected, attach the **driveclient.log** file to a
ticket so that Support can review it.

Failed
------

A backup status of Failed indicates that a serious problem occurred and the
backup job did not run. As with the Error status, check the logs on the
server.

Connection errors
~~~~~~~~~~~~~~~~~

When DriveClient is started, it attempts to connect to the RSE API endpoint
(**rse.drivesrvr.com** or **rse.drivesrvr.co.uk**) to let the API know that it
is available to take commands. If it can't reach that endpoint, or the
associated **api.drivesrvr.com** or **api.drivesrvr.co.uk** endpoint, the
service stops.

The following symptoms might occur:

- On Windows, the following permissions error message might be displayed:
  ``Please check your permissions and try again``. This is the default error
  message that Windows displays when a service fails to start.

- On Linux, the agent simply shuts down.

When the agent shuts down, a line similar to the following line is displayed,
indicating that the logging is stopping. This is the last thing that is
logged before the agent shuts itself off.

.. code::

    INFO |root|rax::AgentPolicy::TearDown(38)] Tearing down logging...

The agent is also shown as Disconnected in the **Backups** area of the Cloud
Control Panel.

If the agent can't communicate with one or more of the following required API
endpoints, you can test the communication as indicated:

- Cloud Backup API: **api.drivesrvr.com** (US accounts) or
  **api.drivesrvr.co.uk** (UK accounts)

  You can test this communication with an HTTP GET request (or Open Standard
  Web Browser) to the URL <https://api.drivesrvr.com/v1.0/help/apihealth>.

- Cloud Backup RSE API: **rse.drivesrvr.com** (US accounts) or
  **rse.drivesrvr.co.uk** (UK accounts)

  You can test this communication with an HTTP GET request (or Open Standard
  Web Browser) to the URL <https://rse.drivesrvr.com/health>.

- Cloud Files API endpoints: These are regional endpoints, but they all have
  the same ``/healthcheck`` command that allows for network connection testing.
  You can test this communication with an HTTP GET request:
  <https://%3Cendpoint%3E/healthcheck> using regional public and ServiceNet
  endpoints, which are shown in the following table. For example,
  <https://storage101.ord1.clouddrive.com/healthcheck>.

  .. list-table::
     :widths: 10 45 45
     :header-rows: 1

     * - Region
       - Public API
       - ServiceNet API
     * - ORD
       - storage101.ord1.clouddrive.com
       - snet-storage101.ord1.clouddrive.com
     * - DFW
       - storage101.dfw1.clouddrive.com
       - snet-storage101.dfw1.clouddrive.com
     * - IAD
       - storage101.iad3.clouddrive.com
       - snet-storage101.iad3.clouddrive.com
     * - LON
       - storage101.lon3.clouddrive.com
       - snet-storage101.lon3.clouddrive.com
     * - SYD
       - storage101.syd2.clouddrive.com
       - snet-storage101.syd2.clouddrive.com
     * - HKG
       - storage101.hkg1.clouddrive.com
       - snet-storage101.hkg1.clouddrive.com

Backup agent logs
~~~~~~~~~~~~~~~~~

The agent logs are stored, by default, in the following directories:

- (Windows) **C:\\ProgramData\\DriveClient\\logs\\driveclient.log**
- (Linux) **/var/log/driveclient.log**

The **log4cxx.xml** configuration file controls agent logging. This file is
located in the Cloud Backup cache folder. Among the things that you can
manually edit in this file are the size of the **driveclient.log** file
(``MaxFileSize``) and how many previous versions (``MaxBackupIndex``) are saved
before they are deleted.

Format of log lines
-------------------

Log lines have the following format:

.. code::

    [DATE TIME | THREADID | LOGLEVEL | USER | CONTEXT] LOG INFORMATION.

- ``DATE TIME``: Time stamp indicating when the log line was written.
- ``THREADID``: An indicator that separates the thread from all of the other
  threads writing to the same log file.
- ``LOGLEVEL``: The depth of the logging. The default is INFO, but Support
  might increase this level to TRACE or DEBUG. The log levels are common log
  levels, such as INFO, WARN, and ERROR.
- ``USER``: The user that is running the service. On Linux,  this value is
  root; on Windows, it is Administrator.
- ``CONTEXT``: Internal information about where the log was generated.
- ``LOG INFORMATION``: The context of the log.

Common log items
----------------

The following common items are included in the **driveclient.log** file:

- ``rax::LoggingPolicy::PerformSetup(134)``: Indicates the start of the
  DriveClient service.
- ``rax::AgentPolicy::TearDown(38)] Tearing down logging...``: Indicates that
  the DriveClient service was properly shut down.

Common errors in the log
------------------------

Common errors in the log include 401 and 403 errors that are received when the
agent is accessing the **rse.drivesrvr.com**, **api.drivesrvr.com**,
**rse.drivesrvr.co.uk**, or **api.drivesrvr.co.uk** endpoints.

When you first start the DriveClient service, the RSA key pair for
authentication might not properly synchronize immediately, which causes a brief
time of 401 and 403 errors in the **driveclient.log** file. This is normal for
the Cloud Backup internal APIs. The DriveClient service handles these errors
and retries the appropriate number of times before canceling the startup of
that service.

If the errors continue for more than 5-10 seconds, contact Rackspace Support.

Recovery of your encrypted vault password
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can't recover your encrypted vault password. The vault password is stored
only on the cloud server that is linked to that encrypted vault. If that
password is forgotten, and the **bootstrap.json** file was overwritten or lost,
there is no way to recover the password.

Inability to back up or restore files (Windows)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Windows has the ability to *exclusively lock* a file, so that no other
process can read or write to it. This locking is common in database
binary files, but many other programs use this locking protocol. If this
locking occurs, the only workarounds are to close the program that has
the exclusive lock or restore the file to a different location.

If you are backing up a file that you know will be exclusively locked,
consider using VSS snapshots (if your version of Windows
supports it), and back up the contents of the VSS snapshot. Using VSS
snapshots enables you to get a proper backup of the file.

The latest version of Cloud Backup for Windows automatically takes a VSS
snapshot of the drive and attempts to back up files from it.

System resource use
~~~~~~~~~~~~~~~~~~~

The amount of resources (memory, CPU, and load) used by the DriveClient is
directly related to how many files are being backed up in each backup
configuration. An increased number of files (or the size of files) can cause
the agent to consume more resources.

Other errors and issues
~~~~~~~~~~~~~~~~~~~~~~~

Following are other errors and problems that you might encounter.

Backup failed with a 403 error from Cloud Files when the account has subusers
-----------------------------------------------------------------------------

This error occurs when a registered subuser who is authorized for Cloud Backup
but not for Cloud Files access attempts a backup. All requests to Cloud Files
return a 403 error. When the subuser attempts to authenticate again, the new
authentication token is the same as the old one.

Account administrators can manage permission levels in the User Management
section of the Cloud Control Panel. Submit a request to your account
administrator for Full access to your account or Administrative access to Cloud
Files for your subuser account. Cloud Backup does not support Dedicated Users
with Cloud access or Federated users.

Cleanup process stuck in "preparing" mode
-----------------------------------------

The cleanup process requires a large number of calculations before it
can start cleaning up for the file rotation. As a result, the cleanup
process could be shown as "preparing" for some time before the files
start being rotated. The percentage complete can't be tracked at this time.

Unexpected Skipped notifications for a backup
-----------------------------------------------

You might get a Skipped notification if you have reregistered servers (the old
server appears offline with a duplicate online server). By design, scheduled
backups for offline servers send a notification of Skipped. To discontinue
getting these notifications for offline servers, select **Disable** from the
**Actions** menu for the **Backup Configuration**.

.. warning::

   We do *not* recommend reregistering a DriveClient agent, especially if the
   server has existing backup configurations and data backed up. Reregistering
   disassociates the server from the prior backup configurations and backed up
   data.

If you have reregistered a DriveClient agent and are unintentionally
disassociated from your backups, you can use the
`migrate vault API operation <https://developer.rackspace.com/docs/cloud-backup/v1/developer-guide/#migrate-vault>`_
to migrate the previous backup vault from the previous agent to a new agent
that has no backup configurations or previous backups run against it.

Files modified during backup are missing or corrupted
-----------------------------------------------------

.. note::

   This issue relates to the data that is backed up and not to the actual file
   on the file system.

The following types of file changes can occur during a backup:

-   Files are overwritten or get deleted. These files are not guaranteed
    to have usable content or to be included in the backup at all.
-   Files, like logs, are appended to. We will make a best effort to
    back up these files, but we expect to be able to restore a
    reasonable and usable form of these files.
-   Files, like databases, might have random updates to any part
    of them. We do not in any way guarantee that these files will be
    restorable, and even if they are restored, we do not guarantee that
    what is restored is not corrupt.

These file types either change too rapidly (databases, logs, caches) or
don't exist long enough to be backed up (session files). Session files
should be avoided entirely. And if the information is valuable to your
business, log files should track it. Caches should also be avoided, as
their data is meant to be discarded.

If you need to back up these types of files, we recommend the following
workarounds:

- For databases, take a snapshot of the database (for example, a database
  dump) and back up the dump.
- For log files, take snapshots of your log files and back them up. To avoid
  running out of disk space, rotate your log files periodically.
