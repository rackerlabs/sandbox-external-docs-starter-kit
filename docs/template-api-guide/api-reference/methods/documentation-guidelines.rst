API methods documentation guidelines
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. COMMENT:  Discard this file once you have used these guidelines to create
   a few method files for your product.


This document provides guidelines for documenting a single HTTP
request (for example, ``GET /v2.0/servers``). It provides the topic
structure and guidelines for content and style within each section.

.. note::

     Headings in parentheses indicate parts of a section that do not have a
     heading in the template. For an example of the template with content that
     follows these guidelines, see
     https://github.rackspace.com/IX/docs-starter-kit/blob/master/api-guide-template/api-docs/api-reference/methods/http-request-example-topic.rst.

Title
-----

Begin the title with an imperative verb. In general, the following methods
equate to the following verbs:

- POST = Create
- GET = Retrieve
- PUT or PATCH = Update
- DELETE = Delete

Guidelines:

- Insert articles to make the title more readable. For example, "Create a
  server" rather than "Create server."
- Use sentence-style capitalization.
- Ensure that the title is unique within a given set of documentation.
  Duplicate titles adversely affect linking.

(URI)
-------

Immediately following the title, show the URI in a code block (no label).
Following are some examples:

``GET /v1.0/{projectId}/{container}``

``GET /v3.0/{projectId}/cloud_networks/{networkId}``

``DELETE /v1.0/{projectId}/services/{serviceId}/assets``

Guidelines:

- Start the route with the method (for example, ``GET``).
- Begin the URI with a slash and then the version number (for example,
  ``/v3.0``). Show the version number as *v.r*.
- If the account number/tenant ID/project ID is required in the URI, show it
  with the placeholder ``{projectId}``.
- Use the following guidelines for placeholders:

  - Enclose placeholders in curly braces.
  - Use lowercase letters except when showing a multiple-word placeholder. To
    show a multiple-word placeholder, do not separate the words with spaces or
    symbols. To distinguish the words in the placeholder, capitalize only the
    first letter of each word after the first word (called camelCase). Do not
    capitalize the first word. For example, ``{projectId}``.

(introduction with brief description)
-------------------------------------

Follow the URI code block with a description (no heading). Start with "This
operation …"

Include only necessary information that applies to the operation as a whole.
Specific information about a parameter should go in the parameter table.
However, if there is more parameter information than can be shown in the
table, place it after the introduction.

(parameter details)
-------------------

Optionally, follow the introduction with details about one or more parameters.
Parameter descriptions belong in the parameters tables (see those sections),
but those tables are not designed to contain multiple paragraphs and extended
details. If you have details to provide that require extra paragraphs or
lists, use this part of the section.

Request
-------

This is the first main section and heading after the title. Use the title
"Request."

This section includes tables for header, URI, query, and request body
parameters, as needed. Precede each table with a basic introduction, such as
"The request has the following ___ parameters." Use the `list-table directive
<http://docutils.sourceforge.net/docs/ref/rst/directives.html#list-table>`_
to create the table.

Parameter tables include the following columns:

- **Name**: Show parameters in regular font, with no surrounding braces
  (for URI placeholders). If it is a subparameter, show its parent parameter,
  too, and bold the subparameter. For example, network. **name**.

- **Type**: Use the full word, with an initial capital. For example:
  String, Boolean

- **Description**: If the parameter is required, start the description with
  *(Required)*. Provide meaningful information about the parameter; don't
  just repeat the parameter’s name. Start the description with an initial
  phrase, punctuated and capitalized as a sentence. For example: "The unique
  identifier of the project." Follow the phrase with a sentence or two, as
  needed. This description should be fairly short. If you have details to
  provide that require extra paragraphs or lists, use the optional "parameter
  details" section following the introduction.

These tables do not need titles.

Organize the parameters and label them as directed in the `style guidelines`_.

If there are no request body parameters, include the header in the request
example, and include the following sentence:
"This operation does not accept a request body."

.. _style guidelines: https://github.com/rackerlabs/docs-rackspace/blob/master/
   doc/style-guide/m-z-style-guidelines.md#parameters

Request example
---------------

This section starts with **Example request: JSON**  (or the language of the
sample, or "header", if there is not body) and contains the code example with
an introductory sentence, such as
"The following example shows the JSON request for retrieving a list of
flavors."

Specify the type of request, if applicable (such as JSON, XML, or cURL).

In the example, include the HTTP request header and show the body (if there
is a body).

Include as many examples as necessary, each preceded by an introductory
sentence.

Response
--------

If you need to say something specific about the response, say it in this
section, and then include a table for body parameters, as needed. Precede the
table with a basic introduction, such as "The response has the following body
parameters." Use the `list-table directive
<http://docutils.sourceforge.net/docs/ref/rst/directives.html#list-table>`_
to create the table.

Parameter tables include the following columns:

- **Name**: Show parameters in regular font, with no surrounding braces
  (for URI placeholders). If it is a subparameter, show its parent parameter,
  too, and bold the subparameter. For example, network.**name**.

- **Type**: Use the full word, with an initial capital. For example: String,
  Boolean

- **Description**: Provide meaningful information about the parameter; don't
  just repeat the parameter’s name. Start the description with an initial
  phrase, punctuated and capitalized as a sentence. For example: "The unique
  identifier of the project." Follow the phrase with a sentence or two, as
  needed. This description should be fairly short. If you have details to
  provide that require extra paragraphs or lists, use the optional "parameter
  details" section following the introduction.

These tables do not need titles.

Organize the parameters and label them as directed in the `style guidelines`_.

If there are no response body parameters, include the header in the response
example, and include the following sentence:
"This operation does not return a response body."

Response example
----------------

This section starts with **Example response: JSON**  (or the language of the
sample, or "header", if there is not body) and contains the code example with
an introductory sentence, such as
"The following example shows the JSON response for retrieving a list of
flavors."

Specify the type of response, if applicable (such as JSON, XML, or cURL).

In the example, include the HTTP request header and show the body (if there is
a body).

You can show multiple examples, by error code. Precede each with an
introductory sentence.

Response codes
--------------

Provide a table (using the `list-table directive
<http://docutils.sourceforge.net/docs/ref/rst/directives.html#list-table>`_)
with the possible response codes for the operation. Introduce it as follows:
"This operation can have the following response codes."

Response code tables include the following columns:

- **Code**: Show the number, in regular font.
- **Name**: Show the response code name, with title-style caps
- **Description**: Use sentences. Use standard, common descriptions if they
  are available (possibly through the use of substitution variables).
