===========================
Providing Data / Services
===========================

.. todo::

   This high level introduction text should be consistent with other parts of the www.onegeology.org site and with statements in the "using" part. Maybe link to a canonical statement of purpose on the website. Does it need updating to cover newer types of data that we are dealing with?

The `mission <http://onegeology.org/what_is/mission.html>`_ of OneGeology is being fulfilled by the cooperation of participating member organisations worldwide. This part of the website gives technical guidance on how to provide services for OneGeology to those organisations that fit within the `prospective member guidelines <http://onegeology.org/participants/home.html#statement>`_ and have `registered <http://onegeology.org/getting_involved/home.html>`_ with OneGeology as participants. Some of the guidance may also be of use to others who wish to set up similar services outside OneGeology.

As described in the pages on `using <http://onegeology.org/use/home.html>`_ OneGeology data there are different kinds of data and levels of interaction with that data that are provided by OneGeology services. As a participant you need to decide what kinds of service to set up. This will depend on what data you have available and what level of access you wish to provide to it. You will also need to decide how much effort you are able to spend to harmonise your data with relevant standards. The next sections give an overview of different kinds of data source you might use and what levels of functionality you could provide with different services.

The aim: One service - many uses
--------------------------------

Geological map data will be made available as a distributed web service, using the OGC 'web feature mapping' approach. The priority of OneGeology is to make available interoperable, Internet-accessible, scientifically-attributed data and to make progress at levels appropriate to participants' capability. Surveys and organisations are encouraged to work together to develop and implement the required interchange standard to make their data interoperable. This can be achieved by using GML (Geography Mark-up Language) based
data.

.. figure:: /images/gml_based_data.jpg
    :width: 417px
    :align: center
    :height: 249px
    :alt: GML-Based data
    :figclass: align-center

    GML Based Data


GML based data (including `GeoSciML <http://www.cgi-iugs.org/tech_collaboration/geosciml.html>`_) can be used in many different ways.
For example, basic data can be rendered into a map that can be interrogated for further detailed information, the data can be formatted into a report, or it can be used in other applications for further development.


Map specifications
------------------

Prerequisites for OneGeology involvement:

- the target scale is 1:1 000 000 but the project will be pragmatic and accept a range of scales and the best available data.
- to provide a WMS you only require a georeferenced scanned paper map or raster or vector digital GIS data.
- to provide feature and complex data queries via GeoSciML based WFS you

  - need to map from your GIS (ESRI ARCINFO, MapInfo, ORACLE etc.) data store to WFS server configuration (Geoserver or Mapserver/Cocoon).
  - need a (trained) person week, but includes getting WFS going with open source software (IT issues).
  - should note that the mapping process will be simple (small part of GeoSciML) if the themes chosen by the geological specification group are simple e.g. simple polygons with few attributes such as bedrock, lithology and age.

WMS = web map service — this is level 1, the minimum for OneGeology
WFS = web feature service, this holds more detailed data.

Technical specifications and requirements
-----------------------------------------

.. figure:: /images/map_explorer.jpg
    :width: 417px
    :align: center
    :height: 249px
    :alt: Map
    :figclass: align-center

    Example of a GeoSciML downloaded map — one of the aims of OneGeology

Level 1 involvement with OneGeology web services
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Geological surveys and similar institutions that wish to contribute to the OneGeology initiative at Level 1 are aiming to provide an **OGC Web Mapping Service (WMS)** from a web server within their organisation, or hosted by a neighbouring organisation, of some basic geological maps.

The maps will appear in the computer users application, which may be a web browser, in a raster or image form. Such image maps will be combinable with other spatial datasets depending on the application the user wishes to apply. If the data that is the source behind the WMS is of digital vector data form with attributes associated with those vectors e.g. information attached to a particular type polygon or boundary then the WMS will allow the display of such attributes for each polygon. If the data source behind the WMS is of a simple scanned raster type e.g. scanned from a paper map and served as a raster image, then such attributes or further informa0tion do not exist for separate polygons.


Level 2 involvement with OneGeology web services
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Geological surveys and similar institutions that wish to contribute to the OneGeology initiative at Level 2 are aiming to provide an **OGC Web Feature Service (WFS)** from a web server within their organisation, or hosted by a neighbouring organisation, of some basic geological 'map' data.

These WFS will allow the user to download data in GeoSciML form resulting from queries (geographic or other attribute based) of the data over the web so that the same query could be sent to some/all of the OneGeology contributors WFS services around the world.

Cookbooks
---------------

What is a cookbook?
^^^^^^^^^^^^^^^^^^^

A cookbook is a best practice manual 'containing a straightforward set of already tried and tested *recipe or instructions* for a specific activity'.

A series of 'cookbooks' giving best practice on using open-source, i.e. freely available, software to set up WFS will be provided by the OneGeology initiative along with guidance on how to configure a WFS using GeoSciML from the institutions' internal digital databases.

These documents will provide specific work-flow guidance notes to enable full participation of your organisation regardless of expertise, location or amount of data available.

Cookbook specification
^^^^^^^^^^^^^^^^^^^^^^

A series of OneGeology-specific branded cookbooks are available as follows:

- Online
    - `Cookbook No 1 <https://onegeology-docs.readthedocs.io/en/latest/webservices.html#wms>`_ - explains how to setup a WMS (view) service (with no GML/GeoSciML).

- PDF Download (to be moved online shortly)
    - `Cookbook No 6 <http://www.onegeology.org/docs/technical/CB6-HowToServe-a-OneGeology-WCS_v1.pdf>`_ - decribes how to set up a WCS (download) web service on your web server using open-source software.
    - `Cookbook No 7 <http://www.onegeology.org/docs/technical/GeoSciML_Cookbook_1.3.pdf>`_ - explains how we map from the backend database to the GeoSciML WFS service.
    - `Cookbook No 8 <http://www.onegeology.org/docs/technical/OneGeologyWFSCookbook_v1.4.pdf>`_- describes how to set up a WFS (download) web service on your web server using open-source software.

The aim is that multilingual versions will be available wherever possible.

Support services
----------------

Services which will be available to OneGeology participants to help advise and assist with serving data to the Portal include:
- This documentation including cookbooks' for step-by-step guidance.
- a support team, and `email <onegeologyhelp@bgs.ac.uk>`_.
- regional workshops to build technology capability within staff.

Work will be based on open-source technologies so all the OGC web services required software can be purchased cost free. However, a contributing survey must either have its own standard Internet server or have access to such a server through a neighbouring or regional organisation.

Register your data or service for the Portal
---------------------------------------------

OneGeology is an initiative to make web accessible the geoscience data held by national geological survey and similar organisations around the World.

OneGeology welcomes all geological surveys and organisations to contribute their data to OneGeology.

Statement guiding prospective participants - http://onegeology.org/participants/home.html#statement

Before you can submit your service to OneGeology, you must first register your organization as a OneGeology data provider by filling out the registration form - http://onegeology.org/getting_involved/get_involved.cfm

If you are willing and able to host your own data you will then need to fill in the Data Coordination form on the OneGeology website - http://onegeology.org/technical_progress/data_coordination.cfm

If you are unable to host your own data for any reason, then you will *ALSO* need to fill in the buddy form on the OneGeology website - http://onegeology.org/technical_progress/buddy_coordination.cfm

Next, send an email to onegeologyhelp@bgs.ac.uk with the URL of the proposed service.

Include in this email:

- The name of the geographical area
- the name of the data provider organization (usually this is the owner of the data)
- the name of the service provider organization

 The OneGeology secretariat will check that they have written confirmation that the service provider owns the right to serve the proposed data and/or has permission from the <span class="toolTip data">data provider</span> to serve that data.

You will be contacted by the OneGeology helpdesk with confirmation of receipt, plus any other feedback.

The service will then be reviewed for conformance with OneGeology requirements and, upon verification, the service URL will be forwarded to BRGM the OneGeology Portal hosts) by the helpdesk team with a request to register the service at http://portal.onegeology.org and catalog - http://onegeology-geonetwork.brgm.fr/geonetwork3/srv/eng/catalog.search#/home">http://onegeology-geonetwork.brgm.fr/geonetwork3/srv/eng/catalog.search#/home

If BRGM have any technical issues with the proposed service they will raise these issues with the helpdesk, and the helpdesk will in turn discuss theses issues with the service provider, if required.

When the service is fit for registration BRGM will email the OneGeology secretariat, your OneGeology service will now be officially registered and its layers are now visible in the OneGeology Portal.

As the reference information stored in the OneGeology portal and catalogue comes from your service directly it is highly recommended if you need to make major changes to information held in your service, to modify your service first and then ask the helpdesk to have your service updated.

If you have any queries please contact onegeologyhelp@bgs.ac.uk

.. _service_provision_service_types:

Service Types
-------------

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


Data formats
-------------

We can put data sources we deal with under the following headings in ascending order of sophistication.

* Paper map. This will need to be scanned to create a digital image and geographically registered to be usable online. At this level it won't be possible to query the information in any way but it can be made available worldwide for anyone who can read the map to see it set in its correct geographical location relative to other data. Hopefully the legend can be scanned and then this can also be made available.
* A spatial raster or vector data file with simple properties for each grid point or spatial object. For example Shapefiles, GeoPackage and GeoTIFF.
* Spatially enabled database with possibly multiple table joins to particular spatial data fields.


Data content
-------------

The main data theme covered by OneGeology is geological map data showing the locations of geological units, faults and other structures. However, we are increasing the diversity of geologically related themes such as minerals, boreholes, hydrogeology and geoparks.  Currently OneGeology only deals with 2D data.

There are commonly differences in the definition of map units between geologic maps produced by different providers or at different times, because of the discrepancies in mapping interpretation and intention. Resolving such differences is a compilation process that often requires additional field work; this is outside the scope of service deployment. However, there are different levels of harmonisation of data that can help make the data from different providers more usable together. OneGeology promotes a number of standards that cover some of the data themes we deal with.

* Harmonising age classification and colours used for particular geological ages so that age maps from different providers are visually comparable.
* Harmonising lithology classification and colours used so that lithology maps from different providers are visually comparable.
* Harmonising commodity classification and colours used so that mineral commodity maps from different providers are visually comparable.
* Using GeoSciML-Lite or ERML-Lite simple feature formats to provide summary geological or mineral commodity data in a common format. Using CGI (or INSPIRE) standard vocabulary values for the categorical property values in these formats enables common queries to be made to services from different providers. (In particular the OneGeology Portal can query ages and lithologies from different data providers.)
* Using GeoSciML or EarthResourceML complex feature formats to provide comprehensive geological or mineral commodity data in a common format. Using CGI (or INSPIRE) standard vocabulary values for the categorical property values in these formats enables common queries to be made to services from different providers, although there may be a trade-off in loss of precision compared with using the data provider's own vocabulary values.


Data preparation
----------------

In very broad terms we can describe preparing your data to be served in a OneGeology compatible service as a kind of ETL (Extract, Transform and Load) workflow. The data needs to be taken from its current format, possibly transformed into a different structure with transformed data values and loaded into as suitable data store for use by your chosen OGC web service software. This section contains some useful information to help in different cases but you will need to have some expertise already with suitable tools to manipulate your data.

If you only have data in the form of paper maps and just intend to provide a simple WMS without attribute data see ":ref:`service_provision_data_preparation_paper_map`".

If you have digital data and wish to make this available as it is and it has a simple format with a list of simple property values for each spatial object then it is likely that the server software we describe later will be able to read your data directly and make it available on the web in a number of standard formats based on the data fields in your source data. If the server software can't read your data format directly then you may need to convert it but most common GIS formats tend to be supported.

If you have digital data and you wish to supply it in a particular standard interchange format such as one of the GeoSciML or ERML simple or complex feature types then you will need to follow a workflow something like the below:

#. Determine which fields in the source data contain the information that is to be delivered in the interchange format fields. Multiple source fields may be combined into single interchange fields, and a single source field may impact values in multiple interchange fields.
#. Determine what steps are necessary to get the content into the interchange format. This may involve some calculation, such as concatenating text from multiple fields to populate the text fields in interchange format. Use of the standard vocabularies for interoperability will likely require mapping vocabulary terms in the source data to identifiers for concepts in the controlled vocabularies.
#. Set up a query to generate a table with field names exactly matching the field names in the interchange schema. In some cases it may be convenient to generate the interchange schema table in several steps, populating subsets of the fields each time. It may be useful to generate a table with unique combinations of contact, fault, or geologic unit properties from the source data, and map each combination to corresponding properties in the interchange format.
#. The table(s) of unique descriptions can then be joined with the geometry elements of map features to generate the final feature classes for the web service.

There are many possible approaches to mapping terms from one vocabulary to another. One situation in which a standard process can be defined is that a controlled vocabulary is used to populate a field in the source data, and that field maps directly to a field in the interchange format. For example, consider a source dataset that contains a ‘dominantLithology’ field with the information used to populate the ‘representativeLithology_uri’ for a GeologicUnitView feature. The recommended procedure in this case is:

#. Produce a table of the unique ‘dominantLithology’ values in the source data
#. Add columns to this table for the corresponding term name and URI from the CGI or INSPIRE standard lithology vocabulary.
#. Determine the best matching value from the CGI standard lithology vocabulary for each unique lithology term.
#. Use an SQL query or other data processing system to join the ‘dominantLithology’ field to the corresponding field in the lookup table to update the ‘representativeLithology_uri’ field to the correct standard lithology term URI.

In general, the most specific term from the interchange vocabulary that completely subsumes (encompasses) the meaning of the term in the source vocabulary should be used. If the source vocabulary has terms that are more specific than the controlled vocabulary, there will be some information lost in this process, but the original source terminology could be preserved in an appropriate text description field. Remember, the primary purpose of the controlled vocabulary fields is for data integration, search criteria, and standardized map legends.

As we don't know your data structure or vocabularies we cannot give detailed instructions on how to map your data to one of the standard formats. However, the sections on :ref:`service_provision_data_preparation_lite` and :ref:`service_provision_data_preparation_complex` describe the feature types and properties covered by GeoSciML and EarthResourceML and which CGI or INSPIRE vocabularies can be used for particular feature properties. This should provide a reference for deciding how to map your source data to one of these standard interchange formats.

.. _service_provision_data_preparation_paper_map:

Scanning a paper map
--------------------

Scanning
^^^^^^^^^

Your chosen paper map may look something like this one from the Dutch Geological Survey of Dutch Guyana or Suriname:

.. figure:: images/paperMap.jpg
   :width: 600
   :height: 528
   :alt: Example geological map to scan

   Example geological map to scan

Step 1
"""""""

It is important to find a large scanner in your city, which could cover a whole paper map.  If this scanner is not available at your survey, you may try the Topographical Survey or a large bookshop or book printer.

Step 2A
""""""""

If you could use a large scanner, you can scan the whole map at one time.  But remember to scan the geological map portion into a separate file from that for the legend i.e. you will have two files one for the map and one for the legend.  Alternatively, make a copy of an original digital image of the whole map face and cut out the map from the legend.

The preferable output format should be .TIFF as this format keeps most information, but if  you have a slow Personal Computer, you could temporarily work with a JPEG copy.  The file size is than much smaller and it can be accessed and geo-referenced faster.

Good software for cropping (or cutting out) the legend or map from the whole scanned image is `IrfanView <http://www.irfanview.com/>`_, `Adobe Photoshop <http://www.adobe.com/uk/products/photoshopfamily.html>`_ or `GNU Image Manipulation Program (GIMP) <https://www.gimp.org/>`_.

Tip: This cropped map is now ready for geo-referencing.

Note, an alternative approach is to georeference the whole scanned image, then use a GIS (such as `QGIS <https://www.qgis.org/en/site/about/index.html>`_) to crop out the map sheet using a polygon mask.  You might use this technique when your original data is a scan of a old map sheet.

Step 2B
"""""""

For larger maps, or if you have only a small scanner, the map should be scanned in parts and later stitched together.

.. figure:: images/scanningAMap.jpg
   :width: 414
   :height: 253
   :alt: Orientation of map for scanning

   Orientation of map for scanning


If you scan in parts always try to keep the crossings of the horizontal and vertical black lines in each of the four corners.  The straight horizontal and vertical black lines on the map are the altitude and longitude.  Then the stitching and geo-referencing will be much easier.

The output format should be .TIFF as this format keeps most pixel information available.

Step 2C
""""""""

If scanners are not available, you could use a good digital camera.  Unfold the map on a well lit place without glare or light reflections.  Sometimes white sheets on the side will diffuse the light and prevent ugly reflections from the sun or from the light-bulb.  Take a picture right above the centre of the map.

Make several pictures with different lighting and shutter speed.  Choose the best colourful result.  Usually the export format is .JPG.

Step 3 ~ Stitching
"""""""""""""""""""

For the stitching of map parts many applications or free software are available, such as such as `GNU Image Manipulation Program (GIMP) <https://www.gimp.org/>`_, `OSSIM ImageLinker <http://www.ossim.org/>`_, or `QGIS <https://www.qgis.org/en/site/about/index.html>`_.

Georeferencing a scanned map
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You have now a .TIFF file or maybe a .JPEG file, which is a representation of your paper map.  This digital file should now be brought into relation with the surface of the earth.  This is called geo-referencing.  For this action you need GIS software.

Commercial GIS software such as ESRI ArcGIS or MapInfo is widely available and ‘no-cost’ GIS software, which also could perform this task, is `ILWIS <https://github.com/52North/IlwisCore/>`_ , `Geothings Map Warper <http://mapwarper.net//>`_ or `QGIS <https://www.qgis.org/en/site/about/index.html>`_.

Note down the Coordinate system of the paper map, as this is necessary for the following process.  Sometimes paper maps are found and we are not sure what coordinate system was being used as it has not been clearly stated on the paper copy.  Some research may have to be done to estimate the original coordinate system used.  For the Suriname map example it is thought probable that the coordinate system originally used was GCS North American 1927.

It is important to find four or more fixed points in the corner of the picture, from which you know exactly the position.  Reliable points are church towers, railway and roads crossings, canals or bridges.  Be careful with coastal features or rivers as these tend to change slowly in time.  More points are desirable to prevent conical distortions, which often happen with digital cameras.

.. figure:: images/crossingPoints.jpg
   :width: 421
   :height: 256
   :alt: Minimum number and location of control points when geo-rectifying a scanned image.

   Minimum number and location of control points when georectifying a scanned image.

Usually these are crossing points of an altitude line and a longitude line.

The x and y coordinates of each crossing should be given to the program.

Be careful to use the relevant degree-minutes-seconds or decimal entries for degrees depending on the particular program’s requirements.  After confirming the picture will be warped by the program so it fits now on the world surface.  Please check the accuracy, preferable with a topographical map, as often even the cartographers have made mistakes, or may have deliberately introduced errors for geopolitical or security reasons.  With slight alterations of the fixed points you can try to make a perfect overlap with a topographical map.

Image formats and transparency
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Although your scanned image will be rectangular in shape, nearly all mapped geographic regions will have irregularly shaped boundaries.  Thus it is preferable to make the background parts of your image transparent rather than a solid background colour which will obscure neighbouring regions.  The variety of image formats that are usable with MapServer and their various advantages and disadvantages is a complex subject which we cannot be authoritative about.

We have found 32-bit TIFF (RGB plus alpha layer) or 8-bit palette PNG with a transparent background colour work; you may wish to experiment.

See `MapServer raster data <http://www.mapserver.org/input/raster.html>`_ for more information.

The legend for the scanned map
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. container:: floatright

   .. figure:: images/legend.jpg
      :width: 200
      :height: 681
      :alt: Paper legend
      :class: img floatright

      Detailed legend for scanning

A WMS based on a scanned map will not have the ability to click on a symbolized polygon and see what attributes and therefore what classification it has according to the legend.  A WMS based on GIS digital data polygons and attributes does have this capability and the legend is automatically created from such information by the MapServer software.  However for this scanned map based WMS it is possible to associate the scanned legend file for the map — which in the case of the Suriname example looked like this — with the WMS service by including the following lines in the Metadata section of the MapServer.map configuration file which is discussed later:

::

   METADATA

   ...

   "WMS_STYLE" "default"
   "WMS_STYLE_DEFAULT_LEGENDURL_HEIGHT" "353"
   "WMS_STYLE_DEFAULT_LEGENDURL_WIDTH" "253"
   "WMS_STYLE_DEFAULT_LEGENDURL_HREF" "http://www.dinoservices.nl/TNO_Suriname_Geology/surinameLegend.png"
   "WMS_STYLE_DEFAULT_LEGENDURL_FORMAT" "image/png"

   ...

Note that the image format should be one that can be directly displayed by a web browser, i.e. JPEG, PNG or GIF.

.. _service_provision_data_preparation_lite:

Lite Schemas
-------------

GeoSciML-Lite and EarthResourceML-Lite (ERML-Lite) are simplified schemas that take the form of a flat table of attributes (conformant to OGC Simple Features Level-0 profile). These were previously called GeoSciML-Portrayal and EarthResourceML-Portrayal.

.. _service_provision_data_preparation_lite_geosciml:

GeoSciML-Lite
^^^^^^^^^^^^^^

The full specification for GeoSciML-Lite is in the `GeoSciML standard <http://docs.opengeospatial.org/is/16-008/16-008.html>`_. OneGeology itself does not currently make direct use of data using these schemas but the age and lithology URI columns in GeologicUnitView are those that an SLD enabled WMS needs to provide for the age and lithology highlighting functionality to work. These schemas do, however, provide a method to exchange simple interoperable data without supporting complex features that may be more easily achievable and that can help qualify for a 4 star accreditation.

There are seven GeoSciML-Lite views descibed in the 4.1 standard, these are:  GeologicUnitView, ShearDisplacmentStructureView, ContactView, BoreholeView, SiteObservationView, GeologicSpecimenView, GeomorphologicUnitView.  Below we lay out what is expected of the views for those features we think that many geological survey organizations will be able to support.

Generally across all GeoSciML-Lite views, missing values should be specified using OGC nil values *http://www.opengis.net/def/nil/ogc/0/* as below:

- above detection range (AboveDetectionRange)
  - Value was above the detection range of the instrument used to estimate it.
- below detection range (BelowDetectionRange)
  - Value was below the detection range of the instrument used to estimate it.
- inapplicable
  - There is no value
- missing
  - The correct value is not readily available to the sender of this data. Furthermore, a correct value may not exist
- template
  - The value will be available later
- unknown
  - The correct value is not known to, and not computable by, the sender of this data. However, a correct value probably exists
- withheld
  - The value is not divulged

Alternatively you could use INSPIRE defined void reasons *http://inspire.ec.europa.eu/codelist/VoidReasonValue/*

In the below tables describing the features, **Bold property names indicate required properties.**, *whilst properties of type _uri are defined as xs:string in the GeoSciML-Lite 4.1 schema, to be conformant with GML SF-0, the intention is that these strings SHALL BE absolute URI's.*

.. _service_provision_data_preparation_lite_contactview:

ContactView features
"""""""""""""""""""""

These features provide a simplified view of GeoSciML Contact Features. In GeoSciML terms this will be an instance of a MappedFeature with key property values from the associated ContactFeature summarized in text (data type xs:string) fields, and properties suffixed with ‘_uri’ that contain URIs referring to other resources, for example controlled concepts in published vocabularies.

**Elements in ContactView mapped feature scheme**


.. raw:: html

    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Implementation data type</th>
                <th>Notes</th>
            </tr>
        </thead>
        <tbody>
        <tr>
            <td class="rqd">identifier</td>
            <td>xs:string</td>
            <td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td>
        </tr>
        <tr>
            <td>name</td>
            <td>xs:string</td>
            <td>Display name for the Contact. Examples: &#8216;<i>depositional contact</i>&#8217;, &#8216;<i>unconformity</i>&#8217;, &#8216;<i>Martin-Escabrosa contact</i>&#8217;</td>
        </tr>
        <tr>
            <td>description</td>
            <td>xs:string</td>
            <td>Text description of the contact, may be a generic description of a contact type taken from an entry on a geological map legend, or a more specific description of the particular contact.</td>
        </tr>
        <tr>
            <td>contactType</td>
            <td>xs:string</td>
            <td>Text label specifying the kind of surface separating two geologic units including primary boundaries such as depositional contacts, all kinds of unconformities, intrusive contacts, and gradational contacts, as well as faults that separate geologic units. Ideally this would be the preferred label for the concept identified by contactType_uri</td>
        </tr>
        <tr>
            <td>observationMethod</td>
            <td>xs:string</td>
            <td>Metadata snippet indicating how the spatial extent of the feature was determined. ObservationMethod is a convenience property that provides a quick and dirty approach to observation metadata.</td>
        </tr>
        <tr>
            <td>positionalAccuracy</td>
            <td>xs:string</td>
            <td>Preferred use is a quantitative value defining the radius of an uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of 100 m for a line feature defines a buffer polygon of total width 200 m centered on the line. Some other text description that quantifies position accuracy may be provided, e.g. a term from a controlled vocabulary. Vocabulary used should be described in the dataset metadata.</td>
        </tr>
        <tr>
            <td>source</td>
            <td>xs:string</td>
            <td>Text describing feature specific details and citations to source materials, and if available providing URLs to reference material and publications describing the geologic feature. This could be a short text synopsis of key information that would also be in the metadata record referenced by metadata_uri.</td>
        </tr>
        <tr>
            <td class="rqd">contactType_uri</td>
            <td class="nbtype">xs:string</td>
            <td>URI referring to a controlled concept from a vocabulary defining the Contact types. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
        </tr>
        <tr>
            <td colspan="3" class="CGI">The current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/contacttype</td>
        </tr>
        <tr>
            <td colspan="3" class="INSPIRE">There is no INSPIRE specific controlled vocabulary for contact type.<br />OneGeology-Europe services applied one of the following CGI vocabulary terms:<br />impact_structure_boundary</a>, volcanic_subsicence_zone_boundary, glacial_stationary_line</td>
        </tr>
        <tr>
            <td>specification_uri</td>
            <td class="nbtype">xs:string</td>
            <td>URI referring to the GeoSciML Contact feature that describes the instance in detail. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
        </tr>
        <tr>
            <td>metadata_uri</td>
            <td class="nbtype">xs:string</td>
            <td>URI referring to a formal metadata record describing the provenance of data.</td>
        </tr>
        <tr>
            <td>genericSymbolizer</td>
            <td>xs:string</td>
            <td>Identifier for a symbol from standard (locally or community defined) symbolization scheme for portrayal. There should be an SLD file available defining the symbol associated with each genericSymbolizer value.</td>
        </tr>
        <tr>
            <td class="rqd">shape</td>
            <td>GM_Object</td>
            <td>Geometry defining the extent of the feature of interest. This is the only element with complex content, and must contain a GML geometry that is valid for the Geography Markup Language (GML) simple features profile (OGC 06-049r1.). The shape value will generally be provided by GIS software, and will need no user input.</td>
        </tr>
        <tr>
            <td colspan="2">Other attribute(s)</td>
            <td>A placeholder allowing any user-defined attributes to be delivered in addition to those specified above.</td>
        </tr>
        </tbody>
    </table>


.. _service_provision_data_preparation_lite_sheardisplacementstructureview:

ShearDisplacementStructureView features
""""""""""""""""""""""""""""""""""""""""

These features represent faults and ductile shear zones. In GeoSciML terms they are instances of MappedFeature with key property values from the associated ShearDisplacementStructure feature summarized in text fields (data type xs:string) and fields containing identifiers (URI) for fault type, deformation style, movement type, geologic age, and a formally-encoded (ideally in GeoSciML) specification for interoperability. The latter are the properties suffixed with ‘_uri’ and will contain URIs referring to other resources, for example controlled concepts in published vocabularies.

The concept of ‘Shear displacement structure’ includes all brittle to ductile style faults or ductile shear zones along which displacement has occurred, from a simple, single ‘planar’ brittle or ductile surface to a fault system comprising multiple strands of both brittle and ductile nature. Because this feature class is constrained to have a linear geometry, it is limited to representing shear displacement structures that are considered single surfaces at the scale of portrayal.

**Elements in Shear Displacement Structure View feature**

.. raw:: html


    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Type</th>
                <th>Notes</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="rqd">identifier</td>
                <td>xs:string</td>
                <td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td>
            </tr>
            <tr>
                <td>name</td>
                <td>xs:string</td>
                <td>Display name for the ShearDisplacementStructure. This may be a generic fault type, e.g. &#8216;<i>thrust fault</i>&#8217;, &#8216;strike-slip fault</i>&#8217;, or a particular fault name, e.g. &#8216;<i>Moine thrust</i>&#8217;, &#8216;san Andreas Fault</i>&#8217;.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>xs:string</td>
                <td>Text description of the ShearDisplacementStructure, typically taken from an entry on a geological map legend.</td>
            </tr>
            <tr>
                <td>faultType</td>
                <td>xs:string</td>
                <td>Type of ShearDisplacementStructure (as defined in GeoSciML).</td>
            </tr>
            <tr>
                <td>movementType</td>
                <td>xs:string</td>
                <td>Summary of the type of movement (e.g. dip-slip, strike-slip) on the ShearDisplacementStructure.</td>
            </tr>
            <tr>
                <td>deformationStyle</td>
                <td>xs:string</td>
                <td>Description of the style of deformation (e.g. brittle, ductile etc) for the ShearDisplacementStructure.</td>
            </tr>
            <tr>
                <td>displacement</td>
                <td>xs:string</td>
                <td>Text summary of displacement across the ShearDisplacementStructure.</td>
            </tr>
            <tr>
                <td>geologicHistory</td>
                <td>xs:string</td>
                <td>Text (possibly formatted with formal syntax) description of the sequence of events that formed and have affected the ShearDisplacementStructure. Events include process and optional environment information.</td>
            </tr>
            <tr>
                <td>observationMethod</td>
                <td>xs:string</td>
                <td>Metadata snippet indicating how the spatial extent of the feature was determined. ObservationMethod is a convenience property that provides a quick and dirty approach to observation metadata when data are reported using a feature view (as opposed to observation view).</td>
            </tr>
            <tr>
                <td>positionalAccuracy</td>
                <td>xs:string</td>
                <td>Preferred use is a quantitative value defining the radius of an uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of 100 m for a line feature defines a buffer polygon of total width 200 m centered on the line. Some other text description that quantifies position accuracy may be provided, e.g. a term from a controlled vocabulary. Vocabulary used should be described in the dataset metadata.</td>
            </tr>
            <tr>
                <td>source</td>
                <td>xs:string</td>
                <td>Text describing feature specific details and citations to source materials, and if available providing URLs to reference material and publications describing the geologic feature. This could be a short text synopsis of key information that would also be in the metadata record referenced by metadata_uri.</td>
            </tr>
            <tr>
                <td class="rqd">faultType_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a controlled concept from a vocabulary defining the fault (ShearDisplacementStructure) type. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
            </tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/faulttype</td>
            </tr>
            <tr>
                <td colspan="3" class="INSPIRE">The current INSPIRE specific controlled vocabulary is: http://inspire.ec.europa.eu/codelist/FaultTypeValue/</td>
            </tr>
            <tr>
                <td class="rqd">movementType_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a controlled concept from a vocabulary defining the ShearDisplacementStructure movement type. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
            </tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/faultmovementtype</td>
            </tr>
            <tr>
                <td colspan="3" class="INSPIRE">There is no INSPIRE specific controlled vocabulary for movement type.</td>
            </tr>
            <tr>
                <td class="rqd">deformationStyle_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a controlled concept from a vocabulary defining the ShearDisplacementStructure deformation style. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
            </tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary URI stem is: http://resource.geosciml.org/classifier/cgi/deformationstyle<br />for concepts see: http://resource.geosciml.org/vocabulary/cgi/201211/deformationstyle.html</td>
            </tr>
            <tr>
                <td colspan="3" class="INSPIRE">There is no INSPIRE specific controlled vocabulary for deformation style</td>
            </tr>
            <tr>
                <td class="rqd">representativeAge_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a controlled concept specifying the most representative stratigraphic age interval for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing the all or part of the feature&#8217;s history.</td>
            </tr>
            <tr>
                <td class="rqd">representativeOlderAge_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a controlled concept specifying the most representative older value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing the all or part of the feature&#8217;s history.</td>
            </tr>
            <tr>
                <td class="rqd">representativeYoungerAge_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a controlled concept specifying the most representative younger value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing the all or part of the feature&#8217;s history.</td>
            </tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary are: http://resource.geosciml.org/classifier/ics/ischart and<br />http://resource.geosciml.org/classifier/cgi/stratchart (for OneGeology-Europe Precambrian Epoch definitions for the Fenno-Scandian Shield)</td>
            </tr>
            <tr>
                <td colspan="3" class="INSPIRE">The current INSPIRE specific controlled vocabulary is: http://inspire.ec.europa.eu/codelist/GeochronologicEraValue/</td>
            </tr>
            <tr>
                <td>numericOlderAge</td>
                <td>xs:double</td>
                <td>Older age in numerical representation in Ma.</td>
            </tr>
            <tr>
                <td>numericYoungerAge</td>
                <td>xs:double</td>
                <td>Younger age in numerical representation in Ma.</td>
            </tr>
            <tr>
                <td>specification_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to the GeoSciML ShearDisplacementStructure feature that describes the instance in detail. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
            </tr>
            <tr>
                <td>metadata_uri</td>
                <td class="nbtype">xs:string</td>
                <td>URI referring to a metadata record describing the provenance of data.</td>
            </tr>
            <tr>
                <td>genericSymbolizer</td>
                <td>xs:string</td>
                <td>Identifier for a symbol from standard (locally or community defined) symbolization scheme for portrayal.</td>
            </tr>
            <tr>
                <td class="rqd">shape</td>
                <td>GM_Object<br />(GM_curve)</td>
                <td>Geometry defining the extent of the feature of interest.</td>
            </tr>
            <tr>
                <td colspan="2">Other attribute(s)</td>
                <td>A placeholder allowing any user-defined attributes to be delivered in addition to those specified above.</td>
            </tr>
        </tbody>
    </table>

.. _service_provision_data_preparation_lite_geologicunitview:

GeologicUnitView features
""""""""""""""""""""""""""

GeologicUnitView features represent outcrops of a particular geologic unit, typically with polygon geometry. The properties of these features provide a simplified view of information associated with GeoSciML GeologicUnit features. A geologic unit in this context is an identifiable body of material within the Earth. GeologicUnitView features are instances of GeoSciML MappedFeature with property values from the associated GeologicUnit specifier summarized in text fields for human data consumers, and with fields containing standard identifiers for geologic unit type, representative lithology, and geologic age. The specification_uri property identifies a description resource specific to the geologic unit cropping out in the extent of the polygon (or other) geometry of the feature. The specification_uri should dereference to yield a formally-encoded representation of the geologic unit, ideally in GeoSciML for interoperability. Properties populated by identifiers are suffixed with ‘_uri’ and contain URIs referring to other resources, for example controlled concepts in published vocabularies.

**Elements in GeologicUnitView feature class**

