
*******************
Setting up a Server
*******************

There are a wide variety of proprietary and open source software packages that can be used to provide the OGC web services of interest to OneGeology. We cannot possibly describe them all but this section gives guidance on how to use some with which we do have experience to set up your OneGeology services. If you are interested and able to provide similar guidance for a software package not listed below then please get in touch to discuss adding your documentation here. Currently the only software we have successfully used to provide *all* the service types relevant for OneGeology is GeoServer.

To start with there are some links to downloadable example data sets which you can use to experiment with setting up the servers before you try getting your own data into an appropriate format.

At the end there is an additional section on setting up the Apache HTTPD server to act as a reverse proxy which may be useful if you need to provide a unified web address and port for accessing your OneGeology and possibly other web services.

.. toctree::
   :maxdepth: 1

   server_setup/example_data
   server_setup/geoserver
   server_setup/mapserver
   server_setup/esri
   server_setup/apache

