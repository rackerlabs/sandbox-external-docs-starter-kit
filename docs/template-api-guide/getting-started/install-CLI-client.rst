.. _install-CLI-client:

Install CLI clients
~~~~~~~~~~~~~~~~~~~

.. COMMENT: Customize this topic per API service. If Rackspace CLI support is
            available, then prefer people to use that. Otherwise, document the
            CLI relevant to the service.

.. important

   If people can use a command line interface (CLI) application to
   interact with your product or service, provide information and links to
   installation and reference documentation like the `sample CLI topic`.

   Decide whether you want this API guide to include examples in multiple
   formats, or stick with one. For example, the
   :rax-devdocs:`Managed DNS API <h#docs-cloud-dns>`
   documentation provides only cURL examples. While the
   the :rax-devdocs:`Cloud Servers` API <#docs-cloud-dns>` provides both
   cURL and CLI examples.

Sample CLI topic
-----------------
If you want to run the examples by using cURL instead of using the CLI, skip
this step and proceed to the next section "Sending API requests to
|product name|".

You can use the designate command-line interface (CLI) client with Managed DNS.
The  designate client is the CLI for the OpenStack DNS service API and its
extensions, and is  a plug-in to the OpenStack CLI.

..  note::

    You can specify the ``--debug`` parameter on any designate command to show
    the underlying  API request for the command. This is a good way to become
    familiar with the API requests.


#. Run the following commands on a Mac OS X or Linux distribution to install
   the OpenStack and designate clients:

   .. code::

      $ sudo pip install -U python-openstackclient
      $ sudo pip install -U python-designateclient

#. Create a CLI configuration file with the content as shown in the following
   example, name the file **clouds.yaml**, and place it under your current
   directory.

   .. code::

      clouds:
         prod:
           auth:
             auth_url: https://identity.api.rackspacecloud.com/v2.0/
             project_id: <RACKSPACE_CLOUD_TENANT_ID>
             username: <RACKSPACE_CLOUD_USERNAME>
             password: <RACKSPACE_CLOUD_PASSWORD>

   For more CLI configuration options, see the
   :os-docs:`Configuration
   <developer/python-openstackclient/configuration.html>`
   topic in the OpenStack client documentation.

#. Export the following environment variables manually, or update your
   ``.bash_profile`` or ``.bashrc`` files with these variables:

   .. code::

      $ export OS_CLOUD=prod

#. Run the following command to see if OpenStack/Designate CLI works:

   .. code::

      $ openstack --help

#. If you get an error such as
   ``Exception: Versioning for this project requires either an sdist tarball,
   or access to an upstream git repository. Are you sure that git is
   installed?``, run the following command:

   .. code::

      $ sudo pip install -U distribute

Now that your command line tool is ready, skip to
*Creating a zone with the CLI*.