.. raw:: html


	<table>
		<thead>
            <tr>
                <th>Name</th>
                <th>Type</th>
                <th>Notes</th>
            </tr>
        </thead>
		<tbody>
			<tr>
                <td class="rqd">identifier</td>
                <td>xs:string</td>
                <td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td>
            </tr>
			<tr>
                <td>name</td>
                <td>xs:string</td>
                <td>Display name for the GeologicUnit; this can be used to put in a geologic unit name, or more likely an abbreviation used to label outcrops of the unit in a map display.</td>
            </tr>
			<tr>
				<td>description</td>
				<td>xs:string</td>
				<td>Text description of the GeologicUnit, typically taken from an entry on a geological map legend.</td>
			</tr>
			<tr>
				<td>geologicUnitType</td>
				<td>xs:string</td>
				<td>Type of GeologicUnit (as defined in GeoSciML).</td>
			</tr>
			<tr>
				<td>rank</td>
				<td>xs:string</td>
				<td>Stratigraphic rank of GeologicUnit (as defined in GeoSciML). Examples: formation, member, group, supergroup.</td>
			</tr>
			<tr>
				<td>lithology</td>
				<td>xs:string</td>
				<td>Text (possibly formatted with formal syntax) description of the GeologicUnit&#8217;s lithology.</td>
			</tr>
			<tr>
				<td>geologicHistory</td>
				<td>xs:string</td>
				<td>Text (possibly formatted with formal syntax) description of the age of the GeologicUnit (where age is a sequence of events and may include process and environment information).</td>
			</tr>
			<tr>
				<td>numericOlderAge</td>
				<td>xs:double</td>
				<td>Older age in numerical representation in Ma.</td>
			</tr>
			<tr>
				<td>numericYoungerAge</td>
				<td>xs:double</td>
				<td>Younger age in numerical representation in Ma.</td>
			</tr>
			<tr>
				<td>observationMethod</td>
				<td>xs:string</td>
				<td>ObservationMethod is a convenience property to provide observation metadata. Example values might include &#8216;<i>field observation by author</i>&#8217;, &#8216;<i>compilation from published maps</i>&#8217;, &#8216;<i>air photo interpretation</i>&#8217;.</td>
			</tr>
			<tr>
				<td>positionalAccuracy</td>
				<td>xs:string</td>
				<td>Preferred use is a quantitative value defining the radius of an uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of 100 m for a line feature defines a buffer polygon of total width 200 m centered on the line. Some other text description that quantifies position accuracy may be provided, e.g. a term from a controlled vocabulary. Vocabulary used should be described in the dataset metadata. For polygon mapped features this is intended for use to indicate the position uncertainty of the contact and fault features bounding the outcrop polygon, which is only necessary if the associated line features are not included with the polygons.</td>
			</tr>
			<tr>
				<td>source</td>
				<td>xs:string</td>
				<td>Text describing feature specific details and citations to source materials, and if available providing URLs to reference material and publications describing the geologic feature. This could be a short text synopsis of key information that would also be in the metadata record referenced by metadata_uri.</td>
			</tr>
			<tr>
                <td class="rqd">geologicUnitType_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI referring to a controlled concept from a vocabulary defining the GeologicUnit types. Mandatory property - if no value is provided then an URI referring to a controlled concept explaining why the value is nil must be provided.</td>
			</tr>
			<tr>
                <td colspan="3" class="CGI">The current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/geologicunittype/</td>
			</tr>
			<tr>
                <td colspan="3" class="INSPIRE">The current INSPIRE specific controlled vocabulary is: http://inspire.ec.europa.eu/codelist/GeologicUnitTypeValue/</td>
			</tr>
			<tr>
                <td class="rqd">representativeLithology_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI referring to a controlled concept specifying the characteristic or representative lithology of the unit. This may be a concept that defines the supertype of all lithology values present within a GeologicUnit or a concept defining the lithology of the dominant CompositionPart (as defined in GeoSciML) of the unit. This identifier is intended for use as the symbol key for a lithologic map portrayal of the geologic unit features.</td>
			</tr>
			<tr>
                <td colspan="3" class="CGI">The current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/lithology</td>
			</tr>
			<tr>
                <td colspan="3" class="INSPIRE">The current INSPIRE specific controlled vocabulary is: http://inspire.ec.europa.eu/codelist/LithologyValue/</td>
			</tr>
			<tr>
                <td class="rqd">representativeAge_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI referring to a controlled concept specifying the most representative stratigraphic age interval for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing all or part of the feature&#8217;s history. This identifier is intended for use as a symbol key for a geologic-age-based portrayal of the geologic unit features.</td>
			</tr>
			<tr>
                <td class="rqd">representativeOlderAge_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI referring to a controlled concept specifying the most representative older value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing all or part of the feature&#8217;s history.</td>
			</tr>
			<tr>
                <td class="rqd">representativeYoungerAge_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI referring to a controlled concept specifying the most representative younger value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing all or part of the feature&#8217;s history.</td>
			</tr>
			<tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary are: http://resource.geosciml.org/classifier/ics/ischart and<br />http://resource.geosciml.org/classifier/cgi/stratchart (for OneGeology-Europe Precambrian Epoch definitions for the Fenno-Scandian Shield)</td>
			</tr>
			<tr>
                <td colspan="3" class="INSPIRE">The current INSPIRE specific controlled vocabulary is: http://inspire.ec.europa.eu/codelist/GeochronologicEraValue/</td>
			</tr>
			<tr>
				<td>specification_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI for a complete description of the geologic unit cropping out within the extent of the feature&#8217;s geometry. Preferred representation is a GeoSciML GeologicUnit feature instance. Mandatory property - if no value is provided then a nil reason URI explaining why the value is nil must be provided</td>
			</tr>
			<tr>
				<td>metadata_uri</td>
                <td class="nbtype">xs:string</td>
				<td>URI referring to a metadata record describing the provenance of data</td>
			</tr>
			<tr>
				<td>genericSymbolizer</td>
				<td>xs:string</td>
				<td>Identifier for a symbol from standard (locally or community defined) symbolization scheme for portrayal</td>
			</tr>
			<tr>
                <td class="rqd">shape</td>
				<td>GM_Object</td>
				<td>Geometry defining the extent of the feature of interest</td>
			</tr>
			<tr>
                <td colspan="2">Other attribute(s)</td>
				<td>A placeholder allowing any user-defined attributes to be delivered in addition to those specified above.</td>
			</tr>
		</tbody>
	  </table>


.. _service_provision_data_preparation_lite_boreholeview:

BoreholeView features
""""""""""""""""""""""

BoreholeView is a simplified view of a GeoSciML Borehole. In GeoSciML terms, this will be an instance of a Borehole feature with key property values summarised as labels (unconstrained character strings) or arbitrarily selected classifiers to be used for thematic mapping purposes. The latter are the properties suffixed with “_uri” and will contain URIs referring to controlled concepts in published vocabularies.

**Elements in BoreholeView feature class**

.. raw:: html

	<table>
		<thead>
            <tr>
                <th>Name</th>
                <th>Type</th>
                <th>Notes</th>
            </tr>
        </thead>
		<tbody>
			<tr>
                <td class="rqd">identifier</td>
                <td>xs:string</td>
                <td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td>
            </tr>
			<tr>
                <td>name</td>
                <td>xs:string</td>
                <td>Display name for the Borehole.</td>
            </tr>
			<tr>
				<td>description</td>
				<td>xs:string</td>
				<td>Text description of the Borehole</td>
			</tr>
			<tr>
				<td>purpose</td>
				<td>xs:string</td>
				<td>The purpose or purposes for which the borehole was drilled. (e.g., mineral exploration, hydrocarbon exploration, hydrocarbon production, groundwater monitoring, geothermal)</td>
			</tr>
			<tr>
				<td>status</td>
				<td>xs:string</td>
				<td>The current status of the borehole (e.g., abandoned, completed, proposed, suspended)</td>
			</tr>
			<tr>
				<td>drillingMethod</td>
				<td>xs:string</td>
				<td>The drilling method, or methods, used for this borehole (e.g., RAB, auger, diamond core drilling, air core drilling, piston)</td>
			</tr>
			<tr>
				<td>operator</td>
				<td>xs:string</td>
				<td>The organisation or agency responsible for commissioning of the borehole (as opposed to the agency which drilled the borehole)</td>
			</tr>
			<tr>
				<td>driller</td>
				<td>xs:string</td>
				<td>The organisation responsible for drilling the borehole (as opposed to commissioning the borehole)</td>
			</tr>
			<tr>
				<td>drillStartDate</td>
				<td class="nbtype">xs:string</td>
				<td>The date of the start of drilling formatted according to ISO8601 (e.g., 2012-03-17)</td>
			</tr>
			<tr>
				<td>drillEndDate</td>
				<td class="nbtype">xs:string</td>
				<td>The date of the end of drilling formatted according to ISO8601 (e.g., 2012-03-28)</td>
			</tr>
			<tr>
				<td>startPoint</td>
				<td>xs:string</td>
				<td>The position relative to the ground surface where the borehole commenced (e.g., open pit floor or wall, underground, natural land surface, sea floor)</td>
			</tr>
			<tr>
				<td>inclinationType</td>
				<td>xs:string</td>
				<td>The type of inclination of the borehole (e.g., vertical, inclined up, inclined down, horizontal)</td>
			</tr>
			<tr>
                <td>boreholeMaterialCustodian</td>
                <td>xs:string</td>
				<td>The organisation that is the custodian of the material recovered from the borehole</td>
			</tr>
			<tr>
                <td>boreholeLength_m</td>
                <td>xs:string</td>
				<td>The length of a borehole, in metres, as determined by the data provider. Length may have different sources (e.g., driller’s measurement, logger’s measurement, survey measurement)</td>
			</tr>
            <tr>
                <td>elevation_m</td>
                <td>xs:string</td>
				<td>The elevation data, in metres, for the borehole (i.e., wellbore) start point. This is a compromise approach to allow for delivery of legacy 2D data without elevation data, and for software that cannot process a 3D GM_Point</td>
			</tr>
            <tr>
                <td>elevation_srs</td>
                <td>xs:string</td>
				<td>An URI of a spatial reference system of the elevation value. (e.g., mean sea level). Mandatory if elevation_m is populated. The SRS shall be a one dimensional vertical SRS (i.e., EPSG code in the range 5600-5799),<br/>
                For example: http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::5711</td>
			</tr>
            <tr>
                <td>positionalAccuracy</td>
                <td>xs:string</td>
				<td>An estimate of the accuracy of the location of the borehole collar location.  Ideally, this would be a quantitative estimate of accuracy (e.g., 20 metres)</td>
			</tr>
            <tr>
                <td>source</td>
                <td>xs:string</td>
				<td> describes details and citations to source materials for the borehole and, if available, providing URLs to reference material and publications describing the borehole. This could be a short text synopsis of key information that would also be in the metadata record referenced by metadata_uri</td>
			</tr>
			<tr>
                <td>parentBorehole_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI referring to one or more representations of a parent borehole (e.g., a parent well of a sidetrack wellbore)<br />If present, parentBorehole_uri SHOULD resolve to a representation of a GeoSciML borehole.<br />
                **If the borehole does not have any parent, this field shall be empty**</td>
			</tr>
			<tr>
				<td>metadata_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI referring to a metadata record describing the provenance of data</td>
			</tr>
			<tr>
				<td>genericSymbolizer</td>
				<td>xs:string</td>
				<td>Identifier for a symbol from standard (locally or community defined) symbolization scheme for portrayal</td>
			</tr>
			<tr>
                <td class="rqd">shape</td>
				<td>GM_Object</td>
				<td>Geometry defining the extent of the feature of interest</td>
			</tr>
			<tr>
                <td colspan="2">Other attribute(s)</td>
				<td>A placeholder allowing any user-defined attributes to be delivered in addition to those specified above</td>
			</tr>
		</tbody>
	  </table>


.. _service_provision_data_preparation_lite_earthresourceml:

EarthResourceML-Lite
^^^^^^^^^^^^^^^^^^^^^

EarthResourceML-Lite is a model and schema for simple map services (eg, WMS and WFS Simple Features). It is an abridged version of the full EarthResourceML model and can be used to deliver simplified views on mineral occurrences and their commodities, mines, mining activities and mine waste products.

There are six EarthResourceML-Lite views descibed in the 2.0 standard, these are:  MineView, CommodityResourceView, MineralOccurrenceView, MiningActivityView, MiningWasteView, and ProcessingPlantView.  Below we lay out what is expected of the views for those features we think that many geological survey organizations will be able to support.

For full details of the ERML-Lite schema see: http://schemas.earthresourceml.org/earthresourceml-lite/2.0/erml-lite.xsd

For full documentation of all the views see http://www.earthresourceml.org/earthresourceml-lite/2.0.1/documentation/


.. _service_provision_data_preparation_lite_mineraloccurrenceview:

MineralOccurrenceView features
"""""""""""""""""""""""""""""""

.. raw:: html

	<table>
		<thead>
            <tr>
                <th>Name</th>
                <th>Type</th>
                <th>Notes</th>
            </tr>
        </thead>
		<tbody>
			<tr>
                <td class="rqd">identifier</td>
                <td>xs:string</td>
                <td>A unique identifier (ideally an URI) to identify this Mineral Occurrence mapped feature</td>
            </tr>
			<tr>
                <td>name</td>
                <td>xs:string</td>
                <td>Name of the Mineral Occurrence, if applicable</td>
            </tr>
			<tr>
				<td class="rqd">mineralOccurrenceType</td>
				<td>xs:string</td>
				<td>The type of mineral occurrence. Examples may include prospect, occurrence, mineral deposit, ore deposit, field, district, lode. Ideally terms should be sourced from the MineralOccurrenceType controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/mineral-occurrence-type</td>
			</tr>
			<tr>
				<td class="rqd">commodity</td>
				<td>xs:string</td>
				<td>The commodity or commodities found at an EarthResource. Multiple commodities terms should be concatenated if required. Ideally terms should be sourced from the CommodityCode controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/commodity-code</td>
			</tr>
			<tr>
				<td>mineName</td>
				<td>xs:string</td>
				<td>The name of a mine associated with the Mineral Occurrence, if applicable</td>
			</tr>
			<tr>
				<td>geologicHistory</td>
				<td>xs:string</td>
				<td>A brief description of the age and mineralisation history of the mineral occurrence</td>
			</tr>
			<tr>
				<td>hostGeologicUnit</td>
				<td>xs:string</td>
				<td>Name or description of the host geologic unit</td>
			</tr>
			<tr>
				<td>mineralDepositModel</td>
				<td>xs:string</td>
				<td>Systematically arranged information describing the interpreted mineralisation model or classification for the mineral occurrence. Ideally, terms should be sourced from a controlled vocabulary. May be empirical (descriptive) or theoretical (genetic). (eg, Porphyry Cu, IOCG, VHMS, Epithermal vein)</td>
			</tr>
			<tr>
				<td>mineralOccurrenceShape</td>
				<td>xs:string</td>
				<td>Shape of the mineral occurrence (eg, lenticular, pipe, tabular). Ideally terms should be sourced from the EarthResourceShape controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/earth-resource-shape</td>
			</tr>
			<tr>
				<td>explorationActivityType</td>
				<td>xs:string</td>
				<td>The type of exploration activity eg, geological mapping, drilling, geophysical surveys, geochemical mapping. Ideally terms should be sourced from the ExplorationActivityType controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/exploration-activity-type</td>
			</tr>
			<tr>
				<td>explorationActivityDuration</td>
				<td>xs:string</td>
				<td>Period, or extent in time, of any exploration activity. eg; 1987-1989</td>
			</tr>
			<tr>
				<td>explorationResult</td>
				<td>xs:string</td>
				<td>The result of the exploration activity eg, mineralised zone identified, geochemical anomaly. Ideally terms should be sourced from the ExplorationResult controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/exploration-result</td>
			</tr>
			<tr>
                <td>observationMethod</td>
                <td>xs:string</td>
				<td>Description of the method that was used to identify the location of the Mineral Occurrence. Ideally terms should be sourced from the FeatureObservationMethod controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/mappedfeatureobservationmethod</td>
			</tr>
			<tr>
                <td>positionalAccuracy</td>
                <td>xs:string</td>
				<td>Text description of the accuracy of the feature location. (eg, accurate, approximate, diagrammatic, indefinite, unknown, 5 metres, 1 kilometre)</td>
			</tr>
            <tr>
                <td>source</td>
                <td>xs:string</td>
				<td>A reference for the source(s) of information for the Mineral Occurrence</td>
			</tr>
            <tr>
                <td class="rqd">mineralOccurrenceType_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the commodity. Ideally should link to the CommodityCode controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/mineral-occurrence-type</td>
			</tr>
            <tr>
                <td class="rqd">representativeCommodity_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the major commodity or commodity group for the Mineral Occurrence. Ideally should link to the CommodityCode controlled vocabulary</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/commodity-code</td>
			</tr>
            <tr>
                <td>mine_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify an associated Mine.</td>
			</tr>
			<tr>
                <td>hostGeologicUnit_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the host geologic unit. Ideally, a link to a GeoSciML GeologicUnit or GeologicUnitView. feature</td>
			</tr>
			<tr>
				<td>mineralDepositModel_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the interpreted mineral deposit model classification for the mineral occurrence. Should link to a controlled vocabulary term</td>
			</tr>
			<tr>
				<td>representativeAge_uri</td>
				<td class="nbtype">xs:string</td>
				<td>An URI referring to a GeologicalTimescale controlled concept specifying the most representative geologic age interval for the mineralisation. This will be defined entirely at the discretion of the data provider and may be a single event selected from the mineral occurrence's geologic history or a value summarising the all or part of its history</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/ics/ischart</td>
			</tr>
            <tr>
				<td>representativeOlderAge_uri</td>
				<td class="nbtype">xs:string</td>
				<td>An URI referring to a GeologicalTimescale controlled concept specifying the oldest interpreted age limit for the mineralisation</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/ics/ischart</td>
			</tr>
            <tr>
				<td>representativeYoungerAge_uri</td>
				<td class="nbtype">xs:string</td>
				<td>An URI referring to a GeologicalTimescale controlled concept specifying the youngest interpreted age limit for the mineralisation</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/ics/ischart</td>
			</tr>
            <tr>
				<td>specification_uri</td>
				<td class="nbtype">xs:string</td>
				<td>An URI to identify a full EarthResourceML description of the Mineral Occurrence feature</td>
			</tr>
			<tr>
                <td class="rqd">shape</td>
				<td>gml:GeometryPropertyType</td>
				<td>Geometry defining the location or extent of the mineral occurrence. Only one geometry type may be used in a single MineralOccurrenceView feature service</td>
			</tr>
			<tr>
                <td colspan="2">Other attribute(s)</td>
				<td>A placeholder allowing any user-defined attributes to be delivered in addition to those specified above</td>
			</tr>
		</tbody>
	  </table>


.. _service_provision_data_preparation_lite_commodityresourceview:

CommodityResourceView features
""""""""""""""""""""""""""""""

.. raw:: html

	<table>
		<thead>
            <tr>
                <th>Name</th>
                <th>Type</th>
                <th>Notes</th>
            </tr>
        </thead>
		<tbody>
			<tr>
                <td class="rqd">identifier</td>
                <td>xs:string</td>
                <td>A unique identifier (ideally an URI) to identify this Commodity Resource mapped feature</td>
            </tr>
			<tr>
                <td class="rqd">commodity</td>
                <td>xs:string</td>
                <td>A commodity found in an EarthResource. Other commodity values at the EarthResource should be listed in separate instances. Ideally terms should be sourced from the CommodityCode controlled vocabulary.</td>
            </tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/commodity-code</td>
			</tr>
			<tr>
				<td>commodityRank</td>
				<td>xs:string</td>
				<td>The importance of a commodity compared to other commodities that occur in the mineral deposit. Several commodities may be of interest in a deposit. This classification is based on the potential or endowment: reserves + resources. eg 'primary commodity', 'secondary commodity', 'by-product'</td>
			</tr>
			<tr>
				<td>commodityImportance</td>
				<td>xs:string</td>
				<td>The size ranking of the commodity resource in comparison to the worldwide distribution of mineral deposits. Commodity rank is based on the total endowment in an EarthResource, i.e. (cumulated) past production + reserves (not including past production) + resources, or if the deposit has never been exploited, reserves + resources. A statistical comparison with a large set of deposits throughout the world enables the determination of the deposit as class A (very large), B (large), or C (medium-sized) for a particular commodity. The rank of a commodity resource is thus not based on political or economic considerations</td>
			</tr>
			<tr>
				<td>mineralOccurrenceName</td>
				<td>xs:string</td>
				<td>Name of an associated mineral occurrence</td>
			</tr>
			<tr>
				<td>mineName</td>
				<td>xs:string</td>
				<td>The name of a mine associated with the commodity resource, if applicable</td>
			</tr>
			<tr>
				<td>totalEndowment</td>
				<td>xs:string</td>
				<td>Endowment refers to that quantity of a mineral in accumulations (deposits) meeting specified physical characteristics such as quality, size and depth. Usually includes all resources and reserves, as a commodity's total endowment does not have to have prospects for eventual economic extraction. It includes the total amount of a commodity originally introduced to a particular location during the deposit forming processes - and thus can include resources, reserves, past production and mining and metallurgical losses. Text string datatype so units of measure can be included in value. eg, 1.57 Mt @ 3.0 g/t Au</td>
			</tr>
			<tr>
				<td>totalReserves</td>
				<td>xs:string</td>
				<td>The economically mineable part of a Measured and/or Indicated mineral resource. It includes diluting materials and allowances for losses, which may occur when the material is mined. ‘Marketable Coal Reserves’ maybe reported in conjunction with, but not instead of, reports of Ore (Coal) Reserves. ‘Saleable product’ (e.g. for industrial minerals) can be reported in conjunction with ore reserve. Synonyms: Ore Reserve; Coal Reserve (s); Diamond (or gemstone) Ore Reserve; Mineral Reserves (not preferred, should be stated that used to mean the same as JORC’s Ore Reserve); Mineable production estimates. Text string data type so units of measure can be included in value. eg, 1.23 Mt @ 3.0 g/t Au</td>
			</tr>
			<tr>
				<td>reservesCategory</td>
				<td>xs:string</td>
				<td>The category of reserves (eg, measured, indicated). Should be a EarthResourceReserveCategory controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/reserve-assessment-category</td>
			</tr>
			<tr>
				<td>totalResources</td>
				<td>xs:string</td>
				<td>Total amount and grade of a concentration or occurrence of material of intrinsic economic interest in or on the Earth's crust in such form, quality and quantity that there are reasonable prospects for eventual economic extraction. eg, 1.57 Mt @ 3.0 g/t Au</td>
			</tr>
			<tr>
				<td>resourcesCategory</td>
				<td>xs:string</td>
				<td>The category of resources (eg, indicated, inferred). Should be a EarthResourceResourceCategory controlled vocabulary term.</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/resource-assessment-category</td>
			</tr>
			<tr>
				<td>classificationMethodUsed</td>
				<td>xs:string</td>
				<td>The classification method used to calculate the measurement of ore. Should be a MineralResourceReportingClassificationMethod controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/classification-method-used</td>
			</tr>
			<tr>
                <td>observationMethod</td>
                <td>xs:string</td>
				<td>Description of the method that was used to identify the location of the commodity occurrence. Ideally, terms should be sourced from a controlled vocabulary. (eg, global positioning system, published map, field observation, downhole survey, aerial photography, field survey).</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/mappedfeatureobservationmethod</td>
			</tr>
			<tr>
                <td>positionalAccuracy</td>
                <td>xs:string</td>
				<td>Text description of the accuracy of the feature location. (eg, accurate, approximate, diagrammatic, indefinite, unknown, 5 metres, 1 kilometre)</td>
			</tr>
            <tr>
                <td>source</td>
                <td>xs:string</td>
				<td>A reference for the source(s) of information for the commodity description.</td>
			</tr>
            <tr>
                <td class="rqd">commodityClassifier_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the commodity. Ideally should link to the CommodityCode controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/commodity-code</td>
			</tr>
            <tr>
                <td>mineralOccurrence_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify an associated Mineral Occurrence</td>
			</tr>
            <tr>
                <td>mine_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify an associated Mine.</td>
			</tr>
			<tr>
                <td>reservesCategory_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the reserve category. Should link to a EarthResourceReserveCategory controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/reserve-assessment-category</td>
			</tr>
			<tr>
				<td>resourcesCategory_uri</td>
                <td class="nbtype">xs:string</td>
				<td>An URI to identify the resource category. Should link to a EarthResourceQuantityAssessmentCategory controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/resource-assessment-category</td>
			</tr>
			<tr>
				<td>classificationMethodUsed_uri</td>
				<td class="nbtype">xs:string</td>
				<td>An URI to identify the classification method used to calculate the measurement of ore. Should link to a MineralResourceReporting ClassificationMethod controlled vocabulary term</td>
			</tr>
            <tr>
                <td colspan="3" class="CGI">Current CGI controlled vocabulary is: http://resource.geosciml.org/classifier/cgi/classification-method-used</td>
			</tr>
            <tr>
				<td>specification_uri</td>
				<td class="nbtype">xs:string</td>
				<td>An URI to identify a full EarthResourceML description of the commodity resource feature</td>
			</tr>
			<tr>
                <td class="rqd">shape</td>
				<td>gml:GeometryPropertyType</td>
				<td>Geometry defining the location or extent of the commodity resource. Only one geometry type may be used in a single CommodityResourceView feature service</td>
			</tr>
			<tr>
                <td colspan="2">Other attribute(s)</td>
				<td>A placeholder allowing any user-defined attributes to be delivered in addition to those specified above</td>
			</tr>
		</tbody>
	  </table>

.. _service_provision_data_preparation_complex:

Complex Feature Data
---------------------

.. todo::

    WIP: The below text has been extracted from the GeoSciML 4.1 Encoding Cookbook for OneGeology and INSPIRE. It needs re-wrting for here. The INSPIRE references need a bit more context explanation for this position in the 1G web pages. Need to remove figure numbering. Compare the way this is explained with the GeoSciML-Lite schemas. Maybe they need a common introduction saying these are data specifications you might want to map your date to as opposed to the other sections which are about file/db formats? Then notes on ERML could be added (although less urgent as we are mainly focussed on ERML-Lite for the moment in 1G. Consider whether can make links to GeoSciML standard HTML documentation rather than reproducing all diagrams etc. here?

GeoSciML is an application-neutral encoding format for geosciences information. It is based on Geography Markup Language v3.2 (GML) (ISO 19136:2007) for representation of features and geometry. GeoSciML was developed by the CGI (Commission for the Management and Application of Geoscience Information), a Commission of the International Union of Geological Sciences (IUGS). Following a memorandum of understanding between IUGS and the Open Geospatial Consortium (OGC), GeoSciML v4.1 was published in 2017 as an OGC standard (`http://www.opengeospatial.org/standards/geosciml <http://www.opengeospatial.org/standards/geosciml>`_). Future releases will be managed by the OGC GeoSciML Standards Working Group (SWG).

GeoSciML has a wide scope allowing the encoding of most information depicted on geological maps, as well as information about boreholes and laboratory analyses. This cookbook, however, concentrates on just those parts of GeoSciML necessary for (i) encoding the INSPIRE Geology application schema and (ii) delivering geological age and lithology information through OneGeology  services.

The INSPIRE geology data specification (D2.8.II.4 Data Specification on Geology –
Draft Technical Guidelines) describes the geological information that needs to
be made available through INSPIRE conformant web services. INSPIRE services can
be encoded using GeoSciML v4.1 in order to achieve maximum global
interoperability and to enable the INSPIRE geology data specification to be
extended to include other geosciences information. A mapping between the INSPIRE
specification and GeoSciML v4.1 is given in Annex 1. Note that the INSPIRE
Geology Data Specification also includes application schema for hydrogeology
and geophysics which are not covered by this cookbook.

Geological age and lithology are used as the basis for querying and portrayal in
OneGeology and this cookbook covers the parts of GeoSciML required to be
delivered as part of a 5 star OneGeology service.

To facilitate semantic interoperability it is important to use shared vocabularies. The CGI has developed suitable vocabularies for many GeoSciML properties and these are available from the GeoSciML resources website (`http://resource.geosciml.org/ <http://resource.geosciml.org/>`_). For INSPIRE the vocabularies that must be used are included in the data specification and are available from the INSPIRE registry (`http://inspire.ec.europa.eu/registry/ <http://inspire.ec.europa.eu/registry/>`_). The OneGeology portal can query services using either CGI or INSPIRE vocabularies.Both sets of vocabularies use http URIs as concept identifiers.

This cookbook is designed to assist users map their data to the GeoSciML data model. In most cases users with digital geoscience data will have their own formalised model of some type, although this will not always be the case. Where a formalised user data model exists then the process of mapping data to GeoSciML will largely involve mapping features/entities in the user model to their equivalents in the GeoSciML logical data model. Where no such user model exists then mapping must be carried out direct from the data.

To carry out the mapping, from either a model or direct from data, requires staff with geoscientific knowledge, familiarity with the user’s own data and data model, and an understanding of the UML formalisation used in documenting GeoSciML. These staff are likely to be geoscientists, possibly those who were involved in developing the organisation’s own data model, and it is these people who are seen as the main users of this cookbook.

Materials and documentation on GeoSciML have been produced by the CGI  and OGC and are available "as is" for download from `http://www.geosciml.org/ <http://www.geosciml.org/>`_ and `http://www.opengeospatial.org/standards/geosciml <http://www.opengeospatial.org/standards/geosciml>`_.

The supporting materials most relevant to this cookbook include:

* Full documentation of the GeoSciML model. This is generated automatically from the GeoSciML UML diagrams and draws on the scope notes in those diagrams. This full documentation, however, does not include any best practice guidance
* An Enterprise Architect version of the UML for the CGI packages
* GeoSciML examples

There are also XML Schema documents which enable validation of the GeoSciML instance documents that you produce from your mapped data. These are listed at `http://schemas.opengis.net/gsml/4.1/ <http://schemas.opengis.net/gsml/4.1/>`_. For the parts covered by this cookbook you will need http://schemas.opengis.net/gsml/4.1/geoSciMLBasic.xsd and, if you are providing borehole data, `http://schemas.opengis.net/gsml/4.1/borehole.xsd <http://schemas.opengis.net/gsml/4.1/borehole.xsd>`_. You can also find some Schematron files which provide extra validation for the INSPIRE profile of GeoSciML. `http://schemas.geosciml.org/geosciml/4.1/geoSciMLBasic_inspire_mandatory.sch <http://schemas.geosciml.org/geosciml/4.1/geoSciMLBasic_inspire_mandatory.sch>`_ checks that all properties required by INSPIRE have been provided and `http://schemas.geosciml.org/geosciml/4.1/geoSciML_inspire_vocabularies.sch <http://schemas.geosciml.org/geosciml/4.1/geoSciML_inspire_vocabularies.sch>`_ checks that the appropriate INSPIRE vocabulary terms have been used.

There are six packages in GeoSciML. Two are required for INSPIRE services: GeoSciML-Basic and Borehole. Only GeoSciML-Basic is required for a 5 star OneGeology service. This section will describe those parts of these packages which are the minimum requirement for conformance with the INSPIRE geology application schema. The parts required for a One Geology service are a subset of the INSPIRE ones and are highlighted as they are covered.

In GeoSciML most properties are optional. For a
OneGeology service you may decide whether to omit or include properties that
are not specified below as required. If you wish to provide explicit reasons
for some missing values you can include the relevant property, add an
xsi:nil="true" attribute and use a nilReason attribute to specify the
reason the value is not being supplied. Unless your service is also an INSPIRE
service, one of the nilReasons defined in ISO 19136:2007 section 8.2.3.1 should
be used:

* **inapplicable** - there is no value
* **missing** - the correct value is not readily available to the sender of this data. Furthermore, a correct value may not exist
* **template** - the value will be available later
* **unknown** - the correct value is not known to, and not computable by, the sender of this data. However, a correct value probably exists
* **withheld** - the value is not divulged

However, for INSPIRE services all attributes in the
data specification should be provided. ‘Voidable’ does not mean ‘optional’ in
INSPIRE. Where no value is provided for an INSPIRE voidable attribute then a nilReason
must be provided. One of the nilReasons defined in the INSPIRE `VoidReasonValue <http://inspire.ec.europa.eu/codelist/VoidReasonValue/>`_
codelist should be used:

* `http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unpopulated <http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unpopulated>`_ - The characteristic is not part of the dataset maintained by the data provider. However, the characteristic may exist in the real world.
* `http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown <http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown>`_ - the correct value for the specific spatial object is not known to, and not computable by, the data provider. However, a correct value may exist.
* `http://inspire.ec.europa.eu/codelist/VoidReasonValue/Withheld <http://inspire.ec.europa.eu/codelist/VoidReasonValue/Withheld>`_ - the characteristic may exist, but it is confidential and not divulged by the data provider.

This doesn’t apply to attributes that exist in
GeoSciML but that aren’t part of the INSPIRE data specification. Where no value
is provided for these they may have any nilReason permitted by GeoSciML or may
simply be omitted if permitted by GeoSciML. Figure 1 shows examples of how to provide nil
values.

.. code-block:: xml

 <gsmlb:geologicUnitType xsi:nil="true" nilReason="http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown" />
 <gsmlb:rank xsi:nil="true" nilReason="inapplicable" />

Figure 1 Examples of encoding nil values

As GeoSciML is a GML schema all objects must have a
value for the mandatory gml:id attribute. This provides an identifier for the
XML element representing the object, and must be unique within the XML
document. XML elements representing a particular object, for example a specific
GeologicUnit, need only be described once in the document. Subsequent
occurrences can reference the element using the gml:id. The gml:id attribute
should not be used for the global identifier of the object, it is simply an
identifier within the XML document.

Vocabulary concepts should be encoded by reference.
This enables information about the concept, such as a full description, to be
accessed from the relevant vocabulary service. The general pattern is that the
href attribute provides the URI of the concept and the title attribute provides
a human readable label for it.

An example of encoding the INSPIRE Geology application
schema in GeoSciML is given in Annex 2. This example is structured as a GeologicCollection
with one of each type of INSPIRE feature included. It is designed to illustrate
GeoSciML encoding rather than illustrate what a real INSPIRE service might look
like.

An example of a response that would be suitable for a
OneGeology 5 star WFS is given in Annex 3.

Mapped Feature and Geologic Feature
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/image001.jpg

   Figure 2: INSPIRE UML class diagram for GeologicFeature, MappedFeature, GeologicEvent and ThematicClass

.. figure:: images/image002.jpg

   Figure 3: UML context diagram for GeoSciML GeologicFeature

The INSPIRE UML class diagram for GeologicFeature, MappedFeature, GeologicEvent and ThematicClass is shown in Figure 2 and the UML of the equivalent GeoSciML classes in Figure 3.

The MappedFeature and GeologicFeature objects are at the core of GeoSciML. A MappedFeature can be considered an occurrence, such as a polygon on a geologic map, of a real world GeologicFeature the full extent of which is unknown. It is independent of geometry, so the same GeologicFeature can have different MappedFeature instances, representing mapped polygons at different scales or a modelled volume for example. Each MappedFeature, however, can be specified by only one GeologicFeature. The specification association, from MappedFeature to GeologicFeature, is required by INSPIRE. An INSPIRE service provides a collection of MappedFeatures. A OneGeology service provides a collection of MappedFeatures specified by GeologicUnit features.

GeologicFeature is the abstract parent class for GeologicUnit, GeologicStructure, GeomorphologicFeature and GeologicEvent. This section will describe those properties which apply to all GeologicFeatures, but these will always be encoded as part of one of the specialist child classes. The INSPIRE GeologicFeature class has two associations, themeClass and geologicHistory. The themeClass association should be encoded using the GeoSciML classifier association, which will be explained in section 2.6, and geologicHistory should be encoded using the GeoSciML geologicHistory property which has GeologicEvent values, explained in section 2.2.

Mapped Feature - mapping frame
""""""""""""""""""""""""""""""

The INSPIRE
mappingFrame property is equivalent to the GeoSciML mappingFrame. Each
MappedFeature has a mappingFrame property constrained by a vocabulary term that
indicates the spatial reference frame within which the MappedFeatures have been
observed, such as a surface of mapping. Values should be drawn from the
MappingFrameValue vocabulary (`http://inspire.ec.europa.eu/codelist/MappingFrameValue <http://inspire.ec.europa.eu/codelist/MappingFrameValue>`_). At
the time of writing an equivalent CGI vocabulary has been drafted but not yet
published.

.. code-block:: xml

 <gsmlb:mappingFrame
   xlink:href="http://inspire.ec.europa.eu/codelist/MappingFrameValue/topOfBedrock"
   xlink:title="top of bedrock"/>

Figure 4: Example of the encoding of sampling frame

Mapped Feature - geometry (shape)
""""""""""""""""""""""""""""""""""

