
======================
Document an API method
======================

.. COMMENT: This file provides an in-depth description of the possible
   sections of an API method file.  Discard this file as soon as you are
   comfortable.

This template provides structure, guidelines, and example content for
documenting a single HTTP request (for example, ``GET /v2.0/servers``). For
more guidelines, see https://github.rackspace.com/IX/docs-starter-kit/blob/master/api-guide-template/api-docs/api-reference/methods/http-request-documentation-guidelines.rst.
For an extended example, see
https://github.rackspace.com/IX/docs-starter-kit/blob/master/api-guide-template/api-docs/api-reference/methods/http-request-example-topic.rst.

Following the title, show the URI in a code block (no label). For example:

.. code::

    PATCH /v1.0/images/{imageId}

Follow the URI code block with a description. Include only information that
applies to the operation as a whole. Place specific information about a
parameter in the parameter table, later in the file. For example:

This operation updates the specified image. You can update only an image that
you own.

.. note::

      In all of the sections that follow, use the headings that are shown.
      The only heading that should be customized is the main title of the
      topic.

Request parameters
~~~~~~~~~~~~~~~~~~

Provide tables for header, URI, query, and request body parameters, as needed
(using the `list-table directive
<http://docutils.sourceforge.net/docs/ref/rst/directives.html#list-table>`_).
Precede each table with a basic introduction. Parameter tables include the
following columns: Name, Type, Description. For example:

The request has the following body parameters:

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - op
     - String
     - *(Required)* The operation to be executed: ``add``, ``remove``, or
       ``replace``. For more information about updating image properties, see
       the beginning of this operation section.
   * - value
     - String
     - The actual value to be added or replaced. This parameter is not required
       for the ``remove`` operation.

If there are no request body parameters, include the following sentence:

This operation does not accept a request body.

Request example
~~~~~~~~~~~~~~~

Provide a request example with an introductory sentence. Specify the type of
request, if applicable (such as JSON, HTTP, or cURL). In the example, include
the HTTP request header and show the body (if there is a body). For example:

The following example shows the JSON request for retrieving a list of flavors:

.. code::

    X-Auth-Token: f064c46a782c444cb4ba4b6434288f7c
    Content-Type: application/json
    Accept: application/json

.. code::

    [
        {"op": "replace", "path": "/name", "value": "Fedora 17"},
        {"op": "replace", "path": "/tags", "value": ["fedora", "beefy"]}
    ]

Response parameters
~~~~~~~~~~~~~~~~~~~

If you need to say something specific about the response, say it in this
section, and then include a table for body parameters, as needed (using the
`list-table directive
<http://docutils.sourceforge.net/docs/ref/rst/directives.html#list-table>`_).
Precede the table with a basic introduction. Parameter tables include the
following columns: Name, Type, Description. For example:

The response has the following body parameters:

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - id
     - String
     - The UUID of the image.
   * - name
     - String
     - The name of the image.
   * - status
     - String
     - The status of the image.

Response example
~~~~~~~~~~~~~~~~

Provide a response example with an introductory sentence. Specify the type of
response, if applicable (such as JSON, HTTP, or cURL). In the example, include
the HTTP request header and show the body (if there is a body). For example:

The following example shows the JSON response for the request:

.. code::

    {
      "id":"e7db3b45-8db7-47ad-8109-3fb55c2c24fd",
      "name":"Fedora 17",
      "status":"queued",
      "visibility":"public",
      "tags": ["fedora", "beefy"],
      "created_at":"2012-08-11T17:15:52Z",
      "updated_at":"2012-08-11T17:15:52Z",
      "self":"/v2/images/e7db3b45-8db7-47ad-8109-3fb55c2c24fd",
      "file":"/v2/images/e7db3b45-8db7-47ad-8109-3fb55c2c24fd/file",
      "schema":"/v2/schemas/image"
    }

Response codes
~~~~~~~~~~~~~~

Provide a `list table
<http://docutils.sourceforge.net/docs/ref/rst/directives.html#list-table>`_
with the possible response codes for the operation. Response code tables
include the following columns: Code, Name, Description. Following is an
example table with just a few possible codes.

This operation can have the following response codes:

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Code
     - Name
     - Description
   * - 200
     - Success
     - The request succeeded.
   * - 400
     - Error
     - A general error has occurred.
   * - 401
     - Unauthorized
     - The request has not been applied because it lacks valid authentication
       credentials for the target resource. The credentials are either expired
       or invalid.
   * - 403
     - Forbidden
     - The server understood the request but is not authorizing it.
