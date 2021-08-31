==========================================
Converting coordinate system in data files
==========================================

.. container::
   :name: outer_container

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
         ogr2ogr.exe which is located in ms4w\\tools\\gdal-ogr where ms4w
         is the top-level folder of your MS4W installation. The easiest
         way to use the programs is to run the batch file
         ms4w\\setenv.bat from a DOS window which will set up your path.
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
