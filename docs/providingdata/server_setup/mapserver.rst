
Using MapServer
===============

Software Installation
---------------------

`MapServer <https://mapserver.org/>`_ can be used to provide a number of OGC Web Services (OWS) types, such as the Web Map Service (WMS), Web Feature Service (WFS) and Web Coverage Service (WCS) standards which are the current focus of interest for the OneGeology portal.  In the following sections we run through how to configure MapServer so it can provide any one of these three service types.

MapServer will work both on Windows and Linux operating systems (both 32-bit and 64-bit), and with a web server of your choosing, the permutations are many and we can not cover all of them, below we take you through some common installations, using Apache HTTP as the web server.

The simplest way to set up MapServer on a Windows server is to use the MapServer for Windows (MS4W) installer provided by Gateway Geomatics, this installs a 32-bit version of the Apache HTTP web server and the 32-bit version of MapServer as well as some demo applications.  For those wishing to use a 64-bit version of Apache HTTP web server, we recommend Apache Lounge and GISInternals.  For installation of MapServer on Linux, (with Apache HTTP web server) we recommend Ubuntu and the Personal Package Archives.

Installing MS4W
^^^^^^^^^^^^^^^

All versions of the MS4W software package, including the latest version are available from the `Gateway Geomatics MS4W <https://ms4w.com/>`_  web site.

Two options are available, a downloadable zip of all the appropriate binaries or an installer.  We will use the installer here as it the easiest option for those setting up a OneGeology service for the first time.  The installer is available from the `Download Packages <https://ms4w.com/download.html>`_ page. Download the latest setup file, for us this was ms4w-3.2.2-setup.exe, to a temporary location on your server.


.. figure:: images/ms4w-setup.png


Run the setup.exe file as an Administrator.  A small dialogue window will pop-up appear detailing the licensing agreement. Please take the time to read the license, and if you accept the conditions click on the *I Agree* button.


.. figure:: images/MS4W-agree-license.png


