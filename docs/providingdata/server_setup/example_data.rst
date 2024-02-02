.. _service_provision_data_preparation_exampledata:

Cookbook example data
=====================

In order to help you test setting up services with data that we know work before you try using your own data we supply a number of example data sets that can be used to set up different kinds of services.

GeoPackage
----------

This is a relatively recent standard format for exchanging vector and raster GIS data in a single file. It can potentially be used for quite complex data structures. The example contains two files that could be used for a Simple WMS with GetFeatureInfo response and a Simple Feature WFS. They can also serve as the basis of an SLD enabled WMS and the GeologicUnitView.gpkg file has the fields that are used for highlighting queries in the OneGeology Portal age and lithology tool. As this format doesn't have the restrictions on field length of Shapefiles the examples are able to use the same names as specified in the GeoSciML-Lite GeologicUnitView and ShearDisplacementView feature types. Field values have been populated with appropriate values from INSPIRE vocabularies so that these examples can be used to produce a simple feature WFS returning standards conformant GeoSciML-Lite features. Download from `<https://github.com/OneGeology/documentation/raw/master/docs/exampledata/geopackagegeoscimllite.zip>`_.

PostGIS data
------------

This data set can be used as a basis for WMS with GetFeatureInfo, SLD enabled WMS usable in OneGeology Portal, Simple Feature WFS conforming to GeoSciML Lite schema and Complex Feature WFS conforming to GeoSciML schema. A PostGIS database could also store raster data but the example dataset does not. PostGIS is more suitable for production services than Image files or Shapefiles and is more capable for providing data and as a basis for services conforming to standard application schemas.

It is assumed that you have :ref:`installed the PostGIS software <service_provision_data_preparation_postgis>` and that you have a spatially enabled database (the default installation will create one called postgis). The following will all be working within this spatially enabled database.

Download the latest version of the database dump file wfscookbook.YYYY-MM-DD.backup from `<https://resources.bgs.ac.uk//OneGeology/wfscookbook/>`_. (Each version will have its release date in place of YYYY-MM-DD.)

Create a separate schema for the example data. The schema name is used in the commands below so, if you change it from ``wfscookbook`` you will need to change these accordingly

.. code-block:: postgresql

   CREATE SCHEMA wfscookbook AUTHORIZATION postgres;

