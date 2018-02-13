.. _planning-example-ug:

==================
Planning (example)
==================

This topic describes what you need to know and do before you run the playbooks
that install Object Storage.

.. contents::
   :depth: 1
   :local:
   :backlinks: none

Installation architecture
~~~~~~~~~~~~~~~~~~~~~~~~~

The following diagram shows one possible configuration for a minimal
installation of Object Storage. In this example, each storage node is a
separate zone in the ring. At a minimum, five zones are recommended. To
increase reliability and performance, you can add additional proxy nodes.

.. figure:: ../figures/swift_install_arch.png
   :alt: Object Storage architecture

Configure and mount storage devices
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Before you can install Object Storage for RPCO, you must configure and mount
the storage devices. Object Storage for RPCO requires a minimum of three object
storage devices with mounted storage drives.

The example commands in this procedure assume that the storage devices are
labeled ``sdc`` through ``sdg``.

#. Determine the storage devices on the node to use for Object Storage.

#. Format each of these devices with XFS. While formatting the devices, add a
   unique label for each device.

   ..  note::

       Without labels, a failed drive can cause mount points to shift and
       data to become inaccessible.

   For example, create the file systems on the devices by using the
   **mkfs** command:

   .. code-block:: console

       $ apt-get -y install xfsprogs

       $ mkfs.xfs -f -i size=1024 -L sdc /dev/sdc
       $ mkfs.xfs -f -i size=1024 -L sdd /dev/sdd
       $ mkfs.xfs -f -i size=1024 -L sde /dev/sde
       $ mkfs.xfs -f -i size=1024 -L sdf /dev/sdf
       $ mkfs.xfs -f -i size=1024 -L sdg /dev/sdg

#. Add the mount locations to the ``/etc/fstab`` file so that the
   storage devices are remounted on boot. The following example mount
   options are recommended when using XFS.

   ..  note::

       Finish all modifications to the ``/etc/fstab`` file before mounting
       the new file systems created within the storage devices.

   .. code-block:: ini

       LABEL=sdc /srv/node/sdc xfs noatime,nodiratime,nobarrier,logbufs=8 0 0
       LABEL=sdd /srv/node/sdd xfs noatime,nodiratime,nobarrier,logbufs=8 0 0
       LABEL=sde /srv/node/sde xfs noatime,nodiratime,nobarrier,logbufs=8 0 0
       LABEL=sdf /srv/node/sdf xfs noatime,nodiratime,nobarrier,logbufs=8 0 0
       LABEL=sdg /srv/node/sdg xfs noatime,nodiratime,nobarrier,logbufs=8 0 0

#. Create the mount points for the devices by using the **mkdir** command:

   .. code-block:: console

       $ mkdir -p /srv/node/sdc
       $ mkdir -p /srv/node/sdd
       $ mkdir -p /srv/node/sde
       $ mkdir -p /srv/node/sdf
       $ mkdir -p /srv/node/sdg

   The mount point is referenced as the ``mount_point`` parameter in the
   ``swift.yml`` file (``/etc/openstack_deploy/conf.d/swift.yml``).

#. Mount the storage devices by using the **mount** command:

   .. code-block:: console

       $ mount /srv/node/sdc
       $ mount /srv/node/sdd
       $ mount /srv/node/sde
       $ mount /srv/node/sdf
       $ mount /srv/node/sdg

For the devices mounted in the preceding steps, the mount locations would be as
follows:

.. list-table::
   :widths: 50 50
   :header-rows: 1

   * - Device
     - Mount location
   * - /dev/sdc
     - /srv/node/sdc
   * - /dev/sdd
     - /srv/node/sdd
   * - /dev/sde
     - /srv/node/sde
   * - /dev/sdf
     - /srv/node/sdf
   * - /dev/sdg
     - /srv/node/sdg

The entry in the ``swift.yml`` for the mounted devices would be as follows:

.. code-block:: ini

    #    drives:
    #        - name: sdc
    #        - name: sdd
    #        - name: sde
    #        - name: sdf
    #        - name: sdg
    #    mount_point: /srv/node

Create networks
~~~~~~~~~~~~~~~

The next step in preparing for the installation of Object Storage for RPCO is
creating the networks that are needed. Object Storage for RPCO requires the
``br-storage`` and ``br-mgmt`` networks. These networks are specified in the
``provider_networks`` section of the
``/etc/openstack_deploy/openstack_user_config.yml`` file.

#. Open the ``/etc/openstack_deploy/openstack_user_config.yml`` file for
   editing.

#. In the ``provider_networks`` section, add the following network information:

   .. code-block:: ini

       # provider_networks
       #   - network:
       #       container_bridge: "br-mgmt"
       #       container_interface: "eth1"
       #       ip_from_q: "container"
       #       group_binds:
       #         - all_containers
       #         - all hosts
       #   - network:
       #       container_bridge: "br-storage"
       #       container_interface: "eth2"
       #       ip_from_q: "storage"
       #       group_binds:
       #         - glance_api
       #         - cinder_api
       #         - cinder_volume
       #         - nova_compute
       #         - swift_proxy
