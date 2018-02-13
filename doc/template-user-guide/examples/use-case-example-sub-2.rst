.. _use-case-example-sub-2:

======================================
Upload the manifest (use case example)
======================================

After you have uploaded the objects to be concatenated, you upload a
manifest object. Use a **PUT** operation, with the
following query parameter at the end of the manifest object name:

.. code::

    ?multipart-manifest=put

The body of the **PUT** operation is an ordered list of files in JSON
data format. Provide the following data for each segment:

-  ``path`` – The container and object name in the following format:
   ``containerName``/``objectName``

-  ``etag`` – The ``ETag`` header from the successful 201 response of
   the **PUT** operation that uploaded the segment. This is the MD5
   checksum of the segment object's data.

-  ``size_bytes`` – The segment object's size in bytes. This value must
   match the ``Content-Length`` of that object.

Following is an example containing three segment objects. This example
illustrates that in contrast to dynamic large objects, you can use a
number of containers and the object names do not have to conform to a
specific pattern.

**Example: Static large object manifest list**

.. code::

    [
            {
              "path": "/mycontainer/objseg1",
              "etag": "0228c7926b8b642dfb29554cd1f00963",
              "size_bytes": 1468006
            },
            {
              "path": "/mycontainer/pseudodir/seg-obj2",
              "etag": "5bfc9ea51a00b790717eeb934fb77b9b",
              "size_bytes": 1572864
            },
            {
              "path": "/other-container/seg-final",
              "etag": "b9c3da507d2557c1ddc51f27c54bae51",
              "size_bytes": 256
            }
    ]
