.. _service_provision_service_types:

*************
Service Types
*************

This guidance covers setting up some different kinds of service which provide different levels of access to your data and different functionality.

.. glossary::

   Simple WMS
      This may just show the map image in its correct location through a GetMap request. The map colours may be data provider specific or standard. This kind of service can be set up with only a georegistered image file as data source. A GetFeatureInfo enabled WMS will also provide the ability to query any point on the map and retrieve a set of properties for that point in text, HTML, XML or other formats. A vector data file or spatial database would be required to support GetFeatureInfo responses.

   SLD enabled WMS
      This allows the map to be styled depending on values of some data underlying the WMS. The OneGeology Portal can ask an SLD enabled WMS to highlight units of particular ages or lithologies if it has underlying data with the GeoSciML-Lite age and lithology fields and using either IUGS-CGI vocabularies or INSPIRE vocabularies. An SLD enabled WMS would usually use a vector data file or spatial database as a data source.

   Simple feature WFS
      This often goes together with the SLD enabled WMS. The features may be created to reflect whatever data fields exist in the source data table or there may be some level of standardisation of some or more of the fields and the values they can contain. OneGeology currently deals specifically with two simple feature standards: GeoSciML-Lite and ERML-Lite. Setting up a simple feature WFS will enable many clients to query and download your data. A simple feature WFS would usually use a vector data file or spatial database as a data source.

   Complex feature WFS
      This can supply data for spatial features with complex properties that may have complex structure, multiple values, alternative value types etc. Using a standard schema for these features and standard vocabularies for categorical properties potentially enables interoperable sophisticated application processing of data from different providers. The OneGeology Portal can currently query services using the GeoSciML schema and associated vocabularies from the IUGS-CGI or INSPIRE. A complex feature WFS would usually use a spatial database as a data source.

   WCS
      This is a more recent addition to OneGeology and the Portal currently can handle raster grids that can be returned in an image format only. Other applications might be able to consume other grid data formats. A WCS could use a variety of grid data formats, image formats, raster or array database as a data source.
