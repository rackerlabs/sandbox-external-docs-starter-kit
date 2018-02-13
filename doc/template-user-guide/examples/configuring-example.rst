.. _configuring-example-ug:

=====================
Configuring (example)
=====================

To configure stand-alone Object Storage for Rackspace Private Cloud Powered By
Openstack (RPCO), you update the following files:

-  ``/etc/openstack_deploy/openstack_user_config.yml``

-  ``/etc/openstack_deploy/user_osa_variables_overrides.yml``

-  ``/etc/openstack_deploy/conf.d/swift.yml``

Update the stand-alone Object Storage configuration files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. In the ``openstack_user_config.yml`` file, set the ``identity_hosts`` and
   ``shared-infra_hosts`` entries to the following values to set up the
   Identity and infrastructure services. The following example shows ``node1``
   through ``node3``. The values must be adjusted for all ``identity_hosts``
   and ``shared-infra_hosts`` entries.

   .. code-block:: ini

       # identity_hosts:
       #   node1:
       #     ip: 192.168.100.1
       #   node2:
       #     ip: 192.168.100.2
       #   node3:
       #     ip: 192.168.100.3
       # shared-infra_hosts:
       #   node1:
       #     ip: 192.168.100.1
       #   node2:
       #     ip: 192.168.100.2
       #   node3:
       #     ip: 192.168.100.3

#. In the ``user_osa_variables_overrides.yml`` file, update the
   following user variables.

   ..  note::

       The ``rackspace_cloud`` variables are needed only if you are using
       the Rackspace Monitoring service.

   .. code-block:: ini

       # container_openstack_password:
       # keystone_auth_admin_password:
       # keystone_auth_admin_token:
       # keystone_container_mysql_password:
       # keystone_service_password:
       # memcached_encryption_key:
       # mysql_debian_sys_maint_password:
       # mysql_root_password:
       # rabbitmq_cookie_token:
       # rabbitmq_password:
       # rackspace_cloud_api_key:
       # rackspace_cloud_auth_url:
       # rackpace_cloud_password:
       # rackspace_cloud_tenant_id:
       # rackspace_cloud_username:
       # rackspace_cloudfiles_tenant_id:
       # rpc_support_holland_password:
       # swift_container_mysql_password:
       # swift_hash_path_prefix:
       # swift_hash_path_suffix:
       # swift_service_password:
       # swift_dispersion_user:
       # swift_dispersion_password:
       # service_syslog:
       # galera_root_password:

#. In the ``/etc/openstack_deploy/conf.d/swift.yml`` file, update the
   ``global_overrides`` values as shown in the following example. The
   parameters are explained following the example.

   .. code-block:: ini

       # global_overrides:
       #   swift:
       #     part_power: 8
       #     weight: 100
       #     min_part_hours: 1
       #     repl_number: 3
       #     storage_network: 'br-storage'
       #     replication_network: 'br-repl'
       #     drives:
       #       - name: sdc
       #       - name: sdd
       #       - name: sde
       #       - name: sdf
       #     mount_point: /mnt
       #     account:
       #     container:
       #     storage_policies:
       #       - policy:
       #           name: gold
       #           index: 0
       #           default: True
       #       - policy:
       #           name: silver
       #           index: 1
       #           repl_number: 3
       #           deprecated: True


   ``part_power``
    Set the partition power value based on the total amount of
    storage that the entire ring will use.

   ``weight``
    The default weight is 100. If the drives are different sizes, set
    the weight value to avoid uneven distribution of data. For
    example, a 1 TB disk would have a weight of 100, while a 2 TB
    drive would have a weight of 200.

   ``min_part_hours``
    The default value is 1. Set the minimum partition hours to the
    amount of time to lock a partition's replicas after a partition
    has been moved. Moving multiple replicas at the same time might
    make data inaccessible. This value can be set separately in the
    ``swift``, ``container``, ``account``, and ``policy`` sections,
    with the value in other sections superseding the value in the
    ``swift`` section.

   ``repl_number``
    The default value is 3. Set the replication number to the number
    of replicas of each object. This value can be set separately in
    the ``swift``, ``container``, ``account``, and ``policy`` sections,
    with the value in the other sections superseding the value in the
    ``swift`` section.

   ``storage_network``
    By default, the swift services will listen on the default
    management IP address. Optionally, specify the interface of the storage
    network.

   ``replication_network``
    Optionally, specify a dedicated replication network interface, so
    dedicated replication can be set up. If this value is not
    specified, no dedicated replication network is set.

   ``drives``
    Set the default drives per host. This is useful when all hosts
    have the same drives. These values can be overridden for each host.

   ``mount_point``
    Set the ``mount_point`` value to the location where the swift
    drives are mounted. For example, with a mount point of ``/mnt``
    and a drive of ``sdc``, a drive is mounted at ``/mnt/sdc`` on the
    swift host. This value can be overridden for each host.

   ``storage_policies``
    Storage policies determine on which hardware data is stored, how
    the data is stored across that hardware, and in which region the
    data resides. Each storage policy must have an unique ``name``
    and a unique ``index`` value. There must be a storage policy with an
    index of 0 in the ``swift.yml`` file to use any legacy containers
    created before storage policies were instituted.

   ``default``
    Set the ``default`` value to ``yes`` for at least one policy. This policy
    is the default storage policy for any non-legacy containers that are
    created.

   ``deprecated``
    Set the ``deprecated ``value to ``yes`` to turn off storage policies.

#. In the ``/etc/openstack_deploy/conf.d/swift.yml`` file, update the Object
   Storage proxy hosts values by setting the IP address of the hosts to which
   Ansible will connect to deploy the swift-proxy containers. The
   ``swift-proxy_hosts`` value should match the infra nodes.

   .. code-block:: ini

       # swift-proxy_hosts:
       #   infra-node1:
       #     ip: 192.0.2.1
       #   infra-node2:
       #     ip: 192.0.2.2
       #   infra-node3:
       #     ip: 192.0.2.3

#. Verify that the ``swift.yml`` file is in the
   ``/etc/openstack_deploy/conf.d/`` folder.

Allow Identity users to use Object Storage
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Users with the ``_member_`` role are authorized Identity (keystone)
users. You can allow these users to create containers and upload
objects to Object Storage by opening the
``user_osa_variables_overrides.yml`` file for editing and setting
``swift_allow_all_users`` to ``True``.

..  note::

    If this value is ``False``, then by default, only users with the
    ``admin`` or ``swiftoperator`` role are allowed to create containers or
    manage projects.

When the back-end type for the Image service (glance) is set to
``swift``, the Image service can access the Object Storage cluster
regardless of whether this value is ``True`` or ``False``.
