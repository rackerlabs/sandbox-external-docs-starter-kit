.. _components-example-ug:

====================
Components (example)
====================

Rackspace Private Cloud powered by VMware (RPC-VMware) is composed of a VMware
vSphere cluster for management (management cluster) that is managed by a
Rackspace back-end vCenter Server, and one or more VMware vSphere clusters
managed by your private cloud vCenter Server for running your workloads
(compute clusters). RPC-VMware provides core components and, optionally, one or
more add-on components that you select. Each of these add-on components might
require management services that run in the two-node, highly available
management cluster and might also have services components that run on your
compute cluster. These management services are managed and maintained by
Rackspace.

The following table describes the management services for the core components
of RPC-VMware. Your private cloud includes these services.

**Management services for core components**

.. list-table::
   :widths: 30 70
   :header-rows: 1

   * - Service
     - Description
   * - Management cluster
     - A two-node hypervisor cluster that uses a separate datastore dedicated
       to the management services VMs. This hypervisor cluster and the VMs
       running on it are managed by a back-end vCenter Server that is
       accessible only to Rackspace for the purpose of operating and
       maintaining your environment.
   * - Management network
     - A single VLAN segment behind your firewall that is used exclusively for
       communication of the management components with the compute cluster.
   * - vCenter Server virtual appliance
     - Provides centralized visibility, proactive management and extensibility
       for VMware vSphere from a single console. vCenter Server is accessible
       from the vSphere client and the vSphere API.
   * - Virtual Machine Recovery (VMR) virtual appliance
     - Enables image-based backup of the management cluster VMs. It allows
       Rackspace to quickly recover management cluster VMs. This VMR appliance
       is for use only by Rackspace and does not back up any of the VMs created
       by the customer on the compute cluster. No customer access is provided
       to the VMR appliance.
   * - VMware vSphere Update Manager™ for Windows Server
     - Automates patch management and eliminates manual tracking and patching
       of vSphere hosts. It compares the state of vSphere
       hosts with baselines and then updates and patches hosts to enforce
       compliance. Rackspace uses this system to maintain dedicated VMware
       services. No customer access is provided.

The following table describes the management services for the optional add-on
components of RPC-VMware that require the provisioning of additional services
on the management cluster. Your private cloud might include one or more of
these services if you have selected any of the add-on components listed.

**Management services for optional components**

.. list-table::
   :widths: 30 70
   :header-rows: 1

   * - Service
     - Description
   * - NSX® Manager virtual appliance
     - The NSX Manager is included if your RPC-VMware cloud includes the
       NSX add-on feature. The NSX Manager provides the graphical user
       interface (GUI) and the REST APIs for creating, configuring, and
       monitoring virtual network components.
   * - vRealize® Operations Manager™ virtual appliance
     - The vRealize Operations Manager virtual appliance is included if your
       RPC-VMware cloud includes the vRealize Operations Manager virtual
       appliance add-on feature. The vRealize Operations Manager virtual
       appliance provides all of vRealize Operations Manager functionality
       such as checking the health of the hosted VMware environment,
       performing capacity planning, and proactively eliminating performance
       bottlenecks. It is accessible via a web interface.
   * - vRealize Automation™ virtual appliance and IaaS server
     - The vRealize Automation virtual appliance and IaaS server arei included
       if your RPC-VMware cloud includes the vRealize Automation add-on
       feature. The vRealize Automation add-on feature provides cloud
       automation, such as the ability to provide VMs and applications as
       on-demand services. The vRealize Automation appliance provides a
       management user interface, a single sign-on (SSO) service, and a
       vRealize Orchestrator instance for vRealize Automation. It is accessible
       via a web interface and a REST API. The
       vRealize Automation IaaS server enables the rapid modeling and
       provisioning of servers in the private cloud as directed by the vRealize
       Automation appliance. It includes workers and agents to integrate with
       vSphere and other infrastructure components.
   * - vRealize Business™ for Cloud virtual appliance
     - The vRealize Business for Cloud virtual appliance is included if your
       RPC-VMware cloud includes the vRealize Business
       for Cloud add-on feature. vRealize Business for Cloud is a cloud
       planning, budgeting, and cost visibility tool that helps to make
       decisions for your private cloud. It is used to establish costs and
       pricing, make cost base decisions, and provide information for
       chargeback. It is accessible via a web client and a public API.