Import the data from the database dump file downloaded above. If you have installed the pgAdmin graphical administration tool you can use the menu option :menuselection:`Tools --> Restore...`. If you are using the command line you can use the command :command:`pg_restore --host localhost --port 5432 --username "postgres" --dbname "postgis" --no-password --no-owner --no-privileges --no-tablespaces --schema wfscookbook --verbose wfscookbook.backup` (assuming you are using the default 'postgis' named database.  You should create a database user with read-only access to these tables for the WFS software to use when accessing them.

.. code-block:: postgresql

   CREATE ROLE ows_reader LOGIN PASSWORD 'your_password'
    VALID UNTIL 'infinity';
   COMMENT ON ROLE ows_reader
   IS 'A role with read only access to data used in web services.';
   grant usage on schema wfscookbook to ows_reader;
   grant select on table geometry_columns to ows_reader;
   grant select on table spatial_ref_sys to ows_reader;
   grant select on all tables in schema wfscookbook to ows_reader;

If you have problems with the above steps which are difficult to resolve you may find that setting ``log_statement=all`` in ``postgresql.conf``, reloading the server and then monitoring the log file is helpful for debugging them.

.. _service_provision_data_preparation_postgis:

Installing PostGIS
^^^^^^^^^^^^^^^^^^

The `PostGIS Installation <https://www.postgis.net/documentation/training/>`_ pages contain instructions on how to install PostGIS for different operating systems. We have used both the `Enterprise DB Windows Installer <https://www.enterprisedb.com/downloads/postgres-postgresql-downloads>`_ on Windows and the `PostgreSQL Yum repository <https://yum.postgresql.org/>`_ on CentOS.

.. todo::

    Don't think we want to go into more detail on installation ourselves?

Image with world file
---------------------

This is an image file with associated worldfile to locate it in geographic coordinates. This is the type of file that you might have if you only have paper maps which you have to scan to use. It is suitable for setting up a simple WMS without any useful GetFeatureInfo response or the ability to be styled by an SLD. Download from `<https://github.com/OneGeology/documentation/raw/master/docs/exampledata/georeferencedimage.zip>`_.

Shapefile
---------

ESRI Shapefile is a very common vector GIS format. The example could be used for a Simple WMS with GetFeatureInfo response and a Simple Feature WFS. It could also serve as the basis of an SLD enabled WMS but it doesn't have the fields that are used in the OneGeology Portal age and lithology tool so wouldn't work with that unless those fields were added. Also, because of the 10 character limit on length of Shapefile field names your server software will need to be able map shorter field names to the longer ones expected by the Portal. The field name length restriction also means that a simple feature WFS can't be made to conform to specific standard Schemas like GeoSciML Lite unless your server software can map the names to the longer standard property names. Download from `<https://github.com/OneGeology/documentation/raw/master/docs/exampledata/shapefileunharmonised.zip>`_.

.. todo::

   Possible need for an id column (WFS?). Convert referenced appendices (now just A) from the old cookbook?

OneGeology does not recommend using Shapefiles as the data source for your services but, if you already have your data in this format, it can be used as a data source with some restrictions.

If you wish to set up a :term:`SLD enabled WMS` or :term:`Simple feature WFS` using the standard fields needed for age and lithology highlighting in the Portal or following one of the standard 'Lite' schemas then the 10 character limit on field names in Shapefiles means your server will need to map shorter Shapefile field names to the longer expected field names in the standards. We provide some :ref:`service_provision_data_preparation_short_names` for some GeoSciML-Lite features that are reasonably readable and would enable using common mapping files to produce services using the full names.

Another consideration might be that, if the coordinate system of your Shapefile is not EPSG:4326 and your service is predominantly to be used in the OneGeology Portal, then your server will have to do a lot of on-the-fly coordinate conversion. To ameliorate this you can `convert the coordinate system of your Shapefile </wmsCookbook/appendixA.html>`_. The tools referred to in the previous link are available from https://gdal.org if you haven't done the MS4W download that it assumes.

.. _service_provision_data_preparation_short_names:

Recommended ESRI shapefile definitions for GeoSciML-Lite
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. todo::

    Create similar recomendation for GSML borehole view and also ERML lite views?

Because the field names in GeoSciML-Lite are longer than 10 characters, you will not be able to have the full attribute (column) name for many of the properties if your portrayal data is loaded into an ESRI shapefile. To prevent truncated names, we are providing a recommended Shapefile implementation with shorter field names. Field names are abbreviated to try and leave characters that convey the full name of the field; lower camel case typographic has been used, except that fields that contain URI’s end with ‘_uri’.

.. table:: Recommended shapefile definition for ContactView
    :widths: auto
    :align: left

    ==================   ====================  ===================
    XML field Name       Shapefile field name  Shapefile data type
    ==================   ====================  ===================
    identifier           identifier            String
    name                 name                  String
    description          descriptio            String
    contactType          contactTyp            String
    observationMethod    obsvMethod            String
    positionalAccuracy   posAccur              String
    source               source                String
    contactType_uri      conTyp_uri            String
    specification_uri    spec_uri              String
    metadata_uri         metada_uri            String
    genericSymbolizer    genericSym            String
    shape                SHAPE                 ESRI geometry
    ==================   ====================  ===================


.. raw:: html

    <div class="linefeed">
    <!-- Force a line -->&nbsp;
    </div>


.. table:: Recommended shapefile definition for ShearDisplacementStructureView
    :widths: auto
    :align: left

    ============================  ====================  ===================
    XML field Name                Shapefile field name  Shapefile data type
    ============================  ====================  ===================
    identifier                    identifier            String
    name                          name                  String
    description                   descriptio            String
    faultType                     faultType             String
    movementType                  movmntType            String
    deformationStyle              defrmStyle            String
    displacement                  displacmnt            String
    geologicHistory               geolHistry            String
    observationMethod             obsvMethod            String
    positionalAccuracy            posAccur              String
    source                        source                String
    faultType_uri                 fltTyp_uri            String
    movementType_uri              movTyp_uri            String
    deformationStyle_uri          defStl_uri            String
    representativeAge_uri         repAge_uri            String
    representativeOlderAge_uri    oldAge_uri            String
    representativeYoungerAge_uri  yngAge_uri            String
    specification_uri             spec_uri              String
    metadata_uri                  metada_uri            String
    genericSymbolizer             genericSym            String
    shape                         SHAPE                 ESRI geometry
    ============================  ====================  ===================


.. raw:: html

    <div class="linefeed">
    <!-- Force a line -->&nbsp;
    </div>


.. table:: Recommended shapefile definition for GeologicUnitView
    :widths: auto
    :align: left

    ============================  ====================  ===================
    XML field Name                Shapefile field name  Shapefile data type
    ============================  ====================  ===================
    identifier                    identifier            String
    name                          name                  String
    description                   descriptio            String
    geologicUnitType              geoUnitTyp            String
    rank                          rank                  String
    lithology                     lithology             String
    geologicHistory               geolHistry            String
    observationMethod             obsvMethod            String
    positionalAccuracy            posAccur              String
    source                        source                String
    geologicUnitType_uri          uniTyp_uri            String
    representativeLithology_uri   repLth_uri            String
    representativeAge_uri         repAge_uri            String
    representativeOlderAge_uri    oldAge_uri            String
    representativeYoungerAge_uri  yngAge_uri            String
    specification_uri             spec_uri              String
    metadata_uri                  metada_uri            String
    genericSymbolizer             genericSym            String
    shape                         SHAPE                 ESRI geometry
    ============================  ====================  ===================


GeoTIFF
-------

GeoTIFF is a raster format with geographic registration included. The example has been obtained from the `EMODNET Portal for Bathymetry <http://portal.emodnet-bathymetry.eu/RGB>`_ and has RGB bands suitable for display as an image although other GeoTIFF's could have more and not necessarily image bands. This could be used for a WMS but is included primarily to test WCS setup. Download from `<https://github.com/OneGeology/documentation/raw/master/docs/exampledata/geotiff.zip>`_.
