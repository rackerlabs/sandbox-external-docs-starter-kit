.. _product-specific-general-api-content:

===================
Content compression
===================

.. COMMENT: Use this topic to provide information that is relevant for your
   product. Create more topic files as needed and add to the index.rst
   Be sure to change the label at the top and the title to fit your content.
   If you have no special content, delete this file and the index entry.

Request and response body data can be encoded with gzip compression to
accelerate interactive performance of API requests and responses. Compression
is controlled by using the ``Accept-Encoding`` header in the request from the
client and is indicated by the ``Content-Encoding`` header in the server
response. Unless the header is explicitly set, encoding is disabled.

+-------------------+------------------+-------+
| Header type       | Name             | Value |
+===================+==================+=======+
| HTTP/1.1 Request  | Accept-Encoding  | gzip  |
+-------------------+------------------+-------+
| HTTP/1.1 Response | Content-Encoding | gzip  |
+-------------------+------------------+-------+
