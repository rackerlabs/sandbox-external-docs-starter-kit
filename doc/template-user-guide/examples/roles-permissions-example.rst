.. _roles-permissions-example-ug:

===============================
Roles and permissions (example)
===============================

Because vCloud Director is a cloud portal that abstracts the resources of
the underlying RPC-VMware environment, your use of the underlying
RPC-VMware services is limited to read-only access to the vCenter Server
user interface and APIs. Although the features listed in the RPC-VMware
handbook are still available, you can consume those features only as
they are enabled in the customer role of the vCloud Director services or
by opening a ticket with Rackspace support to make modifications to the
underlying RPC-VMware services and environment.

Predefined roles
~~~~~~~~~~~~~~~~

To implement the separation of customer and Rackspace duties in
RPC-VMware, Rackspace uses built-in roles in vCloud Director. Rackspace
assigns you a maximum permission role (Organization Administrator) and
any lesser privileged roles that you request for specific users or
groups.

Predefined roles and the permissions that they contain are available in all
organizations. All of the roles in the following table are available
for the customer. Rackspace support has the System Administrator role at the
System organization level, which is used to manage the vCloud Director
configurations.

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - Role
     - Description
   * - Organization Administrator
     - After creating an organization, Rackspace assigns the role of
       Organization Administrator to the user or group provided by the
       customer. Users with the Organization Administrator role can use the
       vCloud Director Web console or the vCloud API to manage users and
       groups in their organization and assign them roles, including the
       Organization Administrator role. A user with this role can use the
       vCloud API to create or update role objects that are local to the
       organization. Roles created or modified by an organization
       administrator are not visible to other organizations.
   * - Catalog Author
     - The permissions associated with the Catalog Author role allow a user to
       create and publish catalogs.
   * - vApp Author
     - The permissions associated with the vApp Author role allow a user to use
       catalogs and create vApps.
   * - vApp User
     - The permissions associated with the vApp User role allow a user to use
       existing vApps.
   * - Console Access Only
     - The permissions associated with the Console Access Only role allow a
       user to view VM states and properties and to use the guest OS.

Permissions
~~~~~~~~~~~~

Customers have the permissions to create, delete, and manage VMs within their
vCloud Director. Rackspace manages the vCloud Director Server, vCenter
Server, and ESXi hosts. Customers have limited permissions on hosts and
servers. The following tables detail the vCloud Director permissions for
the predefined roles that can be assigned for customer use.

**Permissions associated with catalogs**

.. list-table::
   :widths: 25 25 10 10 10 10 10
   :header-rows: 1

   * - Permission
     - Description
     - Admin
     - Catalog Author
     - vApp Author
     - vApp User
     - Console Access Only
   * - Catalog: Add vApp from My Cloud
     - Permission to add a vApp to a catalog from My Cloud.
     - X
     - X
     - X
     -
     -
   * - Catalog: Change Owner
     - Permission to change the owner of a catalog.
     - X
     -
     -
     -
     -
   * - Catalog: Create or delete a Catalog
     - Permission to create and delete catalogs.
     - X
     - X
     -
     -
     -
   * - Catalog: Edit Catalog Properties
     - Permission to edit catalog properties.
     - X
     - X
     -
     -
     -
   * - Catalog: Allow External Publishing or Subscriptions for the Catalogs
     - Permission to publish catalogs for external consumption and to
       subscribe to external catalog feeds.
     - X
     - X
     -
     -
     -
   * - Catalog: Share a Catalog to Users or Groups within Current Organization
     - Permission to share catalogs to users and groups in the same
       organization.
     - X
     - X
     -
     -
     -
   * - Catalog: View Private and Shared Catalogs within Current Organization
     - Permission to view both private and shared catalogs in the organization.
     - X
     - X
     - X
     -
     -
   * - Catalog: View Shared Catalogs from Other Organizations
     - Permission to view catalogs shared from other organizations.
     - X
     -
     -
     -
     -

**Permissions associated with independent disks**

.. list-table::
   :widths: 25 25 10 10 10 10 10
   :header-rows: 1

   * - Permission
     - Description
     - Admin
     - Catalog Author
     - vApp Author
     - vApp User
     - Console Access Only
   * - Disk: Create
     - Permission to create independent disks.
     - X
     - X
     - X
     -
     -
   * - Disk: Delete
     - Permission to delete independent disks.
     - X
     - X
     - X
     -
     -
   * - Disk: Edit Properties
     - Permission to edit the properties of an independent disk.
     - X
     - X
     - X
     -
     -
   * - Disk: View Properties
     - Permission to view the properties of an independent disk.
     - X
     - X
     - X
     - X
     -
