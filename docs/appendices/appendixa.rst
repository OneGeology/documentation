========================================================
Converting coordinate system in data files \| OneGeology
========================================================

.. container::
   :name: outer_container

   .. container:: top_banner_box
      :name: page_top

      Providing geoscience data globally |OneGeology logo|
      `Navigation <#menu>`__\ 
      \ `Main content <#content>`__\ 
      \ `Bottom links <#bottom_links>`__

   .. container:: print

      .. rubric:: OneGeology
         :name: onegeology

   .. container:: technical_progress

      `Home </home.html>`__ > `How to serve a OneGeology
      WMS <home.html>`__ > `Converting coordinate system in data
      files <appendixA.html>`__

   .. container:: clear horizontal_links navigation

      .. container::
         :name: menu

         `About us </what_is/home.html>`__
            -  `The Mission </what_is/mission.html>`__
            -  `Objectives </what_is/objective.html>`__
            -  `How </what_is/how.html>`__
            -  `The Accord </what_is/accord.html>`__
            -  `Members & membership
               type </participants/members.html>`__
            -  `Countries
               involved </participants/app/1gCountries.cfc?method=viewCountries>`__
            -  `Organisational
               bodies </participants/organisational_bodies.html>`__
            -  `Sponsors </participants/sponsors.html>`__
            -  `Interactive
               map </participants/app/1gCountries.cfc?method=viewCountryMap>`__

         `Governance </organisation/home.html>`__
            -  `Administration </organisation/secretariat.html>`__
            -  `Memorandum of understanding </organisation/mou.html>`__
            -  `Technical implementation
               group </organisation/tig.html>`__
            -  `Operational
               group </organisation/operationalGroup.html>`__
            -  `Strategic Steering
               Committee </organisation/strategicSteering.html>`__

         `Technical </technical_progress/technical.html>`__
            -  `GeoSciML </technical_progress/geosciml.html>`__
            -  `ESRI grant
               offer </technical_progress/esriGrantOffer.html>`__
            -  `Providing services </service_provision/home.html>`__
            -  `Register your data or
               service </technical_progress/buddy_home.html>`__
            -  `Web services accreditation
               scheme </technical_progress/accreditationForm.cfm>`__
            -  `How to use a OneGeology service </use/home.html>`__

         `Meetings </meetings/home.html>`__
            -  `Operational Group </meetings/oog_meetings.html>`__
            -  `Strategic Steering
               Committee </meetings/steering_meetings.html>`__
            -  `Technical Implementation
               Group </meetings/technical_meetings.html>`__
            -  `Board </meetings/board_meetings.html>`__

         `Portal </portal/home.html>`__

         `eXtra </eXtra/home.html>`__
            -  `Culture </eXtra/culture/home.html>`__
            -  `Geodiversity </eXtra/Geodiversity/home.html>`__
            -  `OneGeology Kids </eXtra/kids/home.html>`__
            -  `Showcase </eXtra/Showcase/home.html>`__

   .. container::
      :name: content

      .. container:: fullwidth

         .. rubric:: Appendix A: Converting coordinate system in data
            files
            :name: appendix-a-converting-coordinate-system-in-data-files
            :class: technical_progress_side_menu

         As mentioned in the documentation on setting up the WMS, the
         OneGeology project requires that your WMS can serve data in
         latitude-longitude coordinates with the WGS84 ellipsoid and
         datum (EPSG:4326). If your data files are stored in a different
         coordinate reference system, MapServer can convert the
         coordinates to EPSG:4326 or other client requested coordinate
         reference systems on-the-fly. However, to reduce the load on
         your server, as we can expect that a substantial proportion of
         requests to OneGeology servers will be for EPSG:4326 then we
         suggest that you convert your underlying data sets to this
         coordinate reference system so that the conversion won’t have
         to be carried out on every request. The same tools that
         MapServer uses internally are available with command line
         programs bundled in the MS4W package and can be used to convert
         your underlying data sets as follows.

         For shapefiles the main program you will want to use is
         ogr2ogr.exe which is located in ms4w\tools\gdal-ogr where ms4w
         is the top-level folder of your MS4W installation. The easiest
         way to use the programs is to run the batch file
         ms4w\setenv.bat from a DOS window which will set up your path.
         (You may need to edit the setenv.bat file to reflect the
         location where you have installed MS4W.) Next you need to find
         out whether your current data set has a coordinate reference
         system assigned to it. If you have, for example, a dataset in a
         shapefile called datafile.shp you would issue a command like:

         **:\\ > ogrinfo -so datafile.shp datafile**

         (The first datafile.shp refers to the file name; the datafile
         afterwards is a layer name which is redundant in the case of
         shapefiles which only have one layer but is the way ogrinfo
         works.) You should get some information including something
         like that below:

         ::

            Layer SRS WKT:
            PROJCS["British_National_Grid",
             GEOGCS["GCS_OSGB_1936",
             DATUM["OSGB_1936",
             SPHEROID["Airy_1830",6377563.396,299.3249646]],
             PRIMEM["Greenwich",0.0],
             UNIT["Degree",0.0174532925199433]],
             PROJECTION["Transverse_Mercator"],
             PARAMETER["False_Easting",400000.0],
             PARAMETER["False_Northing",-100000.0],
             PARAMETER["Central_Meridian",-2.0],
             PARAMETER["Scale_Factor",0.  999601272],
             PARAMETER["Latitude_Of_Origin",49.0],
             UNIT["Meter",1.0]]

         The details do not matter as long as you don’t get the below:

         | Layer SRS WKT:
         | (unknown)

         In this situation you will need to find out what coordinate
         system your data is in. If the data has a coordinate system
         assigned you can issue a command like that below to convert the
         data (note that the destination file is specified before the
         source file):

         **:\\ > ogr2ogr -t_srs EPSG:4326 new_datafile.shp
         datafile.shp**

         If your data set does not have a coordinate system assigned to
         it but you have found out what it is you can specify the source
         coordinate system on the command line with the parameter
         -s_srs, for example:

         **:\\ > ogr2ogr -s_srs EPSG:27700 -t_srs EPSG:4326
         new_datafile.shp datafile.shp**

         For GeoTIFF files the utilities you will want to use are
         gdalinfo.exe and gdalwarp.exe. Issuing a command like: gdalinfo
         imagefile.tif will result in some information including
         projection information like that below:

         ::

            Driver: GTiff/GeoTIFF
            Size is 522, 252
            Coordinate System is:
            GEOGCS["WGS 84",
             DATUM["WGS_1984",
             SPHEROID["WGS 84",6378137,298.2572235630016,
             AUTHORITY["EPSG","7030"]],
             AUTHORITY["EPSG","6326"]],
             PRIMEM["Greenwich",0],
             UNIT["degree",0.0174532925199433],
             AUTHORITY["EPSG","4326"]]
            Origin = (-180.,000000000000000,83.879999999999995)
            Pixel Size = (0.690000000000000,-0.690000000000000)
            Metadata:

         You can transform an image in a similar way to the ogr2ogr
         utility for shapefiles but unlike ogr2ogr the source and
         destination files are specified in the more common source then
         destination file order so typical command lines would be:

         **:\\ > gdalwarp —t_srs EPSG:4326 imagefile.tif
         new_imagefile.tif**

         or

         **:\\ > gdalwarp -s_srs EPSG:27700 -t_srs EPSG:4326
         imagefile.tif new_imagefile.tif**

         Section last modified: 19 January 2010

         `Back <7_6.html>`__\ \|\ `Next <appendixB.html>`__

   .. container:: horizontal_links

      .. container::

         `Contact us </misc/contact_us.html>`__

      .. container::

         `Newsletters </misc/news.html>`__

      .. container::

         `Downloads </misc/downloads.html>`__

      .. container::

         `Privacy </misc/privacy.html>`__

      .. container::

         `Participating countries
         map </participants/app/1gCountries.cfc?method=viewCountryMap>`__

      .. container::
         :name: pageTopBtn

         `Top <#page_top>`__

   OneGeology © 2017. This site is hosted by the `British Geological
   Survey <http://www.bgs.ac.uk/hosted.html>`__ but responsibility for
   the content of the site lies with OneGeology not with the British
   Geological Survey. Questions, suggestions, or comments regarding the
   contents of this site should be directed to `the OneGeology
   administration <mailto:onegeology@bgs.ac.uk>`__.

.. |OneGeology logo| image:: appendixa/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