The geometry of each MappedFeature is provided by the shape association to GM_Object. Figure 5 gives an example of encoding a polygon. This property is (obviously) required for a OneGeology service and should have Polygon values.

.. code-block:: xml

 <gsmlb:shape>
      <gml:Polygon srsName="urn:ogc:def:crs:EPSG::4326" gml:id="LOCAL_ID_0">
          <gml:exterior>
              <gml:LinearRing>
                  <gml:posList srsDimension="2" count="8">55.0760921318516
 -3.31719604609088 55.0833753209835 -3.31853455922777 55.0825574334633
 -3.31921378657955 55.0801997429522 -3.31978309699423 55.0768616358466
 -3.3194575613054 55.0741365291192 -3.31966903508197 55.0756843873373
 -3.31747948721346 55.0760921318516 -3.31719604609088</gml:posList>
               </gml:LinearRing>
           </gml:exterior>
       </gml:Polygon>
   </gsmlb:shape>

Figure 5: Example of the encoding of MappedFeature geometry (shape)

Geologic Feature - inspireId
"""""""""""""""""""""""""""""

The INSPIRE inspireId
property is of type Identifier and provides the persistent identifier used for
the object by the data provider, for example the code from a stratigraphic
lexicon in the case of a GeologicUnit. In GeoSciML this should be encoded using
gml:identifier which requires both the identifier value, equivalent to
Identifier.localId, and the codespace, equivalent to Identifier.namespace,
identifying the data source (Figure 6).

Geologic Feature - name
""""""""""""""""""""""""

The INSPIRE name property
provides the name of the GeologicFeature, for example the expansion of the code
provided by inspireId. It should be encoded using gml:name (Figure 6). If the feature does not have a name use “Unnamed feature”.

.. code-block::xml

 <gsmlb:GeologicUnit gml:id="INV-SDSM">
           <gml:identifier codeSpace="http://data.bgs.ac.uk/">http://data.bgs.ac.uk/id/Lexicon/NamedRockUnit/INV</gml:identifier>
           <gml:name>INVERCLYDE GROUP</gml:name>

Figure 6:
Example of the encoding of identifier and name for a GeologicUnit

Geologic Age
^^^^^^^^^^^^

In INSPIRE the geologicHistory association
from GeologicFeature to GeologicEvent is the way in which geologic age is
described (Figure 2). This applies to
all types of GeologicFeature: GeologicUnit, GeologicStructure and
GeomorphologicFeature. In GeoSciML age is modeled similarly, although
GeologicEvent is itself a type of GeologicFeature and may have further
geologicHistory properties. At least one GeologicEvent needs to be provided per
GeologicUnit. The OneGeology Portal has a query tool which will retrieve units
of a specified age or ages. The interpretation of the results of this particular
query tool will be clear if you were to provide only a single GeologicEvent for
each GeologicUnit and consider this event represents the formation of the unit.

.. figure:: images/image003.jpg

   Figure 7: UML summary diagram for GeoSciML GeologicEvent

Geologic Event - name
"""""""""""""""""""""

The INSPIRE name property
provides the name of the GeologicEvent, for example ‘Hercynian Orogeny’. Only
major events such as orogenies are likely to have names and other events should
be recorded as ‘Unnamed event’. The field should be encoded using gml:name.

Geologic Event - youngerNamedAge and olderNamedAge
"""""""""""""""""""""""""""""""""""""""""""""""""""

In INSPIRE it is necessary to
provide geologic age expressed using a geochronologic era defined according to
a geologic time scale. Geochronologic era names must be drawn from the GeochronologicEraValue
vocabulary (`http://inspire.ec.europa.eu/codelist/GeochronologicEraValue <http://inspire.ec.europa.eu/codelist/GeochronologicEraValue>`_), which is based on the International Commission for
Stratigraphy (ICS) international stratigraphic chart supplemented with a more
detailed chronology for parts of the Precambrian and Quaternary. Both the
olderNamedAge and the youngerNamedAge attributes should be populated, giving
the age of the start and end of the GeologicEvent respectively. It may be that the
GeologicEvent age is fully enclosed by a single geochronologic era, in which
case the olderNamedAge and the youngerNamedAge attributes should both be
populated with the same value.

These properties are required
for OneGeology services. If the service is not also an INSPIRE service the
values must be drawn from  the CGI vocabulary http://resource.geosciml.org/classifier/ics/ischart/Eras
which is based on the International Commission
for Stratigraphy (ICS) international stratigraphic chart or the supplement `http://resource.geosciml.org/vocabulary/timescale/1GE_PCExtension.rdf <http://resource.geosciml.org/vocabulary/timescale/1GE_PCExtension.rdf>`_
which contains a more detailed chronology for parts of the Precambrian.

Geologic Event - eventProcess
""""""""""""""""""""""""""""""

The eventProcess property
describes one or more processes that took place during the event to modify the
related GeologicFeature. For an INSPIRE service it should be encoded using
terms drawn from the EventProcessValue vocabulary (`http://inspire.ec.europa.eu/codelist/EventProcessValue <http://inspire.ec.europa.eu/codelist/EventProcessValue>`_). If it is provided for a non-INSPIRE OneGeology
service the CGI Event process vocabulary (`http://resource.geosciml.org/classifier/cgi/eventprocess <http://resource.geosciml.org/classifier/cgi/eventprocess>`_)
should be used.

Geologic Event - eventEnvironment
"""""""""""""""""""""""""""""""""""

The eventEnvironment property
describes the environment within which the event took place. It is of type ‘Category’ which
provides the resolvable URI for the vocabulary containing the eventEnvironment
concepts in the codeSpace attribute, the URI identifier for the
eventEnvironment concept in the identifier attribute, and a human readable
version of the concept in the label attribute. For an INSPIRE service the
codeSpace should have the URI for the
EventEnvironmentValue vocabulary (`http://inspire.ec.europa.eu/codelist/EventEnvironmentValue <http://inspire.ec.europa.eu/codelist/EventEnvironmentValue>`_) and the values in the identifier should be taken
from this vocabulary. If it is provided for a non-INSPIRE OneGeology service values
from the CGI Event environment vocabulary (`http://resource.geosciml.org/classifier/cgi/eventenvironment <http://resource.geosciml.org/classifier/cgi/eventenvironment>`_)
should be used for identifier and the URI `http://resource.geosciml.org/classifierscheme/cgi/2016.01/eventenvironment <http://resource.geosciml.org/classifierscheme/cgi/2016.01/eventenvironment>`_ for the codeSpace.

.. todo::

   Used the ConceptScheme URI above for 2016 version. Not what was used for older 201211 version but there isn’t an equivalent “Dataset” object in 2016 vocab.

.. code-block:: xml

   <gsmlb:eventEnvironment>
    <swe:Category
     definition="http://inspire.ec.europa.eu/codelist/EventEnvironmentValue">
     <swe:identifier>http://inspire.ec.europa.eu/codelist/EventEnvironmentValue/riverPlainSystemSetting</swe:identifier>
     <swe:label>river plain system setting</swe:label>
     <swe:codeSpace
      xlink:href="http://inspire.ec.europa.eu/codelist/EventEnvironmentValue"/>
    </swe:Category>
   </gsmlb:eventEnvironment>

Figure 8: Example of encoding eventEnvironment

Geologic Unit and Earth Material
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/image004.jpg

   Figure 9: INSPIRE UML class diagram for GeologicUnit

.. figure:: images/image005.jpg

   Figure 10: UML context diagram for GeoSciML GeologicUnit

The INSPIRE UML class diagram
for GeologicUnit is shown in Figure 9 and the UML of the GeoSciML GeologicUnit package in Figure 10. GeologicUnit is a specialisation of GeologicFeature.  In INSPIRE only the geologicUnitType property is required, along with the
association to compositionPart, and as can be seen this is modelled in an
identical way in GeoSciML.

Geologic Unit - geologic unit type
"""""""""""""""""""""""""""""""""""

The only GeologicUnit attribute that is mandatory for
INSPIRE is geologicUnitType. This indicates the type of the geologic unit, for
example a lithostratigraphic unit or a lithologic unit. Values must be drawn
from the GeologicUnitTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/GeologicUnitTypeValue <http://inspire.ec.europa.eu/codelist/GeologicUnitTypeValue>`_). If
it is provided for a non-INSPIRE OneGeology service the CGI Geologic unit type
vocabulary (`http://resource.geosciml.org/classifier/cgi/geologicunittype <http://resource.geosciml.org/classifier/cgi/geologicunittype>`_)
should be used.

Geologic Unit - composition
""""""""""""""""""""""""""""

The composition association from GeologicUnit to
CompositionPart provides the means for describing the lithology of the
GeologicUnit. In INSPIRE a GeologicUnit must have at least one CompositionPart,
but can have several where the GeologicUnit is composed of several different
lithologies. For each CompositionPart values for three attributes must be
provided: role, material and proportion. The requirements are the same for a
OneGeology service.

Composition Part - role
""""""""""""""""""""""""

Role
defines the relationship of the compositionPart to the GeologicUnit as a whole,
e.g. vein, interbedded constituent, layers, dominant constituent. Values should
be drawn from the CompositionPartRoleValue vocabulary (`http://inspire.ec.europa.eu/codelist/CompositionPartRoleValue <http://inspire.ec.europa.eu/codelist/CompositionPartRoleValue>`_). If it is
provided for a non-INSPIRE OneGeology service the CGI Geologic unit part role
vocabulary (`http://resource.geosciml.org/classifier/cgi/geologicunitpartrole <http://resource.geosciml.org/classifier/cgi/geologicunitpartrole>`_)
should be used.

Composition Part - proportion
"""""""""""""""""""""""""""""

The proportion attribute
defines the proportion of the GeologicUnit as a whole that the CompositionPart
comprises. It is expressed as two fractions giving the upper and lower limits
of the range within which the CompositionPart proportion is considered to lie. It
can be serialised with an swe:QuantityRange element in both INSPIRE and
GeoSciML. However, GeoSciML also provides the gsmlb:GSML_QuantityRange element
which can be substituted here. The latter expresses the limits both as a space
separated tuple compatible with SWE and in separate elements which enables
querying in a WFS. A OneGeology service must use the gsmlb:GSML_QuantityRange
element.

.. code-block:: xml

   <gsmlb:proportion>
    <gsmlb:GSML_QuantityRange>
     <swe:uom code="%" xlink:href="http://unitsofmeasure/ucum.html#para-29"
      xlink:title="percent"/>
     <swe:value>5.0 50.0</swe:value>
     <gsmlb:lowerValue>5.0</gsmlb:lowerValue>
     <gsmlb:upperValue>50.0</gsmlb:upperValue>
    </gsmlb:GSML_QuantityRange>
   </gsmlb:proportion>

Figure
11 Example of the encoding of proportion

Composition Part - material
""""""""""""""""""""""""""""

The material attribute provides
the lithology of the CompositionPart and is of type LithologyValue (a codelist)
in INSPIRE (Figure 9) whereas in GeoSciML it is modelled as a CompoundMaterial (Figure 12). CompoundMaterial is a specialisation of EarthMaterial and the parent class of RockMaterial. The RockMaterial.lithology property is the equivalent of
INSPIRE CompositionPart.material.

.. figure:: images/image007.png

   Figure 12: UML context diagram for GeoSciML RockMaterial

Rock Material -lithology
"""""""""""""""""""""""""""

The lithology attribute
provides the lithology of the CompositionPart. GeoSciML allows multiple
lithologies for each CompositionPart, but in INSPIRE each CompositionPart
should be restricted to a single lithology, although, as indicated in section 2.3.2, a
GeologicUnit can have multiple CompositionParts. Values for lithology should be
drawn from the LithologyValue vocabulary (`http://inspire.ec.europa.eu/codelist/LithologyValue <http://inspire.ec.europa.eu/codelist/LithologyValue>`_). This attribute is required for a OneGeology service
and the same restriction on having a single lithology per CompositionPart
applies. For a non-INSPIRE OneGeology service the CGI Simple lithology
vocabulary (`http://resource.geosciml.org/classifier/cgi/lithology <http://resource.geosciml.org/classifier/cgi/lithology>`_) must be used.

Geologic Structure
^^^^^^^^^^^^^^^^^^^

GeologicStructure is an abstract specialization of
GeologicFeature and in INSPIRE only two types of GeologicStructure are
required, ShearDisplacementStructure (faults) and Fold (Figure 13).

.. figure:: images/image008.jpg

   Figure 13: INSPIRE UML class diagram for GeologicStructure

The GeoSciML modelling of
ShearDisplacementStructure is shown in Figure 14, and of Fold in Figure 15.

.. figure:: images/image009.png

   Figure 14: UML context diagram for GeoSciML ShearDisplacementStructure

.. figure:: images/image010.png

   Figure 15: UML context diagram for GeoSciML Fold

As can be seen in Figure 13, the only properties required by INSPIRE are faultType for ShearDisplacementStructure, and profileType for Fold.

Shear Displacement Structure - faultType
"""""""""""""""""""""""""""""""""""""""""

The faultType property
describes the type of ShearDispacementStructure and should be populated with a
value drawn from the FaultTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/FaultTypeValue <http://inspire.ec.europa.eu/codelist/FaultTypeValue>`_). For a non-INSPIRE OneGeology service the CGI Fault
Type vocabulary (`http://resource.geosciml.org/classifier/cgi/faulttype <http://resource.geosciml.org/classifier/cgi/faulttype>`_)
should be used.

Fold - profileType
"""""""""""""""""""

The profileType property describes
the type of fold defined according to its geometry and the younging direction
of the strata. It should be populated using values from the
FoldProfileTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/FoldProfileTypeValue <http://inspire.ec.europa.eu/codelist/FoldProfileTypeValue>`_). There isn’t currently an equivalent CGI vocabulary.

.. todo::

   As far as I can see there is still no CGI vocabulary for this property. Again not sure why previous version of cookbook didn’t even bother to say “there is no CGI version”?

Geomorphologic Feature
^^^^^^^^^^^^^^^^^^^^^^^

Figure 16 shows the INSPIRE UML class diagram for geomorphology, and Figure 17 the equivalent GeoSciML modeling. As can be seen
these are modeled in an identical way. GeomorphologicFeature is an abstract
specialization of GeologicFeature with two sub-types, AnthropogenicGeomorphologicFeature
and NaturalGeomorphologicFeature.

.. figure:: images/image011.jpg

   Figure 16: INSPIRE UML class diagram for GeomorphologicFeature

.. figure:: images/image012.jpg

   Figure 17: UML context diagram for GeoSciML GeomorphologicFeature

Natural Geomorphologic Feature - NaturalGeomorphologicFeatureType
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. todo::

   For this and next two properties should I explicitly note that there is no current CGI vocabulary?

The
NaturalGeomorphologicFeatureType property describes the type of
NaturalGeomorphologicFeature and should be populated with a value drawn from
the NaturalGeomorphologicFeatureTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/NaturalGeomorphologicFeatureTypeValue <http://inspire.ec.europa.eu/codelist/NaturalGeomorphologicFeatureTypeValue>`_). There isn’t currently an equivalent CGI vocabulary.

Natural Geomorphologic Feature - activity
""""""""""""""""""""""""""""""""""""""""""

The activity property
describes the level of activity of a NaturalGeomorphologicFeature and should be
populated with a value from the GeomorphologicActivityValue vocabulary (`http://inspire.ec.europa.eu/codelist/GeomorphologicActivityValue <http://inspire.ec.europa.eu/codelist/GeomorphologicActivityValue>`_). There isn’t currently an equivalent CGI vocabulary.

Anthropogenic Geomorphologic Feature - AnthropogenicGeomorphologicFeatureType
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

The
AnthopogenicGeomorphologicFeatureType property describes the type of
AnthropogenicGeomorphologicFeature and should be populated with a value drawn
from the AnthropogenicGeomorphologicFeatureTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/AnthropogenicGeomorphologicFeatureTypeValue <http://inspire.ec.europa.eu/codelist/AnthropogenicGeomorphologicFeatureTypeValue>`_). There isn’t currently an equivalent CGI vocabulary.

Thematic Class
^^^^^^^^^^^^^^^

The INSPIRE Thematic Class datatype (Figure 2) is designed to enable information on thematic maps to be delivered. Thematic maps commonly take a standard
geological map and reclassify it using some vocabulary of concepts, for example
a standard lithostratigraphic map might be reclassified into ‘engineering
geology units’ based on various generalized physical properties of the
lithostratigraphic units. This doesn’t involve any new mapping, although it may
lead to units being merged together.

There is no standard for thematic maps and therefore
each data provider must provide their own vocabulary for classifying a
particular map for a particular theme.

Geologic Feature - classifier
"""""""""""""""""""""""""""""

There is no direct
equivalent of Thematic Class in GeoSciML but it can nevertheless be encoded in
GeoSciML using the classifier association from GeologicFeature to ControlledConcept
(Figure 3). This provides the URI of the relevant value in the thematic
classification vocabulary being used.

.. code-block:: xml

 <gsmlb:GeologicUnit gml:id="INV-SDSM">
 <gml:identifier codeSpace="http://data.bgs.ac.uk/">http://data.bgs.ac.uk/id/Lexicon/NamedRockUnit/INV</gml:identifier>
 <gml:name>INVERCLYDE GROUP</gml:name>
 <gsmlb:geologicHistory> [37 lines]
 <!--  -->
 <!-- Example of a thematic classification of a GeologicUnit -->
 <!--  -->
 <gsmlb:classifier
  xlink:href="http://data.bgs.ac.uk/ref/EngineeringGeologyTheme/strongSandstone"
  xlink:title="Engineering Geology theme: Strong Sandstone"/>

Figure 18:  Example of encoding a GeologicUnit with a
thematic classifier

Borehole
"""""""""

The INSPIRE UML class diagram for Borehole is shown in 19 and the UML of the GeoSciML Borehole package in Figure 20. Although the modelling of boreholes in GeoSciML is more complex it includes everything required for INSPIRE which can therefore be encoded with
GeoSciML. One of the main differences is that in GeoSciML Borehole is modelled
as a type of SamplingCurve, drawn from the OGC Observations & Measurements
model.

The
logElement association from Borehole to BoreholeInterval is the means by which
the borehole log is encoded. There should be one BoreholeInterval (logElement)
for every discrete unit described down the borehole. A borehole encoded as a
series of logElements can be seen as a ‘vertical geological map’ with each BoreholeInterval
specified by a GeologicFeature in the same way as polygons on the map. It is
also possible in GeoSciML to encode the borehole as a series of observations,
using the OGC Observations & Measurements model, but as this isn’t a
requirement for INSPIRE it won’t be described further here.

.. figure:: images/image014.jpg

   Figure 19: INSPIRE UML class diagram for Borehole

.. figure:: images/image015.jpg

   Figure 20: UML for the GeoSciML Borehole package

Borehole - inspireId
"""""""""""""""""""""

The INSPIRE inspireId
property is of type Identifier and provides the persistent identifier used for
the borehole by the data provider. In GeoSciML this should be encoded using
gml:identifier which requires both the identifier value, equivalent to
Identifier.localId, and the codespace, equivalent to Identifier.namespace,
identifying the data source (Figure 6).

Borehole - sampledFeature
""""""""""""""""""""""""""

This property isn’t required
by INSPIRE but is mandatory for SamplingFeature and thus Borehole in GeoSciML.
In a typical borehole being encoded the sampledFeatures will be the features,
such as GeologicUnits, which the borehole penetrates and which specify the log elements
(see section 2.7.9). There should be one sampledFeature encoded for each
distinct feature sampled by the borehole. The positions where these features
are intersected by the borehole may be described in the log. Each feature only
needs to be described fully once and then can be referenced with an internal
xlink:href using the gml:id value of the feature. No extra information is
therefore required to encode this property.

Borehole - downholeGeometry
""""""""""""""""""""""""""""""""""

This should be encoded using
the SF_SpatialSamplingFeature shape association to GM_Object to provide a
LineString with the 3D geometry of the borehole (Figure 21). Where the borehole is vertical the X and Y co-ordinates will be the same for all positions. The LineString should be given an identifier using
gml:id for use in referencing the log elements (section 2.7.8)

.. code-block:: xml

     <sams:shape>
        <gml:LineString gml:id="bh.ns94se5.shape" srsName="urn:ogc:def:crs:EPSG:6.15:7405">
          <gml:posList srsDimension="3" count="7">-30.7111 134.2059 321. -30.7112 134.2058 315.
            -30.7113 134.2057 303. -30.7114 134.2056 296.
            -30.7115 134.2055 272. -30.7116 134.2054 271.
            -30.7117 134.2053 270.</gml:posList>
        </gml:LineString>
      </sams:shape>

Figure 21: Example of encoding
the downhole geometry of a borehole

Borehole - location and elevation
"""""""""""""""""""""""""""""""""""

The referenceLocation
association from borehole to OriginPosition allows the encoding of both
location and elevation. Location should be encoded as a two dimensional point
and elevation as a one dimensional value (Figure 22).

.. code-block:: xml

      <gsmlbh:referenceLocation>
        <gsmlbh:OriginPosition gml:id="op1">
          <gsmlbh:location>
            <gml:Point gml:id="pt1" srsName="urn:ogc:def:crs:EPSG:6.15:27700" srsDimension="2">
              <gml:pos>-30.7 134.2</gml:pos>
            </gml:Point>
          </gsmlbh:location>
          <gsmlbh:elevation srsName="urn:ogc:def:crs:EPSG:6.15:5701" srsDimension="1"
            >321.0</gsmlbh:elevation>
        </gsmlbh:OriginPosition>
      </gsmlbh:referenceLocation>

Figure 22: Example of encoding
the location and elevation of a borehole

Borehole - purpose
"""""""""""""""""""

.. todo::

   Again note no CGI vocabulary?

The purpose property
describes the purpose for which the Borehole was drilled and should be
populated with a value from the BoreholePurposeValue vocabulary (`http://inspire.ec.europa.eu/codelist/BoreholePurposeValue <http://inspire.ec.europa.eu/codelist/BoreholePurposeValue>`_). In GeoSciML this property is inside
indexData/BoreholeDetails. There isn’t currently an equivalent CGI vocabulary.

Borehole - boreholeLength
""""""""""""""""""""""""""

The boreholeLength records
the total length down the borehole and should be encoded as a Quantity value,
which requires the units of measurement to be recorded along with the value (Figure 23). The unit of measure should reference the URI of an OGC definition. Again this is found inside the indexData/BoreholeDetails element.

.. code-block:: xml

 <gsmlbh:indexData>
  <gsmlbh:BoreholeDetails>
   <gsmlbh:purpose
    xlink:href="http://inspire.ec.europa.eu/codelist/BoreholePurposeValue/geologicalSurvey"
    xlink:title="geological Survey"/>
   <gsmlbh:boreholeLength>
    <swe:Quantity>
     <swe:uom code="m" xlink:href="http://www.opengis.net/def/uom/OGC/1.0/metre"
      xlink:title="metre"/>
     <swe:value>51.0</swe:value>
    </swe:Quantity>
   </gsmlbh:boreholeLength>
  </gsmlbh:BoreholeDetails>
 </gsmlbh:indexData>

Figure 23: Example of encoding
the purpose and boreholeLength

Borehole Interval - mappingFrame
"""""""""""""""""""""""""""""""""

The BoreholeInterval in
GeoSciML v4.1 does not have a mappingFrame / samplingFrame property as this
will always be the borehole to which it belongs. Thus, although in the INSPIRE
geology theme Schema the property is encoded by referencing the gml:id of the
borehole, for GeoSciML nothing needs specifying explicitly.

BoreholeInterval - geometry (shape)
""""""""""""""""""""""""""""""""""""

The geometry of the BoreholeInterval
is the one dimensional linear segment down the borehole that the BoreholeInterval
refers to. The reference system is the geometry of the borehole, which can be
referenced using the gml:id of the borehole shape property (Figure 21). An example of encoding BoreholeInterval geometry is given in Figure 24. 

.. code-block:: xml

   <gsmlbh:shape>
    <gml:LineString gml:id="ls1" srsName="#bh.ns94se5.shape">
     <gml:posList srsDimension="1" count="2">0.0 2.0</gml:posList>
    </gml:LineString>
   </gsmlbh:shape>

Figure 24: Example of encoding BoreholeInterval
geometry

BoreholeInterval - specification
"""""""""""""""""""""""""""""""""

A BoreholeInterval is
specified by a GeologicFeature in exactly the same way as described in section
2.1 for MappedFeature. The encoding of a GeologicFeature specifying a
MappedInterval is therefore identical to that described above for
MappedFeatures and won’t be repeated here.

BoreholeInterval - mappedIntervalBegin & mappedIntervalEnd
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

The mappedIntervalBegin and
mappedIntervalEnd properties hold the one dimensional co-ordinates of the start
and end of the mappedInterval, as measured down the borehole, encoded as
Quantity values (Figure 25). This information duplicates that held in the shape property, but
queries such as ‘find all MappedIntervals within 10m of the surface’ are
difficult to implement with current technology using the shape property and the
mappedIntervalBegin and mappedIntervalEnd properties have been introduced to
address this problem.

.. code-block:: xml

          <gsmlbh:mappedIntervalBegin>
            <swe:Quantity>
              <swe:uom code="m" xlink:href="http://www.opengis.net/def/uom/OGC/1.0/metre"
                xlink:title="metre"/>
              <swe:value>0.0</swe:value>
            </swe:Quantity>
          </gsmlbh:mappedIntervalBegin>
          <gsmlbh:mappedIntervalEnd>
            <swe:Quantity>
              <swe:uom code="m" xlink:href="http://www.opengis.net/def/uom/OGC/1.0/metre"
                xlink:title="metre"/>
              <swe:value>2.0</swe:value>
            </swe:Quantity>
          </gsmlbh:mappedIntervalEnd>

Figure 25: Example of encoding mappedIntervalBegin and mappedIntervalEnd

Geologic Collection
^^^^^^^^^^^^^^^^^^^^

The GeologicCollection in
INSPIRE is designed to enable features which comprise a higher level object,
such as a geological map or a borehole exploration programme, to be grouped
together. This enables information such as metadata to be provided for the collection
of features as a whole. It is not necessary to use a GeologicCollection where
features do not form part of such a higher level object. The INSPIRE UML class
diagram for GeologicCollection is shown in Figure 26.

.. figure:: images/image019.jpg

   Figure 26: INSPIRE UML class diagram for GeologicCollection

In GeoSciML collections are
modelled with the GSML feature (Figure 28).

Where features are not part
of a GSML collection each individual feature is a member of a
wfs:FeatureCollection. GSML is a GML feature so where a GSML collection is
being delivered it is the GSML collection which is a member of the
wfs:FeatureCollection and individual features are members of the GSML
collection (Figure 27).

.. code-block:: xml

  <wfs:member>
    <gsmlb:GSML gml:id="col1">
      <gml:metaDataProperty> [81 lines]
      <gml:identifier codeSpace="http://data.bgs.ac.uk">http://data.bgs.ac.uk/id/625KGeologyMap</gml:identifier>
      <gml:name>BGS 1:625 000 Digital Geological Map</gml:name>
      <gsmlb:collectionType
       xlink:href="http://inspire.ec.europa.eu/codelist/CollectionTypeValue/geologicalMap"
       xlink:title="geological map"/>
      <gsmlb:member>
      <gsmlb:MappedFeature gml:id="mf.16">
        ....

Figure 27: Example of encoding a GSML collection as a member
of a wfs:FeatureCollection and a MappedFeature as a member of the GSML
collection

.. figure:: images/image020.jpg

   Figure 28: UML class diagram for GeoSciML Collection package

The INSPIRE reference,
beginLifespanVersion and endLifespanVersion properties can all be implemented
in GeoSciML using the standard gml:metaDataProperty to contain elements from
the ISO 19139 metadata schema. The use of MD_Metadata also requires certain
other mandatory properties to be encoded which are not required by the INSPIRE
data specification.

Geologic Collection - inspireId
""""""""""""""""""""""""""""""""

The INSPIRE inspireId
property is of type Identifier and provides the persistent identifier used for
the GeologicCollection by the data provider. In GeoSciML this should be encoded
using gml:identifier which requires both the identifier value, equivalent to Identifier.localId,
and the codespace, equivalent to Identifier.namespace, identifying the data
source (Figure 28).

GeologicCollection - name
""""""""""""""""""""""""""

The INSPIRE name property
provides the name of the GeologicCollection. It should be encoded using
gml:name (Figure 28).

Geologic Collection - collectionType
"""""""""""""""""""""""""""""""""""""

.. todo::

   A CGI vocab based on the INSPIRE code list is a CGI draft schema. Need to check when this gets published.

The collectionType
property describes the type of collection and should be populated with a value
from the CollectionTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/CollectionTypeValue <http://inspire.ec.europa.eu/codelist/CollectionTypeValue>`_) (Figure 28). At the time of writing an equivalent CGI vocabulary has been drafted but not yet published.

Geologic Collection - member
""""""""""""""""""""""""""""""

In INSPIRE there are four
types of feature which can be members of a GeologicCollection: MappedFeature;
Borehole; GeophObject; and GeophObjectSet (Figure 26). GeophObject and GeophObjectSet are features in the geophysics application schema and won’t be discussed further here. In GeoSciML the member
association from GSML to GSMLItem allows the members of a GSML collection to be
any of the types in the GSMLItem union class. The types of member of an INSPIRE
GeologicCollection can be mapped to these: MappedFeature maps to mappedItem and
Borehole to samplingFeatureItem (Figure 28). Figure 27 shows the encoding of a MappedFeature as a member of a GSML collection.

MD_Metadata - contact
"""""""""""""""""""""""

Although the MD_Metadata
contact property is not required by INSPIRE it is mandatory for MD_Metadata. It
identifies the organisation providing the metadata and its role with respect to
the metadata. It is of type CI_ResponsibleParty which requires the encoding of
the organisationName and role properties, the latter with values drawn from the
CI_RoleCode vocabulary (`http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_RoleCode <http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_RoleCode>`_). Figure 29 gives an example of the encoding of contact.

.. code-block:: xml

 <gmd:contact>
     <gmd:CI_ResponsibleParty>
        <gmd:organisationName>
           <gco:CharacterString>British Geological Survey (BGS)</gco:CharacterString>
        </gmd:organisationName>
        <gmd:role>
           <gmd:CI_RoleCode codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_RoleCode"
                  codeListValue="owner">owner</gmd:CI_RoleCode>
        </gmd:role>
     </gmd:CI_ResponsibleParty>
 </gmd:contact>

Figure 29: Example of encoding MD_Metadata.contact

MD_Metadata - dateStamp
""""""""""""""""""""""""

Although the MD_Metadata
dateStamp property is not required by INSPIRE it is mandatory for MD_Metadata.
It provides the date when the metadata was created and should follow the format
defined in ISO8601. An example of encoding dateStamp is given in Figure 30.

.. code-block:: xml

          <gmd:dateStamp>
            <gco:Date>2011-03-08</gco:Date>
          </gmd:dateStamp>

Figure 30: Example of encoding MD_Metadata.dateStamp

Geologic Collection - reference
""""""""""""""""""""""""""""""""

The reference property is of
type DocumentCitation which requires the provision of a name, shortName, date
and link (URL). The first three of these properties can be encoded using the
MD_DataIdentification.citation property which is of type CI_Citation.

DocumentCitation - name
"""""""""""""""""""""""

The DocumentCitation.name
property can be encoded with CI_Citation.title (Figure 31). This property duplicates the information encoded in gml:name (section 2.8.2).

DocumentCitation - shortName
""""""""""""""""""""""""""""

The
DocumentCitation.shortName property can be encoded with
CI_Citation.alternateTitle (Figure 31). This property is optional in INSPIRE and should be used where the GeologicCollection has a well recognised short name.

Document Citation - date
""""""""""""""""""""""""

The DocumentCitation.date
refers to the date cited in the reference, such as publication date or revision
date. It can be encoded with CI_Citation.date (Figure 31) which is of type CI_Date requiring both the date and the dateType to be
provided. The dateType property identifies what the date is referring to and
should be encoded using a value drawn from the CI_DateTypeCode vocabulary (`http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_DateTypeCod <http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_DateTypeCod>`_).

.. code-block:: xml

                <gmd:CI_Citation>
                  <gmd:title>
                    <gco:CharacterString>BGS 1:625 000 Digital Geological Map</gco:CharacterString>
                  </gmd:title>
                  <gmd:alternateTitle>
                    <gco:CharacterString>BGS 625k Map</gco:CharacterString>
                  </gmd:alternateTitle>
                  <gmd:date>
                    <gmd:CI_Date>
                      <gmd:date>
                        <gco:Date>2008</gco:Date>
                      </gmd:date>
                      <gmd:dateType>
                        <gmd:CI_DateTypeCode codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_DateTypeCode"
                          codeListValue="revision">revision</gmd:CI_DateTypeCode>
                      </gmd:dateType>
                    </gmd:CI_Date>
                  </gmd:date>
                  <gmd:date>
                </gmd:CI_Citation>

Figure 31: Example of encoding DocumentCitation using CI_Citation

DocumentCitation - link
"""""""""""""""""""""""

The DocumentCitation.link
property is defined as providing an online link to the document (not to the
citation of the document), and so should provide the URL of the
GeologicCollection. This can be encoded using the MD_Metadata.dataSetURI property (Figure 32).

.. todo::

   James Passmore established that it is likely that CI_OnlineResource is now preferred over MD_Metadata.dataSetURI (rather than John Laxton’s original comment on MD_DigitalTransferOptions.online) from reference: https://geo-ide.noaa.gov/wiki/index.php?title=ISO_FAQ#What_is_the_Dataset_URI.3F. However, we have no examples so we are just going to leave the old advice for the moment. Have updated to use gmx:Anchor rather than gco:CharacterString as BP for links though.

.. code-block:: xml

    <gmd:dataSetURI>
     <gmx:Anchor href="http://www.bgs.ac.uk/products/digitalmaps/digmapgb_625.html" />
    </gmd:dataSetURI>

Figure 32: Example of encoding DocumentCitation.link using MD_Metadata.dataSetURI

Geologic Collection - beginLifespanVersion & endLifespanVersion
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

The beginLifespanVersion and
endLifespanVersion properties can both be encoded using the CI_Citation.date
property (section 2.8.7.3), but
with different values for the dateType property. The date should be encoded
using the format defined in ISO8601. In the revised version of ISO19115 the
CI_DateTypeCode vocabulary has been significantly extended and beginLifespanVersion
should have a dateType code value of validityBegins and endLifespanVersion
should have a dateType code value of validityEnds (Figure 33). The endLifespanVersion property should not be encoded if the GeologicCollection is still valid.

.. code-block:: xml

                  <gmd:date>
                    <gmd:CI_Date>
                      <gmd:date>
                        <gco:Date>2008</gco:Date>
                      </gmd:date>
                      <gmd:dateType>
                        <gmd:CI_DateTypeCode codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_DateTypeCode"
                          codeListValue="validityBegins">validityBegins</gmd:CI_DateTypeCode>
                      </gmd:dateType>
                    </gmd:CI_Date>
                  </gmd:date>
                  <gmd:date>
                    <gmd:CI_Date>
                      <gmd:date>
                        <gco:Date>2013</gco:Date>
                      </gmd:date>
                      <gmd:dateType>
                        <gmd:CI_DateTypeCode codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_DateTypeCode"
                          codeListValue="validityEnds">validityEnds</gmd:CI_DateTypeCode>
                      </gmd:dateType>
                    </gmd:CI_Date>
                  </gmd:date>

Figure 33:
Example of encoding beginLifespanVersion and endLifespanVersion using
CI_Citation.date

MD_DataIdentification - abstract
"""""""""""""""""""""""""""""""""

