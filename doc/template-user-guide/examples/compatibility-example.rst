.. _compatibility-example-ug:

=======================
Compatibility (example)
=======================

This section outlines the compatibility of RackConnect v3.0 with other
Rackspace products and offerings.

.. contents::
   :depth: 1
   :local:
   :backlinks: none

Compatibility with Rackspace public cloud offerings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following table lists the Rackspace public cloud products
that are compatible with RackConnect v3.0. The **Requirements** column lists
the requirements that your RackConnect v3.0 cloud servers must meet for them to
work with the listed product. For example, "ServiceNet" means that your cloud
servers must be provisioned with ServiceNet interfaces for them to work with
the designated product.

.. note::

   Cloud Load Balancers and OnMetal v1 servers are not compatible with
   RackConnect v3.0. OnMetal v2 servers are compatible, but might require
   provisioning a new Cloud Network in your RackConnect environment. Contact
   your support team for assistance.

.. list-table::
   :widths: 25 25 50
   :header-rows: 1

   * - Product
     - Requirements
     - Details
   * - Auto Scale
     - None
     - Auto Scale is an API-based tool that automatically scales resources in
       response to an increase or decrease in overall workload based on
       user-defined thresholds. Auto Scale enables you to automatically scale
       your RackConnect cloud servers resources to adjust to customer demand.

       For details about using Auto Scale with RackConnect v3, see
       `Cloud Bursting with RackConnectV3 <https://developer.rackspace.com/docs/autoscale/v1/developer-guide/#cloud-bursting>`_.
   * - Cloud Backup
     - ServiceNet
     - Cloud Backup is a file-based backup application that enables you to
       choose which files and folders to back up from your cloud servers. You
       can choose to restore your whole system with all of its folders and
       files, or individual files or folders from a given date, to restore to
       an entirely different server.
   * - Cloud Block Storage
     - None
     - Cloud Block Storage is a block-level storage solution that enables you
       to expand the storage capacity of your Rackspace  Cloud Servers.
   * - Cloud Databases
     - ServiceNet
     - Cloud Databases is a stand-alone, API-based relational database service
       built on the OpenStack&reg; cloud that enables you to easily provision
       and manage multiple MySQL database instances. Instances are provisioned
       in a single-tenant, container-based environment per account.

       RackConnect v3.0 is compatible with MySQL Cloud Databases instances.

       **Note:** Cloud Databases is compatible with cloud servers only and
       cannot be used directly with dedicated servers.
   * - Cloud Files
     - ServiceNet
     - Cloud Files provides an easy-to-use online storage for files and media
       that can be delivered globally at fast speeds over the Akamai content
       delivery network (CDN).
   * - Cloud Monitoring
     - Provisioned public IP address
     - Cloud Monitoring provides you with timely and accurate information about
       how your resources are performing. You can quickly create multiple
       monitors that use predefined checks such as PING, HTTPS, and SMTP to
       track your cloud resources and receive instant notification when a
       resource needs your attention.
   * - Cloud Networks
     - None
     - RackConnect v3.0 depends on and leverages Cloud Networks to connect
       from your RackConnect cloud servers to your dedicated environment. You
       use Cloud Networks to create and manage secure, isolated networks in the
       cloud. These networks are fully single tenant and you have complete
       control over the network topology, IP addressing, and which cloud
       servers are attached. Cloud networks are regional in scope and can be
       attached to any of your cloud servers in a given region.
   * - Cloud Orchestration
     - None
     - Rackspace Cloud Orchestration helps you set up projects and servers
       with just a few clicks instead of lengthy installations. You can usually
       be up and running in less than five minutes, depending on the template
       that you choose and other factors. Cloud Orchestration provides
       templates for a LAMP stack to get your web server up and running
       quickly, a Minecraft server, and a WordPress blog, just to name a few.
   * - Hadoop
     - Provisioned public IP address and ServiceNet
     - Hadoop is an open-source project that provides a platform to store and
       process massive amounts of data. Hadoop uses the Map Reduce paradigm to
       split large tasks into many smaller chunks and executes them in
       parallel. Each of these tasks are executed close to the data in the
       Hadoop Distributed File System.
   * - Managed Operations support level
     - ServiceNet
     - Managed Operations provides support beyond Managed Infrastructure,
       including direct assistance with resizes, snapshots, host machine
       issues, adding and removing servers, and managing IP addresses.
       Rackspace provides support for specific software and server
       configurations on Cloud Servers with Managed Operations support.
   * - ObjectRocket
     - ServiceNet
     - The ObjectRocket platform is built for scalability, speed, and safety.
       It provides fully managed instances of MongoDB and Redis in data centers
       across the globe.

       RackConnect v3.0 is compatible with ObjectRocket Redis instances that
       have a ServiceNet IP address in the 10.188.0.0/15 range. If an instance
       has a ServiceNet IP address that is not in this range, contact
       ObjectRocket support.

       RackConnect v3.0 is compatible with MongoDB.

Compatibility with Rackspace dedicated network device offerings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following dedicated network device offerings are compatible with
RackConnect v3.0:

- Cisco ASA Firewalls
- Cisco ASA X Series Firewalls
- BIG-IP F5 Load Balancers
- Brocade Load Balancer

Compatibility with Rackspace dedicated offerings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following dedicated offerings are compatible with RackConnect v3.0.
Compatibility with dedicated offerings is based on network connectivity from
these offerings to and from your RackConnect v3.0 cloud networks. The correct
routes to allow this traffic can be set up by your Network Security team.

- **Managed Colocation**: Network devices in a Managed Colocation environment
  are supported only if the network devices are managed by the Network Security
  team. Customer-managed network devices are not supported.
- **Managed Storage**: The Managed Storage offering is compatible only with
  dedicated servers in a RackConnect configured dedicated environment. The
  Managed Storage offering cannot be used directly with cloud servers.
- **Managed Virtualization**: The Managed Virtualization offering is
  compatible.
- **Private Cloud**: The Private Cloud offering is compatible.
