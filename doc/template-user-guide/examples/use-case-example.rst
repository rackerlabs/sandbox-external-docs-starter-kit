.. _use-case-example:

=================================================
Creating a static large object (use case example)
=================================================

Static large object support is similar to dynamic large object
support because it enables you to upload many objects concurrently
and later download them as a single object. However, unlike dynamic
large object support, static large object support does not rely on the
eventual consistency model for the container listings. Instead, it
uses a user-defined manifest of the object
segments.

The benefits of using static large objects are as follows:

-  The objects that are uploaded and downloaded can be in different
   containers, which can improve performance.

-  There is an explicit list of segments, instead of an implied list as
   with dynamic large objects.

You create a static large object by performing the following steps:

#. Divide your content into pieces and create (upload) a segment object
   to contain each piece. You must record the ``ETag`` response header
   returned by the **PUT** operation. Alternatively, you can calculate
   the MD5 checksum of the segment prior to uploading and include this
   in the ``ETag`` request header. Doing so ensures that the upload
   cannot corrupt your data.

   For detailed information, see
   :ref:`Upload the segments<use-case-example-sub-1>`.

   .. note::

     The maximum number of segment objects per static large object is
     1000. Each segment, except for the final one, must be at least 1 MB.

#. Create a manifest object by listing the name of each segment object
   along with its size and MD5 checksum, in order. You indicate that
   this is a manifest object by including the
   ?\ ``multipart-manifest=put`` query string at the end of the manifest
   object name.

   For detailed information, see
   :ref:`Upload the manifest<use-case-example-sub-2>`.
