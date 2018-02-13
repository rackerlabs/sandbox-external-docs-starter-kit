.. _get-list-images-images:

List images
~~~~~~~~~~~

.. code::

    GET /images

Lists public virtual machine (VM) images.

This operation returns images you created, shared images that you accepted, and
standard images. For more information about standard images, see
:ref:`Standard images <standard-images>`. The response conforms to the schema
found in :ref:`Get images schema <get-images-schema-schemas-images>`.

This operation returns a subset of the larger collection of images and a link
that you can use to get the next set of images. Always check for the presence
of a ``next`` link and use it as the URI in a subsequent ``GET`` request.
Follow this pattern until a ``next`` link is no longer provided. The next link
preserves any query parameters that you send in your initial request. You can
use the ``first`` link to jump back to the first page of the collection. If you
prefer to paginate through images manually, use the ``limit`` and ``marker``
parameters.

The List Images operation accepts several types of query parameters that you
can use to filter the results of the returned collection.

A client can provide direct comparison filters by using most image attributes,
such as ``name=Ubuntu``, ``visibility=public``, and so on. A client cannot
filter on tags or anything defined as a link in the json-schema, such as
``self``, ``file``, or ``schema``.

You can use the ``size_min`` and ``size_max`` query parameters to perform
greater-than and less-than filtering of images based on their ``size``
attribute. The size is measured in bytes and refers to the size of an image
when it is stored on disk.

For example, sending a ``size_min`` filter of 1048576 and size_max of 4194304
filters the container to include only images that are between 1 MB and 4 MB in
size.

You can sort the results of this operation by using the ``sort_key`` and
``sort_dir`` parameters. The API uses the natural sorting of whatever image
attribute is provided as the ``sort_key``.

.. note::
   Public images may reach end-of-life and be removed from the base image list.
   The :how-to:`Hidden Base Images <hidden-base-images>` article lists images
   which have been removed from the base images list but which may still be
   available.


Request
-------

The request has the following query parameters.

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - limit
     - String
     - Requests a specific page size. Expect a response to a limited request
       to return between zero items and the number specified. The typical
       pattern for using the ``limit`` and ``marker`` parameters is to make an
       initial limited request and then to use the ID of the last image from
       the response as the ``marker`` parameter in a subsequent limited
       request.
   * - marker
     - String
     - Requests a specific page size. Expect a response to a limited request
       to return between zero items and the number specified. The typical
       pattern for using the ``limit`` and ``marker`` parameters is to make an
       initial limited request and then to use the ID of the last image from
       the response as the ``marker`` parameter in a subsequent limited
       request.
   * - name
     - String
     - Specifies the name of the image as a string.
   * - visibility
     - String
     - Specifies image visibility as either ``public``, ``private``, or
       ``shared``.
   * - owner
     - String
     - Specifies images shared with the user by the specified tag.


This operation does not accept a request body.

**Example Request: header**

The following example shows the header information.

.. code::

   X-Auth-Token: f064c46a782c444cb4ba4b6434288f7c
   Content-Type: application/json
   Accept: application/json


Response
--------

The request has the following body parameters.

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - **images**\.[]
     - Array
     - An array of images in the list.
   * - images.\ **id**
     - String
     - The UUID of the image.
   * - images.\ **name**
     - String
     - The name of the image.
   * - images.\ **status**
     - String
     - The status of the image. For possible image statuses,
       see :ref:`Statuses <statuses>`.
   * - images.\ **visibility**
     - String
     - Specifies image visibility as ``public``, ``private``, or ``shared``.
   * - images.\ **size**
     - String
     - The size of the image in bytes.
   * - images.\ **checksum**
     - String
     - The checksum of this image.
   * - images.\ **self**
     - String
     - The link to the image.
   * - images.\ **file**
     - String
     - The image file.
   * - **first**
     - String
     - The URI for the first image in the list.
   * - **first**
     - String
     - The URI for the next image in the list.
   * - **last**
     - String
     - The URI for the last image in the list.


**Example response: JSON**

The following example shows the JSON response for the request.

.. code::

   Status Code: 200 OK
   Content-Length: 4543
   Content-Type: application/json
   Date: Wed, 03 Dec 2014 17:13:30 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)
   Via: 1.1 Repose (Repose/2.12)
   x-compute-request-id: req-7b7ffed2-9b1f-46a8-a478-315518d35387


   {
      "images":
      [
         {
            "id":"da3b75d9-3f4a-40e7-8a2c-bfab23927dea",
            "name":"cirros-0.3.0-x86_64-uec-ramdisk",
            "status":"active",
            "visibility":"public",
            "size":2254249,
            "checksum":"2cec138d7dae2aa59038ef8c9aec2390",
            "self":"/v2/images/da3b75d9-3f4a-40e7-8a2c-bfab23927dea",
            "file":"/v2/images/da3b75d9-3f4a-40e7-8a2c-bfab23927dea/file"},
         {
            "id":"0d5bcbc7-b066-4217-83f4-7111a60a399a",
            "name":"cirros-0.3.0-x86_64-uec",
            "status":"active",
            "visibility":"public",
            "size":25165824,
            "checksum":"2f81976cae15c16ef0010c51e3a6c163",
            "self":"/v2/images/0d5bcbc7-b066-4217-83f4-7111a60a399a",
            "file":"/v2/images/0d5bcbc7-b066-4217-83f4-7111a60a399a/file"}
      ],
      "first":"/v2/images?limit=3",
      "next":"/v2/images?limit=3&marker=e6421c88-b1ed-4407-8824-b57298249091",
      "schema":"/v2/schemas/images"
   }

Response codes
--------------

This operation can have the following response codes.

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
   * - 405
     - Method Not Allowed
     - The method received in the request line is known by the origin server
       but is not supported by the target resource.
   * - 413
     - Over Limit
     - The number of items returned is above the allowed limit.
   * - 415
     - Bad Media Type
     - This error might result if the wrong media type is used in the cURL
       request.
   * - 500
     - API Fault
     - The server encountered an unexpected condition that prevented it from
       fulfilling the request.
   * - 503
     - Service Unavailable
     - The server is currently unable to handle the request because of a
       temporary overload or scheduled maintenance, which will likely be
       alleviated after some delay.
