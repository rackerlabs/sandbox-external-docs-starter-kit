.. _api-example-2-ug:

============================
API (example of API content)
============================

The RackConnect API enables you to access certain read-only information about
your cloud servers and their RackConnect configuration. The RackConnect API is
available to all customers who can manage their RackConnect configurations
through the `MyRackspace portal <https://my.rackspace.com/>`_ interface.

You can use the RackConnect API to access the following information:

- When you are scripting or automating any post-server-build configuration
  tasks, you can query the API to learn when RackConnect automation is done
  configuring your server.

- When you are setting up the network configuration manually on your cloud
  server, the API can return the gateway IP address to use as the default
  gateway on your server. You can use this address to correctly configure the
  cloud server network stack.

- When you want to determine the specific actions that the automation will
  perform against one of your cloud servers, you can view the status of each
  automation feature for a specific server.

Service endpoints
~~~~~~~~~~~~~~~~~

The RackConnect API is exposed via regional endpoints. Use the endpoint
that matches the region where your cloud server resides:

-   https://dfw.api.rackconnect.rackspace.com
-   https://hkg.api.rackconnect.rackspace.com
-   https://iad.api.rackconnect.rackspace.com
-   https://lon.api.rackconnect.rackspace.com
-   https://ord.api.rackconnect.rackspace.com
-   https://syd.api.rackconnect.rackspace.com

Authentication
~~~~~~~~~~~~~~

The RackConnect API authenticates all requests based on the source IP
address that is initiating the request. The API endpoints are exposed
only on the private (ServiceNet) network, so the private (ServiceNet)
network IP address of your cloud server is used to determine the source
of the request and to respond with the appropriate information.

API responses are limited to information about the specific cloud server from
which you are querying. Hypervisor-level protections are in place that prevent
these IP addresses from being spoofed, ensuring that the instance making the
request to the API endpoint is, in fact, your cloud server.

**Note:** You cannot query the RackConnect API from outside of your cloud
server.

Rate limits
~~~~~~~~~~~

There is a limit of 30 requests per minute from each of your cloud servers. If
you exceed the number of allowed requests per minute, you receive an
``HTTP 403 (Forbidden)`` response code. The counter resets each minute.

Operations
~~~~~~~~~~

The following operations are supported by the API. The ``format`` query
string parameter is optional on each request. If it is not supplied, the
default response format is used.

.. contents::
   :depth: 1
   :local:
   :backlinks: none

Show automation status of server
--------------------------------

.. code::

    GET /v1/automation_status?format={format}

Returns the automation status of the cloud server (DEPLOYING, DEPLOYED, or
FAILED).

The possible response formats are text (default), JSON, and XML.

The expected HTTP response code is 200 (Success).

Show automation status of server and tasks
------------------------------------------

.. code::

    GET /v1/automation_status/details?format={format}

Returns the automation status of the cloud server (DEPLOYING, DEPLOYED, or
FAILED) and an array of cloud server tasks with their associated statuses.

The possible response formats are JSON (default) and XML.

The expected HTTP response code is 200 (Success).

Show the gateway IP address
---------------------------

.. code::

    GET /v1/gateway_ip?format={format}

Returns the gateway IP address for the cloud server.

The possible response formats are text (default), JSON, and XML.

The expected HTTP response code is 200 (Success). If the gateway IP address
has not yet been assigned, an HTTP 404 (Not Found) response code is returned.

Show automation features and their statuses
-------------------------------------------

.. code::

    GET /v1/automation_features?format={format}

Returns a collection of automation features and their associated statuses for
the cloud server.

The possible response formats are JSON (default) and XML.

The expected HTTP response code is 200 (Success).

Request and response example
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following example uses cURL to retrieve the automation status.
Alternatively, you can use a web browser to query the RackConnect API.

**Request**

.. code::

    $ curl https://dfw.api.rackconnect.rackspace.com/v1/automation_status?format=text

**Response**

.. code::

    DEPLOYED