Although the
MD_DataIdentification abstract property is not required by INSPIRE it is
mandatory for MD_DataIdentification. It should be populated with a text description
of the GeologicCollection (Figure 34).

MD_DataIdentification - language
""""""""""""""""""""""""""""""""""

Although the
MD_DataIdentification language property is not required by INSPIRE it is
mandatory for MD_DataIdentification. It identifies the language(s) used in the
GeologicCollection and should be encoded using the language codes defined in
ISO639-2 (Figure 34).

If the dataset has no natural
language the special code of "zxx" of the ISO 639-2/B reserved for
"no linguistic content; not applicable" shall be used.

MD_DataIdentification - topicCategory
""""""""""""""""""""""""""""""""""""""

Although the
MD_DataIdentification topicCategory property is not required by INSPIRE it is
mandatory for MD_DataIdentification where the metadata is referring to a
dataset. A GeologicCollection can be considered a dataset. MD_DataIdentification
topicCategory should be populated with a value from the MD_TopicCategory_Code
vocabulary (`http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#MD_TopicCategoryCode <http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#MD_TopicCategoryCode>`_) (Figure 34).

.. code-block:: xml

              <gmd:abstract>
                <gco:CharacterString>The data shows polygonal and selected linear geological information, sourced
                  from published BGS 1:625 000 scale maps of Great Britain.  However, geological units are identified
                  using the most up-to-date nomenclature that may differ from that on the printed maps. The maps are
                  generally based on published material at 1:50 000 scale and compiled using techniques of selection,
                  generalisation and exaggeration. The geology is fitted to a relevant topographic base at the time
                  of production. Full UK coverage is available. The data is available in vector format. BGS licensing
                  terms and conditions apply to external use of the data. The data can be used free of charge for
                  non commercial use and is downloadable from the website.</gco:CharacterString>
              </gmd:abstract>
              <gmd:language>
                  <gmd:LanguageCode
                   codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO_19139_Schemas/resources/codelist/ML_gmxCodelists.xml#LanguageCode"
                   codeListValue="eng">English</gmd:LanguageCode>
              </gmd:language>
              <gmd:topicCategory>
                <gmd:MD_TopicCategoryCode>geoscientificInformation</gmd:MD_TopicCategoryCode>
              </gmd:topicCategory>

Figure 34: Example of encoding MD_Identification.abstract, MD_Identification.language and
MD_Identification.topicCategory

.. _service_provision_onegeology_profile:

OneGeology Profile
-------------------

.. todo::

   Some service metadata requirements should be in common for all service types. Would be helpful to clarify what requirements are to make portal work, what to enable searching, what for metadata compliance etc. Would a template GetCap response with highlighted fields where user to put in their own data be more helpful? Might be too long though?  We do already have example WMS GetCap responses in apendices, so could modify/add to those...

   Still requires quite a bit of editing especially in the layer/coverage/feature section which may also need to distinguish between "ad-hoc" simple feature WFS and WFS (simple or complex) conforming to community schemas.

.. todo::

   Changes made

   Changed requirements on number of services per data provider just to say need distinct ones when need different service metadata with some examples for language, buddying services etc.

   Dropped requirements on service name which are just restatements of the OGC standards themselves.

   Dropped requirements on form of service URL

   Removed accreditation scheme boxes with intention of putting them in separate section.
    
A OneGeology service will be an OGC WMS, WFS or WCS. OneGeology defines a profile of these services for two reasons. The first is to make certain parts of the OneGeology Portal work with the services. The second is to make the services as widely usable and findable as possible by ensuring that they all provide some basic metadata such as contact details for further information. Currently, a OneGeology WFS needs to be associated with one or more layers from a OneGeology WMS which portray the data as an image. 

Each of the OGC service types shares some common characteristics. They will each have a service URL. They each respond to a GetCapabilities request by returning a GetCapabilities response that contains administrative and technical metadata about the service.

The OGC standards specify different kinds of metadata that a service should provide, some for the correct operation of the service and some to help human users of the service understand what is being provided. Some of the metadata applies to a whole service being provided at a particular service URL and some is specific to particular layers, coverages or features being provided by that service. This means that separate services need to be set up for each distinct set of service level metadata.

In the profile we make a distinction between the organization that owns or has copyright to provide the data (whom we term the ‘data owner’, or 'data provider') and the organization that serves that data over a web service (whom we term the ‘service provider’). These may be different in the case that a "buddy organisation" is serving the data on behalf of a data owner. As we require the contact details for the data owner to be put in the service metadata then there must be a distinct service for each data owner. If a particular data owner wishes to provide information in more than one language then there will need to be separate services with the service metadata in each language. If a data owner is providing similar data for different scales or geographical extent then this may be all provided within one service or from distinct services depending on what is most convenient.

For example, at the time of writing The British Geological Survey is hosting its own data, and is acting as a buddy to host data for the Afghanistan Geological Survey, and for the Namibian Geological Survey, and for the Falkland Island Government, and for Geoscience Australia for Antarctica data, each of these is only available in English language versions.  The British Geological Survey is also hosting a single language (French) service for Burkina Faso.  The net result is that BGS, acting in the role of service provider, is serving six separate services (six separate service URLs).

In some cases you may already have OGC services set up for other purposes than OneGeology or you may not wish to maintain a separate set of services just for OneGeology. In this case there are two possibilities. Ideally you can add metadata to your services that satisfies both OneGeology and your other requirements. If not, then in many cases, it may be possible to prepare static GetCapabilities response documents with OneGeology specific service metadata and the subset of layers, coverages or features that you wish to be registered with OneGeology. This will point to the main service URLs for retrieval of the individual layers, coverages or features. Some metadata such as layer names can't be different in the static document from the main service. We haven't come up with a general solution for this so you will need to contact us to discuss possibilities on an individual basis.

The service must comply with one of the following OGC standard specifications.

* A WMS must comply with the `WMS 1.1.1 <http://portal.opengeospatial.org/files/?artifact_id=1081&version=1&format=pdf>`_ or `WMS 1.3.0 <http://portal.opengeospatial.org/files/?artifact_id=14416>`_ specification. (This documentation now concentrates on the later version specification.)
* An SLD enabled WMS must comply with the relevant parts of the `SLD 1.1.0 <http://portal.opengeospatial.org/files/?artifact_id=22364>`_ specification.
* A WFS must comply with the `WFS 2.0.0 <http://portal.opengeospatial.org/files/?artifact_id=39967>`_ or `2.0.2 <http://docs.opengeospatial.org/is/09-025r2/09-025r2.html>`_ specification
* A WCS must comply with `WCS 2.0.0 <https://portal.opengeospatial.org/files/09-110r4>`_ or higher specification. At the moment you also need to be able to supply a `WCS 1.0.0 <https://portal.opengeospatial.org/files/05-076>`_ GetCapabilities response for metadata harvesting. This could be achieved by supporting the older WCS version or by just creating a static response document that complies to the format.

OGC service level metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^^

WMS, WFS, and WCS services all provide metadata about the service through their response to a GetCapabilities request. OneGeology places some requirements on this metadata, some to help the Portal operate and some as good practice to enable users to search for services, know how they can use the data and get further information. The different service types have similar but not identical structures for their GetCapabilities responses; differences will be pointed out below. In particular, the WCS 2.0 standard changed the structure considerably, moving coverage specific metadata to DescribeCoverage requests so, for the moment, we need a WCS 1.0.0 structure document to enable us to harvest coverage specific metadata easily.

.. _service_provision_onegeology_profile_service_title:

Service title
""""""""""""""

.. todo::

   We need to consider whether we need to keep specifying service title, especially as more people will be setting up services which aren't just for OneGeology. The service title doesn't appear in the Portal anywhere. It does appear in the catalogue and is somewhat helpful in browsing. We should check that keywords enable useful browsing in the catalogue. Service provider and Data provider are in metadata keywords. Should be possible to add these to services even when they are serving non-OneGeology layers/features/coverages. Language should also be covered by MD_LANG, do we want a separate DS_LANG as well? Anyway, no need to reproduce this metadata in service title. The theme part is fairly superfluous as well. Could suggest the existing naming conventions if a service fits neatly into that category but drop as a requirement.

The service title isn't used by the OneGeology Portal but it does appear in the catalogue of services so it is worth using a title that will be helpful to users browsing a catalogue. We recommend that you follow the previous OneGeology `WMS service title </wmsCookbook/2_2.html>`_ requirements if your service fits into the scheme described there but they are no longer a requirement if, for example, your service is being used for other non-OneGeology purposes as well.

=============  =======  =========================================================
Specification  Version  XPath
=============  =======  =========================================================
WMS            1.3.0    /WMS_Capabilities/Service/Title
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceIdentification/ows:Title
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:label
WCS            2.0.1    /wcs:Capabilities/ows:ServiceIdentification/ows:Title
=============  =======  =========================================================

.. _service_provision_onegeology_profile_service_abstract:

Service abstract
"""""""""""""""""

Information about the service and general information about the map data served in the layers. You may also use this to field to describe the data owner organization, and its goals within OneGeology etc. You can also include in this section information about the scale layering of your service, and any other information that is not automatically extracted / viewable by the OneGeology Portal (or indeed any other client software). We can't enforce definite rules on the content but this is important for users of your data.

=============  =======  ============================================================
Specification  Version  XPath
=============  =======  ============================================================
WMS            1.3.0    /WMS_Capabilities/Service/Abstract
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceIdentification/ows:Abstract
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:description
WCS            2.0.1    /wcs:Capabilities/ows:ServiceIdentification/ows:Abstract
=============  =======  ============================================================

.. _service_provision_onegeology_profile_fees:

Fees
"""""""

Any fees required to use the WMS services and data contained within. If there are no fees you are recommended to explicitly state this using the word "none".

=============  =======  =====
Specification  Version  XPath
=============  =======  =====
WMS            1.3.0    /WMS_Capabilities/Service/Fees
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceIdentification/ows:Fees
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:fees
WCS            2.0.1    /wcs:Capabilities/ows:ServiceIdentification/ows:Fees
=============  =======  =====

.. _service_provision_onegeology_profile_access_constraints:

Access constraints
"""""""""""""""""""

Information about who is allowed to use the data served by the WMS, and for what purpose they can use it for. Remember your WMS is available to any application that is able to access the Internet, not just through the OneGeology Portal.

For clarity to any potential users, it is recommended (within the OGC specifications) that you explicitly state when there are no access constraints on the using the service using the word "none".

Note too that there is no "AccessConstraints" metadata applicable at the layer level. If you need to define different access constraints for different layers in your service you will need to define these differences in the service level metadata. It may be more convenient to have separate services where different access constraints apply.

=============  =======  =====
Specification  Version  XPath
=============  =======  =====
WMS            1.3.0    /WMS_Capabilities/Service/AccessConstraints
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceIdentification/ows:AccessConstraints
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:accessConstraints
WCS            2.0.1    /wcs:Capabilities/ows:ServiceIdentification/ows:AccessConstraints
=============  =======  =====

.. _service_provision_onegeology_profile_keywords:

Keywords
"""""""""

.. todo::

   Does OneGeology keyword in service level do anything, presumably any service URL that is given to be registered is registered so this is only for searching over many catalogues? If we have services that have many non-OneGeology layers do we really have any good reason for making this a requirement? Check the effect in GeoNetwork if we filter by OneGeology Keyword.

A list of keywords or short phrases that users of the OneGeology Portal and other catalogue services could use to search/discover your services. You must include the keyword OneGeology.

.. todo::

   Consider whether it would be better to recommend using INSPIRE extended capabilities for this metadata even for non-INSPIRE services.  Can GeoServer do this? Also will ESRI users outside of Europe be able to get the INSPIRE plugin (or else will need to provide exact details of XML to put into custom GC response)...

We would like you to also supply two special @ style ‘Metadata keywords’ (MD_DATE\@value and MD_LANG\@value) that will be used to populate the OneGeology catalogue of services, and which help make the GetCapabilities response ISO19115 core compliant.

MD_DATE@ is used to add a date for when the information in the GetCapabilites file for the service was last updated, (for MapServer services this would be the same as a change to the .map configuration file). For example the exemplar BGS_Bedrock_and_Superficial_Geology service has a MD_DATE@ keyword of MD_DATE\@2011-06-15

MD_LANG@ is used to add the language (using the ISO 639-3 three letter codes) that the GetCapabilites file is populated with. This may be different from the language that the service returns its data in. For example the exemplar BGS_Bedrock_and_Superficial_Geology service has a MD_LANG@ keyword of MD_LANG\@ENG

=============  =======  =====
Specification  Version  XPath
=============  =======  =====
WMS            1.3.0    /WMS_Capabilities/Service/KeywordList/Keyword
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceIdentification/ows:Keywords/ows:Keyword
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:keywords/wcs:keyword
WCS            2.0.1    /wcs:Capabilities/ows:ServiceIdentification/ows:Keywords/ows:Keyword
=============  =======  =====

.. todo::

   Revise Contact Information and Data provider sections to make one section with note on the bits of information we really require in contact details and the ones you can also helpfully add.

.. _service_provision_onegeology_profile_contact_information:

Contact information
""""""""""""""""""""

In addition to the required organisation name we recommend that you add additional contact information that will enable a user to get in touch with a named person who can act as a contact for any enquiries by post, email or phone. The different service types and versions provide slightly different structured fields for including this information under fairly self-explanatory element names. The below XPaths give the parent elements within which you can find different elements for email, phone etc. Don't forget these are for an international audience, e.g. include country code in telephone numbers.

=============  =======  =====
Specification  Version  XPath
=============  =======  =====
WMS            1.3.0    /WMS_Capabilities/Service/ContactInformation
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceProvider/ows:ServiceContact
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:responsibleParty
WCS            2.0.1    /wcs:Capabilities/ows:ServiceProvider/ows:ServiceContact
=============  =======  =====

.. _service_provision_onegeology_profile_data_provider:

Data provider
""""""""""""""

The full name of the data owner organization not service provider, where these are different, such as in buddied services. In the case of services that also supply non-OneGeology data, the contact should be able to put an enquirer in touch with whoever is responsible for the OneGeology data.

=============  =======  =====
Specification  Version  XPath
=============  =======  =====
WMS            1.3.0    /WMS_Capabilities/Service/ContactInformation/ContactPersonPrimary/ContactOrganization
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceProvider/ows:ProviderName
WCS            1.0.0    /wcs:WCS_Capabilities/wcs:Service/wcs:responsibleParty/wcs:organisationName
WCS            2.0.1    /wcs:Capabilities/ows:ServiceProvider/ows:ProviderName
=============  =======  =====

.. todo::

   This is harvested together with other Contact Person names from WMS into contact information metadata in 1g catalogue and displayed under Contact: information in layer information in portal. The WFS information is harvested into metadata in catalogue I think but not displayed anywhere in portal. For WCS contact information is harvested into catalogue record and displayed in portal layer details.

   No need mentioning the image format element; part of normal software functioning.

.. _service_provision_onegeology_profile_online_resource:

Online resource
""""""""""""""""

.. todo::

   Check what required by WMS specification means. This isn't displayed anywhere in Portal. Harvested in catalogue. In QGIS value doesn't get shown in layer properties (because in attribute?)

A link to the data owner organization web site, or web site with information about the data owner organization. Note this online resource is intended to provide additional information on the provider of the data and is NOT intended to be the same as the online resource attribute referenced in the Capability section of the response. (E.g. NOT the same as the resource cited in /WMS_Capabilities/Capability/Request/GetCapabilities/DCPType/HTTP/Get/OnlineResource in a 1.3.0 response.)

=============  =======  =====
Specification  Version  XPath
=============  =======  =====
WMS            1.3.0    /WMS_Capabilities/Service/OnlineResource
WFS            2.0.0    /wfs:WFS_Capabilities/ows:ServiceProvider/ows:ProviderSite
WCS            1.0.0    WCS 1.0.0 no suitable element.
WCS            2.0.1    /wcs:Capabilities/ows:ServiceProvider/ows:ProviderSite
=============  =======  =====


Layer / Coverage / Feature metadata
------------------------------------

Depending on which service type you are serving the actual data sets that you are supplying will be delivered as a number of layers (WMS), coverages (WCS) or features (WFS). Each of these can have their own specific metadata. The OneGeology portal allows the selection of WMS layers and WCS coverages to view and presents selected aspects of the layer/coverage metadata in its layer list. These metadata are also used to arrange layers/coverages under geographical areas and under themes and enable searching for layers/coverages including searching on some aspects of their functionality.

WFS are a bit different. In the Portal we do not list registered WFS separately but attach them to one or more WMS layers that portray some aspect of one or more of the features of the WFS. In OneGeology we are most focussed on WFS that supply features conforming to particular community standards whether simple feature standards like GeoSciML-Lite and ERML-Lite or complex feature standards like GeoSciML and ERML. In these cases the number of feature types available from a WFS is limited by the number of feature types in the community standards and you would normally be serving data for one data set from each WFS endpoint. (If you serve more than one data set from a given endpoint the client will need to know how to formulate a query that will only retrieve features from a particular data set.) Although the metadata are not presented directly in the Portal it is still recommended to add useful metadata for searching in the catalogue and for presentation in other WFS clients. If you don't yet have a suitable mapping from your data to a full community schema you may still be able to use your server software to generate automatically a simple feature WFS corresponding to a given WMS layer based on the same underlying dataset. In this case the features won't strictly conform to any community schema but may still have some common field names that allow a certain level of interoperability.

