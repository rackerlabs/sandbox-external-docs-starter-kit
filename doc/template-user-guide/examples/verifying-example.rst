.. _verifying-example-ug:

====================================
Verifying the installation (example)
====================================

To verify the installation of stand-alone Object Storage for RPCO, run the
following commands from the proxy server or any server that has
access to Identity (keystone).

#. Ensure that the credentials are set correctly in the ``/root/openrc``
   file and then source it:

   .. code-block:: console

       $ source /root/openrc

#. Run the following command:

   .. code-block:: console

       $ swift stat
       Account: AUTH_11b9758b7049476d9b48f7a91ea11493
       Containers: 0
          Objects: 0
            Bytes: 0
       Content-Type: text/plain; charset=utf-8
       X-Timestamp: 1381434243.83760
       X-Trans-Id: txdcdd594565214fb4a2d33-0052570383
       X-Put-Timestamp: 1381434243.83760

#. Run the following commands to upload files to a container. Create the
   ``test.txt`` and ``test2.txt`` test files locally if needed (they can
   contain anything).

   .. code-block:: console

       $ swift upload myfiles test.txt
       $ swift upload myfiles test2.txt

#. Run the following command to download all files from the ``myfiles``
   container:

   .. code-block:: console

       $ swift download myfiles
         test2.txt [headers 0.267s, total 0.267s, 0.000s MB/s]
         test.txt [headers 0.271s, total 0.271s, 0.000s MB/s]

   If the files download successfully, Object Storage has been installed.
