.. _system-requirements-example-ug:

=============================
System requirements (example)
=============================

To run the Object Storage service for Rackspace Private Cloud Powered By
OpenStack (RPCO), your system must meet the following requirements.

.. contents::
   :depth: 1
   :local:
   :backlinks: none

Hardware
~~~~~~~~

Each node in the cluster must meet the following *minimum*
specifications:

-  Six SAS drives of at least 1 TB capacity each
-  One core for every 3 TB of drive capacity
-  Two GB RAM, plus an additional 250 MB RAM for every TB of drive
   capacity

The amount of disk space depends on how much can fit into the rack
efficiently.

Object Storage is designed to run on commodity hardware. At Rackspace,
storage servers are generic 4U servers with 24 2-TB SATA drives and 8
cores of processing power. RAID on the storage drives is not required
and is not recommended. The disk usage pattern of Object Storage is
unsuitable for RAID.

Operating system
~~~~~~~~~~~~~~~~

Object Storage in RPCO runs on Ubuntu.

Software
~~~~~~~~

Object Storage in RPCO requires the following components of Rackspace
Private Cloud v13:

-  Identity (keystone)
-  Infrastructure services (SQLite database, Memcached, and
   RabbitMQ)

Networking
~~~~~~~~~~

One Gbps or 10 Gbps is suggested internally. An external network should
connect anything external to the proxy servers. The storage network is
intended to be isolated on a private network or multiple private networks.

Database
~~~~~~~~

A SQLite database is part of the Object Storage for RPCO container and account
management process.

Permissions
~~~~~~~~~~~
Object Storage for RPCO can be installed with either root permissions or
as a user with sudo permissions if the ``sudoers`` file is configured to
enable all the permissions.