.. todo::

   Need to explain the above about naming of layers and features according to standard names or not and interoperability functionality just by having field names that can be portrayed in an SLD enabled WMS vs having the feature types as well following the standard names. Of course in latter case a fixed SLD can be used but in former the layer name has to be dynamically matched (as the portal does). Need a clearer explanation of all this. Maybe generic WMS/WFS/WCS standard explanation section with some example layer/feature/coverage names for illustration (don't have to be actual running services although that might help).

.. _service_provision_onegeology_profile_layer_names:

WMS layer and WCS coverage naming
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The OneGeology Portal allows selection of WMS layers and WCS coverages for display from a list and so it is important to have a naming convention that ensures unique titles for each of these layers and coverages. This convention has been designed to give readable, informative titles.

Both WMS and WCS have names which are used by software to select which layers/coverages are returned and human readable titles which are used for presenting in a client interface. The former do not need to be human readable and some server software may not allow much control over their format. The latter are the way layers and coverages are presented to a user for selection so it is important that they are understandable and informative. Thus OneGeology has a naming convention which we require for the human readable titles. It can also be friendly to make the machine readable names understandable for testing or writing custom clients so, although we don't make it a requirement, we do recommend that you follow the conventions below for the machine readable names as well if you can.

.. todo::

   We need to discuss what we want to do with increasing numbers of services that might not be primarily OneGeology ones and that might have their own conventions to adhere to.

   Have changed the requirement for a language code below to just be if there is more than one language version of a service rather than the previous more complex formulation. Haven't consulted on this though.

The titles should contain the following components which are explained in more detail below: **[Geographical extent]** of the data in the layer, then **[Data owner organization]** (not service provider), then **[Language code]** (if more than one language being provided), then **[Scale]**, then **[Theme]**.

Geographic extent
""""""""""""""""""

The first piece of information is the Geographic extent.  Geographic extent should begin wherever practically possible with the Country of the layer extent, even if the layer only covers part of a country, or if the layer covers all of one country (use that as the country code) and some of the surrounding landmass or sea area.  Country information is codified using the `ISO 3166-1 three-letter country codes <https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3>`_

When the layer covers an area such as a defined region, state or province within a country, you should state the country code first and then the provincial information.  Provincial information should wherever practically possible be codified using the `ISO 3166-2 codes <https://en.wikipedia.org/wiki/ISO_3166-2>`_

For example:

* The US state of Kentucky would use US-KY
* The semi-autonomous region of Flanders (Northern Belgium) would use BE-VLG

Note, the ISO 3166-2 codes use a 2 letter country code then hyphen then provincial code.

If you are using your own provincial code (known within your county perhaps but not codified by ISO), you should use the three letter ISO country code, then a space (not a hyphen), and then your provincial code.

The OneGeology Portal divides countries and regions using the United Nations (UN) "World macro regions and components" listing. If you are serving regional data wider than country level, you should use the `UN regions <http://unstats.un.org/unsd/methods/m49/m49regin.htm>`_ where possible.

Where the layer coverage doesn’t correspond to a country and/or when no ISO code or UN region exists to describe the coverage, you should use a short geographic name such as "World".

Data owner
""""""""""""

Geographic extent information is followed by the data owner organization code (not service provider), the same as recommended for the service title.

Language
"""""""""""

If you need to include language in your layer you should use the same ISO 639-1 two-letter language code `(https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) <https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes>`_ as recommended for the service title and include it *after* the data owner organization code .

Scale
""""""

Scale comes next and is shortened using SI symbols:

* "M" for Million (upper case)
* "k" for thousand (lower case)

Such that a 1:1 000 000 scale map would be represented in the layer title as 1:1M and a 1:625 000 scale map would be represented in the layer title as 1:625k.  In the layer names we shorten this further by removing the "1:" portion so that a 1:1 000 000 scale map is represented as 1M and a 1:625 000 scale map is represented as 625k.

Additionally, if the map scale is represented in the layer title as 1:1.5M we can lose the decimal point in the layer name by using 1500k.  **Note**, you do not have to use the 1500k format over the 1.5M format, rather we offer this format as an alternative, if your server software has an issue with dots in the layer name.

Theme
""""""

The theme is the geological description of the data contained in the layer.  As with the service title theme, the layer title theme should be a descriptive phrase in the service language.  For English services the layers will most commonly have titles such as "Bedrock Age", "Bedrock Lithology" etc.

.. todo::

   Check whether the portal really does care that layer names are unique; not sure this is true. Obviously layer names must be unique at a particular service endpoint but the server software should ensure that.

As mentioned above the layer names are for the consumption of the WMS software.  It is important that within the OneGeology Portal the layer names are unique.  The data owner is responsible to guarantee that there is no layer name duplication in all the layers they provide.

When we first started defining the rules for the OneGeology Portal we discovered that MapServer had a 20 character maximum limit on LAYER names (though this limit no longer applies), to get over this issue we defined a set of two and three letter codes to describe the most common layer themes to be used in the layer names, these are described below:

BA — Bedrock Age

BLT — Bedrock Lithology

BLS — Bedrock Lithostratigraphy

SLT — Superficial Lithology

SLS — Superficial Lithostratigraphy

MSF — Major Structural Features

This list is not exclusive, so please create your own if need be.

Note, if you decide to use ESRI ArcGIS server (versions 9.3.1 and below) you will not be able to conform to this layer naming convention, because the software auto-names the map layers 0, 1, 2...  This problem will be dealt with in the OneGeology Registry through the use of auto-generated unique id’s for each registered service layer, this is necessary as in a Catalogue like that for OneGeology one cannot have two layers having the same name i.e. both being named layer name 0.

This issue has been resolved in ESRI ArcGIS server 10

Layer title examples
"""""""""""""""""""""

GBR BGS 1:625k Bedrock Age

FRA BRGM 1:1M Formations géologiques - France Continentale

FRA BRGM 1:1M Formations géologiques - Guyanne

Note, it is acceptable to replace the ISO country code with a more readable name in the layer title

Layer name examples
""""""""""""""""""""

Remember that older versions of MapServer had a limit of 20 Characters for LAYER names; though this restriction no longer applies.

FRA_BRGM_1M_GeoUnits

GBR_BGS_625k_BA

World_25M_GeolUnits

Europe_BGR_5M_BLS

US-KY_KGS_24k_Faults

INSPIRE layer naming considerations
"""""""""""""""""""""""""""""""""""""

If your service falls under the INSPIRE naming conventions, then both the layer name and the layer title are fixed according to the legislation. For example the `D2.8.II.4 Data Specification on Geology–Technical Guidelines <http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_GE_v3.0.pdf>`_ tell us (section 11.1 ~ Layers to be provided by INSPIRE view services) that any layer to do with lithology or age must have the name *GE.GeologicUnit* and title *Geologic Units*.  See the `layer-naming <https://themes.jrc.ec.europa.eu/discussion/view/13952/layer-naming>`_ discussion on the INSPIRE Thematic Clusters Geology forum for fuller details.

To have a multiple layer geology service that adheres to the INSPIRE naming rules we believe the only option is for you to configure group layering. In such a situation, the layer name and title rules set out above relate to the grouped (or sub layers).  Whereas the INSPIRE name and title relate to the group (or parent) layer. If your INSPIRE service is only serving layers of one type, one way of applying group layering would be to use the WMS root layer name and title (not service name and title) as the grouping layer.

.. todo::

   I would just drop any OneGeology requirement on WMS Root Layer name but do a double check of how it appears in different clients to see if it might be helpful for some. Not used by Portal. Does this only apply to WMS as a view service? Can group layers be done in WCS and do we need them or is WCS only a download service or could it be used as a view service as well?

Summary of layer/coverage/feature metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For WMS layers and WCS coverages the machine readable name and human readable name should follow the conventions above. For WFS, if the data is being put out following a standard community schema then the machine readable name will be fixed according to the schema and a reasonable human readable name will probably be defined by the schema as well. If it is a simple WFS mirroring a WMS layer dataset then the names can match the WMS layer names.These go in the below places in the capabilities response.

.. todo::

   Need to mention ignoring any name prefix in machine readable name if relevant (just another constraint of software on machine readable names.

Machine readable name
"""""""""""""""""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/Name (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:name (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/wcs:CoverageId (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Name (2.0.x)

Human readable name
"""""""""""""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/Title (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:label (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Title (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Title (2.0.x)

.. _service_provision_onegeology_profile_layer_abstract:

Abstract
"""""""""

.. todo::

   Consider whether the standard feature description in a community schema WFS is the best thing to put in the abstract or whether it should be more tailored to individual service and data set.

You must provide a description of your layer/coverage data. You may wish to include other metadata, such as information about your organization and other data you make available. You may also wish to include a statement on access constraints. For features following a standard community Schema this may not be so relevant at the feature level in that a service will be providing data for a certain data set and the abstract description of the features will be just the general description of that feature type in the schema.

* /WMS_Capabilities/Capability/Layer/Layer/Abstract (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:description (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Abstract (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Abstract (2.0.x)

.. _service_provision_onegeology_profile_layer_keywords:

Keywords
"""""""""

* /WMS_Capabilities/Capability/Layer/Layer/KeywordList/Keyword (1.3.0)
* /WCS_Capabilities/ContentMetadata/CoverageOfferingBrief/keywords/keyword (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Keywords/ows:Keyword (2.0.x)

The Keyword "OneGeology" must be present to be able to search for services and layers with this keyword. OneGeologyEurope participants should also include relevant keywords chosen from the keyword list created for that project and listed in `Appendix I <https://onegeology.github.io/documentation/appendices.html#appendix-i-onegeology-english-keyword-dictionary-picklist>`_. The main purpose of these keywords is to make your services discoverable by a user searching in a catalogue of services, so a clearly formed but limited list of geosciences domain specific is ideal and all OneGeology global participants may also want to consider using items from this proposed OneGeology-Europe list, which has been formed by looking at many such lists available around the world including the European GEMET thesaurus found at: `http://www.eionet.europa.eu/gemet/en/themes/ <http://www.eionet.europa.eu/gemet/en/themes/>`_.

The following broad concepts are good starting points

`http://www.eionet.europa.eu/gemet/en/concept/2405 <http://www.eionet.europa.eu/gemet/en/concept/2405>`_ (earth science)

`http://www.eionet.europa.eu/gemet/en/concept/3648 <http://www.eionet.europa.eu/gemet/en/concept/3648>`_ (geological process)

Each keyword (or short phrase) must be contained within its own <keyword> element.

In addition to this we also require you to add a number of special ‘Cataloguing keywords’ to help the OneGeology Portal and catalogue services better index your layers.  These special keywords have a term then an ‘@’ symbol and then your value for the term, as below::

   Continent:                          continent@value       Required
   Subcontinent:                       subcontinent@value    Conditional
   Geographic area (usually country):  geographicarea@value  Required
   State(Region or province):          subarea@value         Conditional
   Data provider:                      dataprovider@value    Required
   Service provider:                   serviceprovider@value Required

The geographicarea\@value represents a verbalization of the code that starts a layer name. For most layers geographicarea\@value will be a country; this INCLUDES layers that only show a sub-region or state within a country.

The values for Continent, Subcontinent and Country must be taken from the United Nations (UN) list: `http://unstats.un.org/unsd/methods/m49/m49regin.htm <http://unstats.un.org/unsd/methods/m49/m49regin.htm>`_ used by the OneGeology Portal.

Conditional keywords are required if they apply. E.g. If the geographic area is a state or province then the subarea keyword is required.

In addition we would like that you also supply the following two special ‘Metadata keywords’ for each layer. These keywords help make the GetCapabilities response ISO19115 core compliant. ::

   Layer (Data set) date:              DS_DATE@value
   Layer (Data set) topic category:    DS_TOPIC@value        (one or more as appropriate)

The topic category is taken from the ISO 19119 topic category listing.  A good reference to the categories and what they represent is found at: `https://gcmd.nasa.gov/add/difguide/iso_topics.html <https://gcmd.nasa.gov/add/difguide/iso_topics.html>`_. We anticipate that most layers would have a DS_TOPIC\@geoscientificinformation keyword.

So for example, the layer “AFG AGS 1:1M Bedrock Age” would include the following keywords:

.. code-block:: xml

   <KeywordList>
    <Keyword>OneGeology</Keyword>
    <Keyword>Afghanistan</Keyword>
    <Keyword>continent@Asia</Keyword>
    <Keyword>subcontinent@South-central Asia</Keyword>
    <Keyword>geographicarea@Afghanistan</Keyword>
    <Keyword>serviceprovider@British Geological Survey</Keyword>
    <Keyword>dataprovider@Afghanistan Geological Survey</Keyword>
    <Keyword>DS_TOPIC@geoscientificinformation</Keyword>
    <Keyword>DS_DATE@2008-12-03</Keyword>
    <Keyword>thematic@geology</Keyword>
   </KeywordList>

Note, that we have the country twice, once as one of the OneGeology Portal special keywords, and once as the country only; this is because we recognize that the service may be consumed (and catalogued) by services other than OneGeology. We don’t include a subarea@ keyword in this list because that would not be appropriate in this instance.

To help classify your service in the portal according to the thematic keyword list (as detailed in `Appendix I <https://onegeology.github.io/documentation/appendices.html#appendix-i-onegeology-english-keyword-dictionary-picklist>`_), you should also use one or more *thematic@value keywords*.

**Please note** services using GeoSciML-Lite also require the following keyword: **Geosciml_portrayal_age_or_litho_queryable** (GeoSciML-Lite was previously called GeoSciML-Portrayal.)

For those WMS layers with an associated GeoSciML WFS that you would like to query using the OneGeology Portal thematic analysis tool, you will need to add the appropriate **GeoSciML32_wfs_age_or_litho_queryable** or **GeoSciML4_wfs_age_or_litho_queryable** keyword.

WMS Specific Metadata
^^^^^^^^^^^^^^^^^^^^^^

The following sections were defined for the earlier WMS only specific OneGeology profile and haven't yet been considered for updating to other service types.

.. _service_provision_onegeology_profile_layer_extent:

Extent
""""""""

* /WMS_Capabilities/Capability/Layer/Layer/EX_GeographicBoundingBox (1.3.0)

In WMS version 1.3.0 four elements each describing a single bounding limit (always in the order: west, east, south, north). The purpose of these extent values is to facilitate geographic searches; values may be approximate.

.. todo::

    Not sure about 2* requirement for a LatLon bounding box using EPSG:4326. Where is this used? If it isn't required for the portal then what is it important for? Does GeoNetwork catalogue use it for plotting?

    This probably is GeoNetwork related, certainly for a WMS 1.3.0 the element that is used to show the extent (<EX_GeographicBoundingBox>) is the same element as is used by GeoNetwork / ISO 19139 XML to hold extent data.

    WMS 1.1.1 has LatLonBoundingBox and WMS 1.3.0 has EX_GeographicBoundingBox, they are equivalent.  WFS 1.0.0 has LatLongBoundingBox, WFS 1.1.0 and 2.0.0 have WGS84BoundingBox. WCS 1.0.0 has lonLatEnvelope, WCS 1.1.1 and WCS 2.0.0 have WGS84BoundingBox

.. _service_provision_onegeology_profile_layer_crs:

Spatial/Coordinate reference system
""""""""""""""""""""""""""""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/CRS (1.3.0)

A list of one or more horizontal ’Spatial Reference Systems’ that the layer can handle (will accept requests in and return results based upon those SRS).  In WMS 1.1.1, the returned image is always projected using a pseudo-Plate Carrée projection that plots Longitude along the X-axis and Latitude along the Y-axis.

For example, the exemplar service lists the following Spatial Reference Systems: EPSG:4326, EPSG:3857, CRS:84, EPSG:27700, EPSG:4258

The portal now supports the projection systems below, including two suitable for INSPIRE compliance:

   EPSG:3031
      Antarctic Polar Stereographic (WGS84) `urn:ogc:def:crs:EPSG::3031 <http://epsg-registry.org/export.htm?wkt=urn:ogc:def:crs:EPSG::3031>`_
   EPSG:3034
      Lambert Conformal Conic (ETRS89) `urn:ogc:def:crs:EPSG::3034 <http://epsg-registry.org/export.htm?wkt=urn:ogc:def:crs:EPSG::3034>`_ (suitable for INSPIRE compliance)
   EPSG:3413
      NSIDC Sea Ice Polar Stereographic North (WGS84) `urn:ogc:def:crs:EPSG::3413 <http://epsg-registry.org/export.htm?wkt=urn:ogc:def:crs:EPSG::3413>`_
   EPSG:3857
      Web Mercator (WGS84) `urn:ogc:def:crs:EPSG::3857 <http://epsg-registry.org/export.htm?wkt=urn:ogc:def:crs:EPSG::3857>`_
   EPSG:4258
      2D Latitude / Longitude (ETRS89) `urn:ogc:def:crs:EPSG::4258 <http://epsg-registry.org/export.htm?wkt=urn:ogc:def:crs:EPSG::4258>`_ (suitable for INSPIRE compliance)
   EPSG:4326
      2D Latitude / Longitude (WGS84) `urn:ogc:def:crs:EPSG::4326 <http://epsg-registry.org/export.htm?wkt=urn:ogc:def:crs:EPSG::4326>`_

.. todo::

    How come supporting EPSG:4326 is a 2* requirement. Does the portal need it or not?

    We say that all services MUST support EPSG:4326, so possibly it's a one star requirement.

.. _service_provision_onegeology_profile_layer_bbox:

BoundingBox
""""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/BoundingBox (1.3.0)

The BoundingBox attributes indicate the edges of the bounding box in units of the specified spatial reference system, for example, the exemplar service provides the following BoundingBox information for the GBR BGS 1:625k bedrock lithology layer:

**Example WMS 1.3.0 response**

.. code-block:: xml

   <BoundingBox CRS="EPSG:4326" minx="49.8638" miny="-8.64846" maxx="60.8612" maxy="1.76767" />
   <BoundingBox CRS="EPSG:3857" minx="-962742" miny="6.42272e+006" maxx="196776" maxy="8.59402e+006" />
   <BoundingBox CRS="CRS:84" minx="-8.64846" miny="49.8638" maxx="1.76767" maxy="60.8612" />
   <BoundingBox CRS="EPSG:27700" minx="-77556.4" miny="-4051.91" maxx="670851" maxy="1.23813e+006" />
   <BoundingBox CRS="EPSG:4258" minx="49.8638" miny="-8.64846" maxx="60.8612" maxy="1.76767" />

**Please note the x,y axes order for the geographic coordinate systems EPSG:4258 and EPSG:4326. In WMS version 1.3.0 the x-axis is the first axis in the CRS definition, and the y-axis is the second. So for example EPSG:4326 refers to WGS 84 geographic latitude, then longitude. That is, in this CRS the x axis corresponds to latitude, and the y axis to longitude.  Most EPSG geographic coordinate reference systems follow this (x=lat,y=lon) pattern.**


.. todo::

    Again why 2* requirement for EPSG:4326 BoundingBox and how does this compare with LatLonBoundingBox and is this controllable anyway or just an artefact of software and which basic coord systems you say you will support (so just say we want X coord system supported (so can query in that one) and assume sw will do appropriate bounding boxes if you configure that. WFS and WCS may be different.
    For INSPIRE it is a requirement that each supported CRS has a BBOX in the units of the CRS (for view services, not sure about download services), but not sure where the OneGeology requirement came from.


.. _service_provision_onegeology_profile_layer_data_url:

DataURL (optional)
""""""""""""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/DataURL (1.3.0)

This may be used to provide further information about all the digital data offered by the data provider, though it is primarily used to provide a link to non-standards compliant metadata for the layer in question.

.. code-block:: xml

   <DataURL>
   <Format>text/html</Format>
   <OnlineResource
     xmlns:xlink="http://www.w3.org/1999/xlink"
     xlink:type="simple"
     xlink:href="http://www.bgs.ac.uk/discoverymetadata/13480426.html" />
   </DataURL>

.. _service_provision_onegeology_profile_layer_metadata_url:

MetadataURL (optional)
"""""""""""""""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/MetadataURL (1.3.0)

You **should** supply one or more on-line resources offering detailed, standardized (either as "FGDC:1998" or "ISO 19115:2003") metadata about the layer data. If your metadata is not available in either of these standards you **MUST** instead use a DataURL.

The core ISO 19115:2003 metadata required to be compliant is shown under :ref:`service_provision_onegeology_profile_core_metadata`.  Note, there are no formatting requirements; this information could be provided as xml or html or text or pdf etc as long as it accessible on the web.

.. todo::

    Consider whether using FeatureURL would be a good way to link to associated WFS.  Is it even possible to set in MapServer, GeoServer, ArcGIS... One for GitHub?

**Example WMS 1.3.0 response**

.. code-block:: xml

   <MetadataURL type="ISO 19115:2003">
   <Format>application/xml; charset=UTF-8</Format>
   <OnlineResource
     xmlns:xlink="http://www.w3.org/1999/xlink"
     xlink:type="simple"
     xlink:href="http://metadata.bgs.ac.uk/geonetwork/srv/en/csw?
       service=CSW&
       version=2.0.2&
       request=GetRecordById&
       id=ac9f8250-3ae5-49e5-9818-d14264a4fda4&" />
   </MetadataURL>

Please note: the defined attribute value to indicate ISO 19115:2003 metadata is “ISO 19115:2003” in WMS version 1.3.0 as opposed to “TC211” in version 1.1.1. In version 1.3.0, communities may **ALSO** define their own attributes. We **RECOMMEND** that if you can change this attribute for different WMS version GetCapabilities responses you should use “ISO 19115:2003” for your WMS 1.3.0 response. If you can only configure one response type then you **MUST** use “TC211”.

.. _service_provision_onegeology_profile_layer_legend_url:

Legend url
"""""""""""

* /WMS_Capabilities/Capability/Layer/Layer/Style/LegendURL (1.3.0)

We require you to have some sort of legend to accompany your map data. In many cases your server software will create this for you automatically using the inbuilt SLD capability. If your WMS server is not SLD capable, or if you have a complex legend, you may add the LegendURL manually in your GetCapabilities response document.  See below :ref:`style_examples`.

.. _style_examples:

Layer styling information
""""""""""""""""""""""""""""

The examples below show the styling portion of the GetCapabilities response.  The first shows that the legend will be generated on-the-fly using an SLD GetLegendGraphic request. The second shows a simple request to a static image, generated in advance by the map service provider.

Example style information from a MapServer version 5.6.5 WMS version 1.3.0. GetCapabilities response.  The legend will be created automatically by MapServer and served using an SLD GetLegendGraphic operation.  Note the OnlineResource URL now includes an sld_version parameter.

.. code-block:: xml

   <Style>
       <Name>default</Name>
       <Title>default</Title>
       <LegendURL width="328" height="3013">
           <Format>image/png</Format>
           <OnlineResource
               xmlns:xlink="http://www.w3.org/1999/xlink"
               xlink:type="simple"
               xlink:href="http://ogc.bgs.ac.uk/cgi-bin/BGS_GSN_Bedrock_Geology/wms?
               version=1.3.0&amp;
               service=WMS&amp;
               request=GetLegendGraphic&amp;
               sld_version=1.1.0&amp;
               layer=NAM_GSN_1M_BLS&amp;
               format=image/png&amp;
               STYLE=default&amp;"/>
       </LegendURL>
   </Style>

Example style information from an ArcGIS server WMS version 1.3.0. GetCapabilities response.  A detailed static legend is provided.

.. code-block:: xml

   <Style>
   <Name>default</Name>
   <Title>US-KY KGS 1:500K Kentucky Geologic Formations</Title>
   <LegendURL width="100" height="588">
   <Format>image/png</Format>
   <OnlineResource
     xlink:href="http://.../.../KGS_Geology_and_Faults_MapServer/wms/default2.png&amp;"
     xlink:type="simple"
     xmlns:xlink="http://www.w3.org/1999/xlink" />
   </LegendURL>
   </Style>

.. _service_provision_onegeology_profile_layer_getfeatureinfo:

WMS GetFeatureInfo response
""""""""""""""""""""""""""""

Depending on the data you have available for each layer and depending on your WMS software, you may be able to configure what is returned in response to GetFeatureInfo requests on each layer, either to format the look of the data returned or to restrict the data attributes returned.

Ideally the response should include a field for age/lithology/lithostratigraphy as appropriate for each layer.  You may choose to include other information you consider useful but please try to exclude data fields that only have meaning internal to your organization.

Preferably it should be possible to retrieve the information in at least text/html and text/plain formats.

.. _service_provision_onegeology_profile_core_metadata:

Core TC211/ISO:19115 Metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section has been added to allow you to understand what metadata you need to supply, if you choose to supply additional metadata about a layer as an online resource **AND** if you want to use the MetadataURL to reference that resource.  If you wish to supply an online resource to layer metadata, that doesn’t conform to the minimum standard set out below (or FGDC:1998) then you cannot use the MetadataURL; we recommend that you use the DataURL.  If you also wish to supply a URL to your web site, to highlight all your data products (for example), then you can use the SERVICE level online resource URL; in MapServer you do this by specifying the WMS_SERVICE_ONLINERESOURCE (or OWS_SERVICE_ONLINERESOURCE) keyword.

For example in our exemplar service we have:

::

   OWS_SERVICE_ONLINERESOURCE "http://www.bgs.ac.uk/products/digitalmaps/digmapgb.html"

Note that TC211/ISO:19115:2003 is not itself a format, but a standard for defining formats and profiles.  To comply with the ISO:19115:2003 metadata standard a data format (or profile) must define a core set of metadata elements as shown below.  Note, for the purposes of the OneGeology Portal if you are showing your metadata (when accessed using the MetadataURL) in an HTML/text or pdf page it is sufficient to provide only Mandatory metadata, and Conditional metadata (where appropriate).

.. raw:: html

      <table cellpadding="5" cellspacing="0" class="borderedTable">
      <colgroup ><col width="50%" /></colgroup>
      <thead>
      <tr><th colspan="2"><p>Mandatory (M): The metadata entity or metadata element shall be documented</p>
      <p>Conditional (C):  The metadata entity or metadata element shall be documented if another entity or element has been documented, or if a condition is or isn’t met elsewhere.</p>
      <p>Optional (O): Provided to allow users to document their data more fully.</p></th></tr>
      </thead>
      <tbody>
        <tr>
          <td>**Dataset title** (M)
            <p>A unique title (within your metadata records) for your data.</p></td>
          <td>**Spatial representation type** (O)
            <p>The method used to represent geographic information in the dataset. i.e., vector, grid, TIN etc.</p></td>
        </tr>
        <tr>
          <td>**Dataset reference date** (M)</td>
          <td>**Reference system** (O)</td>
        </tr>
        <tr>
          <td>**Dataset responsible party** (O)</td>
          <td>**Lineage** (O) </td>
        </tr>
        <tr>
          <td>**Geographic location** of the dataset (by four coordinates or by geographic identifier) (C)
            <p>If the metadata applies to a data set which is spatially referenced (such as a OneGeology WMS) this is required.</p></td>
          <td>**On-line resource **(O) </td>
        </tr>
        <tr>
          <td>**Dataset language** (M)
            <p>Language(s) used within the dataset. Required even if the resource does not include any textual information; defaults to the Metadata language.</p></td>
          <td>**Metadata file identifier** (O)
            <p>Unique identifier for this metadata file</p></td>
        </tr>
        <tr>
          <td>**Dataset character set** (C)
            <p>Full name of the character encoding used for the data set.  You must supply this character set if you are not using the ISO/IEC 10646-1 character set and if your character set is not defined by the document encoding.</p></td>
          <td>**Metadata standard name** (O)
            <p>Name of the metadata standard (including profile name) used</p></td>
        </tr>
        <tr>
          <td>**Dataset topic category** (M)
            <p>Main theme(s) of the data set described using the most appropriate term defined in the standard; for OneGeology services these are likely to be one or more from: ‘*geoscientificInformation*’, ‘*economy*’ (for layers showing mineral resources), or ‘*imageryBaseMapsEarthCover*’</p></td>
          <td>**Metadata standard version** (O)
            <p>Version (profile) of the metadata standard used</p></td>
        </tr>
        <tr>
          <td>**Spatial resolution of the dataset** (O)
            <p>Scale or factor which provides a general understanding of the density of the spatial data in the dataset.</p></td>
          <td>**Metadata language** (C)
            <p>Language used to document the metadata. You must supply the metadata language if it is not defined by the document encoding.</p>
            <p>Note for INSPIRE GEMINI metadata you must always supply the metadata language.</p></td>
        </tr>
        <tr>
          <td>**Abstract defining the dataset** (M)
            <p>Brief narrative summary of the content of the resource.</p></td>
          <td>**Metadata character set** (C)
            <p>Full name of the character encoding used for the metadata set. You must supply this character set in your metadata if you are not using the `ISO/IEC 10646-1 character set <https://en.wikipedia.org/wiki/Universal_Character_Set>`_ (https://en.wikipedia.org/wiki/Universal_Character_Set) AND if your character set is not defined by the document encoding.  Note as most XML and HTML pages provide a character set as part of their own metadata, it is likely that you will not need to explicitly state this for your own layer metadata</p></td>
        </tr>
        <tr>
          <td>**Distribution format** (O) </td>
          <td>**Metadata point of contact** (M)
            <p>Party responsible for the metadata information</p></td>
        </tr>
        <tr>
          <td>**Additional extent information for the dataset** (vertical and temporal) (O)</td>
          <td>**Metadata date stamp** (M)</td>
        </tr>
        </tbody>
      </table>

OneGeology Europe participants should note that conformance of an ISO 19115 metadata set to the ISO 19115 Core does not guarantee conformance to INSPIRE metadata, see the INSPIRE technical guidelines document `MD_IR_and_ISO_v1_2_20100616 <http://inspire.ec.europa.eu/documents/Metadata/MD_IR_and_ISO_20131029.pdf>`_ for further details.

GeoSciML
--------

GeoSciML (GeoScience Markup Language) is a GML (Geography Markup Language) application language for geoscience.

**The design, build and deployment of information technologies that enable and advance geoscience information management, analysis and delivery will require systems that are interoperable following international agreed standards that are relevant to the geosciences.**

It is an XML schema for data exchange over the Internet that incorporates the ability to represent geography (geometries e.g. polygons, lines and points using the OGC's GML specification) as part of the features that are being exchanged. The range of features being offered for exchange are defined by the domain or subject area of geoscience or the geological sciences.

GeoSciML accommodates the short-term goal of representing geoscience information associated with geological maps and observations, as well as being extensible in the long-term to other geoscience data. It draws from many geoscience data model efforts, and from these establishes a common suite of feature types based on geological criteria (units, structures, fossils) or artefacts of geological investigations (specimens, sections, measurements). Supporting objects are also considered (timescale, lexicons, etc), so that they can be used as classifiers for the primary objects.

GeoSciML is based on `W3C <http://www.w3c.org>`_, OGC, `CGI Data Model <http://www.seegrid.csiro.au/twiki/bin/view/CGIModel/WebHome>`_  and ultimately `ISO <http://www.iso.org>`_ international standards for data exchange over the Internet. GeoSciML is being designed under the umbrella of the `IUGS Commission <http://www.iugs.org/>`_ on the Management and Application of Geoscience Information (CGI) and its `CGI Interoperability Working Group <http://cgi-iugs.org/tech_collaboration/interoperability_working_group.html>`_.

For further detailed information on the development of GeoSciML, see http://www.cgi-iugs.org/tech_collaboration/geosciml.html

.. figure:: images/geosciml.gif
    :width: 417px
    :align: center
    :height: 249px
    :alt: GeoSciML Data Model
    :figclass: align-center

    GeoSciML Data Model


Web Services
----------------

How to setup web services to serve data to OneGeology. We provide a basic explanation of how to do it easily.

.. _service_provision_data_preparation_exampledata:

Cookbook example data
^^^^^^^^^^^^^^^^^^^^^^

In order to help you test setting up services with data that we know work before you try using your own data we supply a number of example data sets that can be used to set up different kinds of services.

GeoPackage
""""""""""

This is a relatively recent standard format for exchanging vector and raster GIS data in a single file. It can potentially be used for quite complex data structures. The example contains two files that could be used for a Simple WMS with GetFeatureInfo response and a Simple Feature WFS. They can also serve as the basis of an SLD enabled WMS and the GeologicUnitView.gpkg file has the fields that are used for highlighting queries in the OneGeology Portal age and lithology tool. As this format doesn't have the restrictions on field length of Shapefiles the examples are able to use the same names as specified in the GeoSciML-Lite GeologicUnitView and ShearDisplacementView feature types. Field values have been populated with appropriate values from INSPIRE vocabularies so that these examples can be used to produce a simple feature WFS returning standards conformant GeoSciML-Lite features. Download from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/exampledata/geopackagegeoscimllite.zip>`_.

PostGIS data
"""""""""""""

This data set can be used as a basis for WMS with GetFeatureInfo, SLD enabled WMS usable in OneGeology Portal, Simple Feature WFS conforming to GeoSciML Lite schema and Complex Feature WFS conforming to GeoSciML schema. A PostGIS database could also store raster data but the example dataset does not. PostGIS is more suitable for production services than Image files or Shapefiles and is more capable for providing data and as a basis for services conforming to standard application schemas.

It is assumed that you have :ref:`installed the PostGIS software <service_provision_data_preparation_postgis>` and that you have a spatially enabled database (the default installation will create one called postgis). The following will all be working within this spatially enabled database.

Download the latest version of the database dump file wfscookbook.YYYY-MM-DD.backup from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/wfscookbook/>`_. (Each version will have its release date in place of YYYY-MM-DD.)

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
*******************

The `PostGIS Installation <http://www.postgis.net/install>`_ page contains instructions on how to install PostGIS for different operating systems. We have used both the `Enterprise DB Windows Installer <https://www.enterprisedb.com/downloads/postgres-postgresql-downloads>`_ on Windows and the `PostgreSQL Yum repository <https://yum.postgresql.org/>`_ on CentOS.

.. todo::

    Don't think we want to go into more detail on installation ourselves?

Image with world file
""""""""""""""""""""""

This is an image file with associated worldfile to locate it in geographic coordinates. This is the type of file that you might have if you only have paper maps which you have to scan to use. It is suitable for setting up a simple WMS without any useful GetFeatureInfo response or the ability to be styled by an SLD. Download from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/exampledata/georeferencedimage.zip>`_.

Shapefile
"""""""""""

ESRI Shapefile is a very common vector GIS format. The example could be used for a Simple WMS with GetFeatureInfo response and a Simple Feature WFS. It could also serve as the basis of an SLD enabled WMS but it doesn't have the fields that are used in the OneGeology Portal age and lithology tool so wouldn't work with that unless those fields were added. Also, because of the 10 character limit on length of Shapefile field names your server software will need to be able map shorter field names to the longer ones expected by the Portal. The field name length restriction also means that a simple feature WFS can't be made to conform to specific standard Schemas like GeoSciML Lite unless your server software can map the names to the longer standard property names. Download from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/exampledata/shapefileunharmonised.zip>`_.

.. todo::

   Possible need for an id column (WFS?). Convert referenced appendices (now just A) from the old cookbook?

OneGeology does not recommend using Shapefiles as the data source for your services but, if you already have your data in this format, it can be used as a data source with some restrictions.

If you wish to set up a :term:`SLD enabled WMS` or :term:`Simple feature WFS` using the standard fields needed for age and lithology highlighting in the Portal or following one of the standard 'Lite' schemas then the 10 character limit on field names in Shapefiles means your server will need to map shorter Shapefile field names to the longer expected field names in the standards. We provide some :ref:`service_provision_data_preparation_short_names` for some GeoSciML-Lite features that are reasonably readable and would enable using common mapping files to produce services using the full names.

Another consideration might be that, if the coordinate system of your Shapefile is not EPSG:4326 and your service is predominantly to be used in the OneGeology Portal, then your server will have to do a lot of on-the-fly coordinate conversion. To ameliorate this you can `convert the coordinate system of your Shapefile </wmsCookbook/appendixA.html>`_. The tools referred to in the previous link are available from http://www.gdal.org if you haven't done the MS4W download that it assumes.

.. _service_provision_data_preparation_short_names:

Recommended ESRI shapefile definitions for GeoSciML-Lite
********************************************************
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
""""""""

GeoTIFF is a raster format with geographic registration included. The example has been obtained from the `EMODNET Portal for Bathymetry <http://portal.emodnet-bathymetry.eu/RGB>`_ and has RGB bands suitable for display as an image although other GeoTIFF's could have more and not necessarily image bands. This could be used for a WMS but is included primarily to test WCS setup. Download from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/exampledata/geotiff.zip>`_.

Setting up a Server
--------------------

There are a wide variety of proprietary and open source software packages that can be used to provide the OGC web services of interest to OneGeology. We cannot possibly describe them all but this section gives guidance on how to use some with which we do have experience to set up your OneGeology services. If you are interested and able to provide similar guidance for a software package not listed below then please get in touch to discuss adding your documentation here. Currently the only software we have successfully used to provide *all* the service types relevant for OneGeology is GeoServer.

To start with there are some links to downloadable example data sets which you can use to experiment with setting up the servers before you try getting your own data into an appropriate format.

At the end there is an additional section on setting up the Apache HTTPD server to act as a reverse proxy which may be useful if you need to provide a unified web address and port for accessing your OneGeology and possibly other web services.


Using GeoServer
----------------

GeoServer has extensive `documentation <http://docs.geoserver.org/stable/en/user/index.html>`_ which you should refer to in addition to this cookbook. References will be made to relevant parts rather than repeating too much of what is already there. There is also the `geoserver-users mailing list <http://geoserver.org/comm/>`_.

Introduction
^^^^^^^^^^^^^

This section describes how to set up the different kinds of OneGeology compliant service described in :ref:`service_provision_service_types` using free and open source GeoServer software. GeoServer can be used to provide *all* the types of service that OneGeology service providers might need. There are also INSPIRE specific instructions on making your services INSPIRE compliant where relevant. This is entirely optional for OneGeology so you can ignore the INSPIRE sections if this is not of interest to you.

If you are going to use a PostGIS database as a data source you will also need to read :ref:`service_provision_data_preparation_postgis`.

Accompanying this guidance are some example data sets and GeoServer configuration that allow you to set up working services which you may find helpful to adapt for use with your own data.

Pre-requisites / System Requirements
"""""""""""""""""""""""""""""""""""""

The guidance is technical and some assumptions are made about the reader's background knowledge:

* The reader is, or is working closely with, an expert in the geological data to be served.
* The reader has some familiarity with setting up web servers and preferably Java servlet containers.
* The reader is able to install software on their machine and can follow the appropriate installation instructions for GeoServer documented on the GeoServer website.

To set up production services you will need server equipment to run GeoServer. Estimating the level of hardware resources required to support a responsive service is a complex task depending on the amount of your data, its complexity and the demand that will be placed on your service by users. It is out of the scope of this document to give advice on these issues but you can find some assistance from the GeoServer web site and mailing list. To test setting up a service using the example in this guide a modern PC with Intel Core or equivalent processor and 4Gb RAM should certainly be adequate and you can probably get away with less.

The software required includes Java, a Java servlet container such as Apache Tomcat, and GeoServer itself. If you use one of the GeoServer packages that include Jetty then you won't need to install a servlet container separately. There are a lot of different versions and all these software packages are continuously updated. You may have conditions specific to your site which make particular versions preferable. For example, you may already have your data in a different database system such as Oracle Spatial rather than PostGIS. It isn't possible to cover all possible set ups here.

Further pre-requisites required only for particular service types are described under the appropriate section.

Software Installation
""""""""""""""""""""""

The software used here all has extensive documentation and support forums and mailing lists. Here we will just point you to the appropriate places to download the software and get installation instructions.

* `Download <http://geoserver.org/release/stable>`_ and install GeoServer following whichever one of the `installation paths <http://docs.geoserver.org/stable/en/user/installation/index.html>`_ in the GeoServer manual suits your situation best. If you already have a servlet container application such as `Apache Tomcat <http://tomcat.apache.org/>`_ set up or you are familiar with how to set one up then you will probably wish to download the web archive (WAR) and deploy that in your servlet container. If you are not comfortable with configuring a servlet container then you will probably wish to use one of the installer programs.

* Run GeoServer at least once to check the installation has worked. If, for example, you are testing in a local instance of Tomcat on your own machine with default settings you should be able to visit http://localhost:8080/geoserver and click on the :guilabel:`Layer Preview` link to check that the example services shipped with GeoServer work properly. You will have to modify the preceding URL appropriately if you have deployed GeoServer on a different machine or port.

.. figure:: images/geoserver_welcome.jpeg

.. _service_provision_server_setup_geoserver_install_app_schema:

App-schema Plugin Installation
""""""""""""""""""""""""""""""

You will need to install the app-schema plugin if you wish to set up a complex feature WFS or if you are setting up a simple feature WFS using one of the OneGeology recommended "Lite" schemas. If not, you can skip this step.

* `Download <http://geoserver.org/release/stable>`_  and install the app-schema plugin ``geoserver-*-app-schema-plugin.zip`` following the `application schema installation instructions <http://docs.geoserver.org/stable/en/user/data/app-schema/installation.html>`_. Follow the instructions at `WFS service settings <http://docs.geoserver.org/stable/en/user/data/app-schema/wfs-service-settings.html>`_.
* Check you can restart GeoServer without any errors being thrown.

INSPIRE Plugin Installation
""""""""""""""""""""""""""""

If you are providing an INSPIRE download service you will need to provide the extra INSPIRE mandated metadata in the WFS GetCapabilities response. This is optional for OneGeology.

* `Download <http://geoserver.org/release/stable>`_ and install the INSPIRE plugin ``geoserver-*-inspire-plugin.zip`` following the `INSPIRE plugin installation instructions <http://docs.geoserver.org/stable/en/user/extensions/inspire/index.html>`_.

Database
"""""""""""

If you already have your data in a relational database system you will want to check the `Working with Databases <http://docs.geoserver.org/stable/en/user/data/database/index.html>`_ section of the GeoServer manual to see if your database is supported by GeoServer and follow the instructions for installation of any extensions that may be needed for this support. PostGIS support is built into the core GeoServer download.

If you want to try the example data or don't have a supported database system you should :ref:`install PostGIS <service_provision_data_preparation_postgis>`.

You may use a database on the same machine as GeoServer or you can have it on a separate machine which is accessible over a network from your GeoServer machine.

Assumptions
"""""""""""

You will need to have Java installed on the machine on which you are going to install GeoServer. See the `Java Considerations <http://docs.geoserver.org/stable/en/user/production/java.html#production-java>`_ section of the GeoServer manual for the current recommendations. If you want to try other versions of Java you may need to do extra work and be prepared to enter into technical discussions on the geoserver-users email list in order to get it working with these.

Ideally you will be familiar with deploying applications in a servlet container application such as `Apache Tomcat <http://tomcat.apache.org/>`_. If not, you can use one of the all-in-one installers that packages GeoServer already deployed in the `Jetty <https://www.eclipse.org/jetty/>`_ servlet container. Note that Tomcat and Jetty are the two most tested servlet containers used with GeoServer so, although you should be able to use others, there may be extra work involved and you may need to get advice from the geoserver-users email list.

* You have a basic familiarity with relational databases
* You are able to install applications such as Apache Tomcat, GeoServer, PostGIS (if you are using that as a database) etc. on a server with your chosen operating system using their project documentation.

Common Setup
^^^^^^^^^^^^^

.. todo::

   Need to decide whether to talk about workspaces which are more flexible for WMS, simple WFS and WCS but can't be used for complex WFS or just keep it simple and do everything under the single global service URL for everything. Describe the common service metadata like contact info etc. that will be set up similarly for all service types. Point to the sections of the GUI where the different metadata described in profile section can be entered. There is some common ground setting up file based data stores for all services or database based datastores for all services but probably clearer to repeat the data store setup under each service type section.

Logging in
"""""""""""

The Web Administration Interface is a browser-based tool for administering the server software remotely. To deploy a web service in the GeoServer environment, log in to the Web Administration Interface for the GeoServer instance you will be using to deploy your data as a web service. To access this tool, open a web browser and enter the web address into the navigation bar. GeoServer is usually installed such that the administrative interface can be accessed at a URL with the following address pattern:

**http://<host>:<port>/geoserver/web/**, **<port>** is usually **8080**, and <host> is the name or IP address of the server.

If you are testing in a local instance of Tomcat on your own machine with default settings this would be http://localhost:8080/geoserver/web/

The default account settings for GeoServer are as follows:

* Username: admin
* Password: geoserver

For security reasons, it is recommended that you change your password to something more secure as soon as possible. You will see warnings about changing your passwords and links to where to change them when you first log in. There is an overview of the web administration interface in the `GeoServer manual <http://docs.geoserver.org/latest/en/user/webadmin/index.html>`_.

Editing contact information metadata
"""""""""""""""""""""""""""""""""""""

Within the GeoServer Web Administration Interface, click **Contact Information**, under `About & Status <http://docs.geoserver.org/latest/en/user/webadmin/index.html#about-status>`_. This brings you to a Contact Information form in which you can provide contact information for your GeoServer instance. The information entered here becomes part of service-level metadata for the web service that is accessed by the OGC GetCapabilities request. Consequently, Contact Information entered here should be as precise and comprehensive as possible.

This form allows you to enter the :ref:`service_provision_onegeology_profile_contact_information` and :ref:`service_provision_onegeology_profile_data_provider` required by the OneGeology profile.

.. note:: The information entered here is presented differently in the GetCapabilities responses for different types and versions of service.

Workspaces
"""""""""""

In GeoServer `workspaces <https://docs.geoserver.org/latest/en/user/data/webadmin/workspaces.html>`_ are used for organising data. For each workspace there are also `virtual services <https://docs.geoserver.org/latest/en/user/configuration/virtual-services.html>`_ created at different service URLs. So if you have an instance of GeoServer available at http://example.com/geoserver there will be a global service URL at http://example.com/geoserver/ows and, if you have a workspce called ws1, there will also be a virtual service URL at http://example.com/geoserver/ws1/ows. This allows some flexibility and control over making different data sets and services available for different purposes to different users. To start with we suggest you `create a new workspace <http://docs.geoserver.org/latest/en/user/data/webadmin/workspaces.html#add-a-workspace>`_ for your data and, if you are using any of the example data that accompany this guide then create a separate workspace for that as well. The URI you choose is not crucially important, we suggest you pick something under a domain you control to ensure uniqueness but it doesn't have to be a resolvable URI that responds if someone puts it in a browser. You can read the GeoServer documentation if you want to organise things further. However, note that, if you are going to supply simple or complex features through a WFS using standard application schemas such as GeoSciML this constrains how you set up your workspaces; see the relevant sections for more detail.

.. figure:: images/EditWS1.jpg
   :height: 451
   :width: 1036
   :alt: Edit a GeoServer Workspace

   Edit a GeoServer Workspace

Example Data
^^^^^^^^^^^^^

To help you set up your services we provide :ref:`service_provision_data_preparation_exampledata` that you can use to get some working services running. It enables you to get some initial experience setting up a service. Your own services may be set up by customising the examples or you may use them to get some understanding of what is involved when setting up your own service. The following sections on how to set up different types of service say which of the example data sets can be used to test setting up those services.

.. _service_provision_server_setup_geoserver_simple_wms:

Simple WMS
^^^^^^^^^^^

.. todo::

   Setting up the basic WMS copied mostly from existing cb, mentioning scanned image, shapefile, or single table/view db data source options. (Explicitly mention haven't looked at raster database?)

.. todo::

   Consider whether introducing GeoServer workspaces here is useful or overcomplicating...

   If not using workspaces change below image to global space screenshot and talk about enabling WMS there.

.. todo::

   Some of the data source and layer configuration is common to different service types WMS, WFS and WCS. This content originates when we were dealing with WMS only. Need to decide how to handle the common service bits and service specific bits. At the moment thinking of putting common and WMS specific bits here then in the later WFS and WCS sections referring back here for the common bits?

First you need to enable the WMS service. If you select :guilabel:`WMS` under the :guilabel:`Services` section of the left hand menu panel you will be presented with a screen like that below.

.. figure:: images/WMS-serviceProp1.jpg
   :height: 536
   :width: 1014
   :alt: Editing GeoServer WMS service properties (1)

   Editing GeoServer WMS service properties (1)

Check the :guilabel:`Enable WMS` box and also we recommend that you select the :guilabel:`strict CITE compliance` option. At the top of the page you can add various items of the service metadata required by the :ref:`service_provision_onegeology_profile` including :ref:`service_provision_onegeology_profile_service_title`, :ref:`service_provision_onegeology_profile_service_abstract`, :ref:`service_provision_onegeology_profile_fees`, :ref:`service_provision_onegeology_profile_access_constraints`, :ref:`service_provision_onegeology_profile_keywords` and :ref:`service_provision_onegeology_profile_online_resource`.

.. note:: The contents of Maintainer field aren't actually included in any part of the WMS GetCapabilities response

In the middle of the page you can configure a limited list of SRS for the service; it is recommended that you use this option otherwise you will get the full list of GeoServer supported coordinate reference systems (about 5800), which makes the **capabilities** document slow to parse.  Remember you must support EPSG:4326 for the portal.

.. figure:: images/WMS-serviceProp2.jpg
   :height: 489
   :width: 852
   :alt: Editing GeoServer WMS service properties (2)

   Editing GeoServer WMS service properties (2)

INSPIRE Extended Capabilities
"""""""""""""""""""""""""""""""

If you are providing an INSPIRE view service you will need to provide the extra INSPIRE mandated metadata in the WMS GetCapabilities response. GeoServer enables you to configure a scenario 1 style extended capabilities section. All INSPIRE specific requirements are optional for OneGeology use but will work as OneGeology services.

As described in the `plugin documentation <http://docs.geoserver.org/latest/en/user/extensions/inspire/using.html>`_ you should find a section in the WMS service settings of the administration interface where you can choose a language and enter a service metadata URL. For guidance on what to enter in these settings see the `Technical Guidance for the implementation of INSPIRE View Services <https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1>`_.

Check that the GetCapabilities responses contain your edited values.

.. note:: The plugin GUI only has two non-empty values for the Service Metadata Type: "Online ISO 19139 ServiceMetadata document" sets the MIME type to ``application/vnd.iso.19139+xml``, "CSW GetRecord by ID request" sets the MIME type to ``application/vnd.ogc.csw.GetRecordByIdResponse_xml``. If neither of these correspond to the actual MIME type of your metadata resource you could omit this element by choosing the blank option or work around it by manually editing the wfs.xml file inside the GeoServer data directory as documented in issue `GEOS-5157 <https://osgeo-org.atlassian.net/browse/GEOS-5157>`_ . As it isn't clear what a client would do with this information anyway, leaving it blank seems to be a good option.

Configuring a data store
"""""""""""""""""""""""""

The next step is to use the Stores menu option to set up any sources of data for our service.

On the left side of the GeoServer `Web administration interface <http://docs.geoserver.org/latest/en/user/webadmin/index.html>`_, under the `Data <http://docs.geoserver.org/latest/en/user/webadmin/index.html#data>`_ section, click :guilabel:`Stores`. This will bring you to the `Stores <http://docs.geoserver.org/latest/en/user/data/webadmin/stores.html>`_ page. Once there, click `Add New Store <http://docs.geoserver.org/latest/en/user/data/webadmin/stores.html#add-a-store>`_, then choose the type of data source you wish to configure from the list of options.

GeoServer can use a variety of data sources as the basis of a WMS including many of those listed in the GeoServer `Data management <http://docs.geoserver.org/latest/en/user/data/index.html>`_ section. In the :ref:`service_provision_data_preparation_exampledata` the image file, shapefile, GeoPackage, GeoTIFF and PostGIS database all are suitable. You can look up how to set each of these up from the `WorldImage <http://docs.geoserver.org/latest/en/user/data/raster/worldimage.html>`_, `Shapefile <http://docs.geoserver.org/latest/en/user/data/vector/shapefile.html>`_, `GeoPackage <https://docs.geoserver.org/latest/en/user/data/vector/geopkg.html>`_, `GeoTIFF <http://docs.geoserver.org/latest/en/user/data/raster/geotiff.html>`_ and `PostGIS <http://docs.geoserver.org/latest/en/user/data/database/postgis.html>`_ sections of the GeoServer documentation.

Having set up one or more data sources you will need to create WMS layers that display that data.

.. _gs_wms_add_layers:

Adding layers to a workspace
"""""""""""""""""""""""""""""

Having created a workspace and specified one or more data sources for your service, you will now associate this data with layers offered by the service in your workspace.

On the left side of the GeoServer `Web administration interface <http://docs.geoserver.org/latest/en/user/webadmin/index.html>`_, under the `Data <http://docs.geoserver.org/latest/en/user/webadmin/index.html#data>`_ section, click :guilabel:`Layers`. This will bring you to the `Layers <http://docs.geoserver.org/latest/en/user/data/webadmin/layers.html>`_ page. Once there, click `Add a new layer <http://docs.geoserver.org/latest/en/user/data/webadmin/layers.html#add-a-layer>`_, then choose the data source you wish to display as a layer from the drop down box.

Depending on the type of data source you have chosen there may be one or more resources listed that can be published as layers. For example, a shapefile data source would only have one resource listed but a database source could have several depending on the tables and views in the database. Select the resource for the data you want to display and click :guilabel:`Publish`.

.. note::

   If the resource has already been published the action will change to :guilabel:`Publish again`. You can create more than one layer from the same resource if you want to display it in different ways.

You will now be on the `Edit Layer <http://docs.geoserver.org/latest/en/user/data/webadmin/layers.html#data-webadmin-layers-edit-data>`_ page. This page has a large number of configuration options spread across different tabs. We will just describe a subset of them here.

The Data tab of the Edit Layer page
""""""""""""""""""""""""""""""""""""

The :guilabel:`Data` tab allows you to specify various items of layer metadata covered by the :ref:`service_provision_onegeology_profile` so it is very important to enter this information carefully for each layer in your web service. In particular you can configure the :ref:`Name and Title <service_provision_onegeology_profile_layer_names>`, :ref:`service_provision_onegeology_profile_layer_abstract`, :ref:`service_provision_onegeology_profile_layer_bbox`, :ref:`service_provision_onegeology_profile_layer_crs`, :ref:`service_provision_onegeology_profile_layer_keywords` and :ref:`service_provision_onegeology_profile_layer_metadata_url` or :ref:`service_provision_onegeology_profile_layer_data_url`.

GeoServer can compute the bounding box of your data from the data itself or you can enter the limits yourself manually if you think that is more appropriate for your dataset.

.. note::

   GeoServer may not be able to determine the coordinate reference system for some data sources. In this case you will need to enter the correct value in the :guilabel:`Declared SRS` box and choose :guilabel:`Force declared` for the :guilabel:`SRS handling` option. For example the image with world file from the example data has this problem as the coordinate reference system isn't included in the world file.

For further information on the other settings on this tab see the `GeoServer documentation <http://docs.geoserver.org/latest/en/user/data/webadmin/layers.html#edit-layer-data>`_.

The Publishing tab of the Edit Layer page
""""""""""""""""""""""""""""""""""""""""""

After populating the fields in the :guilabel:`Data` tab, click the :guilabel:`Publishing` tab.

This is where you will `select the styles <http://docs.geoserver.org/latest/en/user/data/webadmin/layers.html#wms-settings>`_ that can be used with your layer that will affect, for example, what colour different formations are shown in. This part of the interface only allows you to select the styles that can be used for your layer from a fixed list of available styles. If you want to set up your own styling GeoServer has `extensive customisable styling capabilities <http://docs.geoserver.org/latest/en/user/styling/index.html#styling>`_. This is a complex area so here we just point out that you can `upload an SLD file <http://docs.geoserver.org/latest/en/user/styling/webadmin/index.html#add-a-style>`_ to add to the list of available styles and you can `download some pre-made SLD files <https://github.com/OneGeology/styles>`_. These pre-made SLD files will colour your layers according to some standard colour schemes if your data includes appropriate age or lithology fields coded using CGI or INSPIRE standard vocabularies.

.. note:: If you have a pure image data source such as the one in the example data we recommend you use the default GeoServer :guilabel:`generic` style. Some styles can interfere with the image rendering (e.g. the :guilabel:`giant_polygon` style will result in a grey rectangle over your image area). You will probably also want to uncheck the :guilabel:`Queryable` Layer Settings checkbox as the information returned from image pixels in response to a GetFeatureInfo request is unlikely to be useful to clients.

Creating group layers
"""""""""""""""""""""""

In some situations it is desirable to create a group layer, for example you may want to do this to comply with INSPIRE layer naming regulations to create a layer called GE.GeologicUnit to group all of your layers that are spatial objects of type GeologicUnit.

On the left side of the GeoServer **Web Administration Interface**, under **Data**, click **Layer Groups**. This will bring up the **Layer Groups** page.  Click the add new layer group link to add a new group layer; this opens a New Layer Group page.

.. figure:: images/GS-LayerGroups.jpg
   :height: 296
   :width: 854
   :alt: Create or edit a Group layer

   Create or edit a Group layer

Add the name, title, and abstract.  If you are following INSPIRE regulations note the name and title must be EXACTLY as in the technical guidelines.  You may enter anything in the abstract, though we suggest you provide as much information about the grouping as possible.  Select the workspace you want to use and enter the layers that you want to group; the layers must already be available in the workspace.  The layers will display on top of each other so when adding layers you may wish to chose a layer order, for example if you want to group layers that are point features on top of polygon features.  Note the drawing order is the inverse of what will appear, that is the first drawn layer will appear at the bottom of the resultant map image.

Now select the default projection system for the group and then click the Generate Bounds button, this will generate a bounding box based on the extents of all your listed layers, though you may add the bounding box manually if you wish.  To ensure that a user can see which layers are included in the group, you will also need to choose the *Named Tree* Mode (and not use the default Single mode).

.. figure:: images/GS-LayerGroupsProp1.jpg
   :height: 742
   :width: 787
   :alt: Group layer properties

   Group layer properties

The output of a grouped layer is shown below (excerpt from a GetCapabilities response).

.. figure:: images/GS-LayerGroupsOut1.jpg
   :height: 572
   :width: 899
   :alt: Group layer output

   Group layer output

.. _service_provision_server_setup_geoserver_sld_wms:

SLD enabled WMS
^^^^^^^^^^^^^^^^

You don't have to configure anything special in GeoServer to have an SLD enabled WMS but for the purposes of having your layers work with the OneGeology Portal :ref:`use_portal_thematic_analysis` highlighting functionality your data will need to have the ``representativeAge_uri`` and ``representativeLithology_uri`` fields described in :ref:`service_provision_data_preparation_lite_geologicunitview` using appropriate CGI or INSPIRE vocabulary URIs.

If required you may disable this functionality in the Service metadata, by checking a box in the Dynamic styling section

.. _service_provision_server_setup_geoserver_simple_wfs:

Simple Feature WFS
^^^^^^^^^^^^^^^^^^^^

With GeoServer if you have configured a data store and layer as described in the :ref:`service_provision_server_setup_geoserver_simple_wms` section and the data store is of a suitable type (not, for example, a pure image format or raster format) then you will already have done all the substantive work to create a simple feature WFS serving features with the same name as your layer name and with property elements named according to the fields in the underlying data store. In the :ref:`service_provision_data_preparation_exampledata` the shapefile, GeoPackage and PostGIS database all are suitable. To complete setting up the WFS service metadata select :guilabel:`WFS` from under the :guilabel:`Services` section at the left of the `web administration interface <http://docs.geoserver.org/latest/en/user/webadmin/index.html>`_. The service metadata here is very similar to that described for setting up a :ref:`service_provision_server_setup_geoserver_simple_wms` so refer to that for what to enter. WFS specific settings are described in the `GeoServer documentation <http://docs.geoserver.org/latest/en/user/services/wfs/webadmin.html>`_.

.. note::

   Having WFS enabled will mean that users can download your data (for example, :ref:`use_qgis_simple_wfs`. If you **don't want this** then you should uncheck the :guilabel:`Enable WFS` checkbox. This can only be done at the global level or per workspace. You can't enable and disable WFS for specific layers.

If you want to promote interoperability while still having a simple data structure you could consider conforming to a standard schema such as GeoSciML-Lite or EarthResourceML-Lite and using standard IUGS-CGI or INSPIRE vocabularies for the applicable properties. Depending on your data source, it may be possible to produce features close to a simple feature application schema but there are a few issues that can make it difficult to produce schema valid output. You need to be able to make the names in the fields of your data source correspond to the names of properties in the output application schema. This will not be possible for a Shapefile where there is a 10 character limit on the length of field names and you may not be able to control the case of field names for some databases or you may not have access to alter your database or create appropriate views. Even when you can control the field names and case we have found problems where field names such as "name" and "description" will get assigned to gml:name properties when you might want them in the application schema namespace.

If you can't get schema valid features by manipulating your data source then you will need to :ref:`use the GeoServer Application Schema <service_provision_server_setup_geoserver_simple_app_schema>` extension. This is significantly more difficult to set up and the performance is also lower so you may wish to evaluate whether you can get *close enough* to the standard schema to be useful.

.. _service_provision_server_setup_geoserver_simple_app_schema:

Using application schemas extension
""""""""""""""""""""""""""""""""""""""

If you want your simple feature WFS to conform to a standard schema such as GeoSciML-Lite or EarthResourceML-Lite and your data store isn't sufficiently configurable then you will need to use the GeoServer Application Schema extension. The below documentation assumes you are using a Shapefile data store which will necessitate using this method because Shapefile field names are restricted to 10 characters in length whereas the Lite schemas have fields with longer names.

The Application Schema extension is not included by default so you need to follow the :ref:`service_provision_server_setup_geoserver_install_app_schema` instructions. Once the extension is installed, you will need to create a mapping file, and restart GeoServer to enable the new configuration.

Create mapping file
""""""""""""""""""""

The mapping file is an XML file that maps fields from the data source into the fields of the XML output schema. The example mapping file, below, uses field names in a shapefile that are the automatically truncated names generated by ESRI software mapping from the long field names to the valid Shapefile field names. If other field names are used in the shapefile (e.g. the recommended abbreviations in `Appendix K <http://onegeology.org/wmsCookbook/appendixK.html>`_), the strings in the sourceExpression/OCQL elements should be modified appropriately.

.. code-block:: xml

   <?xml version="1.0" encoding="UTF-8"?>
   <as:AppSchemaDataAccess
   xmlns:as="http://www.geotools.org/app-schema"
   xmlns:ogc="http://www.opengis.net/ogc"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://www.geotools.org/app-schema
   http://ogc.bgs.ac.uk/mapping/AppSchemaDataAccess.xsd">
   <namespaces>
     <Namespace>
       <prefix>gsmlp</prefix>
       <uri>http://xmlns.geosciml.org/geosciml-portrayal/2.0</uri>
     </Namespace>
     <Namespace>
       <prefix>gml</prefix>
       <uri>http://www.opengis.net/gml</uri>
     </Namespace>
   </namespaces>
   <sourceDataStores>
     <DataStore>
       <id>shapefile</id>
       <parameters>
         <Parameter>
           <name>url</name>
           <value>
             file:/home/geoserver/downloads/shapefiles/GeologicUnitView.shp
           </value>
         </Parameter>
         <Parameter>
           <name>memory mapped buffer</name>
           <value>false</value>
         </Parameter>
         <Parameter>
           <name>create spatial index</name>
           <value>true</value>
         </Parameter>
         <Parameter>
           <name>charset</name>
           <value>ISO-8859-1</value>
         </Parameter>
       </parameters>
     </DataStore>
   </sourceDataStores>
   <targetTypes>
     <FeatureType>
       <schemaUri>
         http://schemas.usgin.org/files/geologic-units/2.0/GeoSciML.xsd
       </schemaUri>
     </FeatureType>
   </targetTypes>
   <typeMappings>
     <FeatureTypeMapping>
       <sourceDataStore>shapefile</sourceDataStore>
       <sourceType>GeologicUnitView</sourceType>
       <targetElement>gsmlp:GeologicUnitView</targetElement>
       <attributeMappings>
         <AttributeMapping>
           <targetAttribute>gsmlp:GeologicUnitView</targetAttribute>
           <idExpression>
             <OCQL>getId()</OCQL>
           </idExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:identifier</targetAttribute>
           <sourceExpression>
             <OCQL>identifier</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:name</targetAttribute>
           <sourceExpression>
             <OCQL>name</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:description</targetAttribute>
           <sourceExpression>
             <OCQL>descriptio</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:geologicUnitType</targetAttribute>
           <sourceExpression>
             <OCQL>geologicUn</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:rank</targetAttribute>
           <sourceExpression>
             <OCQL>rank</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:lithology</targetAttribute>
           <sourceExpression>
             <OCQL>lithology</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:geologicHistory</targetAttribute>
           <sourceExpression>
             <OCQL>geologicHi</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:observationMethod</targetAttribute>
           <sourceExpression>
             <OCQL>observatio</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:positionalAccuracy</targetAttribute>
           <sourceExpression>
             <OCQL>positional</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:source</targetAttribute>
           <sourceExpression>
             <OCQL>source</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:geologicUnitType_uri</targetAttribute>
           <sourceExpression>
             <OCQL>geologic_1</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:representativeLithology_uri</targetAttribute>
           <sourceExpression>
             <OCQL>representa</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:representativeAge_uri</targetAttribute>
           <sourceExpression>
             <OCQL>represen_1</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:representativeOlderAge_uri</targetAttribute>
           <sourceExpression>
             <OCQL>represen_2</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:representativeYoungerAge_uri</targetAttribute>
           <sourceExpression>
             <OCQL>represen_3</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:specification_uri</targetAttribute>
           <sourceExpression>
             <OCQL>specificat</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:metadata_uri</targetAttribute>
           <sourceExpression>
             <OCQL>metadata_u</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:genericSymbolizer</targetAttribute>
           <sourceExpression>
             <OCQL>genericSym</OCQL>
           </sourceExpression>
         </AttributeMapping>
         <AttributeMapping>
           <targetAttribute>gsmlp:shape</targetAttribute>
           <sourceExpression>
             <OCQL>the_geom</OCQL>
           </sourceExpression>
         </AttributeMapping>
       </attributeMappings>
     </FeatureTypeMapping>
   </typeMappings>
   </as:AppSchemaDataAccess>

Create this mapping file with the prefix and namespace binding, the connection parameters (data source here is a shapefile), the online location of the schema (XSD), and the field mapping.

You can find more documentation on the mapping file at http://docs.geoserver.org/stable/en/user/data/app-schema/mapping-file.html and information on configuring different kinds of data store at  http://docs.geoserver.org/stable/en/user/data/app-schema/data-stores.html.

Place the file in the GeoServer file location of the datastore. This will be somewhere like :samp:`data/workspaces/{workspace}/{store}/` where `workspace` is the name of your workspace, and `store` is the name of your data store.

Edit datastore.xml file
""""""""""""""""""""""""

This file is located in the same Data Store directory. To enable application-schemas, this file must indicate that the shapefile is no longer used for field names, but the mapping file instead. Example datastore.xml, after editing:

.. code-block:: xml

   <dataStore>
     <id>DataStoreInfoImpl--49e58162:140a6f913de:-8000</id>
     <name>ShearDisplacementStructureView</name>
     <enabled>true</enabled>
     <workspace>
       <id>WorkspaceInfoImpl--1739a454:14097568969:-7fe9</id>
     </workspace>
     <connectionParameters>
       <entry key="dbtype">app-schema</entry>
       <entry key="url">
       file:workspaces/gsmlp/ShearDisplacementStructureView/ShearDisplacementStructureViewAZGS.xml
       </entry>
       <entry key="namespace">http://xmlns.geosciml.org/geosciml-portrayal/2.0</entry>
     </connectionParameters>
     <__default>false</__default>
   </dataStore>

.. _service_provision_server_setup_geoserver_complex_wfs:

Complex Feature WFS
^^^^^^^^^^^^^^^^^^^^

.. note:: This documentation describes setting up complex features by manually editing configuration files for the app-schema extension. Since it was written the `Hale Studio <https://www.wetransform.to/products/halestudio/>`_ graphical data transformation engine has been given the capability to create GeoServer app-schema configuration files. We recommend that you investigate this tool.

This section describes selected parts of the configuration files from the example set. This should give you a good overview of the configuration files needed and what the different parts do. They produce valid GeoSciML v3.2, v4.1 and INSPIRE Annex II Geology theme features and so, hopefully will provide a good starting point to adapt for your own services. However, the mapping for your service from your source data may require some features not used in the example. For these cases you should refer to the `Working with Application Schemas <http://docs.geoserver.org/stable/en/user/data/app-schema/index.html>`_ section of the GeoServer manual which contains comprehensive documentation on the different kinds of mapping from source to output XML that are possible. (It uses GeoSciML v2 based examples.)

Because a single ``gsmlb:GeologicUnit`` can be observed at several distinct locations on the Earth's surface, several ``gsmlb:MappedFeature`` features may point via their ``gsmlb:specification`` property to the same ``gsmlb:GeologicUnit``.

.. include:: WFS_output_abbr_1G.literal

Versions of the cookbook example set and configurations since 2016-08-17 also include ``gsmlb:MappedFeature`` features pointing to ``gsmlb:ShearDisplacementStructure`` (faults).

Obtaining example configuration
""""""""""""""""""""""""""""""""

Download the latest version of the example configuration files in data_625k.YYYY-MM-DD.zip from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/wfscookbook/>`_ and expand it to a spare location on your server. Copy the files from this expanded directory to the matching locations in your GeoServer data directory. The main configuration files are inside the ``workspaces`` directory. The contents of the ``demo`` directory are some example requests which are documented below. Overwrite any files that already exist, although there shouldn't be any in a fresh installation (apart from the containing directories). Note that the web interface does not yet support app-schema store for layer administration so you will have to edit these files directly when configuring your service.

Copy the latest version of one of the files app-schema.cgi.YYYY-MM-DD.properties or app-schema.inspire.YYYY-MM-DD.properties from `<ftp://ftp.bgs.ac.uk/pubload/OneGeology/wfscookbook/>`_ to ``WEB-INF/classes/app-schema.properties`` depending on whether you wish to use CGI or INSPIRE vocabularies for property values. (Don't forget to rename the file, removing the `.inspire` or `.cgi` and datestamp parts.)

Edit the database connection parameters appropriately for your installation of PostgreSQL. If you want to use a JNDI data connection configured in your servlet container then you will also need to edit the appropriate places in the ``datastore.xml`` files described in a subsequent section. So it will be easier for initial testing just to enter the host, database, user and password parameters.

Perform any configuration required by your servlet container, and then start the servlet.

One configuration item you may need to change is to increase the memory available for Java. The method depends on how you have installed GeoServer but if you get ``java.lang.OutOfMemoryError: Java heap space`` errors with the request below you will need to increase the memory with a directive such as ``-Xmx256M``. The details of tuning memory and other options of the Java Virtual Machine are complex and not dealt with in this cookbook. Some information is in the GeoServer User Manual under the `Running in a Production Environment <http://docs.geoserver.org/stable/en/user/production/index.html>`_ section.

If you have used the Windows Installer you can apply this by editing the file ``C:\Program Files (x86)\GeoServer 2.4.5\wrapper\wrapper.conf`` (The exact file location will depend on where you installed GeoServer and which version you are using.) Find the line ``wrapper.java.maxmemory=128`` and increase the value 128 (or whatever it happens to be) to something like 256.

If you are running in Apache Tomcat on Windows you can use the "Configure Tomcat" program that the Tomcat Windows installer provides. In the "Java" tab you can put a maximum memory value such as 256 (MB) in the Maximum Memory pool field.

* The first time GeoServer starts with the tutorial configuration, it will download all the schema (XSD) files it needs and store them in the ``app-schema-cache`` folder in the data directory. **You must be connected to the internet for this to work.**

Complex Feature Test requests
""""""""""""""""""""""""""""""

When GeoServer is running, test app-schema WFS in a web browser. You can query the feature types using these links. (Change ``localhost:8080`` in the examples below if you have deployed it at a different location.):

.. todo:: See if I can work out how to add longURL class to the below links. Otherwise need to re-add to html afterwards. rest class attribute lowerecases everything and doesn't get applied to link only.

* `http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:MappedFeature&count=25 <http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:MappedFeature&count=25>`_

* `http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:GeologicUnit&count=25 <http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:GeologicUnit&count=25>`_

From GeoServer 2.7 there is also support for WFS 2.0 paged queries such as below. The performance has been tuned so that you should be able to retrieve a small subset range of features anywhere within a large set of features matching a particular query.

* `http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:MappedFeature&count=10&startindex=9 <http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:MappedFeature&count=10&startindex=9>`_ - Get features 10 to 20 (startindex is 0 for first feature)

* `http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:MappedFeature&count=10&startindex=9999 <http://localhost:8080/geoserver/wfs?service=WFS&version=2.0.0&request=GetFeature&namespaces=xmlns(gsmlb,http%3A%2F%2Fwww.opengis.net%2Fgsml%2F4.1%2FGeoSciML-Basic)&typeNames=gsmlb:MappedFeature&count=10&startindex=9999>`_ - Get features 10000 to 10010

(At the time of writing the response is not fully WFS 2.0 compliant as the returned collection only returns a link to retrieve the previous set of results, not to the next set of results. However, a client that can formulate the paged queries should be able to work these out itself.)

You can also obtain WFS responses by using the `Demo requests <http://localhost:8080/geoserver/web/?wicket:bookmarkablePage=:org.geoserver.web.demo.DemoRequestsPage>`_ page in the GeoServer web interface. You can select some of the example age and lithology queries that are supplied with the example data directory from the request drop-down list or put ``http://localhost:8080/geoserver/ows`` into the service URL section and try pasting in your own queries. Some of the examples are reproduced below with their names as listed on the demo queries page.

.. figure:: images/geoserver_demo_requests.jpeg

A query for mapped features showing outcrops of geologic units of a particular age

``WFS_getFeature1GCgiAge.xml`` (Use ``WFS_getFeature1GInspireAge.xml`` if you have chosen the INSPIRE configuration.)

.. literalinclude:: WFS_getFeature1GCgiAge.xml
      :language: xml

A OneGeology query for mapped features showing outcrops of geological units with particular lithologies

``WFS_getFeature1GCgiLith.xml`` (Use ``WFS_getFeature1GInspireLith.xml`` if you have chosen the INSPIRE configuration.)

.. literalinclude:: WFS_getFeature1GCgiLith.xml
      :language: xml

A bounding box query to retrieve mapped features with shapes that overlap the specified bounding box

``WFS_getFeature1GBBOX.xml``

.. literalinclude:: WFS_getFeature1GBBOX.xml
   :language: xml

.. note:: App-schema cannot be configured using the web interface, you will need to edit the configuration files directly. You will see the configured workspaces and stores appear in the web interface but not the layers (features). The properties that can be edited in the web interface are very limited.

INSPIRE Extended Capabilities
"""""""""""""""""""""""""""""""

If you are providing an INSPIRE download service you will need to provide the extra INSPIRE mandated metadata in the WFS GetCapabilities response. GeoServer enables you to configure a scenario 1 style extended capabilities section. All INSPIRE specific requirements are optional for OneGeology use but will work as OneGeology services.

As described in the `plugin documentation <http://docs.geoserver.org/latest/en/user/extensions/inspire/using.html>`_ you should find a section in the WFS service settings of the administration interface where you can choose a language, enter a service metadata URL and type and add one or more spatial dataset identifiers. For guidance on what to enter in these settings see the `Technical Guidance for the implementation of INSPIRE Download Services <https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services>`_.

Check that the GetCapabilities responses contain your edited values.

.. note:: The plugin GUI only has two non-empty values for the Service Metadata Type: "Online ISO 19139 ServiceMetadata document" sets the MIME type to ``application/vnd.iso.19139+xml``, "CSW GetRecord by ID request" sets the MIME type to ``application/vnd.ogc.csw.GetRecordByIdResponse_xml``. If neither of these correspond to the actual MIME type of your metadata resource you could omit this element by choosing the blank option or work around it by manually editing the wfs.xml file inside the GeoServer data directory as documented in issue `GEOS-5157 <https://osgeo-org.atlassian.net/browse/GEOS-5157>`_ . As it isn't clear what a client would do with this information anyway, leaving it blank seems to be a good option.

INSPIRE Pre-defined Dataset Download
"""""""""""""""""""""""""""""""""""""

If you decide that you are going to provide an INSPIRE pre-defined dataset download service direct from your WFS rather than pre-generating the full datasets and just providing links to the download through ATOM then you can do this by creating a Stored Query such as the one below. The example data directory includes the CreateStoredQuery command in the Demos examples.

.. code-block:: xml

 <?xml version="1.0" encoding="UTF-8"?>
 <wfs:CreateStoredQuery
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation=
   "http://www.opengis.net/wfs/2.0
    http://schemas.opengis.net/wfs/2.0/wfs.xsd"
  xmlns:gsmlb="http://www.opengis.net/gsml/4.1/GeoSciML-Basic"
  xmlns:fes="http://www.opengis.org/fes/2.0"
  xmlns:wfs="http://www.opengis.net/wfs/2.0"
  xmlns:gml="http://www.opengis.net/gml/3.2"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  service="WFS"
  version="2.0.0">
  <wfs:StoredQueryDefinition
   id='http://inspire.ec.europa.eu/operation/download/GetSpatialDataSet'>
   <wfs:Parameter name='CRS' type='xsd:string'/>
   <wfs:Parameter name='DataSetIdCode' type='xsd:string'/>
   <wfs:Parameter name='DataSetIdNamespace' type='xsd:string'/>
   <wfs:Parameter name='Language' type='xsd:string'/>
   <wfs:Parameter name="count" type="xsd:integer"></wfs:Parameter>
   <wfs:QueryExpressionText
    returnFeatureTypes='gsmlb:MappedFeature'
    language='urn:ogc:def:queryLanguage:OGC-WFS::WFS_QueryExpression'
    isPrivate='false'>
    <wfs:Query typeNames='gsmlb:MappedFeature' srsName="${CRS}">
    </wfs:Query>
   </wfs:QueryExpressionText>
  </wfs:StoredQueryDefinition>
 </wfs:CreateStoredQuery>

This can then be invoked with a request like:

 `http://localhost:8080/geoserver/ows?service=WFS&version=2.0.0&request=GetFeature&storedquery_id=http://inspire.ec.europa.eu/operation/download/GetSpatialDataSet&DataSetIdCode=13603180&DataSetIdNamespace=http://data.bgs.ac.uk/id/dataHolding/&CRS=urn:ogc:def:crs:EPSG::4326&Language=eng&count=20& <http://localhost:8080/geoserver/ows?service=WFS&version=2.0.0&request=GetFeature&storedquery_id=http://inspire.ec.europa.eu/operation/download/GetSpatialDataSet&DataSetIdCode=13603180&DataSetIdNamespace=http://data.bgs.ac.uk/id/dataHolding/&CRS=urn:ogc:def:crs:EPSG::4326&Language=eng&count=20&>`_

app-schema.properties
"""""""""""""""""""""""

This file (in the ``WEB-INF/classes`` directory) is not strictly required but is very useful for storing certain configuration parameters that will be re-used in different parts of the other configuration files and for storing configuration parameters like database usernames and passwords outside of the GeoServer data directory so that the latter can be copied freely. The `Property Interpolation <http://docs.geoserver.org/stable/en/user/data/app-schema/property-interpolation.html>`_ section of the GeoServer manual contains more information on how properties can be set and used in other parts of the configuration files. In the reference configuration files this contains database connection parameters, some commonly used URI values and the setting to turn on `joining <http://docs.geoserver.org/stable/en/user/data/app-schema/joining.html>`_. In fact with current versions of GeoServer (certainly pre-dating v2.4.5) joining is turned on by default and is the recommended setting. There may be some limited situations as described in the `joining documentation <http://docs.geoserver.org/stable/en/user/data/app-schema/joining.html>`_, however, when you need to switch this off. The cookbook example also uses property interpolation to set database column name prefixes to choose whether to use columns that include CGI URI values or INSPIRE URI values.

Data directory
""""""""""""""""

The example configuration files can be copied into an existing GeoServer data directory so that you can get a working service to try out up and running as quickly as possible. The parts relevant for configuration of a complex feature WFS are contained in the ``workspaces`` directory described in the next section. Other parts of your service configuration like service metadata, security etc. can be set up using the web interface. Thus, when you come to set up your own service, you will probably start with the default GeoServer data directory, configure service metadata etc. in the web interface, and copy the complex feature configuration files from the reference ``data/workspaces`` directory to your own data directory for editing there.

Workspace layout
""""""""""""""""""

The files for configuring complex feature output are contained in the ``data/workspaces`` directory. Inside this directory there is a sub-directory for each namespace of features you will be serving and other namespaces that these features may use somewhere in their content. In the example this includes::

 workspaces
 ├── base
 ├── gco
 ├── ge
 ├── gmd
 ├── gml
 ├── gsml
 ├── gsmlb
 ├── gsmlem
 ├── gsmlga
 ├── gsmlgs
 ├── gsmlgu
 ├── gsmlu
 ├── swe
 └── xlink

These cover all the namespaces used by features in the example data set. If you use different application schemas or even additional GeoSciML packages such as boreholes, you will need to create similar directories for the namespaces used in those schemas. The ``gsmlb`` directory contains mappings to create MappedFeature, GeologicUnit and ShearDisplacementStructure features using the GeoSciML v4.1 Basic package. The ``ge`` and ``base`` directories contain mappings to create features conforming to the :ref:`inspire_geology_schema`. The other ``gsml*`` directories contain mappings using the older (and more complex) GeoSciML v3.2. The remaining directories are for namespaces that are imported by the others.

.. todo::

  I'm not quite sure where the prefix for the namespace is decided and what would happen if the schemas used more than one.
  I'm not sure if the examples without mapping files are only necessary if they are secondary namespaces and I'm not sure if the namespace.xml and workspace.xml files need to be defined for those with datastore and mapping files - are they redundant? They are only described in the documentation for secondary namespaces. They are created for simple feature stores in standard geoserver; are they used by UI?
  If namespace.xml and workspace.xml are used by all workspaces then describe them next as needing setting up for each namespace. Can these be set in the UI?
  Think about making example set have all namespaces used by GeoSciML even if not in features in example set as this will give a headstart for people creating them.

The example configuration defines 2 feature types to be served by the WFS. Their configurations are stored in data store sub-directories of the appropriate namespace directory and are named according to the pattern ``prefix_Feature`` for a feature ``prefix::Feature``::

 workspaces
 ├── base
 ├── gco
 ├── ge
 ├── gmd
 ├── gml
 ├── gsml
 ├── gsmlb
 │   └── gsmlb_GeologicUnit
 │   └── gsmlb_MappedFeature
 │   └── gsmlb_ShearDisplacementStructure
 ├── gsmlem
 ├── gsmlga
 ├── gsmlgs
 ├── gsmlgu
 ├── gsmlu
 ├── swe
 └── xlink


Each of the data store directories contains files similar to the following example for ``gsmlb::MappedFeature``::

 gsmlb_MappedFeature
 ├── AppSchemaDataAccess.xsd
 ├── datastore.xml
 ├── gsmlb_MappedFeature
 │   └── featuretype.xml
 └── gsmlb_MappedFeature.xml

The ``AppSchemaDataAccess.xsd`` file isn't used for the configuration, it is just provided as a convenience when you are editing a mapping file such as ``gsmlb_MappedFeature.xml`` to allow a validating XML editor to give you hints that you have the structure of the file correct. The following sections will describe the ``datastore.xml`` file which creates an application schema data store and specifies the mapping file described in the section after which contains the substantive portion of the configuration mapping source data fields to output in the complex feature types.

.. todo::

  There isn't a description of featuretype.xml, does this need creating?, what is it used by and is it configured by UI?

datastore.xml
""""""""""""""

Each data store configuration file ``datastore.xml`` specifies the location of a mapping file and triggers its loading as an app-schema data source. This file should not be confused with the source data store, which is specified inside the mapping file.

For ``gsmlb:MappedFeature`` the file is ``workspaces/gsmlb/gsmlb_MappedFeature/datastore.xml``

.. include:: datastore.literal

.. note:: Ensure that there is no whitespace inside an ``entry`` element.

For other feature types the pattern is the same where you replace the names and ids appropriately and change the namespace if necessary. The url entry is a file: URI pointing to the location of the mapping file relative to the GeoServer data directory. The dbtype entry will always be app-schema to define complex feature types.

Mapping files
"""""""""""""""""

Configuration of app-schema feature types is performed in mapping files e.g.

* ``workspaces/gsmlb/gsmlb_GeologicUnit/gsmlb_GeologicUnit.xml``

* ``workspaces/gsmlb/gsmlb_MappedFeature/gsmlb_MappedFeature.xml``

* ``workspaces/gsmlb/gsmlb_ShearDisplacementStructure/gsmlb_ShearDisplacementStructure.xml``


Namespaces
""""""""""""""

Each mapping file contains namespace prefix definitions. The below extract is from ``gsmlb_MappedFeature.xml``

.. code-block:: xml

 <namespaces>
  <Namespace>
   <prefix>gml</prefix><uri>http://www.opengis.net/gml/3.2</uri>
  </Namespace>
  <Namespace>
   <prefix>gsmlb</prefix><uri>http://www.opengis.net/gsml/4.1/GeoSciML-Basic</uri>
  </Namespace>
  <Namespace>
   <prefix>swe</prefix><uri>http://www.opengis.net/swe/2.0</uri>
  </Namespace>
  <Namespace>
   <prefix>xlink</prefix><uri>http://www.w3.org/1999/xlink</uri>
  </Namespace>
  <Namespace>
   <prefix>xsi</prefix><uri>http://www.w3.org/2001/XMLSchema-instance</uri>
  </Namespace>
 </namespaces>

Only those namespace prefixes used in the mapping file need to be declared although you may find it easier just to put all the namespaces used by your target schema in all of them.

Source data store
""""""""""""""""""

The data for this tutorial is contained in the PostGIS database set up in the previous section.

For this example, each feature type uses an identical source data store configuration. The ``Parameter`` elements contain values for various database connection parameters. Here we are using `property interpolation <http://docs.geoserver.org/stable/en/user/data/app-schema/property-interpolation.html>`_ so that these don't have to get changed in each mapping file if they change and so that the configuration files can be shared without exposing password information. The values of the interpolated variables (which have the form ``${name}``) should be defined in the ``WEB-INF/classes/app-schema.properties`` file. An example which you can use as a template to fill in with your own values is at ftp://ftp.bgs.ac.uk/pubload/OneGeology/wfscookbook/app-schema.inspire.YYYY-MM-DD.properties. (Updated versions will have different dates instead of YYYY-MM-DD. The example service can be configured to use INSPIRE vocabulary values or IUGS-CGI vocabulary values by setting appropriate variables in this file.)

.. code-block:: xml

 <sourceDataStores>
  <DataStore>
   <id>datastore</id>
   <parameters>
    <Parameter>
     <name>dbtype</name><value>${cgi.dbtype}</value>
    </Parameter>
    <!--
    <Parameter>
     <name>jndiReferenceName</name><value>${cgi.jndi}</value>
    </Parameter>
    -->
    <Parameter>
     <name>host</name><value>${cgi.host}</value>
    </Parameter>
    <Parameter>
     <name>port</name><value>${cgi.port}</value>
    </Parameter>
    <Parameter>
     <name>database</name><value>${cgi.database}</value>
    </Parameter>
    <Parameter>
     <name>user</name><value>${cgi.user}</value>
    </Parameter>
    <Parameter>
     <name>passwd</name><value>${cgi.passwd}</value>
    </Parameter>
    <Parameter>
     <name>schema</name><value>${cgi.schema}</value>
    </Parameter>
    <Parameter>
     <name>Expose primary keys</name><value>true</value>
    </Parameter>
   </parameters>
  </DataStore>
 </sourceDataStores>

See `http://docs.geoserver.org/stable/en/user/data/app-schema/data-stores.html <http://docs.geoserver.org/stable/en/user/data/app-schema/data-stores.html>`_ for a description of how to use other types of data store.


Target types
"""""""""""""

The XML Schemas which are required to define a feature type and its properties are specified in the ``targetTypes`` section. The type of the output feature is defined in ``targetElement`` in the ``typeMapping`` section. The below example is from ``gsmlb_MappedFeature.xml``

.. code-block:: xml

 <targetTypes>
  <FeatureType>
   <schemaUri>
    http://schemas.opengis.net/gsml/4.1/geoSciMLBasic.xsd
   </schemaUri>
  </FeatureType>
 </targetTypes>

In this case the schema is published, but because the OASIS XML Catalog is used for schema resolution, a private or modified schema in the catalog can be used if desired.

Mappings
"""""""""

The ``typeMappings`` element begins with configuration elements. From ``gsmlb_MappedFeature.xml``

.. code-block:: xml

 <typeMappings>
  <FeatureTypeMapping>
   <sourceDataStore>datastore</sourceDataStore>
   <sourceType>mapped_feature_gu</sourceType>
   <targetElement>gsmlb:MappedFeature</targetElement>

* The mapping starts with ``sourceDataStore``, which gives the arbitrary identifier used above to name the source of the input data in the ``sourceDataStores`` section.

* ``sourceType`` gives the name of the source simple feature type. In this case it is the simple feature type ``mapped_feature_gu``, sourced from the table of the same name in the PostGIS database set up in the previous chapter. In versions of the cookbook example configuration since 2016-08-16 this has been changed to point to the view ``mapped_feature_all`` which includes both outcrop polygons of geologic units and linear fault traces.

* When working with databases ``sourceType`` is the name of a table or view. Database identifiers must be lowercase for PostGIS or uppercase for Oracle Spatial.

* ``targetElement`` is the name of the output complex feature type.

gml:id mapping
"""""""""""""""

The first mapping sets the ``gml:id`` to be the feature id specified in the source simple feature property which comes from the database column of the same name.

.. code-block:: xml

 <AttributeMapping>
  <targetAttribute>gsmlb:MappedFeature</targetAttribute>
  <idExpression><OCQL>uuid</OCQL></idExpression>
 </AttributeMapping>


* ``targetAttribute`` is the XPath to the element for which the mapping applies, in this case, the top-level feature type.

* ``idExpression`` is a special form that can only be used to set the ``gml:id`` on a feature. In the tutorial database we have a column ``uuid`` suitable for use as a ``gml:id`` attribute value. If your database doesn't have such a column you may be able to use the special function ``getId()`` here instead. This will synthesise an id from the table or view name, a dot ".", and the primary key of the table. If this is not desirable, any other field or CQL expression can be used, if it evaluates to an `NCName <http://www.w3.org/TR/1999/REC-xml-names-19990114/#NT-NCName>`_. In versions of the cookbook example configuration since 2016-08-16 this uses the column ``mf_id``.

The above would generate output like

.. code-block:: xml

 <gsmlb:MappedFeature gml:id="bgsn_digmap20111213000014089_625k">
 ...


inspireId mapping
""""""""""""""""""""

A common property that many INSPIRE themes will have is an inspireId. An example mapping for this property is contained in the ``workspaces/ge/ge_GeologicUnit/ge_GeologicUnit.xml`` file. The relevant section is reproduced below

.. code-block:: xml

   <AttributeMapping>
    <targetAttribute>ge:inspireId/base:Identifier/base:localId</targetAttribute>
    <sourceExpression><OCQL>bgs_namedrockunit_uri</OCQL></sourceExpression>
   </AttributeMapping>
   <AttributeMapping>
    <targetAttribute>ge:inspireId/base:Identifier/base:namespace</targetAttribute>
    <sourceExpression><OCQL>'http://data.bgs.ac.uk/'</OCQL></sourceExpression>
   </AttributeMapping>

Ordinary mapping
""""""""""""""""""

Most mappings consist of a target and source. Here is a simple property with a text value from ``gsmlb_GeologicUnit.xml``

.. code-block:: xml

 <AttributeMapping>
  <targetAttribute>gml:description</targetAttribute>
  <sourceExpression>
   <OCQL>description</OCQL>
  </sourceExpression>
 </AttributeMapping>

* In this case, the value of ``gml:description`` is just the value of the ``description`` column in the ``geol_unit`` table.

* For a database, the field name is the name of the column (the table/view is set in ``sourceType`` above). Database identifiers must be lowercase for PostGIS or uppercase for Oracle Spatial.

* CQL expressions can be used to calculate content. Use caution because queries on CQL-calculated values prevent the construction of efficient SQL queries.

* Source expressions can be CQL literals, which are single-quoted.

The above would generate output like

.. code-block:: xml

 <gml:description>STRATHCLYDE GROUP - SEDIMENTARY ROCK CYCLES,
  STRATHCLYDE GROUP TYPE</gml:description>

Client properties
""""""""""""""""""

In addition to the element content, a mapping can set values of XML attributes on property elements. These are called "client properties" in GeoServer terminology. Here is one from ``gsmlb_CompositionPart.xml``

.. code-block:: xml

 <AttributeMapping>
  <targetAttribute>gsmlb:material/gsmlb:RockMaterial/gsmlb:lithology</targetAttribute>
  <ClientProperty><name>xlink:href</name><value>${dic.col.prefix}lithology_uri</value></ClientProperty>
  <ClientProperty><name>xlink:title</name><value>${dic.col.prefix}lithology_label</value></ClientProperty>
 </AttributeMapping>

* This mapping leaves the content of the ``gsmlb:lithology`` element empty but sets an ``xlink:href`` attribute to the value of the ``${dic.col.prefix}lithology_uri`` column and an ``xlink:title`` attribute to the value of the ``${dic.col.prefix}lithology_label`` column. Note that in this case the property attributes being set are nested two levels below the parent ``gsmlb:CompositionPart``. Note also that we are using property interpolation here to select the exact name of the database column to be used based on a variable set in the app-schema.properties file. This was useful so the example dataset can be configured to use vocabularies from different authorities but is less likely to be useful for your services.

* As can be seen from this example, multiple ``ClientProperty`` mappings can be set.

This would generate output like

.. code-block:: xml

   <gsmlb:lithology
    xlink:href=
     "http://resource.geosciml.org/classifier/cgi/lithology/clastic_mudstone"
    xlink:title="Mudstone"/>

Feature chaining
"""""""""""""""""

In feature chaining, one feature type is used as a property of an enclosing feature type, by value or by reference. The following examples show the parts of the ``gsmlb_MappedFeature.xml`` and ``gsmlb_GeologicUnit.xml`` mapping files that put the gsmlb:GeologicUnit elements inside the gsmlb:specification properties of gsmlb:MappedFeature elements. In versions of the cookbook example since 2016-08-16 the below mapping has been commented out to be replaced by a more complex example described in the next section on Polymorphism.

In ``gsmlb_MappedFeature.xml``

.. code-block:: xml

 <AttributeMapping>
  <targetAttribute>gsmlb:specification</targetAttribute>
  <sourceExpression>
   <OCQL>lex_rcs</OCQL>
   <linkElement>gsmlb:GeologicUnit</linkElement>
   <linkField>FEATURE_LINK</linkField>
  </sourceExpression>
 </AttributeMapping>

In ``gsmlb_GeologicUnit.xml``

.. code-block:: xml

 <AttributeMapping>
  <targetAttribute>FEATURE_LINK</targetAttribute>
  <sourceExpression><OCQL>lex_rcs</OCQL></sourceExpression>
 </AttributeMapping>

* In this case from the mapping for ``gsmlb:MappedFeature``, we specify a mapping for its ``gsmlb:specification`` property.

* The ``linkElement`` specifies which feature (or other complex type) should be used as the value of the property.

* The ``link_specification`` field of the source ``gsmlb_MappedFeature`` simple feature is use as the "foreign key", which maps to the special ``FEATURE_LINK`` field in each ``gsmlb:GeologicUnit``.

* The mapping of the special ``FEATURE_LINK`` attribute in ``gsmlb_GeologicUnit.xml`` to the foreign key field of the underlying table means that every ``gsmlb:GeologicUnit`` with ``lex_rcs`` equal to the ``lex_rcs`` of the ``gsmlb:MappedFeature`` under construction is included as a ``gsmlb:specification`` property of the ``gsmlb:MappedFeature`` (by value).

Feature chaining has been used to construct the property ``gsmlb:specification`` of ``gsmlb:MappedFeature``. This property is a ``gsmlb:GeologicUnit``. The WFS response for ``gsmlb:MappedFeature`` combines the output of both feature types into a single response. The first ``gsmlb:MappedFeature`` has a ``gsmlb:specification`` property value of the ``gsmlb:GeologicUnit`` with the same ``lex_rcs`` code. The next time a mapped feature with the same ``lex_rcs`` code appears, rather than including the whole geologic unit inline again the property has an xlink:href attribute pointing to the first occurrence. The relationships between the feature instances are data driven.

Polymorphism
""""""""""""""
In versions of the cookbook example since 2016-08-16 the above mapping with ``gsmlb:MappedFeature``'s pointing to ``gsmlb:GeologicUnit``'s has been extended so that ``gsmlb:MappedFeature/gsmlb:specification`` can contain or point to either a ``gsmlb:GeologicUnit`` as above or a ``gsmlb:ShearDisplacementStructure`` (representing a fault). Setting up an attribute to have different forms like this is described in the `Polymorphism <http://docs.geoserver.org/stable/en/user/data/app-schema/polymorphism.html>`_ section of the GeoServer manual. The cookbook example implements this by having a column ``feature_type`` in the ``mapped_feature_all`` view which indicates whether a row is related to an entry in the ``geol_unit`` table (for ``gsmlb:GeologicUnit`` features) or the ``fault`` table (for ``gsmlb:ShearDisplacementStructure`` features). It then uses the Recode function to switch between which feature type is the ``linkElement`` based on the value of this column.

.. code-block:: xml

   <AttributeMapping>
    <targetAttribute>gsml:specification</targetAttribute>
    <sourceExpression>
     <OCQL>specification_id</OCQL>
     <linkElement>Recode(feature_type, 'gu', 'gsmlb:GeologicUnit', 'sds', 'gsmlb:ShearDisplacementStructure')</linkElement>
     <linkField>FEATURE_LINK</linkField>
    </sourceExpression>
   </AttributeMapping>

.. _inspire_geology_schema:

INSPIRE Geology Theme Schema
"""""""""""""""""""""""""""""

If you want to produce a service with data conforming to the INSPIRE Geology theme schema you can examine the configuration files in the ``ge`` and ``base`` directories which were created by copying those in the ``gsmlb`` directory and changing the namespaces and schema locations. The only parts which needed adding which couldn't be adapted from the GeoSciML configuration files were those adding mappings for inspireId properties. It should be fairly simple for you to copy your own mapping files from a GeoSciML configuration to produce an INSPIRE Geology theme schema configuration following a similar process.

.. _service_provision_server_setup_geoserver_wcs:

WCS
^^^^^

Exemplar data used in this cookbook
""""""""""""""""""""""""""""""""""""""

For the purposes of this cookbook we will use the Bathymetry Multi-colour 3-Band GeoTiffs supplied by the EMODnet project and available for download from the “Portal for Bathymetry” (http://portal.emodnet-bathymetry.eu/)

Metadata to be used in configuring your service and coverages (layers)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Your coverage service and coverage (layer) metadata should follow the :ref:`service_provision_onegeology_profile`.

Whilst GeoServer can use a number of data formats as inputs for its WCS services at present you must use GeoTIFFs if you want to provide output in image/png or image/jpeg formats, such that the coverages can be viewed within the portal.

.. todo::

   Same question as WMS section about whether to describe individual workspace set up or just deal with single global service URL. There is a lot of overlap between this WCS content on setting up data stores, service etc. and the WMS section so think about whether can be made common section or needs repeating for each. Just pointing to GeoServer documentation sections might simplify it enough to make similarities clearer.

Stores
""""""""

The next step is to use the ‘Stores’ menu option to set up a Raster data source for each of our exemplar (EMODnet) GeoTIFFs.    To do this, go to the left hand menu ‘Stores’ option, and click the  ‘Add new store’ link.  Under the Raster Data Sources heading select ‘GeoTIFF - Tagged Image File Format with Geographic information’.  Select the newly created Workspace from the drop down list.

.. figure:: images/wcs_fig04.jpg

Add a Data Source name (recommended that you omit spaces here) which will become part of the identifier for your data in the service.   Use the Connection Parameters URL to link to the actual data.

In this example we have our EMODnet data on our server at::

   C:\1Gdata\Emodnet

The file protocol URL to access this path is::

   file://C:\1Gdata\Emodnet

So in this case to access our Tiff the URL is::

   file://C:\1Gdata\Emodnet\Aegean Sea - Levantine Sea [Multi Colour].tif

Remember to enable the data source by ticking the box.

When you save your store you should get an option to Publish your data source as a Layer.

.. figure:: images/wcs_fig05.jpg

You will need to repeat these steps to create a data source for all of the GeoTIFFs that you wish to make available in your service.

Layers
"""""""""""

If you didn’t Publish the data as part of the data source configuration, the final step is to create a layer using your data sources.  Select the Layers option in the left hand menu, then find the Workspace:Datasource name combination required from the drop down list.

.. figure:: images/wcs_fig06.jpg

That’s essentially it, as the information that you can add (as opposed to the information that is auto-populated) in the layer properties is not used in either the GetCapabilities or the DescribeCoverage response.

Service level metadata
"""""""""""""""""""""""

To configure service level metadata, choose the WCS option in the Services section of the Left hand menu.  Then select your workspace from the dropdown list.

.. figure:: images/wcs_fig07.jpg

To get your service to be available you must tick the Enable WCS option box.

To conform to the OneGeology WCS profile you must also tick the Strict CITE compliance option box.

Online Resource here is a link to your (or any other) web site (not your service), that provides information about your data.

Title must follow the WMS naming conventions

Abstract covers the service in general.  You may also add information about the individual layers.

Fees and Access Constraints for your service, if you have no constraints then you MUST explicitly state this using ‘none’.

Keywords can include a language code and reference a vocabulary.

For example in the example shown below we have a keyword only “OneGeology”, a keyword with vocabulary “infoCoverageAccessService [ISO]”, and a keyword with vocabulary and language code “marine geology (en) [GEMET]” .  The new keyword shown in the form will become (when the Add Keyword button is clicked) “Meeresgeologie (de) [GEMET]”

The GEMET keywords come from http://www.eionet.europa.eu/gemet/en/themes/

.. figure:: images/wcs_fig08.jpg

Finally you need to configure a limited list of projection systems that your service will provide, REMEMBER the service must support EPSG:4326.

.. figure:: images/wcs_fig09.jpg

The above list gives the following in the GetCapabilities response::

   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/27700</wcscrs:crsSupported>
   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/3034</wcscrs:crsSupported>
   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/3413</wcscrs:crsSupported>
   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/3857</wcscrs:crsSupported>
   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/4258</wcscrs:crsSupported>
   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/4326</wcscrs:crsSupported>
   <wcscrs:crsSupported>http://www.opengis.net/def/crs/EPSG/0/404000</wcscrs:crsSupported>

INSPIRE Extended Capabilities
""""""""""""""""""""""""""""""""

If you are providing an INSPIRE download service you will need to provide the extra INSPIRE mandated metadata in the WCS GetCapabilities response. GeoServer enables you to configure a scenario 1 style extended capabilities section. All INSPIRE specific requirements are optional for OneGeology use but will work as OneGeology services.

As described in the `plugin documentation <http://docs.geoserver.org/latest/en/user/extensions/inspire/using.html>`_ you should find a section in the WCS service settings of the administration interface where you can choose a language, enter a service metadata URL and type and add one or more spatial dataset identifiers. For guidance on what to enter in these settings see the `Technical Guidance for the implementation of INSPIRE Download Services using Web Coverage Services (WCS) <https://inspire.ec.europa.eu/id/document/tg/download-wcs>`_.

Check that the GetCapabilities responses contain your edited values.

.. note:: The plugin GUI only has two non-empty values for the Service Metadata Type: "Online ISO 19139 ServiceMetadata document" sets the MIME type to ``application/vnd.iso.19139+xml``, "CSW GetRecord by ID request" sets the MIME type to ``application/vnd.ogc.csw.GetRecordByIdResponse_xml``. If neither of these correspond to the actual MIME type of your metadata resource you could omit this element by choosing the blank option or work around it by manually editing the wfs.xml file inside the GeoServer data directory as documented in issue `GEOS-5157 <https://osgeo-org.atlassian.net/browse/GEOS-5157>`_ . As it isn't clear what a client would do with this information anyway, leaving it blank seems to be a good option.

Troubleshooting
"""""""""""""""""

.. figure:: images/wcs_fig10.jpg

If you start getting error messages when using GeoServer, you will probably need to increase the JAVA permgen space.  This can occur when you are serving lots of raster data. See http://osgeo-org.1560.x6.nabble.com/Session-times-out-when-adding-new-stores-or-layers-td4910354.html

GeoServer troubleshooting
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. todo::

   Currently this just has content from old WMS cookbook. Should review issues and make an up-to-date list

Q: I made a change in the database on my server and now the service is not working
   A: Try clearing the cache and reloading GeoServer on the Server Status page. If that doesn’t work, try hard restarting the service through Apache Tomcat.
Q: Can I use a replicated Feature Class to create a service on GeoServer?
   A: No.
Q: I set up my services under three separate workspaces. When I connected to the WMS in ArcCatalog, all the layers appeared as one bundle. Is there a way to separate them out so I can add them individually?
   A: Yes.

Though setting up your services under different workspaces seems to imply that they can be accessed as discrete services, GeoServer defaults to providing one capabilities document containing the information for all of the services set up on your instance of GeoServer. To access workspaces individually, you will need customize your Get request to specify the desired workspace.

For example: a Geological Survey might run three services on GeoServer:

* GeologicUnitView
* FaultView
* ContactView

To perform a GetCapabilities request for GeologicUnitView, your GetCapabilities request will appear as follows:

\http://services.a.survey.gov/geoserver/GeologicUnitView/ows?service=WMS&request=GetCapabilities&

This URL opens the WMS **capabilities document** for the GeologicUnitView workspace only. A generic form of the service endpoint for the request is as follows:

\http://[host server]/geoserver/[Workspace Name]/ows?

Q: Is it possible to configure GeoServer so that I do not need to use PostGIS?
   A: Try installing the ArcSDE plug-in for GeoServer. To do this, you will need to download the extension from GeoServer’s website. Make sure to match the versions of the extension and GeoServer.  If you can get it to work, you should be able to connect to other SDE databases running on, for instance, MS SQL or Oracle.
Q: All of my data are in Shapefiles. Can I deploy a shapefile as a GeoSciML-Lite service?
   A: The problem you will run into is the truncation of field names that occurs in shapefiles. Ideally you will have a full version of the data in PostGIS. As mentioned in the above document, to be compliant with GeoSciML-Lite, you will need to make sure there is no truncation in field names; they must be an exact match for the GeoSciML-Lite schema. To map table fields to XML elements with different names you will have to use the `Application Schema extension <http://docs.geoserver.org/stable/en/user/data/app-schema/index.html>`_ for GeoServer.

Using MapServer
----------------

Software Installation
^^^^^^^^^^^^^^^^^^^^^^

`MapServer <http://mapserver.org/>`_ can be used to provide a number of OGC Web Services (OWS) types, such as the Web Map Service (WMS), Web Feature Service (WFS) and Web Coverage Service (WCS) standards which are the current focus of interest for the OneGeology portal.  In the following sections we run through how to configure MapServer so it can provide any one of these three service types.

MapServer will work both on Windows and Linux operating systems (both 32-bit and 64-bit), and with a web server of your choosing, the permutations are many and we can not cover all of them, below we take you through some common installations, using Apache HTTP as the web server.

The simplest way to set up MapServer on a Windows server is to use the MapServer for Windows (MS4W) installer provided by Gateway Geomatics, this installs a 32-bit version of the Apache HTTP web server and the 32-bit version of MapServer as well as some demo applications.  For those wishing to use a 64-bit version of Apache HTTP web server, we recommend Apache Lounge and GISInternals.  For installation of MapServer on Linux, (with Apache HTTP web server) we recommend Ubuntu and the Personal Package Archives.

Installing MS4W
^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Obtain the OneGeology template application in the 20Mbytes approx. sized 1G\_WMS-exemplar-data-MS6-update.zip file from the `BGS FTP website <ftp://ftp.bgs.ac.uk/pubload/OneGeology/>`_.

If you are using a web browser clicking on this URL may take you directly to it without requesting a password.  If you prefer to use the older DOS prompt style FTP user interface then as normal with such anonymous ftp services enter anonymous if prompted for a userid and type your email address as the password to allow the FTP manager to monitor who is using the service.

Unzip the OneGeology template application to the same drive and directory level as the MS4W location resulting from the MapServer installation e.g. if you installed MS4W on C:\\MS4W then point the unzip extract to C:.  It should create a number of files inside the *ms4w* directory.  The main part of the two example applications are inside a BGS\_Bedrock\_and\_Superficial\_Geology directory (for the shapefile based example) and BGS\_Bedrock\_Raster\_Map directory (for the image file based example) which will be created inside ms4w\\apps\\cookbookExemplars.

The MapServer executables for the two applications are found in similarly named folders in ms4w\\apps\\exemplars, and the web server configuration files are found in ms4w\\httpd.d

After unzipping the exemplar files, restart your web service.  Now when you browse to localhost/index.html you will get links to the two exemplar services.


Configuring your own services using the exemplars as examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

C:\\ms4w\\Apache\\cgi-bin\\
"""""""""""""""""""""""""""

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
"""""""""""""""""""""""""""""""""

Inside the \\ms4w\\apps\\cookbookExemplars folder you will find two folders: "BGS\_Bedrock\_and\_Superficial\_Geology" and "BGS\_Bedrock\_Raster\_Map".  These folders contain the exemplar data, and map configuration files.

We will assume you are basing your service on the BGS\_Bedrock\_and\_Superficial\_Geology example; substitute with BGS\_Bedrock\_Raster\_Map if that is closer to your requirements.  When you have decided which exemplar service is most suitable for your needs, you should copy that exemplar folder to a new folder that will be your new service.

Note the names of these folders do not have to match the names of the service, but you would be advised to ensure that the folder name gives some hint as to its contents and purpose.  For example we call one of our exemplar folders "BGS\_Bedrock\_Raster\_Map" to indicate that this service application holds a raster map as datasource, rather than a shapefile.

Make more copies with appropriate names if you are also making multiple language services.

Inside this folder there is a wwwroot\\index.html file.  This has some example queries which will enable you to test your service when you have set it up.  For these to work for your new service you will need to edit the file and change all occurrences of the string "BGS\_Bedrock\_and\_Superficial\_Geology" with the name you have created for your service.

C:\\ms4w\\httpd.d\\
"""""""""""""""""""

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
""""""""""""""""""""""""""

Now you should edit the index.html file in the Apache web root \\ms4w\\Apache\\htdocs\\ and add a link to your new service.  Note, the link you use is the value of the Alias (line one of the httpd conf file).

Again make more copies if making multiple language services.


Installing and configuring Apache HTTP web server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

MS4W, as described above, installs both MapServer and the Apache HTTP webserver software.  Other installations of MapServer require configuring of the web server as a separate process.  This section takes you through installing alternate Apache HTTP webserver software, and through the additional configuration you will need to do to create a OneGeology service that follows the same pattern as above.


64-bit Apache HTTP server
""""""""""""""""""""""""""""

if tyou want to run a 64-bit version of MapServer on Windows such as provided by GISInternals, you will also need to in install a 64-bit version of Apache.

If instead you want to use the latest stable release of Apache-HTTP, that is the version 2.4.n releases (latest is currently 2.4.29), you must instead go to the Apache Lounge site: `http://www.apachelounge.com/download/ <http://www.apachelounge.com/download/>`_. There are several options here both in server architecture (32 bit and 64 bit), and server functionality, for you to choose from to fit your needs.

For the purposes of this example we have selected a 64-bit package from Apache Lounge and installed it to our C:\\ drive as C:\\Apache24\\.


httpd.d configuration files
"""""""""""""""""""""""""""

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
"""""""""""

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
""""""""""""""""""""""""""""""""

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The most recent versions of the GISInternals GDAL and MapServer packages are available online at: `http://www.gisinternals.com <http://www.gisinternals.com>`_

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
^^^^

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
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We shall now configure the two BGS exemplar services (a shapefile version and a raster version) available from the BGS FTP server.

.. code-block:: sh

  #cd /usr/local/src
  #wget ftp://ftp.bgs.ac.uk/pubload/OneGeology/1G_WMS-exemplar-data-MS6-update.zip
  #unzip 1G_WMS-exemplar-data-MS6-update.zip

We now need to move the contents of the zip file to the correct locations on our server.

First we move our index pages to the root directory of the web server (/var/www/ on Ubuntu).

.. code-block:: sh

  #mv ms4w/Apache/htdocs/* /var/www/

Create a ows shell script
"""""""""""""""""""""""""

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
""""""""""""""""""""""""""""

The final step is to modify the WEB > IMAGEPATH path (to "/var/tmp/") and the WEB > IMAGEURL path (to "/tmp/") in each of our onegeology.map files

That’s it!



Alternative MapServer configurations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
""""""""""""""""""""

You may use the IIS web server instead of Apache to run the MapServer CGI.  See the previous cookbook for details of how to do this with IIS version 6.  We haven't been able to update the cookbook for the latest version of IIS, but the MapServer documentation (`IIS Setup for MapServer <http://mapserver.org/installation/iis.html>`_) gives a good guide for how to do this in general for IIS 7 and up.

Compiling MapServer on Linux
"""""""""""""""""""""""""""""

You may wish to compile your own version of MapServer on a \*nix operating system of your own choosing.  We haven't done this for a while and the guidance in our previous cookbook was very out of date.  There is guidance on the MapServer site that takes you through the process (`Compiling on Unix <http://mapserver.org/installation/unix.html>`_)


General configuration
^^^^^^^^^^^^^^^^^^^^^^

MapServer services are configured through the use of Mapfile templates (\*.map).  You can use a single Mapfile to configure a service, or you can use a master file that includes other files.  The benefits of using multiple files include ease of maintenance across multiple similar services, and readability.  Here we will use multiple files to show how the various parts of a MapServer (OGC) service need to be configured.  You can configure multiple service types through a single configuration, if desired.


The start of a Mapfile begins with a **MAP** statement and ends with an **END** statement

Comments are shown by lines beginning with a **#** sign

The order of statements in the Mapfile doesn't matter, here we tend to group alphabetically for readability.

For further details on Mapfile configuration options available see http://mapserver.org/mapfile/map.html


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
       "OWS_ABSTRACT" "The 1:625k DiGMap data covering the whole of the United Kingdom is available in this OGC web service for all uses - including commercial use subject to the conditions in the Access Constraints section and is being served as a contribution to the OneGeology initiative (www.onegeology.org)."
       "OWS_ACCESSCONSTRAINTS" "The 1:625k DiGMap data is available for free download for your personal, teaching, research, or non-commercial use (as described on http://www.bgs.ac.uk/about/copyright/non_commercial_use.html). Your use of any information provided by the British Geological Survey (BGS) is at your own risk. Neither BGS nor the Natural Environment Research Council (NERC) gives any warranty, condition, or representation as to the quality, accuracy, or completeness of the information or its suitability for any use or purpose. All implied conditions relating to the quality or suitability of the information, and all liabilities arising from the supply of the information (including any liability arising in negligence) are excluded to the fullest extent permitted by law."
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

       "WFS_ABSTRACT" "The 1:625k DiGMap data covering the whole of the United Kingdom is available in this OGC WFS service for your personal, non-commercial use only and is being served as a contribution to the OneGeology initiative(www.onegeology.org).  \
       The contents of this WFS service are not intended for direct use but are transformed by a mediator layer into separate WFS services which provide data in GeoSciML. This process is described in Chapter 2 of the OneGeology WFS Cookbook available at www.onegeology.org."
       "WMS_ABSTRACT" "The 1:625k DiGMap data covering the whole of the United Kingdom is available in this OGC WMS service for your personal, non-commercial use only and is being served as a contribution to the OneGeology initiative (www.onegeology.org).\
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

The SRS specifies the coordinate system (spatial reference system) that the WMS can serve data in.  These are commonly specified using EPSG codes **and must include** `EPSG:4326 <http://epsg.io/4326>`_ so that all services have at least one coordinate system in common.  We would like if you could specify the Spherical Mercator projection (`EPSG:3857 <http://epsg.io/3857>`_) to allow your service to be used in Google Maps.  You may specify other systems that are appropriate for your region if you wish; for example we would expect most European services to support either (or both of) `EPSG:4258 <http://epsg.io/4258>`_ and `EPSG:3034 <http://epsg.io/3034>`_ to ensure compliance with INSPIRE coordinate system requirements.


Adding alternate character set support
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^

This section is added to help you debug common errors in your Mapfile.

Symbol definition error
""""""""""""""""""""""""

getString(): Symbol definition error.  Parsing error near (*matching text*):(line *line-number*)

This error may occur when your layer classes have a name which includes an apostrophe or other quotation mark that matches the quotation marks used to delimit the CLASS name.  For example if your class name is delimited using single quotes such as below and your class name includes a word with a single quote (d'Irma), you will get this error.

.. code-block:: mapfile

   NAME 'Formation d'Irma : calcaire, dolomie à tromatolites, argilite'

You can correct the error by swapping the file name delimiters to double quotes (as below), in the CLASS name causing the problem; you don’t need to change all the delimiters in all the CLASS names in the Mapfile, just the one(s) with the problem.

.. code-block:: mapfile

   NAME "Formation d'Irma : calcaire, dolomie à stromatolites, argilite"

Unknown identifier
"""""""""""""""""""""

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
""""""""""""""""""""""

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
^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^

We provide two exemplar MapServer services, the first is based on a simple raster file, and is used to illustrate a basic WMS, the second uses a vector datasource (shapefiles) to illustrate how to configure a more advanced WMS (and may also be used for a Simple Feature WFS).

Raster image data exemplar (LAYER configuration)
""""""""""""""""""""""""""""""""""""""""""""""""

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
"""""""""""""""""""""""""""""""""""""""""""

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
"""""""""""""""""""""""""""""""""

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
^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^

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
^^^^

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
-----------------

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


Using ArcGIS
-------------

.. todo::

   * SLD Enabled WMS
   * Complex Feature WFS


The following notes are based on ESRI ArcGIS server version 10.5 (SP1)

WMS
^^^

Prepare the map document
"""""""""""""""""""""""""

Initial set up of WMS services is relatively straightforward and simply requires the creation of a map document (.mxd) containing the data you want to add to the service.

It is important to pay attention to the layer names in the map document, since the individual service layer names will use the map document layer names. The service will also use the map document layer names for the respective layer titles in the GetCapabilities document.

.. figure:: images/image048.jpg
   :alt: Using ArcMap layer names in the service

   Figure 1 - Using ArcMap layer names in the service

Eg. an unmodified GetCapabilities (version 1.3.0) response for the above example would look like:

.. code-block:: xml

   <Layer>
   <Title>BGS_BEDROCK_GEOLOGY</Title>
   <CRS>CRS:84</CRS>
   <CRS>EPSG:4326</CRS>
   ...
   <Layer queryable="1">
       <Name>GBR_BGS_625k_BA</Name>
       <Title>GBR_BGS_625k_BA</Title>
       <Abstract></Abstract>
       <CRS>CRS:84</CRS>
       <CRS>EPSG:4326</CRS>
      ...
       <Style>
           <Name>default</Name>
           <Title>GBR_BGS_625k_BA</Title>
           <LegendURL width="68" height="2048">
               <Format>image/png</Format>
               <OnlineResource xlink:href="..." xlink:type="simple"/>
           </LegendURL>
       </Style>
   </Layer>
   <Layer queryable="1">
       <Name>GBR_BGS_625k_BLT</Name>
       <Title>GBR_BGS_625k_BLT</Title>
       <Abstract></Abstract>
   ...

Publishing your WMS
""""""""""""""""""""

Once you are happy with the layer names, the easiest way to publish your WMS is doing it directly from the map document:

* Go to *File > Share As > Service…* to open the *Share as Service* dialog.

* Select *Publish a service* and click *Next >*.

* On the *Publish a Service* dialog, choose/add a connection to your ArcGIS Server instance and write a name for your map service. The name you enter will be part of the WMS url, so you must ensure that meets the OneGeology profile naming conventions. Click *Next >.*

* Select whether to *Use existing folder* or *Create new folder*. The folder name will also appear as part of the WMS url. Click *Continue*.

* In the *Service Editor* dialog, go to *Capabilities* and select *WMS*. If you wish, you can unselect KML.

.. note::
	If you **do not** want to expose the data behind your WMS service, make sure that the **WFS** option is **unselected**.

* Now go to *Capabilities > WMS* to access the WMS properties

.. figure:: images/image049.jpg
   :alt: Adding a new WMS service in ArcGIS

   Figure 2 - Adding a new WMS service in ArcGIS

* You will be presented with a form to edit your service level metadata (as above) or you may opt to use external capabilities. We suggest at this stage that you should use the form to fill in as much detail as possible, though you should note that you will eventually need to use external files to enter any layer level metadata and add missing service level metadata parameters; we can use the data you enter initially as the basis for these external static files.

* You also need to tick the *Use layer names from the map document* option; otherwise, the layer names will be given numbers instead. Again, you will need to ensure that the ArcMap layer names follow the naming guidelines.

* ArcGIS Server creates only one style named *default* for every layer, but allows you to do include additional styles for each layer using a SLD file. The default style matches the symbology set in the map document.

* Once you finish configuring your WMS, click *Publish* on the top-right corner of the *Service Editor* dialog to create your service.

Your new service will have a URL like below, with the folder name part being optional:

::

   http://[hostname]/ArcGIS/services/[folder name]/[map service title]/MapServer/WMSServer

Edit the GetCapabilities documents
""""""""""""""""""""""""""""""""""""

ArcGIS Server doesn’t create any static GetCapabilities xml documents, but does allow you to use external files. You will need to use such external files if you want to add any additional spatial reference systems, correct the keywords listing, change the LegendURL images, add better abstracts and layer titles, or add an INSPIRE extended capabilities section. We think to provide a fully compliant WMS it is highly likely that you will need to use a set of static files.

The first step to editing your files is to create them.

The quickest way to do this is to use the response documents from your initial service. You will need to have a file for all the WMS versions that you want your service to support. We require at least a version 1.3.0 document but you could also have a 1.1.1 response.

Your WMS version 1.1.1 GetCapabilities document is generated using a request like:

::

   http://[hostname]/ArcGIS/services/[folder name]/[map service title]/MapServer/WMSServer?service=WMS&request=GetCapabilities&version=1.1.1&

**Save this as [short service name]111.xml**

Your WMS version 1.3.0 GetCapabilities document is generated using a request like:

::

   http://[hostname]/ArcGIS/services/[folder name]/[map service title]/MapServer/WMSServer?service=WMS&request=GetCapabilities&version=1.3.0&

**Save this as [short service name]130.xml**

It doesn’t really matter what name you give these files, as long as you use the same name prefix for all files that belong to the same service.

You need to put these files on the server (or at a location available to your server), and make them browsable. These files only need to be browsable internally by the ArcGIS server.

Now go back to your map service and edit it using either `ArcGIS Server Manager <http://server.arcgis.com/en/server/latest/publish-services/windows/editing-service-properties-in-manager.htm>`_ or `ArcMap <http://server.arcgis.com/en/server/latest/publish-services/windows/editing-service-properties-in-arcgis-for-desktop.htm>`_.

.. figure:: images/image050.jpg
   :alt: Setting up external capabilities files

   Figure 3 - Setting up external capabilities files

Select *WMS*, then select the *Use External capabilities files* option and in the *Specify the location and prefix* dialog add the web address to the folder containing the capabilities response documents plus your *[short service name]* prefix.

For example, for a service called BGS_BEDROCK_GEOLOGY, we may save our initial GetCapabilities response documents using a prefix “BEDROCK-“, giving us a file called BEDROCK-130.xml for our version 1.3.0 GetCapabilities response document, BEDROCK-111.xml for our version 1.1.1 GetCapabilities response document. We might then save these to a location on our web server such as *C:\\Inetpub\\wwwroot\\GetCapabilitiesFiles\\,* which would be browsable locally as *http://localhost/GetCapabilitiesFiles/*.  When we select the “Use External capabilities files” option, we then provide the web address and **prefix** as *http://localhost/GetCapabilitiesFiles/BEDROCK-*

Having created your files, you may then edit them as required. We would recommend you make a second copy of the files in case you make an error whilst editing.

INSPIRE
""""""""""

If you want your OneGeology service to comply to INSPIRE standards, in addition to meet the requirements of the OneGeology profile, you need to ensure that the following conditions are fulfilled:

1. Layer name and layer title must follow INSPIRE naming conventions. For example the `D2.8.II.4 Data Specification on Geology–Technical Guidelines <http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_GE_v3.0.pdf>`_ tell us (section 11.1 ~ Layers to be provided by INSPIRE view services) that any layer to do with lithology or age must have the name *GE.GeologicUnit* and title *Geologic Units*. See the `layer-naming <https://themes.jrc.ec.europa.eu/discussion/view/13952/layer-naming>`_ discussion on the INSPIRE Thematic Clusters Geology forum for fuller details.

2. Layers must support at least one of the INSPIRE coordinate systems. See `D2.8.I.1 INSPIRE Specification on Coordinate Reference Systems - Guidelines <http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_Specification_CRS_v3.0.pdf>`_.

3. Your GetCapabilities document must include the INSPIRE Extended Capabilities tag.

There are two ways of achieving these conditions using ESRI software. The first one is using a standard ArcGIS map document and standard ArcGIS Server tools, where you’ll need to modify layer names to make them compliant, change service properties to include required coordinate systems and modify the get capabilities document to include the INSPIRE Extended Capabilities section. The second option is using the ArcGIS for INSPIRE extension, which provides tools and new services to ensure compliance with INSPIRE directives. If you want to go for the second option, there is an `ESRI OneGeology Grant  <http://www.onegeology.org/technical_progress/esriGrantOffer.html>`_ for OneGeology members.

ArcGIS Server
^^^^^^^^^^^^^

INSPIRE Layer Names
"""""""""""""""""""

In order to make your service INSPIRE compliant, you will need to configure the name of your layers (e.g. GE.GeologicUnit); however, this clashes with OneGeology naming standards. In this situation, it is desirable to create a group layer. For example, you may want to create a layer called GE.GeologicUnit to group all of your layers that are spatial objects of type GeologicUnit. The layer name and title rules set out in the OneGeology profile relate to the grouped (or child) layers, whereas the INSPIRE name and title relate to the group (or parent) layer.

If your INSPIRE service is only serving layers of one type, one way of applying group layering would be to use the root layer name and title (not service name and title) as the grouping layer. If, on the other hand, your INSPIRE service is serving layers of several types (e.g. GE.GeologicUnit and GE.GeologicFault), we believe the only option is for you to configure actual group layering.

To **add group layers to a new service** simply `add a group layer <http://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/working-with-group-layers.htm#GUID-058900C7-6A45-4260-83D8-9039C00D875C>`_ to the map document that will create your service, rename it and place your layers inside. The WMS service published form this map document will keep the same group layer structure.

.. figure:: images/image051.jpg
   :alt: Adding group layers to the service

   Figure 4 - Adding group layers to the service

If you want **add group layers to an existing service**, open the map document that created the service, modify it as described above and publish it again as a WMS service; however, when publishing the service, make sure that you select the option “Overwrite an existing service”. This will save you having to delete the original service as well as having to type again all service properties.

Note that ArcGIS Server will generate only the *<Title>* tag of group layers in the GetCapabilities document. The content of this tag will be the same that you wrote in the map document. In order to comply with INSPIRE layer naming regulations for group layers, you will need to manually add the *<Name>* tag, filling it in with the adequate group layer name, by editing the GetCapabilities document using an external capabilities file.

Group layers created in ArcGIS Server will not have a style associated to them and the group layer itself will not display a map.

INSPIRE Coordinate Systems
""""""""""""""""""""""""""

ArcGIS Server always adds 2 coordinate systems: EPSG:4326 (or CRS:84 for version 1.3.0) and the coordinate system set on the map document creating the service. To add any additional coordinate systems go to your map service and edit it using either `ArcGIS Server Manager <http://server.arcgis.com/en/server/latest/publish-services/windows/editing-service-properties-in-manager.htm>`_ or `ArcMap <http://server.arcgis.com/en/server/latest/publish-services/windows/editing-service-properties-in-arcgis-for-desktop.htm>`_.  On the *Service Editor* dialog go to *Capabilities > WMS* and, in the *Additional spatial reference systems* text box, type any well-known EPSG ID in the format indicated below.

.. figure:: images/esriimage009.png
   :alt: Additional spatial reference systems option

   Figure 5 - Additional spatial reference systems option

INSPIRE extended capabilities
"""""""""""""""""""""""""""""

The extended capabilites section is inserted into your external GetCapabilities section, between the Exception element block and the first Layer element.

For example to add a scenario 1 INSPIRE extended capabilities section (where you have an external XML document or service that provides such an XML document containing metadata for your WMS service) you would insert a section like below:

.. code-block:: xml

   </Exception>
   <inspire_vs:ExtendedCapabilities xmlns:inspire_vs="http://inspire.ec.europa.eu/schemas/inspire_vs/1.0">
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
   <Layer>

Alternatively, to add a scenario 2 INSPIRE extended capabilities section (where you have no external metadata document for your WMS service) you would insert a section like below:

.. code-block:: xml

   </Exception>
   <inspire_vs:ExtendedCapabilities xmlns:inspire_vs="http://inspire.ec.europa.eu/schemas/inspire_vs/1.0">
       <inspire_common:ResourceLocator>
           <inspire_common:URL>http://ogc2.bgs.ac.uk/cgi-bin/BGS_OGE_Bedrock_and_Surface_Geology_in3/ows?</inspire_common:URL>
       </inspire_common:ResourceLocator>
       <inspire_common:ResourceType>service</inspire_common:ResourceType>
       <inspire_common:TemporalReference>
           <inspire_common:DateOfLastRevision>2015-10-23</inspire_common:DateOfLastRevision>
       </inspire_common:TemporalReference>
       <inspire_common:Conformity>
           <inspire_common:Specification>
               <inspire_common:Title>-</inspire_common:Title>
               <inspire_common:DateOfLastRevision>2015-10-23</inspire_common:DateOfLastRevision>
           </inspire_common:Specification>
           <inspire_common:Degree>notEvaluated</inspire_common:Degree>
       </inspire_common:Conformity>
       <inspire_common:MetadataPointOfContact>
           <inspire_common:OrganisationName>Mr Matthew Harrison</inspire_common:OrganisationName>
           <inspire_common:EmailAddress>enqiries@bgs.ac.uk</inspire_common:EmailAddress>
       </inspire_common:MetadataPointOfContact>
       <inspire_common:MetadataDate>2015-10-23</inspire_common:MetadataDate>
       <inspire_common:SpatialDataServiceType>view</inspire_common:SpatialDataServiceType>
       <inspire_common:MandatoryKeyword xsi:type='inspire_common:classificationOfSpatialDataService'>
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
   <Layer>

In addition (for both scenarios) you will need to **reference the inspire_common schema and namespace** in your root element, so it will become something like:

.. code-block:: xml

   <WMS_Capabilities
       xmlns:inspire_common="http://inspire.ec.europa.eu/schemas/common/1.0"
       xmlns="http://www.opengis.net/wms" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:esri_wms="http://www.esri.com/wms"
       version="1.3.0"
       xsi:schemaLocation="http://www.opengis.net/wms http://schemas.opengis.net/wms/1.3.0/capabilities_1_3_0.xsd
       http://inspire.ec.europa.eu/schemas/inspire_vs/1.0 http://inspire.ec.europa.eu/schemas/inspire_vs/1.0/inspire_vs.xsd
       http://www.esri.com/wms http://../arcgis/services/.../MapServer/WmsServer?version=1.3.0%26service=WMS%26request=GetSchemaExtension">

INSPIRE Extension
"""""""""""""""""""

The ArcGIS for INSPIRE extension allows to create an INSPIRE compliant WMS through a new ESRI map service, specific to this extension, called INSPIRE View service. In our experience, creating a INSPIRE compliant WMS service using custom INSPIRE extension tools is more difficult than using standard ArcGIS tools, due to the complexity of the datasets that you have to use, the scarce amount of documentation and the limited ESRI support for the extension.

Create INSPIRE geodatabase
""""""""""""""""""""""""""

The first step to use ArcGIS for INSPIRE is creating a geodatabase with one of the templates supplied by the extension.  To create a geodatabase for Geology follow the steps in `this document <http://enterprise.arcgis.com/en/inspire/10.5/get-started/pdf/InstallationGuide_ArcGISForINSPIRE_GDB_10_5_EN.pdf>`_ in sections 3.3.1 and 3.3.4.

Populate INSPIRE geodatabase
""""""""""""""""""""""""""""

Fill in the geodatabase with your data. There are multiple feature classes and tables; fill in the ones that are relevant to you.

Note that all feature classes will be grouped on a feature dataset called *GE*. You’ll need to add your features to the appropriate feature class so that they can be used by the INSPIRE extension. Feel free to add new fields to these feature classes if you want to show attributes not available by default on the template; however, refrain from deleting any existing field as you might break one of the multiple relationships set on the template.

Customise layers in INSPIRE geodatabase
"""""""""""""""""""""""""""""""""""""""

You’ll do this by modifying the *LayerInfo* table. In this extension, each INSPIRE layer consists normally of four hidden sublayers.  We need to modify the *LayerInfo* table to make the relevant sublayers visible and to be able to change the name and title of the sublayers (`see Customization Guide <http://enterprise.arcgis.com/en/inspire/10.5/get-started/pdf/CustomizationGuide_ArcGISForINSPIRE_LayerInfo_10_5_EN.pdf>`_). The INSPIRE layer will act as a group layer and will follow INSPIRE naming conventions. The sublayers will follow OneGeology naming conventions. In the following example, we are going to configure two sublayers to represent bedrock units symbolised by age and by lithology. These layers are going to be looking at the same feature class in the geodabase template, defined in the FC_NAME field as *geUnitS* (short for geology unit surface). Given that in this example we are dealing only with geologic features represented as polygons, the final *LayerInfo* table could look like this (table transposed for visibility reasons):

.. todo:: clean up table HTML or replace by rst table.

.. raw:: html

   <table border=1 cellspacing=0 cellpadding=0 width=0 style='width:375.65pt;border-collapse:collapse;border:none'>
    <tr style='height:15.0pt;color:white;'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;background: black;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt;color:white;'>
     <p align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>FIELD NAME
     </td>
     <td width=116 style='vertical-align:center;width:99.2pt;border:solid windowtext 1.0pt;border-left: none;background:black;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt;color:white;'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ROW 1
     </td>
     <td width=123 style='width:99.25pt;border:solid windowtext 1.0pt;border-left: none;background:black;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt;color:white;'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ROW 2
     </td>
     <td width=136 style='width:4.0cm;border:solid windowtext 1.0pt;border-left: none;background:black;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt;color:white;'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ROW 3
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>OBJECTID
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>2
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>4
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>12
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ID
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>417
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>420
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>421
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>THEME
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>FC_NAME
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>geUnitS
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>geUnitS
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>STYPE
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-1
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-1
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-1
     </td>
    </tr>
    <tr style='height:15.75pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.75pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>APP_SCHEMA
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.75pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.75pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.75pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>IR_VERSION
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>0
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>0
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>
     </td>
    </tr>
    <tr style='height:30.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:30.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>LAYER_NAME
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:30.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GE.GeologicUnit
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:30.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GBR_BGS_625k_BA
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:30.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GBR_BGS_625k_BLT
     </td>
    </tr>
    <tr style='height:23.9pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:23.9pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>LAYER_TITLE
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:23.9pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geologic Units
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:23.9pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GBR BGS 1:625k Bedrock Age
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:23.9pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GBR BGS 1:625k Bedrock Lithology
     </td>
    </tr>
    <tr style='height:21.8pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:21.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>SPATIAL_OBJECT_TYPE
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:21.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:21.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>MappedFeature
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:21.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>MappedFeature
     </td>
    </tr>
    <tr style='height:13.7pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:13.7pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>DEF_QUERY
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:13.7pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:13.7pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:13.7pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>PARENT_ID
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>-1
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>417
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>417
     </td>
    </tr>
    <tr style='height:22.55pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:22.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>SPATIAL_OBJECT_
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>TYPE_PREFIX
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:22.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ge
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:22.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ge
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:22.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>ge
     </td>
    </tr>
    <tr style='height:27.8pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:27.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>LAYER_KEYWORDS
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:27.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology, Lithology, Age, Geologic unit
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:27.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology, Lithology, Age, Geologic unit
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:27.8pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>Geology, Lithology, Age, Geologic unit
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>IS_HIDDEN
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>0
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>0
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>0
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>IS_VISIBLE
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>1
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>1
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>1
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>MIN_SCALE
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'></td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'></td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>
     </td>
    </tr>
    <tr style='height:15.0pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>MAX_SCALE
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'></td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:15.0pt'></td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:15.0pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>
     </td>
    </tr>
    <tr style='height:13.55pt'>
     <td width=126 style='width:63.8pt;border:solid windowtext 1.0pt;border-top: none;background:#F2F2F2;padding:0cm 5.4pt 0cm 5.4pt;height:13.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GDBTEMPLATE_NAME
     </td>
     <td width=116 style='width:99.2pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:13.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GE
     </td>
     <td width=123 style='width:99.25pt;border-top:none;border-left:none; border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt; padding:0cm 5.4pt 0cm 5.4pt;height:13.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GE
     </td>
     <td width=136 style='width:4.0cm;border-top:none;border-left:none;border-bottom: solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt; height:13.55pt'>
     <p  align=center style='margin-bottom:0cm;margin-bottom:.0001pt; text-align:center;line-height:normal'>GE
     </td>
    </tr>
   </table>

Table 1 Custom *Layer Info* table

* Rows with ID = 417 and ID = 420 were kept; the remaining rows were deleted. In addition, a new row with ID = 421 was added. Note that you don’t need to delete any row, this was done purely to create a simpler example.

* As specified in the PARENT_ID field, row ID 417 is the group layer, whereas rows 420 and 421 are its sublayers.

* The group layer doesn’t point to any feature class. Both child layers point at the same feature class (geUnitS), since we want the same dataset with different symbology (this can be set once layers are loaded on the map document).

* Group layer name and title must conform to INSPIRE standards.  Child layer titles must conform to OneGeology standards (ideally layer names too, but the GetCapabilities document created with the ArcGIS for INSPIRE extension doesn’t honour the layer names defined on the *LayerInfo* table if more than one layer is pointing at the same feature class).

* Child layers must have a value of *0* in the IS_HIDDEN field so that they are visible on the INSPIRE VIEW service.

Add INSPIRE layers to your map document
"""""""""""""""""""""""""""""""""""""""

Open a map document and add your layers to the map using the *Add INSPIRE Layer* button (if you can’t see this button, make sure that you have the *INSPIRE Tools* toolbar enabled).

.. figure:: images/image052.jpg
   :alt: Add INSPIRE Tools to map document

   Figure 6 - Add INSPIRE Tools to map document

This will open *INSPIRE Layer Wizard* where you can first select your INSPIRE database and second select the INSPIRE layers you wish to add. Note that this dialog will reflect changes done in the *LayerInfo* table therefore your custom layers should now be available. See `Create the INSPIRE View Service map document. <http://server.arcgis.com/en/inspire/latest/inspire-services/create-inspire-view-service-map-document.htm>`_

.. figure:: images/image053.jpg
   :alt: INSPIRE Layer wizard

   Figure 7 - INSPIRE Layer wizard

Click *Create*, and your selected layers will be added to the map document. The *LayerInfo* table specifies the hierarchical structure of the layers in the service as well as their names and titles, so we don’t need to (and shouldn’t) modify the layer names in the map document.

.. figure:: images/image054.jpg
   :alt: INSPIRE layers on map document

   Figure 8 - INSPIRE layers on map document

Note that, as well as the layers shown on the map, a few tables have also been added to the map document. These tables are required for the creation of the INSPIRE service therefore they shouldn’t be removed.

.. figure:: images/image055.jpg
   :alt: Additional INSPIRE related tables added to map document

   Figure 9 - Additional INSPIRE related tables added to map document

Now you can proceed to style your layers using the appropriate symbology. The symbology set on the map document will be defined within the GetCapabilities document as a style named *default*. In addition, each layer will have another style called *inspire_common:DEFAULT*, which is meant to assign by default a common style to INSPIRE layers; however, in ArcGIS server version 10.5, this default visualization style only supports Annex I INSPIRE layers.

.. figure:: images/image056.jpg
   :alt: INSPIRE layer styles

   Figure 10 - Each INSPIRE layer will have 2 styles: *inspire_common:DEFAULT* and *default*

.. figure:: images/image057.jpg
   :alt: The symbology set in the map document will correspond to the "default" style

   Figure 11 - The symbology set in the map document will correspond to the *default* style

Publish INSPIRE View service
""""""""""""""""""""""""""""

A INSPIRE View service is the ESRI equivalent of a INSPIRE compliant WMS. Publishing a INSPIRE View service is very similar to publishing a WMS, the only difference being that you need to select and configure one additional capability.

* Go to *File > Share As > Service…* to open the *Share as Service* dialog.

* Select *Publish a service* and click *Next >*.

* On the *Publish a Service* dialog, choose/add a connection to your ArcGIS Server instance and write a name for your map service. The name you enter will be part of the WMS url, so you must ensure that meets the OneGeology profile naming conventions.

* Select whether to *Use existing folder* or *Create new folder*. The folder name will also appear as part of the WMS url. Click *Continue*.

* In the *Service Editor* dialog, go to *Capabilities*. You’ll notice that the ArcGIS for INSPIRE extension has added three new capabilities. Select *WMS* and *ArcGIS for INSPIRE View Service*. Note that in order for the INSPIRE View service to work, the WMS capability must be enabled.

.. figure:: images/image058.jpg
   :alt: Capabilities option in Service Editor dialog

   Figure 12 - *Capabilities* option in *Service Editor* dialog


* Now go to *Capabilities > ArcGIS for INSPIRE View Service* to access the INSPIRE View Service properties

.. figure:: images/image059.jpg
   :alt: ArcGIS for INSPIRE View Service properties in Service Editor dialog

   Figure 13 - *ArcGIS for INSPIRE View Service* properties in *Service Editor* dialog


* The properties of the above dialog can be left as they are, unless you want to modify the supported languages. Also, make sure that if you checked the *Use layer names from the map document* option in the WMS capabilities, you also check the *WMS uses layernames from map document* option in the ArcGIS for INSPIRE View Service capabilities. This won’t affect your INSPIRE View Service, only the WMS service that is being created in parallel.

* Click *Publish* on the top-right corner of the *Service Editor* dialog to create your service. We’ll deal with Advance Properties after the service has been published because the properties for INSPIRE layers will be available then.

For more information go to `Create an INSPIRE View Service <http://server.arcgis.com/en/inspire/latest/inspire-services/create-the-inspire-view-service.htm>`_.

Configure INSPIRE View service
""""""""""""""""""""""""""""""

Once the service has been published, we are going to use ArcCatalog to configure INSPIRE View service properties which will be reflected on the service’s GetCapabilities document.

* On ArcCatalog, go to the *GIS Servers* folder, select the appropriate instance of ArcGIS Server and navigate to your service.

* Right-click on the service and go to *Service Properties…*

.. figure:: images/image060.jpg
   :alt: Accessing Service Properties

   Figure 14 - Accessing *Service Properties*

* On the Service Editor go to *Capablities > ArcGIS for INSPIRE View Service* (see figure 13) and click *Advanced Properties* to open the *Editing the InspireView properties* dialog.

The *Editing the InspireView properties* dialog allows you to set the options below. Fields in yellow are compulsory and, depending on the options you choose, there might be disabled fields in grey. We recommend you fill in as many fields as you can.

* Select INSPIRE external capabilities scenario

.. figure:: images/image061.jpg
   :alt: Inspire View properties: extended capabilities type

   Figure 15 - Inspire View properties: extended capabilities type

* Service properties. Do not modify *Online resource* on this dialog, as it will change the value of the property *xlink:href* in all *OnlineResource* tags in the get capabilities document. You’ll need create a custom GetCapabilities document if you want to change the tag */WMS_Capabilities/Service/OnlineResource* to provide a link to the data owner organization web site, or web site with information about the data owner organization, as requested in the OneGeology profile.

.. figure:: images/image062.jpg
   :alt: Inspire View properties: service information

   Figure 16 - Inspire View properties: service information

* Contact information

.. figure:: images/image063.jpg
   :alt: Inspire View properties: contact information

   Figure 17 - Inspire View properties: contact information

* GEMET Keywords

.. figure:: images/image064.jpg
   :alt: Inspire View properties: GEMET Keywords

   Figure 18 - Inspire View properties: GEMET Keywords

* Layer properties. Note the highlighted sublayer names. One of them doesn’t honour the name defined in the *LayerInfo* table, taking the name of the other sublayer and adding “1” at the end of it. This seems to be a bug within the INSPIRE extension. Since OneGeology naming conventions for layer names are only a recommendation, the service will still comply with the OneGeology profile.

.. figure:: images/image065.jpg
   :alt: Inspire View properties: Layers informatio

   Figure 19 - Inspire View properties: Layers information

Custom INSPIRE View service GetCapabilities document
""""""""""""""""""""""""""""""""""""""""""""""""""""

If you need to modify any option that’s not on the *Editing the InspireView properties* dialog, like the Online Resource tag mentioned above, you need to go to the service cached capabilities folder (*C:\\arcgisserver\\directories\\arcgisforinspire\\[folder_name]\\[map service title]_MapServer\\[folder_name]_ [map service title]_MapServer_inspireview*) and create a file called *GetCapabilities<version>_<3 letter language code>.xml*. Your service will now use the custom GetCapabilities file instead of the dynamically created one (e.g. *GetCapabilities130_ENG.xml*), also stored in the same location. When creating your custom file it’s recommended to start from a copy of the dynamically created file.

Use INSPIRE View service
""""""""""""""""""""""""

Your service will be accessible from the following endpoint:

::

   http://[hostname]/ArcGIS/services/[folder_name]/[map service title]/exts/InspireView/service

For more information see `Use an INSPIRE View service <http://server.arcgis.com/en/inspire/latest/inspire-services/use-the-inspire-view-service.htm>`_.

ArcGIS server issues
^^^^^^^^^^^^^^^^^^^^^

* When using the SLD parameter to get an external SLD file, ArcGIS 10.0 expects the layer name and styles parameter to be to be sent as part of a GetMap request, even though this is not required by the WMS+SLD specification. A bug has been raised with ESRI on this issue (`NIM095568 <http://support.esri.com/en/bugs/nimbus/TklNMDk1NTY4>`_) back in version 10.0, but it’s still present.

.. todo::

   SLD Enabled WMS content.

Simple Feature WFS
^^^^^^^^^^^^^^^^^^^

Creating a simple feature WFS requires almost the same steps as creating a WMS. The only difference being that, when publishing the service, you need to select the WFS capability.

.. figure:: images/image066.jpg
   :alt: Enabling WFS capabilities in Service Editor dialog

   Figure 20 - Enabling WFS capabilities in *Service Editor* dialog

After activating WFS, you’ll have access to the properties of this capability. Some of these properties will coincide with WMS properties, but there will also be WFS specific properties, such us namespace, prefix or maximum number of features returned.

.. figure:: images/image067.jpg
   :alt: WFS service properties

   Figure 21 - WFS service properties

For more information on how to create a simple feature WFS service and how to edit its GetCapabilities document, go to the WMS section of this cookbook or to ESRI’s documentation about `WFS services <http://server.arcgis.com/en/server/latest/publish-services/windows/wfs-services.htm>`_.

.. todo::

   Complex Feature WFS content.

WCS
^^^^

Create a map document
""""""""""""""""""""""

In ArcGIS, a WCS can be created mainly through 3 routes: a map document with raster data, a raster dataset or a mosaic dataset. Publishing a mosaic dataset requires ArcGIS Image Server, so unless you have this extension enabled, the only way to publish multiple rasters at once on a single WCS will be through a map document; therefore we’re are going to focus on this route. For more information see `WCS services <http://server.arcgis.com/en/server/latest/publish-services/windows/wcs-services.htm>`_.

Start by creating a map document and adding your rasters to it. Note that, if you have feature data in your map document, it’ll be excluded from your WCS.

.. figure:: images/image068.jpg
   :alt: Adding WCS data to your map document

   Figure 22 - Adding WCS data to your map document

Publish the WCS service
""""""""""""""""""""""""""

* Go to *File > Share As > Service… *to open the *Share as Service* dialog.

* Select *Publish a service* and click *Next >*.

* On the *Publish a Service* dialog, choose/add a connection to your ArcGIS Server instance and write a name for your map service. The name you enter will be part of the WCS url. Click *Next >.*

* Select whether to *Use existing folder* or *Create new folder*. The folder name will also appear as part of the WCS url. Click *Continue*.

* In the *Service Editor* dialog, go to *Capabilities* and select *WCS*.

* Now go to *Capabilities > WCS* to access the WCS properties

.. figure:: images/image069.jpg
   :alt: WCS service properties

   Figure 23 - WCS service properties

* Fill in all relevant service-level and contact properties.

* Check *Use layer names from the map document* so that layer names/identifiers use the layer names given in the map document rather than numbers.

* Click *Publish* on the top-right corner of the *Service Editor* dialog to create your service.

Your new service will have a URL like below, with the folder name part being optional:

::

   http://[hostname]/ArcGIS/services/[folder_name]/[map service title]/MapServer/WCSServer

Edit the GetCapabilities document
""""""""""""""""""""""""""""""""""

ArcGIS server doesn’t create any static GetCapabilities xml documents, but does allow you to use external files. You will need to use such external files if you want to add any supported CRS, add keywords and abstracts for coverages or modify coverage titles. Note that, independently of the supported CRSs added, ESRI WCSs will always support the over 6000 projections that come with the ArcGIS projection engine.

The quickest way to create your custom GetCapabilities document is to use the response documents from your initial service. You will need to have a file for all the WCS versions that you want your service to support.

Your WCS version 1.1.0 GetCapabilities document is generated using a request like:

::

   http://[hostname]/argis/services/[folder name]/[map service title]/MapServer/WCSServer?service=WCS&request=GetCapabilities&version=1.1.0&

**Save this as [short service name]110.xml**

Your WCS version 2.0.1 GetCapabilities document is generated using a request like:

::

   http://[hostname]/argis/services/[folder name]/[map service title]/MapServer/WCSServer?service=WCS&request=GetCapabilities&version=2.0.1&

**Save this as [short service name]201.xml**

It doesn’t really matter what name you give these files, as long as you use the same name prefix for all files that belong to the same service.

You need to put these files on the server (or at a location available to your server), and make them browsable. These files only need to be browsable internally by the ArcGIS server.

Now go back to your map service and edit it using either `ArcGIS Server Manager <http://server.arcgis.com/en/server/latest/publish-services/windows/editing-service-properties-in-manager.htm>`_ or `ArcMap <http://server.arcgis.com/en/server/latest/publish-services/windows/editing-service-properties-in-arcgis-for-desktop.htm>`_.

Go to *Capabilities > WCS*, then select the “Use External capabilities files” option and in the ‘Specify the location and prefix’ dialog add the web address to the folder containing the capabilities response documents plus your [short service name] prefix.

.. figure:: images/image070.jpg
   :alt: WCS service properties: external capabilities

   Figure 24 - WCS service properties: external capabilities

For example, for a service called BGS_EMODnet_Bathymetry, we may save our initial GetCapabilities response documents using a prefix “EMODnet-“, giving us a file called EMODnet-201.xml for our version 2.0.1 GetCapabilities response document, EMODnet-110.xml for our version 1.1.0 GetCapabilities response document and so on. We might then save these to a location on our web server such as *C:\\Inetpub\\wwwroot\\GetCapabilitiesFiles\\* which would be browseable locally as *http://localhost/GetCapabilitiesFiles/*.  When we select the “Use External capabilities files” option, we then provide the web address and **prefix**
as *http://localhost/GetCapabilitiesFiles/EMODnet-*

Having created your files, you may then edit them as required. We would recommend you make a second copy of the files in case you make an error whilst editing.

We have found that, if you make a GetCapabilities request using external capabilities files, it always defaults to version 1.1.0, even if you specify a different version as a url parameter. For instance, *http://[my_server]s:6080/arcgis/services/[folder_name]/BGS_EMODnet_bathymetry/MapServer/WCSServer?request=GetCapabilities&service=WCS&version=2.0.1* will return the GetCapabilities document for version 1.1.0 (if available, otherwise you will get an error), even though we’ve created the version 2.0.1 of the document. The only exception is version 1.0.0, which does return the correct version of the GetCapabilities document if specified in the url.

For more information, see `Use external capabilities files with WCS Services <http://server.arcgis.com/en/server/latest/publish-services/windows/using-external-capabilities-files-with-wcs-services.htm>`_.


Using Apache HTTP server as a reverse proxy
--------------------------------------------

To serve a OneGeology WMS through the OneGeology Portal that service must be served using port 80; the default port for any http web service. If you are already serving another web service on port 80 on the same server (such as a GeoNetwork spatial data metadata catalogue for example), then you will need to use a different port number for the existing service. In itself this shouldn’t be too difficult to do, however this might cause problems for your customers due to restrictive firewall rules that prevent them consuming any web service not served on the standard web port number. One way around this is to merge the services together; another possibility (as detailed below) is to use the Apache HTTP web server as a reverse proxy, that is, to handle all requests to the second service as if that service was coming from the MS4W Apache service. The user is thus unaware that there is more than one web service. Each service proxied in this way runs on a separate port number, and may still be accessed directly on that port (depending on your configuration), but it is also available as if it were running on port 80.

(`Comprehensive information on configuring Apache <http://httpd.apache.org/docs/2.2/urlmapping.html>`_)

The first step is to change the `port numbers <http://www.iana.org/assignments/port-numbers>`_ on which your other web servers work; in this example we have two other web services (a Tomcat based web service which we will run on port 8080, and a jetty based web service which we will run on port 8008). Note that both these ports are recognized alternate ports for http traffic but they may not be open to such traffic in your corporate firewall.

Now we need to edit the Apache HTTP server httpd.conf file. If you have installed the MS4W Apache HTTP server as part of the ms4w-and-exemplar-data.zip download this would be located at: c:\\ms4w\\Apache\\conf\\httpd.conf.

Check that the following modules are uncommented (by removing the # sign from the line start).

Change

.. code-block:: apacheconf

    #LoadModule proxy_module modules/mod_proxy.so
    #LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
    #LoadModule proxy_http_module modules/mod_proxy_http.so

To:

.. code-block:: apacheconf

    LoadModule proxy_module modules/mod_proxy.so
    LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
    LoadModule proxy_http_module modules/mod_proxy_http.so

Note, we have used mod\_proxy here as it is included with the Apache HTTP Server binaries, but you could use other proxy modules such as mod\_jk if desired.

Now you need to add or uncomment the following directives (as appropriate for your configuration file); we suggest adding these directives at the end of the file for clarity.

.. code-block:: apacheconf

    TraceEnable off
    #Important for security!!

    ProxyRequests Off
    #This sets up the reverse proxy, if ’ ProxyRequests On’ is set you have a forward proxy.

    ProxyPreserveHost On

Now for each service (or set of pages within a service) that you wish to proxy you need to add the following set of directives:

A <Proxy> or a <ProxyMatch> block to restrict access to your resources, a ProxyPass directive (to map that web service into the local server URL space), and a ProxyPassReverse directive (which lets Apache adjust the URL in the Location, Content-Location and URI headers on HTTP redirect responses).


Examples:

Adding a reverse proxy to the BRGM OneGeology Europe connector for WP6 WMS. This connector runs on the Tomcat server running on port 8080, but will appear to be running as part of the Apache http service running on port 80.

.. code-block:: apacheconf

    <Proxy /1GEconnector>
        Order deny,allow
        Allow from all
    </Proxy>

    ProxyPass /1GEconnector http://localhost:8080/1GEconnector
    ProxyPassReverse /1GEconnector http://localhost:8080/1GEconnector

Adding a reverse proxy to our Jetty web service which is running a GeoNetwork catalogue. The Jetty service is running on port 8008 but will appear to be running as part of the Apache http service running on port 80. You would normally be able to use ’ localhost’ or ’ 127.0.0.1’ to specify a web service running on the same physical server as your Apache web server, but in this instance Jetty has been configured to only accept requests from the server IP (194.66.252.156).


.. code-block:: apacheconf

    <Proxy /geonetwork>
        Order deny,allow
        Allow from all
    </Proxy>

    ProxyPass /geonetwork http://194.66.252.156:8008/geonetwork
    ProxyPassReverse /geonetwork http://194.66.252.156:8008/geonetwork

Adding a reverse proxy to our Jetty web service which is running an Intermap mapping client (used by the GeoNetwork catalogue). The Jetty service is running on port 8008 but will appear to be running as part of the Apache http service running on port 80.

.. code-block:: apacheconf

    <Proxy /intermap>
        Order deny,allow
        Allow from all
    </Proxy>

    ProxyPass /intermap http://194.66.252.156:8008/intermap
    ProxyPassReverse /intermap http://194.66.252.156:8008/intermap


Adding a reverse proxy to our cocoon service, which we need to run our old WFS. The cocoon service runs on the Tomcat server running on port 8080, but will appear to be running as part of the Apache http service running on port 80. In this example we are using a ProxyMatch block, which allows us to use a regular expression to map the allowable paths to cocoon.

.. code-block:: apacheconf

    <ProxyMatch http://[^/]*/cocoon/*>
        Order deny,allow
        Allow from 127.0.0.1
    </ProxyMatch>

    ProxyPass /cocoon http://127.0.0.1:8080/cocoon/
    ProxyPassReverse /cocoon http://127.0.0.1:8080/cocoon/

That’s it as far as the Apache HTTP server is concerned, but you may also wish to configure your other web servers so that they always proxy their HTTP content through Apache.

To do this in Tomcat, you need to modify a Connector block in the server.xml configuration file as below:

Change:

.. code-block:: xml

    <Connector
        port="8080"
        protocol="HTTP/1.1"
        connectionTimeout="20000"
        redirectPort="8443" />

To:

.. code-block:: xml

    <Connector
        port="8080"
        protocol="HTTP/1.1"
        connectionTimeout="20000"
        redirectPort="8443"
        proxyName="yourserver.org"
        proxyPort="80" />

ProxyName: is the domain name or IP of the standard (Apache HTTP Server) web service and can be omitted if you are running your Tomcat service on the same server as the http service.

To do this in Jetty you need to make a similar change in the jetty.xml file