The next screen will offer a selection of installation options.  To run a OneGeology service you only need to accept the default options, but you can choose other options if you wish, such as p.mapper (if you want to use PHP//MapScript), or MapBender, OpenLayers, or GeoMoose, if you want to develop your own client application.


.. figure:: images/ms4w-select-options.png


Once you have made your option selection select *Next* and choose an installation folder for the MS4W folder.  The default location will be into your *C:* drive.


.. figure:: images/MS4W-default-path.png


**Note** You shouldn't specify the MS4W folder as this will be created as part of the installation.

Finally, you need to choose a port to run your web service on.  You should use the default port of 80 if at all possible, otherwise other official web server ports are: 591, 8008, and 8080.


.. figure:: images/MS4W-default-port.png


When you have finished click *Install*  the dialogue will show you the progress of the installation process.  If the installer finds that you are missing the appropriate Microsoft Visual C++ distribution to run MapServer, then it will provide an additional window as part of the installation, providing a license agreement which you need to agree to and *Install*.

.. figure:: images/MS4W-installCpp.png


If the installation works correctly you will be taken to a page on your newly installed web server as below:


.. figure:: images/MS4W-localhost-post-install.png



Configuring the exemplar services
"""""""""""""""""""""""""""""""""

Obtain the OneGeology template application in the 20Mbytes approx. sized 1G\_WMS-exemplar-data-MS6-update.zip file from the `BGS Resources website <https://resources.bgs.ac.uk/OneGeology/>`_.

Unzip the OneGeology template application to the same drive and directory level as the MS4W location resulting from the MapServer installation e.g. if you installed MS4W on C:\\MS4W then point the unzip extract to C:.  It should create a number of files inside the *ms4w* directory.  The main part of the two example applications are inside a BGS\_Bedrock\_and\_Superficial\_Geology directory (for the shapefile based example) and BGS\_Bedrock\_Raster\_Map directory (for the image file based example) which will be created inside ms4w\\apps\\cookbookExemplars.

The MapServer executables for the two applications are found in similarly named folders in ms4w\\apps\\exemplars, and the web server configuration files are found in ms4w\\httpd.d

After unzipping the exemplar files, restart your web service.  Now when you browse to localhost/index.html you will get links to the two exemplar services.


Configuring your own services using the exemplars as examples
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

C:\\ms4w\\Apache\\cgi-bin\\
'''''''''''''''''''''''''''

Create a folder inside ms4w\\Apache\\cgi-bin with a name that follows the OneGeology profile.

It is not within the scope of OneGeology at this stage to address the problem of translating geological terms between different languages so the above service can be in the language you usually use for your data.  However, if you already have your data in other languages, in particular English if that is not your default language, then we would like to encourage you to provide services in these other languages as well.  These should be served from separate services with different URLs.  In MapServer this means making another copy of the above directory and renaming it to use the appropriate language in the directory name.

At this stage you should have a sub-folder structure within c:\\ms4w\\Apache\\cgi-bin like:

.. code-block:: text

  \BGS_Bedrock_and_Superficial_Geology
     Holds MapServer cgi libraries for the ‘BGS_Bedrock_and_Superficial_Geology’ shapefile-based exemplar service.
  \BGS_Bedrock_Geology
     Holds MapServer cgi libraries for the ‘BGS_Bedrock_Geology’ raster-based exemplar service.
  \Your-Organization-code_Your-Service-Theme
     EMPTY
  \Your-Organization-code_Your-alternate-language(service)-code_Your-Service-Theme
     EMPTY

.. todo::

   need to add content about copying cgi-bin executables from ms4w install to the exemplar folders (or overwring that content ~ need to check zip). Also need to add section about renaming the mapserv.exe to ows or wms.  And add to the section above about copying to a new folder when creating your own service.



C:\\ms4w\\apps\\cookbookExemplars
'''''''''''''''''''''''''''''''''

Inside the \\ms4w\\apps\\cookbookExemplars folder you will find two folders: "BGS\_Bedrock\_and\_Superficial\_Geology" and "BGS\_Bedrock\_Raster\_Map".  These folders contain the exemplar data, and map configuration files.

We will assume you are basing your service on the BGS\_Bedrock\_and\_Superficial\_Geology example; substitute with BGS\_Bedrock\_Raster\_Map if that is closer to your requirements.  When you have decided which exemplar service is most suitable for your needs, you should copy that exemplar folder to a new folder that will be your new service.

Note the names of these folders do not have to match the names of the service, but you would be advised to ensure that the folder name gives some hint as to its contents and purpose.  For example we call one of our exemplar folders "BGS\_Bedrock\_Raster\_Map" to indicate that this service application holds a raster map as datasource, rather than a shapefile.

Make more copies with appropriate names if you are also making multiple language services.

Inside this folder there is a wwwroot\\index.html file.  This has some example queries which will enable you to test your service when you have set it up.  For these to work for your new service you will need to edit the file and change all occurrences of the string "BGS\_Bedrock\_and\_Superficial\_Geology" with the name you have created for your service.

C:\\ms4w\\httpd.d\\
'''''''''''''''''''

Now you will need to create an httpd conf file in the \\ms4w\\httpd.d\\ folder that has the same name as your service; for example, the "BGS\_Bedrock\_and\_Superficial\_Geology" exemplar service has a conf file called "httpd\_BGS\_Bedrock_and\_Superficial\_Geology\_Exemplar.conf" and the "BGS\_Bedrock\_Geology" exemplar service has a corresponding conf file called "httpd\_BGS\_Bedrock\_Geology.conf"

You need to copy one of the exemplar .conf files and rename it to match the name of your service, you will then need to change the paths in the file to match your service name and folder configuration.

Using the raster exemplar service (as shown below), you will need to change all references to "BGS\_Bedrock\_Geology" to match the name of your service, and all references to "BGS\_Bedrock\_Raster\_Map" to match the name of your app folder.  Note, you do not need to add the drive letter.

.. code-block:: apacheconf

  Alias /BGS_Bedrock_Geology/ "/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/www/"

  <Directory "/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/www/">
      AllowOverride None
      Options Indexes FollowSymLinks Multiviews
      Order allow,deny
      Allow from all
  </Directory>

  SetEnvIf Request_URI "/cgi-bin/exemplars/BGS_Bedrock_Geology/ows" MS_Mapfile=/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/onegeology.map
  SetEnvIf Request_URI "/fcgi-bin/exemplars/BGS_Bedrock_Geology/ows" MS_Mapfile=/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/onegeology.map


C:\\ms4w\\Apache\\htdocs\\
''''''''''''''''''''''''''

Now you should edit the index.html file in the Apache web root \\ms4w\\Apache\\htdocs\\ and add a link to your new service.  Note, the link you use is the value of the Alias (line one of the httpd conf file).

Again make more copies if making multiple language services.


Installing and configuring Apache HTTP web server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

MS4W, as described above, installs both MapServer and the Apache HTTP webserver software.  Other installations of MapServer require configuring of the web server as a separate process.  This section takes you through installing alternate Apache HTTP webserver software, and through the additional configuration you will need to do to create a OneGeology service that follows the same pattern as above.


64-bit Apache HTTP server
"""""""""""""""""""""""""

if tyou want to run a 64-bit version of MapServer on Windows such as provided by GISInternals, you will also need to in install a 64-bit version of Apache.

If instead you want to use the latest stable release of Apache-HTTP, that is the version 2.4.n releases (latest is currently 2.4.29), you must instead go to the Apache Lounge site: `http://www.apachelounge.com/download/ <http://www.apachelounge.com/download/>`_. There are several options here both in server architecture (32 bit and 64 bit), and server functionality, for you to choose from to fit your needs.

For the purposes of this example we have selected a 64-bit package from Apache Lounge and installed it to our C:\\ drive as C:\\Apache24\\.


httpd.d configuration files
'''''''''''''''''''''''''''

For this installation we will now create a httpd.d folder on our D:\\ drive, to hold our OneGeology service configuration files, as: D:\\WxS\\ms\\httpd.d\\ , and create an http\_ file (i.e. ‘httpd_BGS_Bedrock_and_Superficial_Geology_Exemplar.conf’) for our exemplar service as below.

.. code-block:: apacheconf

  #===============================================================================================#
  Alias /BGS_Bedrock_and_Superficial_Geology_Exemplar/ "D:/WxS/ms/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/wwwroot/"

  <Directory "D:/WxS/ms/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/wwwroot/">
      AllowOverride None
      Options FollowSymLinks Multiviews
      Require all granted
  </Directory>
  #===============================================================================================#

  SetEnvIf Request_URI "/cgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/wms" MS_Mapfile=D:/WxS/ms/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/onegeology.map

Note, that there is a change in the way access permissions are handled between versions 2.2.n and 2.4.n of Apache, so if you are copying the existing MS4W httpd\_ conf files you will need to change your <Directory> information;  that is, you will need to replace the ‘*Order allow,deny*’ and ‘*Allow from all*’ directives with ‘*Require all granted*’

apache.conf
'''''''''''

Finally you will need to add some information to the Apache-HTTP server configuration file (C:\\Apache24\\conf\\httpd.conf) as per the below snippets.

.. code-block:: apacheconf

  <IfModule alias_module>
    ...
    # Alias: Maps web paths into filesystem paths and is used to
    # access content that does not live under the DocumentRoot.

    Alias /ms_tmp "D:/WxS/ms/out/tmp"

    # ScriptAlias: This controls which directories contain server scripts.
    # ScriptAliases are essentially the same as Aliases, except that
    # documents in the target directory are treated as applications and
    # run by the server when requested rather than as documents sent to the
    # client.

    ScriptAlias /cgi-bin/ "C:/Apache24/cgi-bin/"
    ...
  </IfModule>
  ...
  <Directory "C:/Apache24/cgi-bin">
      AllowOverride None
      Options None
      Require all granted
  </Directory>
  ...
  # Parse our MapServer Apache conf files
  Include D:/WxS/ms/httpd.d/httpd_*.conf


Create alias configuration files
''''''''''''''''''''''''''''''''

Next we need to create an alias to our data files and MapServer html templates.  The way you do this varies considerably depending on your Linux version.  In older versions of Ubuntu these aliases are created in the **alias** file located in the **/etc/apache2/conf.d/** directory.  In recent versions you should add these aliases to the **httpd.conf** file in **/etc/apache2/**

We need to create information in the style of the contents of the .conf files (found in our unzipped contents ../ms4w/httpd.d/ directory).  We will combine the contents of both .conf files (that deal with the html templates and data content) into our ‘alias’ configuration file.

You may choose any text editor, but probably the easiest to use is nano.

.. code-block:: sh

  # cd /etc/apache2
  # nano httpd.conf

.. code-block:: apacheconf

  Alias /BGS_Bedrock_Geology /usr/local/src/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/wwwroot/

  <Directory /usr/local/src/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/wwwroot/>
       AllowOverride None
       Options Indexes FollowSymLinks Multiviews
       Order allow,deny
       Allow from all
  </Directory>

  Alias /BGS_Bedrock_and_Superficial_Geology /usr/local/src/ms4w/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/wwwroot/

  <Directory /usr/local/src/ms4w/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/wwwroot/>
       AllowOverride None
       Options Indexes FollowSymLinks Multiviews
       Order allow,deny
       Allow from all
  </Directory>

^O (to save changes)

ENTER

^X (to exit)

You will probably need to restart the Apache web server at this point:

.. code-block:: sh

  #/etc/init.d/apache2 restart

We can test these using the lynx browser

.. code-block:: sh

  #lynx http://127.0.0.1/BGS_Bedrock_and_Superficial_Geology/index.html

or using wget:

.. code-block:: sh

  #cd /tmp
  #wget http://127.0.0.1/BGS_Bedrock_Geology/index.html
  #less index.html


Installing GISInternals packages for Windows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The most recent versions of the GISInternals GDAL and MapServer packages are available online at: `https://www.gisinternals.com/ <https://www.gisinternals.com/>`_

In most instances we would recommend using the MS4W packages to install Apache and MapServer to give yourself a Windows implementation of MapServer, but in some instances, for example if you want the latest version of MapServer or if you want to use 64-bit software, you can alternatively use one of the GISinternals packages for your MapServer service.

In this section we will assume you are familiar with configuring a MS4W service and just provide some notes to assist you configure this alternative MapServer on Windows service using Apache-HTTP as your web server.

Once you have a working web service installed, you now need to obtain the corresponding GISInternals binaries, for example in this case we downloaded the zip file **release-1600-x64-gdal-1-9-2-MapServer-6-2-0.zip**, and unzipped onto our C:\\ drive as C:\\apps\\gisinternals\\.

Now we must run the SDKShell.bat batch file to set up some environment variables, for example it adds the following locations to the system PATH:

.. code-block:: text

   C:\apps\gisinternals\bin;
   C:\apps\gisinternals\bin\gdal\python\osgeo;
   C:\apps\gisinternals\bin\proj\apps;
   C:\apps\gisinternals\bin\gdal\apps;
   C:\apps\gisinternals\bin\ms\apps;
   C:\apps\gisinternals\bin\gdal\csharp;
   C:\apps\gisinternals\bin\ms\csharp;
   C:\apps\gisinternals\bin\curl;

The MapServer executable file (mapserv.exe) is found in the C:\\apps\\gisinternals\\bin\\ms\\apps folder.  As ever, you can check the version by using the -v option in a command window like:

.. code-block:: doscon

   c:\apps\gisinternals\bin\ms\apps>mapserv.exe -v
   MapServer version 7.1-dev OUTPUT=PNG OUTPUT=JPEG OUTPUT=KML SUPPORTS=PROJ SUPPORTS=AGG SUPPORTS=FREETYPE SUPPORTS=CAIRO SUPPORTS=SVG_SYMBOLS SUPPORTS=SVGCAIRO SUPPORTS=ICONV SUPPORTS=FRIBIDI SUPPORTS=WMS_SERVER SUPPORTS=WMS_CLIENT SUPPORTS=WFS_SERVER SUPPORTS=WFS_CLIENT SUPPORTS=WCS_SERVER SUPPORTS=SOS_SERVER SUPPORTS=FASTCGI SUPPORTS=THREADS SUPPORTS=GEOS INPUT=JPEG INPUT=POSTGIS INPUT=OGR INPUT=GDAL INPUT=SHAPEFILE

Data
""""

You may put your OneGeology data for your service (and the Mapfile etc) anywhere on your server, but here we will follow the same pattern as we have for used for the MS4W services.  In this case we have extracted the exemplar shapefile data to a location on our D:\\ drive as:

* D:\\WxS\\ms\\apps\\cookbookExemplars\\BGS_Bedrock_and_Superficial_Geology

  * data (folder)
  * templates (folder)
  * wwwroot (folder)
  * onegeology.map (file)
  * ICSClasses.txt (file)

You will need to make a few change to the Mapfile from the downloaded exemplar file.  For example you will need to tell MapServer where to find the proj files so that you can reproject your data.  You do this by adding a CONFIG statement at the top of the Mapfile like:

.. code-block:: mapfile

  MAP
     CONFIG "PROJ_LIB" "C:/apps/gisinternals/bin/proj/SHARE"

You will also need to change the IMAGEPATH statement to point at your chosen temporary file location (within the WEB section of the Mapfile) like:

.. code-block:: mapfile

  #====================================================================#
  # Start of WEB interface definition (including WMS enabling metadata)
  #====================================================================#
      WEB
          HEADER "tmpl/query_header.html"
          FOOTER "tmpl/query_footer.html"
          IMAGEPATH "D:/WxS/ms/out/tmp/"
          IMAGEURL "/ms_tmp/"

MapServer cgi-bin
"""""""""""""""""

For this installation we will now create some folders in the Apache-HTTP cgi-bin folder to hold our copy of the mapserv.exe executable (which we will rename as ‘wms’) as:

* C:\\Apache24\\cgi-bin (folder)

    * exemplars (folder)

        * BGS_Bedrock_and_Superficial_Geology (folder)

            * wms (file)

At this stage you will have a working MapServer service such that a request like the below (where we also specify the ‘map’ variable explicitly) will give you a GetCapabilities reponse document.

.. code-block:: text

  http://[your-server-name]/cgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/wms?
    service=WMS&
    request=GetCapabilities&
    map=D:/WxS/ms/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/onegeology.map&


Installing MapServer on Linux using PPAs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This installation guide will give you simple step-by-step instructions of installing MapServer onto a Linux server and assumes you have an Apache HTTP webserver already running.

Users of Ubuntu/Debian systems should find that they are able to get the latest version of MapServer by adding the following Personal Package Archives to their system’s software sources:

  ppa:ubuntugis/ppa
     Official stable UbuntuGIS packages
  ppa:ubuntugis/ubuntugis-unstable
     Unstable releases of Ubuntu GIS packages


For example, the Official stable version PPA can be added like:

.. code-block:: sh

   sudo add-apt-repository ppa:ubuntugis/ppa
   sudo apt-get update

And the MapServer files need to create a OneGeology service can be added like:

.. code-block:: sh

   sudo apt install cgi-mapserver mapserver-bin tinyows


The MapServer executable file is called **mapserv** and in our installation is found at //usr//bin//mapserv


.. code-block:: sh

  #cp mapserv /usr/lib/cgi-bin/mapserv

The mapserv binary created needs to have —rwxr-xr-x permissions to be able to execute

You can check permissions using:

.. code-block:: sh

  #ls —l mapserv

If needed you can change permissions using:

.. code-block:: sh

  #chmod 755 mapserv

To test you have compiled mapserv with all appropriate options you can check the version:

.. code-block:: sh

  #./mapserv —v

You should get an output like:

.. code-block:: text

  MapServer version 7.0.4 OUTPUT=PNG OUTPUT=JPEG OUTPUT=KML SUPPORTS=PROJ SUPPORTS=AGG SUPPORTS=FREETYPE SUPPORTS=CAIRO SUPPORTS=SVG_SYMBOLS SUPPORTS=RSVG SUPPORTS=ICONV SUPPORTS=FRIBIDI SUPPORTS=WMS_SERVER SUPPORTS=WMS_CLIENT SUPPORTS=WFS_SERVER SUPPORTS=WFS_CLIENT SUPPORTS=WCS_SERVER SUPPORTS=SOS_SERVER SUPPORTS=FASTCGI SUPPORTS=THREADS SUPPORTS=GEOS INPUT=JPEG INPUT=POSTGIS INPUT=OGR INPUT=GDAL INPUT=SHAPEFILE

To test you have mapserv accessible through your web server you can use the ‘lynx’ text browser package (available through apt-get):

.. code-block:: sh

  #apt-get install lynx
  #lynx http://127.0.0.1/cgi-bin/mapserv

Or you could simply use the wget program (which will retrieve the output as a text file):

.. code-block:: sh

  #cd /tmp
  #wget http://127.0.0.1/cgi-bin/mapserv
  #less mapserv

You should get the message "No query information to decode. QUERY_STRING is set but empty"

Congratulations! You have now got MapServer installed and configured to run in your web server.


Configuring MapServer exemplar services on a LAMP server
""""""""""""""""""""""""""""""""""""""""""""""""""""""""

We shall now configure the two BGS exemplar services (a shapefile version and a raster version) available from the BGS Resources server.

.. code-block:: sh

  #cd /usr/local/src
  #wget https://resources.bgs.ac.uk/OneGeology/1G_WMS-exemplar-data-MS6-update.zip
  #unzip 1G_WMS-exemplar-data-MS6-update.zip

We now need to move the contents of the zip file to the correct locations on our server.

First we move our index pages to the root directory of the web server (/var/www/ on Ubuntu).

.. code-block:: sh

  #mv ms4w/Apache/htdocs/* /var/www/

Create a ows shell script
'''''''''''''''''''''''''

Next we need to create a ‘ows’ shell script for each of our Map Services; which we need to place in an associated directory.

.. code-block:: sh

  #cd /usr/lib/cgi-bin
  #mkdir --parents exemplars/BGS_Bedrock_Geology
  #nano exemplars/BGS_Bedrock_Geology/ows

.. code-block:: sh

  #!/bin/sh
  MS_Mapfile=/usr/local/src/ms4w/apps/cookbookExemplars/BGS_Bedrock_Raster_Map/onegeology.map
  export MS_Mapfile
  exec /usr/lib/cgi-bin/mapserv
  exit 0

^O (to save changes)

ENTER

^X (to exit)

.. code-block:: sh

  #chmod 755 exemplars/BGS_Bedrock_Geology_Raster/ows

and similarly for our shapefile based service

.. code-block:: sh

  #mkdir --parents exemplars/BGS_Bedrock_and_Superficial_Geology
  #nano exemplars/BGS_Bedrock_and_Superficial_Geology/ows

.. code-block:: sh

  #!/bin/sh
  MS_Mapfile=/usr/local/src/ms4w/apps/cookbookExemplars/BGS_Bedrock_and_Superficial_Geology/onegeology.map
  export MS_Mapfile
  exec /usr/lib/cgi-bin/mapserv
  exit 0

^O (to save changes)

ENTER

^X (to exit)

.. code-block:: sh

  #chmod 755 exemplars/BGS_Bedrock_and_Superficial_Geology/ows

Modify paths in the Mapfile
''''''''''''''''''''''''''''

The final step is to modify the WEB > IMAGEPATH path (to "/var/tmp/") and the WEB > IMAGEURL path (to "/tmp/") in each of our onegeology.map files

That’s it!



Alternative MapServer configurations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to use other permutations and get stuck remember you can ask the OneGeology Helpdesk any MapServer configuration issues in relation to your OneGeology services, and we will endeavour to help you.

As well as the OneGeology Helpdesk there are a number of other resources to help guide you in your installation, including:

MS4W documentation
   https://ms4w.com/documentation.html

MapServer documentation
   http://mapserver.org/documentation.html

GIS StackExchange (MapServer questions)
   https://gis.stackexchange.com/search?q=is%3Aquestion+%5BMapServer%5D

GIS StackExchange (MS4W questions)
   https://gis.stackexchange.com/search?q=is%3Aquestion+%5Bms4w%5D

StackOverflow (Apache web server questions)
   https://stackoverflow.com/search?q=is%3Aquestion+%5Bapache%5D

Mailing Lists
   http://mapserver.org/community/lists.html#mapserver-users

   https://lists.ms4w.com/mailman/listinfo/ms4w-users


MapServer and IIS
"""""""""""""""""

You may use the IIS web server instead of Apache to run the MapServer CGI.  See the previous cookbook for details of how to do this with IIS version 6.  We haven't been able to update the cookbook for the latest version of IIS, but the MapServer documentation (`IIS Setup for MapServer <https://mapserver.org/installation/iis.html>`_) gives a good guide for how to do this in general for IIS 7 and up.

Compiling MapServer on Linux
""""""""""""""""""""""""""""

You may wish to compile your own version of MapServer on a \*nix operating system of your own choosing.  We haven't done this for a while and the guidance in our previous cookbook was very out of date.  There is guidance on the MapServer site that takes you through the process (`Compiling on Unix <https://mapserver.org/installation/unix.html>`_)


General configuration
---------------------

MapServer services are configured through the use of Mapfile templates (\*.map).  You can use a single Mapfile to configure a service, or you can use a master file that includes other files.  The benefits of using multiple files include ease of maintenance across multiple similar services, and readability.  Here we will use multiple files to show how the various parts of a MapServer (OGC) service need to be configured.  You can configure multiple service types through a single configuration, if desired.


The start of a Mapfile begins with a **MAP** statement and ends with an **END** statement

Comments are shown by lines beginning with a **#** sign

The order of statements in the Mapfile doesn't matter, here we tend to group alphabetically for readability.

For further details on Mapfile configuration options available see https://mapserver.org/mapfile/map.html


.. code-block:: mapfile

   MAP
       # You must supply a NAME for your service, which in OGC services will be the Root Layer Name
       NAME "BGS_EN_Bedrock_and_Superficial_Geology"

       # You may supply some extra configuration details using one or more CONFIG statements
       CONFIG "MS_ERRORFILE" "D:/logs/MapServer/Pub/TFL/ms_error.log"
       CONFIG "PROJ_LIB" "C:/apps/gisinternals/bin/proj/SHARE"
       CONFIG "PGEO_DRIVER_TEMPLATE" "DRIVER=Microsoft Access Driver (*.mdb, *.accdb);DBQ=%s"
       CONFIG "OGR_SKIP" "ODBC"

       # You may configure the level of DEBUG detail you want from your service
       DEBUG 0

       # You must supply an EXTENT, which defines the extent of the map to be created
       # The EXTENT is specified in min-x, min-y, max-x, max-y order
       # The EXTENT is specified in units of the default service projection
       EXTENT -8.6476 49.8639 1.76943 60.8622

       # You may specify a set of fonts for your service
       # The location of any included file is relative to the location of Mapfile
       # See below section on alternate character set support
       FONTSET "../DefaultMapIncludes/fontset.lst"

       # You may supply information on the output formats you wish to support
       # See http://mapserver.org/mapfile/outputformat.html#outputformat
       INCLUDE "../DefaultMapIncludes/BGS-service-std-output-plus1.map"

       # You must provide information on the styling of the legend
       LEGEND
           IMAGECOLOR 255 255 255
           STATUS ON
           KEYSIZE 18 12
           LABEL
               TYPE BITMAP
               SIZE MEDIUM
               COLOR 0 0 89
           END
       END

       # You may specify the Maximum Size of the map image
       MAXSIZE 3072

       # You must supply the default PROJECTION for the service
       # For OneGeology services this would normally be EPSG:4326
       PROJECTION
          "init=epsg:4326"
       END

       # You may specify the path to the folder holding your shapefile data
       # The path is relative to the location of the mapfile
       SHAPEPATH "data"

       # You must specify the default SIZE of the map image
       # SIZE is specified in Pixels
       SIZE 600 800

       # You must state whether the map is active or not.
       STATUS ON

       # You can specify the location of a Symbol set that defines symbols used in your styles
       SYMBOLSET "../DefaultMapIncludes/symbols.sym"

       # You must specify the UNITS of the map coordinates
       UNITS dd

       WEB
           #==================================================================================#
           # The WEB section includes all the general configuration for the WEB service
           #==================================================================================#

           # See below section on the WEB object
       END

       # LAYER specific configuration would follow
       INCLUDE "BedrockLithology.map"
       ...

   END


The **WEB** section of the Mapfile (extract shown below) sets general information for your web service including a general description, contact information, etc.

.. code-block:: mapfile

   WEB
       # The FOOTER template is applied after everything else is sent for a query result
       FOOTER "templates/query_footer.html"
       # The HEADER template is applied before anything else is sent for a query result
       HEADER "templates/query_header.html"

       # IMAGEPATH is the temporary directory for writing temporary files and images
       IMAGEPATH "/ms4w/tmp/ms_tmp/"
       # IMAGEURL Base URL for IMAGEPATH
       IMAGEURL "/ms_tmp/"

       METADATA
           #==================================================================================#
           # The METADATA section is used to populate information into the Web Service metadata response
           # The METADATA detailed here is part of the information found in a GetCapabilities response
           #==================================================================================#
           # OWS_ metadata applies to all available services (WMS, WFS, WCS, SOS...)
           # WCS_ metadata applies to WCS services only. Values will override an OWS setting
           # WFS_ metadata applies to WFS services only. Values will override an OWS setting
           # WMS_ metadata applies to WMS services only. Values will override an OWS setting
           #==================================================================================#

           # See below section on the WEB > METADATA object
       END
   END

In any **METADATA** section instead of  the "WMS\_" prefix  you may use "OWS\_" prefix.  The "OWS\_" prefix is used by WMS, WFS, WCS, GML, and other services, so you only have to specify that metadata type once.  If you have "OWS_ABSTRACT" and "WMS_ABSTRACT", the "OWS_ABSTRACT" will be used by any WFS / WCS service whilst the "WMS_ABSTRACT" will be used by the WMS.

.. code-block:: mapfile

   METADATA
       "OWS_ABSTRACT" "The 1:625k DiGMap data covering the whole of the United Kingdom is available in this OGC web service for all uses - including commercial use subject to the conditions in the Access Constraints section and is being served as a contribution to the OneGeology initiative (onegeology.org)."
       "OWS_ACCESSCONSTRAINTS" "The 1:625k DiGMap data is available for free download for your personal, teaching, research, or non-commercial use (as described on https://www.bgs.ac.uk/bgs-intellectual-property-rights/using-bgs-copyright-material/). Your use of any information provided by the British Geological Survey (BGS) is at your own risk. Neither BGS nor the Natural Environment Research Council (NERC) gives any warranty, condition, or representation as to the quality, accuracy, or completeness of the information or its suitability for any use or purpose. All implied conditions relating to the quality or suitability of the information, and all liabilities arising from the supply of the information (including any liability arising in negligence) are excluded to the fullest extent permitted by law."
       "OWS_ADDRESS" "Environmental Science Centre"
       "OWS_ADDRESSTYPE" "postal"
       "OWS_CITY" "Keyworth"
       "OWS_CONTACTELECTRONICMAILADDRESS" "enquiries@bgs.ac.uk"
       "OWS_CONTACTFACSIMILETELEPHONE" "+44 (0)115 936 3200"
       "OWS_CONTACTINSTRUCTIONS" ""
       "OWS_CONTACTORGANIZATION" "British Geological Survey"
       "OWS_CONTACTPERSON" "Garry Baker"
       "OWS_CONTACTPOSITION" ""
       "OWS_CONTACTVOICETELEPHONE" "+44 (0)115 936 3100"
       "OWS_COUNTRY" "United Kingdom"

       # The following statement enables all WMS, WFS, WCS operations on all layers in the service
       # The statemant can be overridden by service specific statements, either here or in the LAYERS
       "OWS_ENABLE_REQUEST" "*"

       "OWS_FEES" "none"
       "OWS_HOURSOFSERVICE" "Mon-Fri, 09:00-17:00"
       #===========================================================================#
       # OWS_KEYWORDLIST
       # Put your organisation name and any other information you want to include.
       # You MUST include "OneGeology" as one of the keywords.
       # Do NOT use spaces after the commas in the keyword listing.
       #===========================================================================#
       "OWS_KEYWORDLIST" "OneGeology,geology,map,United Kingdom,bedrock,superficial,lithology,lithostratigraphy,age,MD_LANG@ENG,MD_DATE@2011-06-15"

       #"OWS_ONLINERESOURCE" "http://another-service/or/some-different-path/ows?"
       "OWS_POSTCODE" "NG12 5GG"
       "OWS_ROLE" "PointOfContact"
       "OWS_SERVICE_ONLINERESOURCE" "http://www.bgs.ac.uk/products/digitalmaps/digmapgb.html"
       "OWS_SLD_ENABLED" "TRUE"
       "OWS_STATEORPROVINCE" "Nottinghamshire"
       #===========================================================================#
       # "OWS_SRS" For WCS/WFS you need to list the default projection _FIRST_
       #===========================================================================#
       "OWS_SRS" "EPSG:27700 EPSG:3857 EPSG:4258 EPSG:4326"

       "OWS_TITLE" "BGS Bedrock and Superficial geology"
       "OWS_UPDATESEQUENCE" "2017-02-09T14:00:00Z"

       "WFS_ABSTRACT" "The 1:625k DiGMap data covering the whole of the United Kingdom is available in this OGC WFS service for your personal, non-commercial use only and is being served as a contribution to the OneGeology initiative(onegeology.org).  \
       The contents of this WFS service are not intended for direct use but are transformed by a mediator layer into separate WFS services which provide data in GeoSciML. This process is described in Chapter 2 of the OneGeology WFS Cookbook available at onegeology.org."
       "WMS_ABSTRACT" "The 1:625k DiGMap data covering the whole of the United Kingdom is available in this OGC WMS service for your personal, non-commercial use only and is being served as a contribution to the OneGeology initiative (onegeology.org).\
       Separate bedrock geology and superficial deposits layers are available in this service. Layers available for bedrock are lithostratigraphy, age, and lithology. Layers available for superficial deposits layer are lithostratigraphy and lithology. \
       For information about more of the British Geological Survey’s maps that are available digitally please visit http://www.bgs.ac.uk/products/digitalmaps/digmapgb.html"

       # INSPIRE WMS must provide a bounding box for all supported projections
       "WMS_BBOX_EXTENDED" "TRUE"

       # You can specify which output formats you want per operation
       "WMS_FEATURE_INFO_MIME_TYPE" "text/html"
       "WMS_GETMAP_FORMATLIST" "image/png,image/jpeg"

       "WMS_KEYWORDLIST_GEMET_ITEMS" "Bathymetry"
       "WMS_KEYWORDLIST_ISO_ITEMS" "infoMapAccessService"
       "WMS_KEYWORDLIST_VOCABULARY" "GEMET,ISO"

       #"WMS_ONLINERESOURCE" "http://another-service/or/some-different-path/wms?"
       "WMS_SRS" "EPSG:4326 EPSG:3857 EPSG:27700 EPSG:4258"
       "WMS_ROOTLAYER_TITLE" "BGS Bedrock and Superficial Geology"
   END

You may use the "WMS_ONLINERESOURCE" (and "OWS_ONLINERESOURCE" etc) metadata sections to change the service endpoint for your service.  For example, you can do this to force users (clients) to always use the IP version of your service rather than the server name (or vice versa), or to force them to always use the cgi-bin version rather than the fcgi-bin version (or vice versa), or to get them to use a different server.  That is, you can have an initial GetCapabilities response document that itself advertises a different service endpoint for the subsequent GetMap requests.  There are several reasons why you might want to do this; one such reason is when you have an existing service that has multiple layers only some of some of which are conformant to OneGeology and in which the service metadata doesn't otherwise conform to the OneGeology WMS profile.  In such an example, you can set up a service that has a GetCapabilities document that is conformant to the OneGeology WMS profile and which advertises only some of the layers of the other service through the use of the "WMS_ONLINERESOURCE" metadata.

The SRS specifies the coordinate system (spatial reference system) that the WMS can serve data in.  These are commonly specified using EPSG codes **and must include** `EPSG:4326 <https://epsg.org/crs_4326/WGS-84.html>`_ so that all services have at least one coordinate system in common.  We would like if you could specify the Spherical Mercator projection (`EPSG:3857 <https://epsg.org/crs_3857/WGS-84-Pseudo-Mercator.html>`_) to allow your service to be used in Google Maps.  You may specify other systems that are appropriate for your region if you wish; for example we would expect most European services to support either (or both of) `EPSG:4258 <https://epsg.org/crs_4258/ETRS89.html>`_ and `EPSG:3034 <https://epsg.org/crs_3034/ETRS89-extended-LCC-Europe.html>`_ to ensure compliance with INSPIRE coordinate system requirements.


Adding alternate character set support
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are serving a non-English language service, you may need or want to change the font and character sets.

To specify a font set you need to use the FONTSET keyword which references a file that contains the mappings from the font name aliases, which you will use in your Mapfile, to the actual font file names on your computer. See the MAP section above for an example of referencing a fontset file (fontset.lst)

.. code-block:: text

   arial C:\Windows\Fonts\Arial.ttf
   arialuni C:\Windows\Fonts\ARIALUNI.TTF
   esricaves2 C:\Windows\Fonts\esri_376.ttf
   fradm C:\Windows\Fonts\FRADM.TTF
   khmer C:\Windows\Fonts\KhmerUI.ttf
   msgothic C:\Windows\Fonts\MSGOTHIC.TTC
   msmincho C:\Windows\Fonts\MSMINCHO.TTC
   opensym C:\Windows\Fonts\opens___.ttf
   sc C:\Windows\Fonts\DejaVuSansCondensed.ttf
   scb C:\Windows\Fonts\DejaVuSansCondensed-Bold.ttf
   sym C:\Windows\Fonts\symbol.ttf
   verdana C:\Windows\Fonts\verdana.ttf


You only need one font specified in your Mapfile but you may list as many as you like in your fontset file.

The below example shows how you could modify the LABEL section of the LEGEND, to allow you to display Chinese characters.

.. code-block:: mapfile

   LEGEND
       OUTLINECOLOR 200 200 200
       KEYSPACING 10 10
       LABEL
           TYPE truetype
           FONT "msgothic"
           SIZE 8
           ENCODING "UTF-8"
       END
   END

The important parts to note in the above example are:

* TYPE truetype (the default is TYPE bitmap)
* FONT "msgothic" (the font alias we set up in our fontset.lst file)
* SIZE 8 (size should be specified in points, you can’t use words like “small” or “medium” which you do with bitmap fonts.)
* ENCODING "UTF-8" (You must also save your Mapfile in this character set encoding).


Creating your own symbology
^^^^^^^^^^^^^^^^^^^^^^^^^^^

symbols.sym, is a set of defined symbols that can be used to style your map layers.

.. code-block:: mapfile

   SYMBOLSET
       SYMBOL
           NAME "circle"
           TYPE ellipse
           FILLED false
           POINTS
             1 1
           END
           ANCHORPOINT 0.5 0.5
       END
       SYMBOL
           NAME "circlef"
           TYPE ellipse
           FILLED true
           POINTS
             10 10
           END
           ANCHORPOINT 0.5 0.5
       END
       SYMBOL
           NAME "divides"
           TYPE TRUETYPE
           FONT "opensym"
           CHARACTER '&#8739;'
           FILLED true
           ANTIALIAS true
       END
       SYMBOL
           NAME "v-line"
           TYPE vector
           FILLED false
           POINTS
             0  0
             5  10
             10 0
           END
       END
   END

Example include files
^^^^^^^^^^^^^^^^^^^^^

.. code-block:: mapfile

   # BGS-Attribution.map
   # May be included at SERVICE and/or LAYER metadata level
   "WMS_ATTRIBUTION_LOGOURL_FORMAT" "image/gif"
   "WMS_ATTRIBUTION_LOGOURL_HREF" "http://ogc.bgs.ac.uk/img/bgs_c_t_275x60.gif"
   "WMS_ATTRIBUTION_LOGOURL_HEIGHT" "60"
   "WMS_ATTRIBUTION_LOGOURL_WIDTH" "275"
   "WMS_ATTRIBUTION_ONLINERESOURCE" "http://www.bgs.ac.uk/"
   "WMS_ATTRIBUTION_TITLE" "British Geological Survey (BGS)"

   "WMS_AUTHORITYURL_NAME" "BritishGeologicalSurvey"
   "WMS_AUTHORITYURL_HREF" "http://data.bgs.ac.uk/ref/BritishGeologicalSurvey"

.. code-block:: mapfile

   # BGS-service-std-output-plus1.map
   # Included at the map level to extend or modify the output formats available to the service
   # For example we can use this to enable GeoJSON and zipped shapefie as formats for WFS
   #IMAGECOLOR: Background color for the map canvas
   IMAGECOLOR 255 255 255
   IMAGETYPE png
   OUTPUTFORMAT
       NAME png
       DRIVER "AGG/PNG"
       MIMETYPE "image/png"
       IMAGEMODE RGBA
       EXTENSION "png"
       TRANSPARENT ON
       FORMATOPTION "INTERLACE=ON,TRANSPARENT=ON"
   END
   OUTPUTFORMAT
       NAME "SHAPEZIP"
       DRIVER "OGR/ESRI Shapefile"
       MIMETYPE "application/shapefile"
       FORMATOPTION "STORAGE=filesystem"
       FORMATOPTION "FORM=zip"
       FORMATOPTION "FILENAME=shape.zip"
   END
   OUTPUTFORMAT
       NAME "SPATIALITEZIP"
       DRIVER "OGR/SQLITE"
       MIMETYPE "application/spatialite"
       FORMATOPTION "DSCO:SPATIALITE=YES"
       FORMATOPTION "STORAGE=memory"
       FORMATOPTION "FORM=zip"
       FORMATOPTION "FILENAME=result.db"
   END
   OUTPUTFORMAT
       NAME "MIDMIF"
       DRIVER "OGR/MapInfo File"
       FORMATOPTION "STORAGE=filesystem"
       FORMATOPTION "FORM=multipart"
       FORMATOPTION "DSCO:FORMAT=MIF"
       FORMATOPTION "FILENAME=result.mif"
   END
   OUTPUTFORMAT
       NAME "MultiMIDMIF"
       DRIVER "OGR/MapInfo File"
       FORMATOPTION "STORAGE=filesystem"
       FORMATOPTION "FORM=multipart"
       FORMATOPTION "DSCO:FORMAT=MIF"
       FORMATOPTION "FILENAME=result"
   END
   OUTPUTFORMAT
       NAME "CSV"
       DRIVER "OGR/CSV"
       MIMETYPE "text/csv"
       FORMATOPTION "LCO:GEOMETRY=AS_WKT"
       FORMATOPTION "STORAGE=filesystem"
       FORMATOPTION "FORM=simple"
       FORMATOPTION "FILENAME=result.csv"
   END
   OUTPUTFORMAT
       NAME "CSVSTREAM"
       DRIVER "OGR/CSV"
       MIMETYPE "text/csv; streamed"
       FORMATOPTION "LCO:GEOMETRY=AS_WKT"
       FORMATOPTION "STORAGE=stream"
       FORMATOPTION "FORM=simple"
       FORMATOPTION "FILENAME=result.csv"
   END
   OUTPUTFORMAT
       NAME "OGRGML"
       DRIVER "OGR/GML"
       MIMETYPE "text/xml; subtype=gml/2.1.2; driver=ogr"
       FORMATOPTION "STORAGE=memory"
       FORMATOPTION "FORM=multipart"
       FORMATOPTION "FILENAME=result.gml"
   END
   OUTPUTFORMAT
       NAME "GeoJSON"
       DRIVER "OGR/GEOJSON"
       MIMETYPE "application/json; subtype=geojson"
       FORMATOPTION "STORAGE=stream"
       FORMATOPTION "FORM=SIMPLE"
   END


Debugging common errors
^^^^^^^^^^^^^^^^^^^^^^^

This section is added to help you debug common errors in your Mapfile.

Symbol definition error
"""""""""""""""""""""""

getString(): Symbol definition error.  Parsing error near (*matching text*):(line *line-number*)

This error may occur when your layer classes have a name which includes an apostrophe or other quotation mark that matches the quotation marks used to delimit the CLASS name.  For example if your class name is delimited using single quotes such as below and your class name includes a word with a single quote (d'Irma), you will get this error.

.. code-block:: mapfile

   NAME 'Formation d'Irma : calcaire, dolomie à tromatolites, argilite'

You can correct the error by swapping the file name delimiters to double quotes (as below), in the CLASS name causing the problem; you don’t need to change all the delimiters in all the CLASS names in the Mapfile, just the one(s) with the problem.

.. code-block:: mapfile

   NAME "Formation d'Irma : calcaire, dolomie à stromatolites, argilite"

Unknown identifier
""""""""""""""""""

loadLayer(): Unknown identifier. Parsing error near (*matching text*):(line *line-number*)

This error can occur when you are missing an enclosing KEYWORD in the Mapfile.  For example in the below example, the CLASS keyword has been commented out, leaving the STYLE section uncommented; STYLE is now found in an unexpected position in the Mapfile, resulting in an error.

.. code-block:: mapfile

   #CLASS
       STYLE
           COLOR 161 8 0
           MINSIZE 1
           MAXSIZE 10
       END #style
   #END #class

Missing magic string
""""""""""""""""""""

When running a GetFeatureInfo request with the info\_format set as text/html, you will get an error like the below, if you do not include a magic string in each of your HTML template documents.

Content-type: text/xml isValidTemplate(): Web application error. Missing magic string, *template-file* doesn’t look like a MapServer template.

You need to add **<!-- MapServer Template -->** to the top of ALL templates.

Example the exemplar template query\_footer.html is:

.. code-block:: html

   <!-- MapServer Template -->
   </body>
   </html>

The recently updated exemplar service kits include this NEW requirement, but those updating from older services might miss this.

`More information on this and related issues. <http://mapserver.org/development/rfc/ms-rfc-56.html>`_

Connecting to a database
^^^^^^^^^^^^^^^^^^^^^^^^

If your data is stored in a database you can access it by setting the CONNECTION and CONNECTIONTYPE directives (to specify the connection) and the DATA directive (to specify the data you want to retrieve or query). These directives are put in the LAYER section of your map file.

The below example shows a typical connection to a PostgreSQL/PostGIS database.  Such a connection might be shared across several layers in your service.

.. code-block:: mapfile

       CONNECTION "user='your_user_name' password='your_password' dbname='m4eu' host='localhost' port='5432'"
       CONNECTIONTYPE postgis

The below two examples show the types of query that you might want to do to provide your layer.  The first example is a query to retrieve some data from a table based on an attribute value.  The second example is a more straight forward query that you might use when you want to retrieve all the data from a table.

.. code-block:: mapfile

       DATA "shape FROM (SELECT * FROM commodityresourceview_vw WHERE commodity IN ('copper','lead','tin','zinc')) AS base_metal USING UNIQUE identifier USING srid=4258"

.. code-block:: mapfile

       DATA "geom FROM public.metallic_min"

If your MapServer software has been compiled to include Oracle Spatial then you can connect and query the database like in the below example.

..  code-block:: mapfile

       CONNECTION "your_user_name/your_password@your_server_ip:1521/your_database_name"
       CONNECTIONTYPE oraclespatial

       DATA "ITEM_SHAPE_WGS84 FROM PUBLISHED.QL_ACD_ITEM_PLY_WEB_UG USING UNIQUE ITEM_INDEX_ID SRID 4326"

If you have your data in a file geodatabase, then similarly you could connect like below. Note you may also need to set the CONFIG "PGEO_DRIVER_TEMPLATE" and CONFIG "OGR_SKIP"  directives in the MAP section of the map file, as shown in the General map configuration section.

..  code-block:: mapfile

       CONNECTION "data2/OGE.mdb"
       CONNECTIONTYPE ogr

       DATA "V5_625k_ONEGEOLOGY_FAULTS_AT_SURFACE"

For more details on connecting to a database see the `MapServer Data Input pages <https://mapserver.org/input/index.html>`_


WMS
---

We provide two exemplar MapServer services, the first is based on a simple raster file, and is used to illustrate a basic WMS, the second uses a vector datasource (shapefiles) to illustrate how to configure a more advanced WMS (and may also be used for a Simple Feature WFS).

Raster image data exemplar (LAYER configuration)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

An example of adding a PNG layer is included in the BGS\_Bedrock\_Raster\_Map application.  The LAYER section is reproduced below for reference.  This data was simply created as a raster from the bedrock shapefile for the purposes of serving as an example.  In this case we won’t be setting up a response to GetFeatureInfo request; we are just returning a coloured map.  There is more `detailed documentation <http://www.mapserver.org/input/raster.html>`_ , in particular as regards efficient serving of large images, using 8-bit vs. 24-bit images, tiling etc.

Example extract from Mapfile below:

.. code-block:: mapfile

   LAYER
       NAME "BGS_625k_BAR"
       DATA "bedrock625ll.png"
       DUMP TRUE

       METADATA
           "WMS_ABSTRACT" "GBR BGS 1:625k Bedrock Age"

           "WMS_DATAURL_FORMAT" "text/html"
           "WMS_DATAURL_HREF" "http://www.bgs.ac.uk/discoverymetadata/13480426.html"

           "WMS_KEYWORDLIST" "OneGeology,bedrock,chronostratigraphy,continent@Europe,subcontinent@Northern Europe,geographicarea@United Kingdom,DS_DATE@2011-06-15,age,dataprovider@British Geological Survey,DS_TOPIC@geoscientificInformation,geology,serviceprovider@British Geological Survey"

           "WMS_METADATAURL_FORMAT" "application/vnd.iso.19139+xml"
           "WMS_METADATAURL_HREF" "http://.../geonetwork/srv/en/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&ID=ac9f8250-3ae5-49e5-9818-d14264a4fda4&"
           "WMS_METADATAURL_TYPE" "TC211"

           "WMS_SRS" "EPSG:4326 EPSG:3857 EPSG:27700 EPSG:4258"

           "WMS_STYLE" "default"
           "WMS_STYLE_DEFAULT_LEGENDURL_HEIGHT" "353"
           "WMS_STYLE_DEFAULT_LEGENDURL_WIDTH" "253"
           "WMS_STYLE_DEFAULT_LEGENDURL_FORMAT" "image/png"
           # The legendURL must be accessible externally, so do not use ‘localhost’ or ‘127.0.0.1’
           "WMS_STYLE_DEFAULT_LEGENDURL_HREF" "http://.../BGS_Bedrock_Geology/bedrockAgeLegend.png"

           "WMS_TITLE" "GBR BGS 1:625k Bedrock Age"
       END

       PROCESSING "CLOSE_CONNECTION=DEFER"

       PROJECTION
           "init=EPSG:4326"
       END

       STATUS ON
       TOLERANCE 10
       TYPE RASTER
   END


Vector data exemplar (LAYER configuration)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The example file includes the following shapefile based layers:

* UK bedrock geology classified by lithology, lithostratigraphy, and age
* UK superficial geology classified by lithology and lithostratigraphy.

These are typical of the sorts of layer expected for OneGeology but you may have slightly different theme layers and slightly different available classification schemes.  Please consult with the OneGeology helpdesk if you are uncertain about exactly what layers and classifications to serve.

The fields you will need to edit for each **LAYER** section are described below.  The NAME must be unique for each layer.  This is a identifier used by WMS clients to select layers rather than being for human consumption.  It is recommended that the NAME does not contain spaces, special characters, or begin with a number (which could cause problems through interfaces such as OGC services. The OneGeology catalogue service requires that the NAMEs are unique within all the OneGeology layers we have decided some naming conventions as shown in the example.  These are described explicitly in the :ref:`OneGeology Profile <service_provision_onegeology_profile>`.

DATA should specify the name of your shapefile.  The HEADER, TEMPLATE, and FOOTER values refer to files with snippets of HTML template which format the results of GetFeatureInfo requests when requested in text/html format.  The examples have been written for the data fields in the example shapefiles; it should be straightforward for you to edit them to match the fields in your shapefiles.  The PROJECTION section should specify the coordinate system that your data is actually in.  This might not be EPSG:4326 if you have your data in some regional projected system.  However, as most OneGeology clients will want to retrieve your data in the EPSG:4326 system we suggest it will be better for performance reasons to convert your data files to EPSG:4326 rather than have MapServer convert them on-the-fly in response to requests.

.. code-block:: mapfile

  LAYER
       NAME "GBR_BGS_625k_BLT" #Bedrock lithology
       TYPE POLYGON
       STATUS ON
       DATA "bedrock625ll"
       TRANSPARENCY 100
       TOLERANCE 0
       TOLERANCEUNITS pixels
       TRANSFORM TRUE
       PROCESSING "CLOSE_CONNECTION=DEFER"
       HEADER "tmpl/bedrock_lithology_query_header.html"
       TEMPLATE "tmpl/bedrock_lithology_query_body.html"
       FOOTER "tmpl/bedrock_lithology_query_footer.html"
       PROJECTION
           "init=epsg:4326"
       END

In the METADATA section you should edit the following values:

WMS\_TITLE
   the human readable layer name and should follow the conventions in the OneGeology Profile

WMS\_ABSTRACT
   expands on the title with any extra information you feel would be useful.

WMS\_SRS
   These values specify which coordinate systems your WMS can supply the data in and **MUST** include at least **EPSG:4326**. Other coordinate systems are up to you; for example you may wish to include the EPSG:3857 (spherical mercator) coordinate system, which is used by several web mapping clients such as Bing Maps, Google Maps, and Yahoo maps.

GML\_INCLUDE\_ITEMS and WMS\_INCLUDE\_ITEMS
   These items will depend on the data fields in your shapefile and which ones you wish to make available by a GetFeatureInfo request.  Items should be a comma separated list of field names.  These should be the same as the fields included in the HTML templates above. It is optional to include any information here but obviously if you have fields with geological unit names or ages they would be useful to include. The GML prefix applies to the GML response only and the WMS prefix applies to the plain text response only.

WMS\_METADATAURL\_HREF and WMS\_DATAURL\_HREF
   are supposed to contain URLs for web pages which describe the dataset used for the layer in more detail.  It is possible that you may already have suitable web pages on your organization’s website, or you may wish to create suitable pages to be served by this same server.  These URL’s give users of your WMS service quick and easy links back to your web pages that may describe your available data offerings in more detail. The differences between the metadataurl and dataurl are:

WMS\_METADATAURL\_HREF
   the metadataurl must only link to a page which describes your layer data  corresponding to either the TC211/ISO:19115:2003 or FGDC-STD-001-1998 metadata standards.  See  :ref:`service_provision_onegeology_profile_core_metadata` for the core metadata required to be TC211/ISO:19115:2003 compliant

WMS\_DATAURL\_HREF
   the dataurl is to be used when you have some layer metadata that doesn’t conform to either of these standards.

The UK geology layer examples point to some pre-existing web pages on the BGS website which were suitable so that you can get an idea of what you might use for your own data.

.. code-block:: mapfile

   METADATA
       "GML_FEATUREID" "ID"
       "GML_INCLUDE_ITEMS" "RCS_D"

       "OWS_ABSTRACT" "GBR BGS 1:625k scale Bedrock Lithology"
       "OWS_DATAURL_FORMAT" "text/html"
       "OWS_DATAURL_HREF" "http://www.bgs.ac.uk/discoverymetadata/13480426.html"
       "OWS_KEYWORDLIST" "OneGeology,bedrock,lithology,continent@Europe,subcontinent@Northern Europe,geographicarea@United Kingdom,geology,dataprovider@British Geological Survey,DS_TOPIC@geoscientificInformation,serviceprovider@British Geological Survey,DS_DATE@2011-06-15,thematic@Bedrock,thematic@Lithology"
       "OWS_METADATAURL_HREF" "http://.../geonetwork/srv/en/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecordById&ID=9df8df52-d788-37a8-e044-0003ba9b0d98&"
       "OWS_METADATAURL_TYPE" "TC211"
       "OWS_TITLE" "GBR BGS 1:625k Bedrock Lithology"

       "WFS_ENCODING" "UTF-8"
       "WFS_GETFEATURE_FORMATLIST" "csv,csvstream,ogrgml,shapezip,midmif,multimidmif,geojson"
       "WFS_METADATAURL_FORMAT" "text/xml"
       "WFS_SRS" "EPSG:4326 EPSG:27700 EPSG:3034 EPSG:3857 EPSG:4258"

       "WMS_FEATURE_INFO_MIME_TYPE" "text/html,application/vnd.ogc.gml,text/plain"
       "WMS_GETMAP_FORMATLIST" "image/png,image/jpeg,image/tiff,application/x-pdf,image/svg+xml"
       "WMS_INCLUDE_ITEMS" "RCS_D"
       "WMS_METADATAURL_FORMAT" "application/xml; charset=UTF-8"
       "WMS_SRS" "CRS:84 EPSG:27700 EPSG:3034 EPSG:3413 EPSG:3857 EPSG:4258 EPSG:4326"
   END

The CLASS related items are the most complicated.  These sections are setting up the legend and colour scheme of your map polygons, lines and points. You will need a separate item for each rock type or lithology you have in your data.  This will depend on your data and which field in your shapefile (or other datasource) you are going to use for colouring the map.  The example below specifies that the RCS\_D field will be used for specifying which colour to use with the CLASSITEM VALUE.  Then for each CLASS section the EXPRESSION specifies the value of RCS\_D this colour will apply to and the COLOR and BACKGROUNDCOLOR give the respective RGB colour values.

.. code-block:: mapfile

   CLASSITEM 'RCS_D'
   CLASS
       NAME 'ANORTHOSITE'
       EXPRESSION 'ANORTHOSITE'
       #RASTERFILL_STYLE_SOLID
       STYLE
           COLOR 237 237 237
           BACKGROUNDCOLOR 255 255 255
       END #style
   END #class

  #...  more classes needed to assign colours

  # for each value of RCS_D

Colour codes for the lithostratigraphical and lithology layers are specific to the British Geological Survey, you should use the codes used by your geological survey.  However, for OneGeology it has been agreed, where possible, to serve a chronostratigraphic age layer using the new `IUGS 2009 colour scheme <https://www.seegrid.csiro.au/wiki/pub/CGIModel/GeologicTime/ISChart2009.pdf>`_ .  This will give some form of harmonization between the different chronostratigraphic layers served by the contributing geological surveys and this is only possible where such an internationally agreed scheme exists.  In this case the British Geological Survey had to refine, re-allocate, and ‘map’ its internal ages to fit the IUGS 2009 one.  The file ‘ICSClasses.txt’ contains a full list of names and CLASS definitions for the appropriate colours for all the IUGS 2009 colours.  In the Mapfile we have commented out the terms that are not actually used in the BGS map; please do the same for your map.

Configuring HTML query templates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

All templates must include the **<!-- MapServer Template -->** statement on the first line of the file.

You may include any HTML and even some JavaScript in your templates, all entities must be properly encoded.

The output of attribute values from the datasource or environment variables are denoted by square brackets, so in the below example we are outputting the value of the RCS\_D attribute as part of an HTML table in the bedrock lithology layer of our exemplar service.

.. code-block:: html

   <!-- MapServer Template -->
   <!-- LAYER QUERY BODY -->
   <tr>
   <td>[RCS_D]</td>
   </tr>

The following are examples of how we might configure our WMS GetFeatureInfo responses


Debugging your requests
"""""""""""""""""""""""

In this example we are using MapServer environment variables to help us debug the request that was used to generate the response

.. code-block:: html

   <!-- MapServer Template -->
   <!-- ERL footer (start)-->
   <!-- Request URL: -->
   <h3>Debug</h3>
   <div id="gfiref">
   <p>The <a href="http://ogcdev.bgs.ac.uk/cgi-bin/BGS_EN_MINERALS/ows?SERVICE=WMS&amp;VERSION=1.3.0&amp;REQUEST=[REQUEST]&amp;BBOX=[BBOX]&amp;CRS=[CRS]&amp;WIDTH=[WIDTH]&amp;HEIGHT=[HEIGHT]&amp;INFO_FORMAT=text/html&amp;STYLES=&amp;bgcolor=0xFFFFFF&amp;transparent=TRUE&amp;language=eng&amp;FORMAT=image/png&amp;LAYERS=[LAYERS]&amp;QUERY_LAYERS=[QUERY_LAYERS]&amp;I=[I]&amp;J=[J]&amp;">request</a> used to generate this report was:</p>
   <pre>
   http://ogcdev.bgs.ac.uk/cgi-bin/BGS_EN_MINERALS/ows?
     SERVICE=WMS&amp;
     VERSION=1.3.0&amp;
     REQUEST=[REQUEST]&amp;
     BBOX=[BBOX]&amp;
     CRS=[CRS]&amp;
     WIDTH=[WIDTH]&amp;
     HEIGHT=[HEIGHT]&amp;
     INFO_FORMAT=text/html&amp;
     STYLES=&amp;
     bgcolor=0xFFFFFF&amp;
     transparent=TRUE&amp;
     language=eng&amp;
     FORMAT=image/png&amp;
     LAYERS=[LAYERS]&amp;
     QUERY_LAYERS=[QUERY_LAYERS]&amp;
     I=[I]&amp;
     J=[J]&amp;
     </pre>
   </div>
   <h3>Data retrieval tests</h3>
   <p><b>WFS GetFeature for area of GetMap request</b><br />
   <a href="http://ogcdev.bgs.ac.uk/cgi-bin/BGS_EN_MINERALS/ows?service=WFS&amp;request=GetFeature&amp;version=2.0.0&amp;typename=erl:CommodityResourceView&amp;CRS=[CRS]&amp;bbox=[BBOX][CRS],&amp;">http://ogcdev.bgs.ac.uk/cgi-bin/BGS_EN_MINERALS/ows?service=WFS&amp;request=GetFeature&amp;version=2.0.0&amp;typename=erl:CommodityResourceView&amp;CRS=[CRS]&amp;bbox=[BBOX],[CRS]&amp;</a></p>
   <!-- ERL footer (end)-->



Handling fields for which you have no data
""""""""""""""""""""""""""""""""""""""""""

As GeoSciML-Lite requires data (or URIs pointing to null value reasons) for data that was not required in the OneGeology-Europe services, you have a few options with MapServer if you don't have the required data (for example a specification\_uri for all features). Option 1 would be to create a column in the data source and populate the rows with null value URIs (such as for example with the value http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown/). Option 2 would be to populate the missing values within the GetFetaureInfo request template, such as below:

.. code-block:: html

   <!-- MapServer Template -->
   <dl>
       <dt>identifier</dt>
       <dd>[OBJECTID]</dd>
       <dt>name</dt>
       <dd>[Name]</dd>
       <dt>faultType_uri</dt>
       <dd>[faultType_uri]</dd>
       <dt>positionalAccuracy (m)</dt>
       <dd>[PositionalAccuracy]</dd>
       <dt>movementType_uri</dt>
       <!-- Here we provide an INSPIRE nil reason for the missing movementType_uri -->
       <dd>http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown</dd>
       <dt>deformationStyle_uri</dt>
       <!-- Here we provide an INSPIRE nil reason for the missing deformationStyle_uri -->
       <dd>http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown</dd>
       <dt>representativeOlderAge_uri</dt>
       <dd>[representativeOlderAge_uri]</dd>
       <dt>representativeYoungerAge_uri</dt>
       <dd>[representativeYoungerAge_uri]</dd>
       <dt>representativeAge_uri</dt>
       <dd>[representativeAge_uri]</dd>
       <dt>specification_uri</dt>
       <!-- Here we supply a link to our Feature (using our Simple Fetaure GeoSciML-Lite WFS).
       This information isn't in the database and we can update to a full GeoSciML response when available
       In the actual template we have this as a link -->
       <dd>http://ogc2.bgs.ac.uk/cgi-bin/BGS_OGE_Bedrock_and_Surface_Geology_in3/ows?service=WFS&amp;
       request=GetFeature&amp;version=1.1.0&amp;FeatureID=GBR_BGS_EN_1M_Surface_Fault.[OBJECTID]&amp;</dt>
       <!-- Here we supply a link to some metadata for our datasource that isn't in the database
       In the actual template we have this as a link -->
       <dd>http://metadata.bgs.ac.uk/geonetwork/srv/en/iso19139.xml?id=6075</dd>
   </dl>


Using JavaScript
""""""""""""""""

Here we embed some JavaScript into a response to give a TimeSeries schart for the data point selected

.. code-block:: html

   <!--MapServer Template -->
   <table summary="Query response for Terrafirma 1:5k ground motion WMS layer" class="hasTS">
   <thead><tr><th class="title"><b>Terrafirma 1:5000 ground motion report</b></th></tr></thead>
   <tfoot><tr><td title="Time series data for selected point">
   <script type="text/javascript"><!--
   var [Id]_tsline=[['1992-05-11',[D19920511]],['1993-02-15',[D19930215]],['1993-03-22',[D19930322]],['1993-05-31',[D19930531]],['1993-08-09',[D19930809]],['1993-10-18',[D19931018]],['1993-11-22',[D19931122]],['1995-04-19',[D19950419]],['1995-05-24',[D19950524]],['1995-05-25',[D19950525]],['1995-06-28',[D19950628]],['1995-06-29',[D19950629]],['1995-08-02',[D19950802]],['1995-08-03',[D19950803]],['1995-09-06',[D19950906]],['1995-10-11',[D19951011]],['1995-10-12',[D19951012]],['1995-12-21',[D19951221]],['1996-02-28',[D19960228]],['1996-02-29',[D19960229]],['1996-04-03',[D19960403]],['1996-04-04',[D19960404]],['1996-05-08',[D19960508]],['1996-05-09',[D19960509]],['1996-06-12',[D19960612]],['1996-07-17',[D19960717]],['1996-08-22',[D19960822]],['1996-10-31',[D19961031]],['1996-12-05',[D19961205]],['1997-01-09',[D19970109]],['1997-02-13',[D19970213]],['1997-03-20',[D19970320]],['1997-04-24',[D19970424]],['1997-05-29',[D19970529]],['1997-08-07',[D19970807]],['1997-09-11',[D19970911]],['1997-10-16',[D19971016]],['1997-11-20',[D19971120]],['1997-12-25',[D19971225]],['1998-01-29',[D19980129]],['1998-03-05',[D19980305]],['1998-04-09',[D19980409]],['1998-05-14',[D19980514]],['1998-06-18',[D19980618]],['1998-07-23',[D19980723]],['1998-08-27',[D19980827]],['1998-10-01',[D19981001]],['1998-11-05',[D19981105]],['1998-12-10',[D19981210]],['1999-02-18',[D19990218]],['1999-03-25',[D19990325]],['1999-07-08',[D19990708]],['1999-08-11',[D19990811]],['1999-08-12',[D19990812]],['1999-09-15',[D19990915]],['1999-09-16',[D19990916]],['1999-10-20',[D19991020]],['1999-10-21',[D19991021]],['1999-11-25',[D19991125]],['1999-12-30',[D19991230]],['2000-02-02',[D20000202]],['2000-02-03',[D20000203]],['2000-03-09',[D20000309]],['2000-04-13',[D20000413]],['2000-11-09',[D20001109]],['2000-12-14',[D20001214]],['2001-10-25',[D20011025]],['2002-10-10',[D20021010]],['2002-12-19',[D20021219]],['2003-05-08',[D20030508]],['2004-01-08',[D20040108]],['2004-07-01',[D20040701]],['2004-10-14',[D20041014]],['2004-12-23',[D20041223]],['2005-01-27',[D20050127]]]; //-->
   </script>
   </td></tr></tfoot>
   <tbody>
   <tr><td>Point ID: <b>[Id]</b></td></tr>
   ...
   <tr><td>Azimuth: <b>[Azimuth]</b></td></tr>
   <tr><td id="[Id]_chart1" class="tschart" title="Time series chart for selected point"></td></tr>
   <tr><th title="Header for time series data" class="gfiTableHeader">Measurements on dates (YYYY-MM-DD) are in mm</th></tr>
   ...
   <tr><td><!-- D20050127 -->2005-01-27: <b>[D20050127]</b></td></tr>
   </tbody>
   </table>
   <script type="text/javascript"><!--
       $("#[Id]_chart1:hidden").show();
       var plot1 = $.jqplot('[Id]_chart1', [[Id]_tsline], {
           title:'Time series plot for selected point',
           axes:{xaxis:{renderer:$.jqplot.DateAxisRenderer}},
           series:[{lineWidth:3, markerOptions:{style:'circle'}}]
       }); // -->
   </script>

Configuring group layering
^^^^^^^^^^^^^^^^^^^^^^^^^^

In some situations, for example when you have too many individual layers, or if you have to comply with some strict naming conventions (such as INSPIRE) you may need to consider configuring group layering.  In group layering you nest one set of layers inside another (group) layer, you can still call (e.g. make a GetMap request on) any of the individual grouped layers or you can call all the grouped layers at the same time using the grouping layer.  For example in the below MapServer GetCapabilities response on a service with group layers you could make a GetMap request on the group layer called GE.GeologicFault and would get a map comprising both the grouped layers (GE.GeologicFault\_GBR\_BGS\_EN\_1M\_Surface and GE.GeologicFault\_GBR\_BGS\_EN\_1M\_Bedrock), or you could perform a GetMap request on either of the individual layers.

.. figure:: images/GroupLayering.jpg
  :width: 1032
  :height: 350
  :alt: Group layering in a GetCapabilities response

  Group layering in a GetCapabilities response

To configure group layering in MapServer first you need to configure a service with all the layers that need to be grouped.  The next step is to add a **GROUP** keyword (with the name of the group layer) into the LAYER section of all the layers you want to be grouped together. Finally, in ONE of the METADATA sections of the layers you want to group you need to add a **WMS\_GROUP\_TITLE** and a **WMS\_GROUP\_ABSTRACT** value.  For example in the MapServer service configuration file for the above GetCapabilities response we have the following configuration:

.. code-block:: mapfile
  :emphasize-lines: 2,40,41,46

  LAYER
      GROUP "GE.GeologicFault"
      NAME "GE.GeologicFault_GBR_BGS_EN_1M_Surface"
      TYPE LINE
      STATUS ON
      EXTENT -8.01697 49.9678 0.715821 60.8368
      MAXSCALEDENOM 3000000
      CONNECTIONTYPE ogr
      CONNECTION "data2/OGE.mdb"
      DATA "V5_625k_ONEGEOLOGY_FAULTS_AT_SURFACE"
      PROCESSING "CLOSE_CONNECTION=DEFER"
      OPACITY 100
      TOLERANCE 10
      TOLERANCEUNITS pixels
      TRANSFORM TRUE
      # Same template OK for surface and bedrock faults
      HEADER "templ/OGE_1M_bedrock_GeologicStructure_headerGSMLP.html"
      TEMPLATE "templ/OGE_1M_bedrock_GeologicStructure_bodyGSMLP.html"
      FOOTER "templ/OGE_1M_bedrock_GeologicStructure_footerGSMLP.html"
      PROJECTION
          "init=epsg:4326"
      END
      METADATA
          INCLUDE "../DefaultMapIncludes/BGS-Attribution.map"
          "OWS_TITLE" "BGS 1:1 Million surface geologic structure"
          "OWS_ABSTRACT" "BGS surface fault geology originally created for OneGeology Europe"
          "OWS_EXTENT" "-8.01697 49.9678 0.715821 60.8368"
          "OWS_SRS" "CRS:84 EPSG:27700 EPSG:3034 EPSG:4258 EPSG:4326"
          "GML_INCLUDE_ITEMS" "all"
          "GML_FEATUREID" "OBJECTID"
          "OWS_METADATAURL_HREF" "http://www.bgs.ac.uk/discoverymetadata/13480426.html"
          "OWS_METADATAURL_FORMAT" "text/html"
          "OWS_METADATAURL_TYPE" "TC211"
          "OWS_DATAURL_HREF" "http://www.bgs.ac.uk/products/digitalmaps/digmapgb_625.html"
          "OWS_DATAURL_FORMAT" "text/html"
          "OWS_KEYWORDLIST" "OneGeology,continent@Europe,subcontinent@Northern Europe,geographicarea@United Kingdom,serviceprovider@British Geological Survey,dataprovider@British Geological Survey,thematic@Harmonized structure,thematic@Surface geology,DS_TOPIC@geoscientificinformation,DS_DATE@2010,thematic@Structure,thematic@Fault"
          "WFS_SRS" "EPSG:4326 EPSG:27700 EPSG:3034 EPSG:4258"
          "WMS_GROUP_TITLE" "Geologic Faults"
          "WMS_GROUP_ABSTRACT" "MappedFeature (spatial objects whose specification property is of type ShearDisplacementStructure)"
      END
      INCLUDE "FaultTypeClassesIn3.map"
  END
  LAYER
      GROUP "GE.GeologicFault"
      NAME "GE.GeologicFault_GBR_BGS_EN_1M_Bedrock"

      CONNECTION "data2/OGE.mdb"
      CONNECTIONTYPE ogr

      DATA "V5_625k_ONEGEOLOGY_FAULTS"
      EXTENT -8.09708 49.9678 0.781767 60.8368

      FOOTER "templ/OGE_1M_bedrock_GeologicStructure_footerGSMLP.html"
      HEADER "templ/OGE_1M_bedrock_GeologicStructure_headerGSMLP.html"
      TEMPLATE "templ/OGE_1M_bedrock_GeologicStructure_bodyGSMLP.html"

      MAXSCALEDENOM 3000000

      METADATA
           INCLUDE "../DefaultMapIncludes/BGS-Attribution.map"
           "GML_INCLUDE_ITEMS" "all"
           "GML_FEATUREID" "OBJECTID"
           "OWS_ABSTRACT" "BGS bedrock fault geology  originally created for OneGeology Europe. \
           The bedrock fault layer shows faults with superficial deposits (Quaternary and Recent) removed."
           "OWS_DATAURL_FORMAT" "text/html"
           "OWS_DATAURL_HREF" "http://www.bgs.ac.uk/products/digitalmaps/digmapgb_625.html"
           "OWS_EXTENT" "-8.09708 49.9678 0.781767 60.8368"
           "OWS_KEYWORDLIST" "OneGeology,continent@Europe,subcontinent@Northern Europe,geographicarea@United Kingdom,serviceprovider@British Geological Survey,dataprovider@British Geological Survey,thematic@Harmonized structure,thematic@Bedrock,DS_TOPIC@geoscientificinformation,DS_DATE@2010,thematic@Structure,thematic@Fault"
           "OWS_METADATAURL_FORMAT" "text/html"
           "OWS_METADATAURL_HREF" "http://www.bgs.ac.uk/discoverymetadata/13480426.html"
           "OWS_METADATAURL_TYPE" "TC211"
           "OWS_SRS" "CRS:84 EPSG:27700 EPSG:3034 EPSG:4258 EPSG:4326"
           "OWS_TITLE" "BGS 1:1 Million bedrock geologic structure"
           "WFS_SRS" "EPSG:4326 EPSG:27700 EPSG:3034 EPSG:4258"
      END

      OPACITY 100
      PROCESSING "CLOSE_CONNECTION=DEFER"

      PROJECTION
           "init=epsg:4326"
      END

      STATUS ON
      TOLERANCE 10
      TOLERANCEUNITS pixels
      TRANSFORM TRUE
      TYPE LINE

      INCLUDE "FaultTypeClassesIn3.map"
  END


Simple feature WFS
------------------

Whilst MapServer is not able to provide a complex feature WFS (such as is required to supply GeoSciML 4.0)  it is possible to configure it to provide a simple feature WFS.  If you have already set up a WMS with a vector data source it is possible with only minor additions to the SERVER and LAYER configuration to enable a WFS service.  If your data supports it, you can also configure a portrayal service, to provide a GeoSciML-Lite simple feature service for example.


A WFS service will be enabled by the presence of an **OWS\_ENABLE\_REQUEST** or **WFS\_ENABLE\_REQUEST** statement in the MAP > WEB > METADATA section, or in the LAYER > METADATA section.

.. code-block:: mapfile

   # The following statment enables all operations for all OGC services
   "OWS_ENABLE_REQUEST" "*"

   # The following statement disables all WFS operations
   "WFS_ENABLE_REQUEST" "!*"

   # The following statement disables GetCapabilities and DescribeFeatureType operations but allows GetFeature
   # If !GetCapabilities is set in a LAYER > METADATA section level, and in the WEB > METADATA section
   # WFS GetCapabilities is enabled, the feature type (layer)  won't appear in the WFS GetCapabilities response.
   "WFS_ENABLE_REQUEST" "!GetCapabilities !DescribeFeatureType GetFeature"


The MapServer WFS Server pages http://mapserver.org/ogc/wfs_server.html give full details of the options to configure a WFS service but below we give some hints to get you going with ERML-Lite and GeoSciML-Lite schemas.

In the MAP > WEB > METADATA section you can set the default WFS language, and also configure a namespace prefix and uri like:

.. code-block:: mapfile

   "WFS_LANGUAGES" "eng"

   # For GeoSciML-Lite use:
   "WFS_NAMESPACE_PREFIX" "gmlsp"
   "WFS_NAMESPACE_URI" "http://xmlns.geosciml.org/geosciml-portrayal/4.0"

   # ERML-Lite use:
   "WFS_NAMESPACE_PREFIX" "erl"
   "WFS_NAMESPACE_URI" "http://xmlns.earthresourceml.org/earthresourceml-lite/1.0"


In any LAYER > METADATA section you can define any number of GML constants. You can use this mecahnism as a way to add nil values or other constant information that is missing from your data source but required by the GeoSciML-Lite schema, or simply because you wish to supply it.

In the below example we have used this mechanism to populate specification\_uri and metadata\_uri which were required with GeoSciML-Portrayal version 2; in the current GeoSciML-Lite 4.0 version these propreties are now optional.

.. code-block:: mapfile

   "GML_CONSTANTS" "specification_uri,metadata_uri"
   "GML_metadata_uri_TYPE" "string"
   "GML_metadata_uri_VALUE" "http://metadata.bgs.ac.uk/geonetwork/srv/en/iso19139.xml?id=6074"
   "GML_specification_uri_TYPE" "string"
   "GML_specification_uri_VALUE" "http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unpopulated/"

Once a constant has been defined for a layer, the constant can be accessed in a template using the standard notation.

In any LAYER > METADATA section you can specify which items in your datasource to include (or exclude) in your Feature response, so in this below example we are saying effectively include everything (GML\_INCLUDE\_ITEMS) except (GML\_EXCLUDE\_ITEMS).

.. code-block:: mapfile

   "GML_INCLUDE_ITEMS" "all"
   "GML_EXCLUDE_ITEMS" "AgeMax,AgeMin,EventEnvironment,EventProcess,Lithology_1,ProportionTerms_1,GeologicUnitPartRole_1,Lithology_2,ProportionTerms_2,GeologicUnitPartRole_2,Lithology_3,ProportionTerms_3,GeologicUnitPartRole_3,Lithology_4,ProportionTerms_4,GeologicUnitPartRole_4,Lithology_5,ProportionTerms_5,GeologicUnitPartRole_5,MetamorphicGrade,NameIndex,BodyMorphology,SamplingFrame,GUObservationMethod,GUPurpose,SHAPE_Length,SHAPE_Area,RELEASED,gu_id,mf_id"


In any LAYER > METADATA section you can specify an alias to be used in your feature response, so for example if your feature identifier is called OBJECTID in your database you can alias it to the required identifier, or if you want to change the case of a field (or property) from Name to name you would use:

.. code-block:: mapfile

   "GML_OBJECTID_ALIAS" "identifier"
   "GML_Name_ALIAS" "name"

You can specify your own grouping of the properties (and the order in which they appear) within a feature and give this grouping a name like below. If you have used any aliases you must reference the original name and not the alias value in the grouping, though the alias will appear in the output.

.. code-block:: mapfile

   "GML_GROUPS" "ShearDisplacementStructureView"
   "GML_ShearDisplacementStructureView_GROUP" "OBJECTID,Name,faultType,observationMethod,positionalAccuracy,faultType_uri,movementType_uri,deformationStyle_uri,representativeAge_uri,representativeOlderAge_uri,representativeYoungerAge_uri,specification_uri,metadata_uri"

By default MapServer outputs the geometry in a field called _msGeometry_ to change the name of the field to a value relevant to your schema you use GML\_GEOMETRIES, like:

.. code-block:: mapfile

   "GML_GEOMETRIES" "shape"


WCS
---

In the same way as WMS and WFS are enabled on a service, WCS operations are enabled using either the **OWS\_ENABLE\_REQUEST** or **WCS\_ENABLE\_REQUEST"** statement in the MAP > WEB > METADATA section (enabling WCS for all coverages) or in the LAYER > METADATA section for enabling operations on a per coverage (layer) basis.

For example:

.. code-block:: mapfile

   # The following statement enables all core WCS operations (GetCapabilities, GetCoverage and DescribeCoverage)
   "WCS_ENABLE_REQUEST" "*"

In addition to default metadata specified above a OneGeology WCS service should specify the following information in the MAP > WEB > METADATA.


.. code-block:: mapfile

   # You need to provide both an _ABSTRACT and a _DESCRIPTION to cover all WCS versions
   #============================================================================================#
   "WCS_ABSTRACT" "The European Marine Observation and Data Network (EMODnet) is a long term marine data initiative from the European Commission Directorate-General for Maritime Affairs and Fisheries (DG MARE) underpinning its Marine Knowledge 2020 strategy. EMODnet is a consortium of organisations assembling European marine data, data products and metadata from diverse sources in a uniform way. The main purpose of EMODnet is to unlock fragmented and hidden marine data resources and to make these available to individuals and organisations (public and private), and to facilitate investment in sustainable coastal and offshore activities through improved access to quality-assured, standardised and harmonised marine data which are interoperable and free of restrictions on use."

   "WCS_DESCRIPTION" "The European Marine Observation and Data Network (EMODnet) is a long term marine data initiative from the European Commission Directorate-General for Maritime Affairs and Fisheries (DG MARE) underpinning its Marine Knowledge 2020 strategy. EMODnet is a consortium of organisations assembling European marine data, data products and metadata from diverse sources in a uniform way. The main purpose of EMODnet is to unlock fragmented and hidden marine data resources and to make these available to individuals and organisations (public and private), and to facilitate investment in sustainable coastal and offshore activities through improved access to quality-assured, standardised and harmonised marine data which are interoperable and free of restrictions on use."

   "WCS_KEYWORDLIST" "OneGeology,infoCoverageAccessService,Europe,EMODnet,Bathymetry,MD_LANG@ENG,MD_DATE@2015-04-14"

   #============================================================================================#
   # "WCS_LABEL" Is MANDATORY metadata for WCS version 1.0.0 GetCapabilities in SERVICE and LAYER metadata.
   # "WCS_LABEL" should be the same value as the WCS_TITLE (which is used as its replacement in later WCS versions).
   #============================================================================================#
   "WCS_LABEL" "BGS EMODnet bathymetry"
   "WCS_TITLE" "BGS EMODnet bathymetry"

   # You need to list the default projection first
   "WCS_SRS" "EPSG:4326 EPSG:3031 EPSG:3034 EPSG:3413 EPSG:3857 EPSG:4258"

The following is an example of a coverage LAYER

.. code-block:: mapfile

   LAYER
       NAME "BGS_EMODNET_CentralMed-MCol"
       DATA "Adriatic Sea - Ionian Sea - Central Mediterranean [Multi Colour].tif"

       METADATA
           INCLUDE "../DefaultMapIncludes/BGS-Attribution.map"
           INCLUDE "emodnet-mcol-legend.map"
           "band1_BAND_DESCRIPTION" "Red"
           "band2_BAND_DESCRIPTION" "Green"
           "band3_BAND_DESCRIPTION" "Blue"
           "WCS_BAND_INTERPRETATION" "Colour"
           "WCS_BANDCOUNT" "3"
           "WCS_BAND_NAMES" "band1 band2 band3"
           "WCS_DESCRIPTION" "European Marine Observation and Data Network (EMODnet) bathymetry for the Adriatic Sea - Ionian Sea - Central Mediterranean region. Native data is multi-colour GeoTiff."
           "WCS_IMAGEMODE" "BYTE"
           "WCS_INTERVAL" "0 255"
           "WCS_LABEL" "Adriatic Sea - Ionian Sea - Central Mediterranean [Multi Colour]"
           "WCS_NATIVE_FORMAT" "image/tiff"
           "WCS_RANGESET_AXES" "bands"
           "WCS_RANGESET_DESCRIPTION" "Depth"
           #===================================================
           # "WCS_RANGESET_LABEL" is mandatory 1.0.0 metadata
           #===================================================
           "WCS_RANGESET_LABEL" "Red/Green/Blue colour interpretations"
           #===================================================
           # "WCS_RANGESET_NAME" is mandatory 1.0.0 metadata
           #===================================================
           "WCS_RANGESET_NAME" "band"
           "WCS_SIGNIFICANT_FIGURES" "3"
           "WCS_SIZE" "2977 3883"
           "OWS_ABSTRACT" "European Marine Observation and Data Network (EMODnet) bathymetry for the Adriatic Sea - Ionian Sea - Central Mediterranean region. Native data is multi-colour GeoTiff."
           "OWS_KEYWORDLIST" "OneGeology,continent@Europe,dataprovider@EMODnet,serviceprovider@British Geological Survey,DS_TOPIC@geoscientificInformation,DS_DATE@2011-06-30,Bathymetry,CRS_SUPPORTED@EPSG:4326 EPSG:3031 EPSG:3034 EPSG:3413 EPSG:3857 EPSG:4258"
           "OWS_SRS" "EPSG:4326 EPSG:3031 EPSG:3034 EPSG:3413 EPSG:3857 EPSG:4258"
           "OWS_TITLE" "Adriatic Sea - Ionian Sea - Central Mediterranean [Multi Colour]"
       END

       PROJECTION
           "init=epsg:4326"
       END

       STATUS ON
       TOLERANCE 10
       TYPE RASTER
    END


Further details for configuring WCS with Mapserver can be found at: `WCS Server <http://mapserver.org/ogc/wcs_server.html>`_

INSPIRE metadata
----------------

INSPIRE specific metadata can either be referenced in an external INSPIRE service metadata document (scenario 1) or can be directly embedded in the capabilities document (scenario 2). MapServer supports both scenarios.  In either scenario an extended capabilities section is added to the GetCapabilities response for the service, using metadata configured in the **SERVICE > WEB > METADATA** section of the Mapfile.

For example to add a scenario 1 INSPIRE extended capabilities section for an INSPIRE View service (WMS) you would use something like the below:

.. code-block:: mapfile

           "WMS_LANGUAGES" "eng"
           "WMS_INSPIRE_CAPABILITIES" "URL"
           "WMS_INSPIRE_METADATAURL_FORMAT" "application/xml"
           "WMS_INSPIRE_METADATAURL_HREF" "http://metadata.bgs.ac.uk/geonetwork/srv/en/csw?SERVICE=CSW&REQUEST=GetRecordById&ID=7822e848-822d-45a5-8584-56d352fd2170&elementSetName=full&OutputSchema=csw:IsoRecord&"

Which would create:

.. code-block:: xml

   <inspire_vs:ExtendedCapabilities>
       <inspire_common:MetadataUrl xsi:type="inspire_common:resourceLocatorType">
           <inspire_common:URL>http://metadata.bgs.ac.uk/geonetwork/srv/en/csw?SERVICE=CSW
           &amp;REQUEST=GetRecordById&amp;ID=7822e848-822d-45a5-8584-56d352fd2170&amp;elementSetName=full&amp;OutputSchema=csw:IsoRecord&amp;
           </inspire_common:URL>
           <inspire_common:MediaType>application/xml</inspire_common:MediaType>
       </inspire_common:MetadataUrl>
       <inspire_common:SupportedLanguages>
           <inspire_common:DefaultLanguage>
               <inspire_common:Language>eng</inspire_common:Language>
           </inspire_common:DefaultLanguage>
       </inspire_common:SupportedLanguages>
       <inspire_common:ResponseLanguage>
           <inspire_common:Language>eng</inspire_common:Language>
       </inspire_common:ResponseLanguage>
   </inspire_vs:ExtendedCapabilities>

And similarly for a WFS (INSPIRE download service) you would use something like:

.. code-block:: mapfile

           "WFS_INSPIRE_CAPABILITIES" "url"
           "WFS_INSPIRE_DSID_CODE" "c8a4207f-adb8-43fc-ad70-8ae1f7d4b50d"
           "WFS_INSPIRE_DSID_NS" "http://ogc.bgs.ac.uk"
           "WFS_INSPIRE_METADATAURL_FORMAT" "application/xml"
           "WFS_INSPIRE_METADATAURL_HREF" "http://ogc.bgs.ac.uk/terrafirma/metadata/TerraFirmaSRVMD.xml"
           "WFS_LANGUAGES" "eng"

To create:

.. code-block:: xml

   <ows:ExtendedCapabilities>
       <inspire_dls:ExtendedCapabilities>
           <inspire_common:MetadataUrl xsi:type="inspire_common:resourceLocatorType">
               <inspire_common:URL>
                   http://ogc.bgs.ac.uk/terrafirma/metadata/TerraFirmaSRVMD.xml
               </inspire_common:URL>
               <inspire_common:MediaType>application/xml</inspire_common:MediaType>
           </inspire_common:MetadataUrl>
           <inspire_common:SupportedLanguages>
               <inspire_common:DefaultLanguage>
                   <inspire_common:Language>eng</inspire_common:Language>
               </inspire_common:DefaultLanguage>
           </inspire_common:SupportedLanguages>
           <inspire_common:ResponseLanguage>
               <inspire_common:Language>eng</inspire_common:Language>
           </inspire_common:ResponseLanguage>
           <inspire_dls:SpatialDataSetIdentifier>
               <inspire_common:Code>c8a4207f-adb8-43fc-ad70-8ae1f7d4b50d</inspire_common:Code>
               <inspire_common:Namespace>http://ogc.bgs.ac.uk</inspire_common:Namespace>
           </inspire_dls:SpatialDataSetIdentifier>
       </inspire_dls:ExtendedCapabilities>
   </ows:ExtendedCapabilities>

and finally for a WCS (INSPIRE download service) you could use something like:

.. code-block:: mapfile

           "WCS_INSPIRE_CAPABILITIES" "url"
           "WCS_INSPIRE_DSID_CODE" "http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&layer=PARENTMATERIAL&,http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&layer=REFIEFM&,http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&layer=LVBATHY&,http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&layer=POPN&"
           "WCS_INSPIRE_METADATAURL_FORMAT" "text/html"
           "WCS_INSPIRE_METADATAURL_HREF" "http://ogc2.bgs.ac.uk/ARGI_UPP/"
           "WCS_LANGUAGES" "eng"

To create:

.. code-block:: xml

   <ows:ExtendedCapabilities>
     <inspire_dls:ExtendedCapabilities>
       <inspire_common:MetadataUrl xsi:type="inspire_common:resourceLocatorType">
         <inspire_common:URL>http://ogc2.bgs.ac.uk/UGA_ARGI/</inspire_common:URL>
         <inspire_common:MediaType>text/html</inspire_common:MediaType>
       </inspire_common:MetadataUrl>
       <inspire_common:SupportedLanguages>
         <inspire_common:DefaultLanguage>
           <inspire_common:Language>eng</inspire_common:Language>
         </inspire_common:DefaultLanguage>
       </inspire_common:SupportedLanguages>
       <inspire_common:ResponseLanguage>
         <inspire_common:Language>eng</inspire_common:Language>
       </inspire_common:ResponseLanguage>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&amp;layer=PARENTMATERIAL&amp;</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&amp;layer=REFIEFM&amp;</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&amp;layer=LVBATHY&amp;</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?request=GetMetadata&amp;layer=POPN&amp;</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
     </inspire_dls:ExtendedCapabilities>
   </ows:ExtendedCapabilities>

To add a scenario 2 INSPIRE extended capabilities section (where you have no external metadata document for your service) you could add the following parameters for a WMS:

.. code-block:: mapfile

           "WMS_LANGUAGES" "eng"
           "WMS_INSPIRE_CAPABILITIES" "embed"
           "WMS_INSPIRE_KEYWORD" "infoMapAccessService"
           "WMS_INSPIRE_MPOC_EMAIL" "enqiries@bgs.ac.uk"
           "WMS_INSPIRE_MPOC_NAME" "Mr Matthew Harrison"
           "WMS_INSPIRE_METADATADATE" "2014-03-28"
           "WMS_INSPIRE_RESOURCELOCATOR" "http://ogc.bgs.ac.uk/cgi-bin/TFL-PSI/ows?"
           "WMS_INSPIRE_TEMPORAL_REFERENCE" "2014-06-06"

Which would create:

.. code-block:: xml

   <inspire_vs:ExtendedCapabilities>
       <inspire_common:ResourceLocator>
           <inspire_common:URL>http://ogc.bgs.ac.uk/cgi-bin/TFL-PSI/ows?</inspire_common:URL>
       </inspire_common:ResourceLocator>
       <inspire_common:ResourceType>service</inspire_common:ResourceType>
       <inspire_common:TemporalReference>
           <inspire_common:DateOfLastRevision>2014-06-06</inspire_common:DateOfLastRevision>
       </inspire_common:TemporalReference>
       <inspire_common:Conformity>
           <inspire_common:Specification>
               <inspire_common:Title>-</inspire_common:Title>
               <inspire_common:DateOfLastRevision>2014-06-06</inspire_common:DateOfLastRevision>
           </inspire_common:Specification>
           <inspire_common:Degree>notEvaluated</inspire_common:Degree>
       </inspire_common:Conformity>
       <inspire_common:MetadataPointOfContact>
           <inspire_common:OrganisationName>Mr Matthew Harrison</inspire_common:OrganisationName>
           <inspire_common:EmailAddress>enqiries@bgs.ac.uk</inspire_common:EmailAddress>
       </inspire_common:MetadataPointOfContact>
       <inspire_common:MetadataDate>2014-03-28</inspire_common:MetadataDate>
       <inspire_common:SpatialDataServiceType>view</inspire_common:SpatialDataServiceType>
       <inspire_common:MandatoryKeyword>
           <inspire_common:KeywordValue>infoMapAccessService</inspire_common:KeywordValue>
       </inspire_common:MandatoryKeyword>
       <inspire_common:SupportedLanguages>
           <inspire_common:DefaultLanguage>
               <inspire_common:Language>eng</inspire_common:Language>
           </inspire_common:DefaultLanguage>
       </inspire_common:SupportedLanguages>
       <inspire_common:ResponseLanguage>
           <inspire_common:Language>eng</inspire_common:Language>
       </inspire_common:ResponseLanguage>
   </inspire_vs:ExtendedCapabilities>

Similarly for an INSPIRE WFS (download) service you would use:

.. code-block:: mapfile

           "WFS_INSPIRE_CAPABILITIES" "embed"
           "WFS_INSPIRE_DSID_CODE" "c8a4207f-adb8-43fc-ad70-8ae1f7d4b50d"
           "WFS_INSPIRE_DSID_NS" "http://ogc.bgs.ac.uk"
           "WFS_INSPIRE_KEYWORD" "infoFeatureAccessService"
           "WFS_INSPIRE_MPOC_EMAIL" "enqiries@bgs.ac.uk"
           "WFS_INSPIRE_MPOC_NAME" "Mr Matthew Harrison"
           "WFS_INSPIRE_METADATADATE" "2016-04-13"
           "WFS_INSPIRE_RESOURCELOCATOR" "http://ogc.bgs.ac.uk/cgi-bin/TFL-PSI/ows?"
           "WFS_INSPIRE_TEMPORAL_REFERENCE" "2016-04-13"
           "WFS_LANGUAGES" "eng"

To create:

.. code-block:: xml

   <ows:ExtendedCapabilities>
       <inspire_dls:ExtendedCapabilities>
           <inspire_common:ResourceLocator>
               <inspire_common:URL>http://ogc.bgs.ac.uk/cgi-bin/TFL-PSI/ows?</inspire_common:URL>
           </inspire_common:ResourceLocator>
           <inspire_common:ResourceType>service</inspire_common:ResourceType>
           <inspire_common:TemporalReference>
               <inspire_common:DateOfLastRevision>2016-04-13</inspire_common:DateOfLastRevision>
           </inspire_common:TemporalReference>
           <inspire_common:Conformity>
               <inspire_common:Specification>
                   <inspire_common:Title>-</inspire_common:Title>
                   <inspire_common:DateOfLastRevision>2016-04-13</inspire_common:DateOfLastRevision>
               </inspire_common:Specification>
               <inspire_common:Degree>notEvaluated</inspire_common:Degree>
           </inspire_common:Conformity>
           <inspire_common:MetadataPointOfContact>
               <inspire_common:OrganisationName>Mr Matthew Harrison</inspire_common:OrganisationName>
               <inspire_common:EmailAddress>enqiries@bgs.ac.uk</inspire_common:EmailAddress>
           </inspire_common:MetadataPointOfContact>
           <inspire_common:MetadataDate>2016-04-13</inspire_common:MetadataDate>
           <inspire_common:SpatialDataServiceType>download</inspire_common:SpatialDataServiceType>
           <inspire_common:MandatoryKeyword>
               <inspire_common:KeywordValue>infoFeatureAccessService</inspire_common:KeywordValue>
           </inspire_common:MandatoryKeyword>
           <inspire_common:SupportedLanguages>
               <inspire_common:DefaultLanguage>
                   <inspire_common:Language>eng</inspire_common:Language>
               </inspire_common:DefaultLanguage>
           </inspire_common:SupportedLanguages>
           <inspire_common:ResponseLanguage>
               <inspire_common:Language>eng</inspire_common:Language>
           </inspire_common:ResponseLanguage>
           <inspire_dls:SpatialDataSetIdentifier>
               <inspire_common:Code>c8a4207f-adb8-43fc-ad70-8ae1f7d4b50d</inspire_common:Code>
               <inspire_common:Namespace>http://ogc.bgs.ac.uk</inspire_common:Namespace>
           </inspire_dls:SpatialDataSetIdentifier>
       </inspire_dls:ExtendedCapabilities>
   </ows:ExtendedCapabilities>


Finally for an INSPIRE WCS (download) service you could use:

.. code-block:: mapfile

           "WCS_INSPIRE_CAPABILITIES" "embed"
           "WCS_INSPIRE_DSID_CODE" "ARGI_UPP:PARENTMATERIAL,ARGI_UPP:REFIEFM,ARGI_UPP:LVBATHY,ARGI_UPP:POPN"
           "WCS_INSPIRE_KEYWORD" "infoCoverageAccessService"
           "WCS_INSPIRE_MPOC_EMAIL" "enqiries@bgs.ac.uk"
           "WCS_INSPIRE_MPOC_NAME" "Mr Matthew Harrison"
           "WCS_INSPIRE_METADATADATE" "2016-04-13"
           "WCS_INSPIRE_RESOURCELOCATOR" "http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?"
           "WCS_INSPIRE_TEMPORAL_REFERENCE" "2016-01-01"
           "WCS_LANGUAGES" "eng"

To create:

.. code-block:: xml

   <ows:ExtendedCapabilities>
     <inspire_dls:ExtendedCapabilities>
       <inspire_common:ResourceLocator>
         <inspire_common:URL>http://ogc2.bgs.ac.uk/cgi-bin/UGA_ARGI/ows?</inspire_common:URL>
       </inspire_common:ResourceLocator>
       <inspire_common:ResourceType>service</inspire_common:ResourceType>
       <inspire_common:TemporalReference>
         <inspire_common:DateOfLastRevision>2016-01-01</inspire_common:DateOfLastRevision>
       </inspire_common:TemporalReference>
       <inspire_common:Conformity>
         <inspire_common:Specification>
           <inspire_common:Title>-</inspire_common:Title>
           <inspire_common:DateOfLastRevision>2016-01-01</inspire_common:DateOfLastRevision>
         </inspire_common:Specification>
         <inspire_common:Degree>notEvaluated</inspire_common:Degree>
       </inspire_common:Conformity>
       <inspire_common:MetadataPointOfContact>
         <inspire_common:OrganisationName>James Passmore</inspire_common:OrganisationName>
         <inspire_common:EmailAddress>enquiries@bgs.ac.uk</inspire_common:EmailAddress>
       </inspire_common:MetadataPointOfContact>
       <inspire_common:MetadataDate>2018-10-04</inspire_common:MetadataDate>
       <inspire_common:SpatialDataServiceType>download</inspire_common:SpatialDataServiceType>
       <inspire_common:MandatoryKeyword>
         <inspire_common:KeywordValue>infoCoverageAccessService</inspire_common:KeywordValue>
       </inspire_common:MandatoryKeyword>
       <inspire_common:SupportedLanguages>
         <inspire_common:DefaultLanguage>
           <inspire_common:Language>eng</inspire_common:Language>
         </inspire_common:DefaultLanguage>
       </inspire_common:SupportedLanguages>
       <inspire_common:ResponseLanguage>
         <inspire_common:Language>eng</inspire_common:Language>
       </inspire_common:ResponseLanguage>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>ARGI_UPP:PARENTMATERIAL</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>ARGI_UPP:REFIEFM</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>ARGI_UPP:LVBATHY</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
       <inspire_dls:SpatialDataSetIdentifier>
         <inspire_common:Code>ARGI_UPP:POPN</inspire_common:Code>
       </inspire_dls:SpatialDataSetIdentifier>
     </inspire_dls:ExtendedCapabilities>
   </ows:ExtendedCapabilities>




**Note 1** Although MapServer supports multi-lingual GetCapabilities responses we don't discuss them here because the OneGeology profile mandates having separate services per language offered.

**Note 2** You don't have to set a namespace separately for the SpatialDataSetIdentifier, and can have multiple datasets identified (by providing a comma separated list).  If you want to specify code and namespace and have multiple multiple codes, your lists must be the same length.

**Note 3** Since MapServer version 7.2, by default filling in a complete set of service and layer metadata will also give you a full ISO 19139 XML metadata record for your dataset, which is available through a GetMetadata request, and is automatically added to your service where the GetCapabilites response supports a dataset metadata URL.
