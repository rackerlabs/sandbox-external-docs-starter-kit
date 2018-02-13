========================
Send Requests to the API
========================

You have several options for sending requests through an API:

-  Developers and testers may prefer to use cURL, the command-line tool
   from http://curl.haxx.se/.

   With cURL you can send HTTP requests and receive responses back from
   the command line.

-  If you like to use a more graphical interface, the ReST client for
   Firefox also works well for testing and trying out commands, see
   https://addons.mozilla.org/en-US/firefox/addon/restclient/.

-  You can also download and install rest-client, a Java application to
   test ReSTful web services, from
   http://code.google.com/p/rest-client/.

Send API Requests Using cURL
----------------------------

cURL is a command-line tool that is available on most UNIX®-like
environments and Mac OS X® and can be downloaded for Windows® in order
to interact with the ReST interfaces. For more information on cURL,
visit http://curl.haxx.se/.

cURL allows you to transmit and receive HTTP requests and responses from
the command-line or from within a shell script. This makes it possible
to work with the ReST API directly without using one of the client APIs.

The cURL examples in this guide use the following command-line options.

.. list-table::
   :widths: 30 70
   :header-rows: 1

   * - Option
     - Description
   * - **-d**
     - Sends the specified data in a **POST** request to the HTTP server. Use
       this option to send a JSON request body to the server.
   * - **-H**
     - Specifies an extra HTTP header in the request. You can specify any
       number of extra headers. Precede each header with the ``-H`` option.

       Common headers in Rackspace API requests are as follows:

       - ``Content-Type``: Required for operations with a request body.

         Specifies the format of the request body. Following is the syntax
         for the header where format is ``json``:

         .. code::

                Content-Type: application/json

       - ``X-Auth-Token``: Required. Specifies the authentication
         token.


       - ``X-Auth-Project-Id``: Optional. Specifies the project ID,
         which can be your account number or another value.


       - ``Accept``: Optional. Specifies the format of the response
         body.

         Following is the syntax for the header where the format is
         ``json``, which is the default:

         .. code::

              Accept: application/json

   * - **-i**
     - Includes the HTTP header in the output.

   * - **-s**
     - Specifies silent or quiet mode, which makes cURL mute. No progress or
       error messages are shown.

       If your cURL command is not generating any output, try replacing the
       ``-s`` option with ``-i``.

   * - **-T**
     - Transfers the specified local file to the remote URL.
   * - **-X**
     - Specifies the request method to use when communicating with the HTTP
       server. The specified method is used instead of the default method,
       which is **GET**.


ppxml
~~~~~

For commands that return an XML response, you can append the following
code to the command to call ``ppxml`` to pretty-print output:

.. code::

    | ppxml

If you do not want to pretty-print XML output, omit this code.

In order to use ``ppxml``, you need to set the ``ppxml`` alias as
follows:

.. code::

    $ alias ppxml='python -c "import sys, xml.dom.minidom;/
      print xml.dom.minidom.parseString(sys.stdin.read()).toprettyxml()"'

json.tool
~~~~~~~~~

For commands that return a JSON response, you can append the following
code to the command to call the json.tool to pretty-print output:

.. code::

    | python -m json.tool

To use the json.tool, import the json module. For information about the
json.tool, see `json — JSON encoder and
decoder <http://docs.python.org/2/library/json.html>`__.

If you do not want to pretty-print JSON output, omit this code.
