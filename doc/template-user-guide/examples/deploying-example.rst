.. _deploying-example-ug:

=====================================================
Run the Object Storage playbooks (deployment example)
=====================================================

The Ansible Object Storage playbooks prepare the target hosts for Object
Storage services and depend on the values in the ``swift.yml`` file.

Before running the stand-alone Object Storage playbooks, ensure that the
configuration files have been updated.

#. Change to the ``/opt/rpc-openstack/openstack-ansible/playbooks``
   directory.

#. To install Object Storage and the necessary components of OpenStack, run
   the ``setup-everything.yml`` playbook:

   .. code-block:: console

      $ openstack-ansible setup-everything.yml
