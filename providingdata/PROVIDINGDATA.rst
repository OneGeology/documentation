Providing Data
======================


.. todo::

   This high level introduction text should be consistent with other parts of the www.onegeology.org site and with statements in the "using" part. Maybe link to a canonical statement of purpose on the website. Does it need updating to cover newer types of data that we are dealing with?

The `mission <http://onegeology.org/what_is/mission.html>`_ of OneGeology is being fulfilled by the cooperation of participating member organisations worldwide. This part of the website gives technical guidance on how to provide services for OneGeology to those organisations that fit within the `prospective member guidelines <http://onegeology.org/participants/home.html#statement>`_ and have `registered <http://onegeology.org/getting_involved/home.html>`_ with OneGeology as participants. Some of the guidance may also be of use to others who wish to set up similar services outside OneGeology.

As described in the pages on `using <http://onegeology.org/use/home.html>`_ OneGeology data there are different kinds of data and levels of interaction with that data that are provided by OneGeology services. As a participant you need to decide what kinds of service to set up. This will depend on what data you have available and what level of access you wish to provide to it. You will also need to decide how much effort you are able to spend to harmonise your data with relevant standards. The next sections give an overview of different kinds of data source you might use and what levels of functionality you could provide with different services.


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

Scanning a paper map
--------------------

Scanning
^^^^^^^^^

Your chosen paper map may look something like this one from the Dutch Geological Survey of Dutch Guyana or Suriname:

.. figure:: paperMap.jpg
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

.. figure:: scanningAMap.jpg
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

.. figure:: crossingPoints.jpg
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

   .. figure:: legend.jpg
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

Lite Schemas
-------------

GeoSciML-Lite and EarthResourceML-Lite (ERML-Lite) are simplified schemas that take the form of a flat table of attributes (conformant to OGC Simple Features Level-0 profile). These were previously called GeoSciML-Portrayal and EarthResourceML-Portrayal.

.. _service_provision_data_preparation_lite_geosciml:

GeoSciML-Lite
^^^^^^^^^^^^^^

The full specification for GeoSciML-Lite is in the `GeoSciML standard <http://docs.opengeospatial.org/is/16-008/16-008.html>`_. OneGeology itself does not currently make direct use of data using these schemas but the age and lithology URI columns in GeologicUnitView are those that an SLD enabled WMS needs to provide for the age and lithology highlighting functionality to work. These schemas do, however, provide a method to exchange simple interoperable data without supporting complex features that may be more easily achievable and that can help qualify for a 4 star accreditation.

There are seven GeoSciML-Lite views descibed in the 4.1 standard, these are:  GeologicUnitView, ShearDisplacmentStructureView, ContactView, BoreholeView, SiteObservationView, GeologicSpecimenView, GeomorphologicUnitView.  Below we lay out what is expected of the views for those features we think that many geological survey organizations will be able to support.

Generally across all GeoSciML-Lite views, missing values should be specified using OGC nil values *http://www.opengis.net/def/nil/ogc/0/* as below:

.. raw:: html

      <dl>
          <dt>above detection range (AboveDetectionRange)</dt>
          <dd>Value was above the detection range of the instrument used to estimate it.</dd>
          <dt>below detection range (BelowDetectionRange)</dt>
          <dd>Value was below the detection range of the instrument used to estimate it.</dd>
          <dt>inapplicable</dt>
          <dd>There is no value</dd>
          <dt>missing</dt>
          <dd>The correct value is not readily available to the sender of this data. Furthermore, a correct value may not exist</dd>
          <dt>template</dt>
          <dd>The value will be available later</dd>
          <dt>unknown</dt>
          <dd>The correct value is not known to, and not computable by, the sender of this data. However, a correct value probably exists</dd>
          <dt>withheld</dt>
          <dd>The value is not divulged</dd>
      </dl>

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

Complex Feature Data
------------------

.. todo::

    WIP: The below text has been extracted from the GeoSciML 4.1 Encoding Cookbook for OneGeology and INSPIRE. It needs re-wrting for here. The INSPIRE references need a bit more context explanation for this position in the 1G web pages. Need to remove figure numbering. Compare the way this is explained with the GeoSciML-Lite schemas. Maybe they need a common introduction saying these are data specifications you might want to map your date to as opposed to the other sections which are about file/db formats? Then notes on ERML could be added (although less urgent as we are mainly focussed on ERML-Lite for the moment in 1G. Consider whether can make links to GeoSciML standard HTML documentation rather than reproducing all diagrams etc. here?

GeoSciML is an application-neutral encoding format for geosciences information. It is based on Geography Markup Language v3.2 (GML) (ISO 19136:2007) for representation of features and geometry. GeoSciML was developed by the CGI (Commission for the Management and Application of Geoscience Information), a Commission of the International Union of Geological Sciences (IUGS). Following a memorandum of understanding between IUGS and the Open Geospatial Consortium (OGC), GeoSciML v4.1 was published in 2017 as an OGC standard (`http://www.opengeospatial.org/standards/geosciml <http://www.opengeospatial.org/standards/geosciml>`_). Future releases will be managed by the OGC GeoSciML Standards Working Group (SWG).

GeoSciML has a wide scope allowing the encoding of most information depicted on geological maps, as well as information about boreholes and laboratory analyses. This cookbook, however, concentrates on just those parts of GeoSciML necessary for (i) encoding the INSPIRE Geology application schema and (ii) delivering geological age and lithology information through OneGeology  services.

The
INSPIRE geology data specification (D2.8.II.4 Data Specification on Geology –
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

To facilitate semantic interoperability it is
important to use shared vocabularies. The CGI has developed suitable
vocabularies for many GeoSciML properties and these are available from the
GeoSciML resources website (`http://resource.geosciml.org/ <http://resource.geosciml.org/>`_).
For INSPIRE the vocabularies that must be used are included in the data
specification and are available from the INSPIRE registry (`http://inspire.ec.europa.eu/registry/ <http://inspire.ec.europa.eu/registry/>`_). The OneGeology portal can query services
using either CGI or INSPIRE vocabularies.Both sets of vocabularies use http
URIs as concept identifiers.

This cookbook is designed to assist users map their
data to the GeoSciML data model. In most cases users with digital geoscience
data will have their own formalised model of some type, although this will not
always be the case. Where a formalised user data model exists then the process
of mapping data to GeoSciML will largely involve mapping features/entities in
the user model to their equivalents in the GeoSciML logical data model. Where
no such user model exists then mapping must be carried out direct from the
data.

To carry out the mapping, from either a model or direct from data, requires staff
with geoscientific knowledge, familiarity with the user’s own data and data
model, and an understanding of the UML formalisation used in documenting
GeoSciML. These staff are likely to be geoscientists, possibly those who were
involved in developing the organisation’s own data model, and it is these
people who are seen as the main users of this cookbook.

Materials
and documentation on GeoSciML have been produced by the CGI  and OGC and are
available "as is" for download from `http://www.geosciml.org/ <http://www.geosciml.org/>`_
and `http://www.opengeospatial.org/standards/geosciml <http://www.opengeospatial.org/standards/geosciml>`_.
The supporting materials most
relevant to this cookbook include:

* Full documentation of the GeoSciML model. This is generated automatically from the GeoSciML UML diagrams and draws on the scope notes in those diagrams. This full documentation, however, does not include any best practice guidance
* An Enterprise Architect version of the UML for the CGI packages
* GeoSciML examples

There are also XML Schema documents which enable
validation of the GeoSciML instance documents that you produce from your mapped
data. These are listed at `http://schemas.opengis.net/gsml/4.1/ <http://schemas.opengis.net/gsml/4.1/>`_.
For the parts covered by this cookbook you will need http://schemas.opengis.net/gsml/4.1/geoSciMLBasic.xsd
and, if you are providing borehole data, `http://schemas.opengis.net/gsml/4.1/borehole.xsd <http://schemas.opengis.net/gsml/4.1/borehole.xsd>`_.
You can also find some Schematron files which provide extra validation for
the INSPIRE profile of GeoSciML. `http://schemas.geosciml.org/geosciml/4.1/geoSciMLBasic_inspire_mandatory.sch <http://schemas.geosciml.org/geosciml/4.1/geoSciMLBasic_inspire_mandatory.sch>`_
checks that all properties required by INSPIRE have been provided and `http://schemas.geosciml.org/geosciml/4.1/geoSciML_inspire_vocabularies.sch <http://schemas.geosciml.org/geosciml/4.1/geoSciML_inspire_vocabularies.sch>`_
checks that the appropriate INSPIRE vocabulary terms have been used.

There are six packages in GeoSciML. Two are required
for INSPIRE services: GeoSciML-Basic and Borehole. Only GeoSciML-Basic is
required for a 5 star OneGeology service. This section will describe those
parts of these packages which are the minimum requirement for conformance with
the INSPIRE geology application schema. The parts required for a One Geology
service are a subset of the INSPIRE ones and are highlighted as they are
covered.

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

Figure 1 Examples of encoding
nil values

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

The INSPIRE UML class diagram
for GeologicFeature, MappedFeature, GeologicEvent and ThematicClass is shown in
Figure 2 and the UML of the equivalent GeoSciML classes in Figure 3.

The MappedFeature and
GeologicFeature objects are at the core of GeoSciML. A MappedFeature can be
considered an occurrence, such as a polygon on a geologic map, of a real world
GeologicFeature the full extent of which is unknown. It is independent of
geometry, so the same GeologicFeature can have different MappedFeature
instances, representing mapped polygons at different scales or a modelled
volume for example. Each MappedFeature, however, can be specified by only one
GeologicFeature. The specification association, from MappedFeature to
GeologicFeature, is required by INSPIRE. An INSPIRE service provides a
collection of MappedFeatures. A OneGeology service provides a collection of
MappedFeatures specified by GeologicUnit features.

GeologicFeature is the abstract parent class for
GeologicUnit, GeologicStructure, GeomorphologicFeature and GeologicEvent. This
section will describe those properties which apply to all GeologicFeatures, but
these will always be encoded as part of one of the specialist child classes. The
INSPIRE GeologicFeature class has two associations, themeClass and
geologicHistory. The themeClass association should be encoded using the
GeoSciML classifier association, which will be explained in section 2.6, and geologicHistory should be encoded using the GeoSciML geologicHistory property
which has GeologicEvent values, explained in section 2.2.

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

Figure 4: Example of the
encoding of sampling frame

Mapped Feature - geometry (shape)
""""""""""""""""""""""""""""""""""

The geometry
of each MappedFeature is provided by the shape association to GM_Object. Figure 5 gives an example of encoding a polygon. This property is (obviously) required for a OneGeology service and should have Polygon values.

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

The
INSPIRE UML class diagram for Borehole is shown in 19 and the UML of the GeoSciML Borehole package in Figure 20. Although the modelling of boreholes in GeoSciML is more complex it includes everything required for INSPIRE which can therefore be encoded with
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

PostGIS
---------

Installing PostGIS
^^^^^^^^^^^^^^^^^^^

The `PostGIS Installation <http://www.postgis.net/install>`_ page contains instructions on how to install PostGIS for different operating systems. We have used both the `Enterprise DB Windows Installer <https://www.enterprisedb.com/downloads/postgres-postgresql-downloads>`_ on Windows and the `PostgreSQL Yum repository <https://yum.postgresql.org/>`_ on CentOS.

.. todo::

    Don't think we want to go into more detail on installation ourselves?

Shapefile
----------

.. todo::

   Possible need for an id column (WFS?). Convert referenced appendices (now just A) from the old cookbook?

OneGeology does not recommend using Shapefiles as the data source for your services but, if you already have your data in this format, it can be used as a data source with some restrictions.

If you wish to set up a :term:`SLD enabled WMS` or :term:`Simple feature WFS` using the standard fields needed for age and lithology highlighting in the Portal or following one of the standard 'Lite' schemas then the 10 character limit on field names in Shapefiles means your server will need to map shorter Shapefile field names to the longer expected field names in the standards. We provide some `recommended shapefile definitions <short_names.html>`_ for some GeoSciML-Lite features that are reasonably readable and would enable using common mapping files to produce services using the full names.

Another consideration might be that, if the coordinate system of your Shapefile is not EPSG:4326 and your service is predominantly to be used in the OneGeology Portal, then your server will have to do a lot of on-the-fly coordinate conversion. To ameliorate this you can `convert the coordinate system of your Shapefile </wmsCookbook/appendixA.html>`_. The tools referred to in the previous link are available from http://www.gdal.org if you haven't done the MS4W download that it assumes.

Recommend ESRI shapefile definitions for GeoSciML-Lite
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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





******************
OneGeology Profile
******************

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
==========================

WMS, WFS, and WCS services all provide metadata about the service through their response to a GetCapabilities request. OneGeology places some requirements on this metadata, some to help the Portal operate and some as good practice to enable users to search for services, know how they can use the data and get further information. The different service types have similar but not identical structures for their GetCapabilities responses; differences will be pointed out below. In particular, the WCS 2.0 standard changed the structure considerably, moving coverage specific metadata to DescribeCoverage requests so, for the moment, we need a WCS 1.0.0 structure document to enable us to harvest coverage specific metadata easily.

.. _service_provision_onegeology_profile_service_title:

Service title
-------------

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
----------------

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
----

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
------------------

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
--------

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
-------------------

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
-------------

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
---------------

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
===================================

Depending on which service type you are serving the actual data sets that you are supplying will be delivered as a number of layers (WMS), coverages (WCS) or features (WFS). Each of these can have their own specific metadata. The OneGeology portal allows the selection of WMS layers and WCS coverages to view and presents selected aspects of the layer/coverage metadata in its layer list. These metadata are also used to arrange layers/coverages under geographical areas and under themes and enable searching for layers/coverages including searching on some aspects of their functionality.

WFS are a bit different. In the Portal we do not list registered WFS separately but attach them to one or more WMS layers that portray some aspect of one or more of the features of the WFS. In OneGeology we are most focussed on WFS that supply features conforming to particular community standards whether simple feature standards like GeoSciML-Lite and ERML-Lite or complex feature standards like GeoSciML and ERML. In these cases the number of feature types available from a WFS is limited by the number of feature types in the community standards and you would normally be serving data for one data set from each WFS endpoint. (If you serve more than one data set from a given endpoint the client will need to know how to formulate a query that will only retrieve features from a particular data set.) Although the metadata are not presented directly in the Portal it is still recommended to add useful metadata for searching in the catalogue and for presentation in other WFS clients. If you don't yet have a suitable mapping from your data to a full community schema you may still be able to use your server software to generate automatically a simple feature WFS corresponding to a given WMS layer based on the same underlying dataset. In this case the features won't strictly conform to any community schema but may still have some common field names that allow a certain level of interoperability.

.. todo::

   Need to explain the above about naming of layers and features according to standard names or not and interoperability functionality just by having field names that can be portrayed in an SLD enabled WMS vs having the feature types as well following the standard names. Of course in latter case a fixed SLD can be used but in former the layer name has to be dynamically matched (as the portal does). Need a clearer explanation of all this. Maybe generic WMS/WFS/WCS standard explanation section with some example layer/feature/coverage names for illustration (don't have to be actual running services although that might help).

.. _service_provision_onegeology_profile_layer_names:

WMS layer and WCS coverage naming
---------------------------------

The OneGeology Portal allows selection of WMS layers and WCS coverages for display from a list and so it is important to have a naming convention that ensures unique titles for each of these layers and coverages. This convention has been designed to give readable, informative titles.

Both WMS and WCS have names which are used by software to select which layers/coverages are returned and human readable titles which are used for presenting in a client interface. The former do not need to be human readable and some server software may not allow much control over their format. The latter are the way layers and coverages are presented to a user for selection so it is important that they are understandable and informative. Thus OneGeology has a naming convention which we require for the human readable titles. It can also be friendly to make the machine readable names understandable for testing or writing custom clients so, although we don't make it a requirement, we do recommend that you follow the conventions below for the machine readable names as well if you can.

.. todo::

   We need to discuss what we want to do with increasing numbers of services that might not be primarily OneGeology ones and that might have their own conventions to adhere to.

   Have changed the requirement for a language code below to just be if there is more than one language version of a service rather than the previous more complex formulation. Haven't consulted on this though.

The titles should contain the following components which are explained in more detail below: **[Geographical extent]** of the data in the layer, then **[Data owner organization]** (not service provider), then **[Language code]** (if more than one language being provided), then **[Scale]**, then **[Theme]**.

Geographic extent
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^

Geographic extent information is followed by the data owner organization code (not service provider), the same as recommended for the service title.

Language
^^^^^^^^

If you need to include language in your layer you should use the same ISO 639-1 two-letter language code `(https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) <https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes>`_ as recommended for the service title and include it *after* the data owner organization code .

Scale
^^^^^

Scale comes next and is shortened using SI symbols:

* "M" for Million (upper case)
* "k" for thousand (lower case)

Such that a 1:1 000 000 scale map would be represented in the layer title as 1:1M and a 1:625 000 scale map would be represented in the layer title as 1:625k.  In the layer names we shorten this further by removing the "1:" portion so that a 1:1 000 000 scale map is represented as 1M and a 1:625 000 scale map is represented as 625k.

Additionally, if the map scale is represented in the layer title as 1:1.5M we can lose the decimal point in the layer name by using 1500k.  **Note**, you do not have to use the 1500k format over the 1.5M format, rather we offer this format as an alternative, if your server software has an issue with dots in the layer name.

Theme
^^^^^

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
^^^^^^^^^^^^^^^^^^^^

GBR BGS 1:625k Bedrock Age

FRA BRGM 1:1M Formations géologiques - France Continentale

FRA BRGM 1:1M Formations géologiques - Guyanne

Note, it is acceptable to replace the ISO country code with a more readable name in the layer title

Layer name examples
^^^^^^^^^^^^^^^^^^^

Remember that older versions of MapServer had a limit of 20 Characters for LAYER names; though this restriction no longer applies.

FRA_BRGM_1M_GeoUnits

GBR_BGS_625k_BA

World_25M_GeolUnits

Europe_BGR_5M_BLS

US-KY_KGS_24k_Faults

INSPIRE layer naming considerations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If your service falls under the INSPIRE naming conventions, then both the layer name and the layer title are fixed according to the legislation. For example the `D2.8.II.4 Data Specification on Geology–Technical Guidelines <http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_GE_v3.0.pdf>`_ tell us (section 11.1 ~ Layers to be provided by INSPIRE view services) that any layer to do with lithology or age must have the name *GE.GeologicUnit* and title *Geologic Units*.  See the `layer-naming <https://themes.jrc.ec.europa.eu/discussion/view/13952/layer-naming>`_ discussion on the INSPIRE Thematic Clusters Geology forum for fuller details.

To have a multiple layer geology service that adheres to the INSPIRE naming rules we believe the only option is for you to configure group layering. In such a situation, the layer name and title rules set out above relate to the grouped (or sub layers).  Whereas the INSPIRE name and title relate to the group (or parent) layer. If your INSPIRE service is only serving layers of one type, one way of applying group layering would be to use the WMS root layer name and title (not service name and title) as the grouping layer.

.. todo::

   I would just drop any OneGeology requirement on WMS Root Layer name but do a double check of how it appears in different clients to see if it might be helpful for some. Not used by Portal. Does this only apply to WMS as a view service? Can group layers be done in WCS and do we need them or is WCS only a download service or could it be used as a view service as well?

Summary of layer/coverage/feature metadata
------------------------------------------

For WMS layers and WCS coverages the machine readable name and human readable name should follow the conventions above. For WFS, if the data is being put out following a standard community schema then the machine readable name will be fixed according to the schema and a reasonable human readable name will probably be defined by the schema as well. If it is a simple WFS mirroring a WMS layer dataset then the names can match the WMS layer names.These go in the below places in the capabilities response.

.. todo::

   Need to mention ignoring any name prefix in machine readable name if relevant (just another constraint of software on machine readable names.

Machine readable name
^^^^^^^^^^^^^^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/Name (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:name (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/wcs:CoverageId (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Name (2.0.x)

Human readable name
^^^^^^^^^^^^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/Title (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:label (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Title (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Title (2.0.x)

.. _service_provision_onegeology_profile_layer_abstract:

Abstract
^^^^^^^^

.. todo::

   Consider whether the standard feature description in a community schema WFS is the best thing to put in the abstract or whether it should be more tailored to individual service and data set.

You must provide a description of your layer/coverage data. You may wish to include other metadata, such as information about your organization and other data you make available. You may also wish to include a statement on access constraints. For features following a standard community Schema this may not be so relevant at the feature level in that a service will be providing data for a certain data set and the abstract description of the features will be just the general description of that feature type in the schema.

* /WMS_Capabilities/Capability/Layer/Layer/Abstract (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:description (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Abstract (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Abstract (2.0.x)

.. _service_provision_onegeology_profile_layer_keywords:

Keywords
^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/KeywordList/Keyword (1.3.0)
* /WCS_Capabilities/ContentMetadata/CoverageOfferingBrief/keywords/keyword (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Keywords/ows:Keyword (2.0.x)

The Keyword "OneGeology" must be present to be able to search for services and layers with this keyword. OneGeologyEurope participants should also include relevant keywords chosen from the keyword list created for that project and listed in `Appendix I </wmsCookbook/appendixI.html>`_. The main purpose of these keywords is to make your services discoverable by a user searching in a catalogue of services, so a clearly formed but limited list of geosciences domain specific is ideal and all OneGeology global participants may also want to consider using items from this proposed OneGeology-Europe list, which has been formed by looking at many such lists available around the world including the European GEMET thesaurus found at: `http://www.eionet.europa.eu/gemet/en/themes/ <http://www.eionet.europa.eu/gemet/en/themes/>`_.

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

To help classify your service in the portal according to the thematic keyword list (as detailed in `Appendix I </wmsCookbook/appendixI.html>`_), you should also use one or more *thematic@value keywords*.

**Please note** services using GeoSciML-Lite also require the following keyword: **Geosciml_portrayal_age_or_litho_queryable** (GeoSciML-Lite was previously called GeoSciML-Portrayal.)

For those WMS layers with an associated GeoSciML WFS that you would like to query using the OneGeology Portal thematic analysis tool, you will need to add the appropriate **GeoSciML32_wfs_age_or_litho_queryable** or **GeoSciML4_wfs_age_or_litho_queryable** keyword.

WMS Specific Metadata
---------------------

The following sections were defined for the earlier WMS only specific OneGeology profile and haven't yet been considered for updating to other service types.

.. _service_provision_onegeology_profile_layer_extent:

Extent
^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/EX_GeographicBoundingBox (1.3.0)

In WMS version 1.3.0 four elements each describing a single bounding limit (always in the order: west, east, south, north). The purpose of these extent values is to facilitate geographic searches; values may be approximate.

.. todo::

    Not sure about 2* requirement for a LatLon bounding box using EPSG:4326. Where is this used? If it isn't required for the portal then what is it important for? Does GeoNetwork catalogue use it for plotting?

    This probably is GeoNetwork related, certainly for a WMS 1.3.0 the element that is used to show the extent (<EX_GeographicBoundingBox>) is the same element as is used by GeoNetwork / ISO 19139 XML to hold extent data.

    WMS 1.1.1 has LatLonBoundingBox and WMS 1.3.0 has EX_GeographicBoundingBox, they are equivalent.  WFS 1.0.0 has LatLongBoundingBox, WFS 1.1.0 and 2.0.0 have WGS84BoundingBox. WCS 1.0.0 has lonLatEnvelope, WCS 1.1.1 and WCS 2.0.0 have WGS84BoundingBox

.. _service_provision_onegeology_profile_layer_crs:

Spatial/Coordinate reference system
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/Style/LegendURL (1.3.0)

We require you to have some sort of legend to accompany your map data. In many cases your server software will create this for you automatically using the inbuilt SLD capability. If your WMS server is not SLD capable, or if you have a complex legend, you may add the LegendURL manually in your GetCapabilities response document.  See below :ref:`style_examples`.

.. _style_examples:

Layer styling information
^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Depending on the data you have available for each layer and depending on your WMS software, you may be able to configure what is returned in response to GetFeatureInfo requests on each layer, either to format the look of the data returned or to restrict the data attributes returned.

Ideally the response should include a field for age/lithology/lithostratigraphy as appropriate for each layer.  You may choose to include other information you consider useful but please try to exclude data fields that only have meaning internal to your organization.

Preferably it should be possible to retrieve the information in at least text/html and text/plain formats.

.. _service_provision_onegeology_profile_core_metadata:

Core TC211/ISO:19115:2003 Metadata
----------------------------------

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

*******************
Setting up a Server
*******************

There are a wide variety of proprietary and open source software packages that can be used to provide the OGC web services of interest to OneGeology. We cannot possibly describe them all but this section gives guidance on how to use some with which we do have experience to set up your OneGeology services. If you are interested and able to provide similar guidance for a software package not listed below then please get in touch to discuss adding your documentation here. Currently the only software we have successfully used to provide *all* the service types relevant for OneGeology is GeoServer.

To start with there are some links to downloadable example data sets which you can use to experiment with setting up the servers before you try getting your own data into an appropriate format.

At the end there is an additional section on setting up the Apache HTTPD server to act as a reverse proxy which may be useful if you need to provide a unified web address and port for accessing your OneGeology and possibly other web services.

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
SERVER SETUP folder

XXXXXXXXXXXXXXXXXXX

GeoSciML
--------

GeoSciML (GeoScience Markup Language) is a GML (Geography Markup Language) application language for geoscience.

**The design, build and deployment of information technologies that enable and advance geoscience information management, analysis and delivery will require systems that are interoperable following international agreed standards that are relevant to the geosciences.**

It is an XML schema for data exchange over the Internet that incorporates the ability to represent geography (geometries e.g. polygons, lines and points using the OGC's GML specification) as part of the features that are being exchanged. The range of features being offered for exchange are defined by the domain or subject area of geoscience or the geological sciences.

GeoSciML accommodates the short-term goal of representing geoscience information associated with geological maps and observations, as well as being extensible in the long-term to other geoscience data. It draws from many geoscience data model efforts, and from these establishes a common suite of feature types based on geological criteria (units, structures, fossils) or artefacts of geological investigations (specimens, sections, measurements). Supporting objects are also considered (timescale, lexicons, etc), so that they can be used as classifiers for the primary objects.

GeoSciML is based on `W3C <http://www.w3c.org>`_, OGC, `CGI Data Model <http://www.seegrid.csiro.au/twiki/bin/view/CGIModel/WebHome>`_  and ultimately `ISO <http://www.iso.org>`_ international standards for data exchange over the Internet. GeoSciML is being designed under the umbrella of the `IUGS Commission <http://www.iugs.org/>`_ on the Management and Application of Geoscience Information (CGI) and its `CGI Interoperability Working Group <http://cgi-iugs.org/tech_collaboration/interoperability_working_group.html>`_.

For further detailed information on the development of GeoSciML, see http://www.cgi-iugs.org/tech_collaboration/geosciml.html

.. figure:: /images/geosciml.gif
    :width: 417px
    :align: center
    :height: 249px
    :alt: GeoSciML Data Model
    :figclass: align-center

    GeoSciML Data Model


Web Services
----------------

How to setup web services to serve data to OneGeology. We provide a basic explanation of how to do it easily.

WMS
--------

- Be awesome
- Make things faster

WFS
------------

Install $project by running:

    install project

WCS
----------

- Issue Tracker: github.com/$project/$project/issues
- Source Code: github.com/$project/$project


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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
"""""

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
""""""""""""""""""

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
""""""""""""""

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
"""""""""""""""""

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The OneGeology Portal allows selection of WMS layers and WCS coverages for display from a list and so it is important to have a naming convention that ensures unique titles for each of these layers and coverages. This convention has been designed to give readable, informative titles.

Both WMS and WCS have names which are used by software to select which layers/coverages are returned and human readable titles which are used for presenting in a client interface. The former do not need to be human readable and some server software may not allow much control over their format. The latter are the way layers and coverages are presented to a user for selection so it is important that they are understandable and informative. Thus OneGeology has a naming convention which we require for the human readable titles. It can also be friendly to make the machine readable names understandable for testing or writing custom clients so, although we don't make it a requirement, we do recommend that you follow the conventions below for the machine readable names as well if you can.

.. todo::

   We need to discuss what we want to do with increasing numbers of services that might not be primarily OneGeology ones and that might have their own conventions to adhere to.

   Have changed the requirement for a language code below to just be if there is more than one language version of a service rather than the previous more complex formulation. Haven't consulted on this though.

The titles should contain the following components which are explained in more detail below: **[Geographical extent]** of the data in the layer, then **[Data owner organization]** (not service provider), then **[Language code]** (if more than one language being provided), then **[Scale]**, then **[Theme]**.

Geographic extent
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^

Geographic extent information is followed by the data owner organization code (not service provider), the same as recommended for the service title.

Language
^^^^^^^^

If you need to include language in your layer you should use the same ISO 639-1 two-letter language code `(https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) <https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes>`_ as recommended for the service title and include it *after* the data owner organization code .

Scale
^^^^^

Scale comes next and is shortened using SI symbols:

* "M" for Million (upper case)
* "k" for thousand (lower case)

Such that a 1:1 000 000 scale map would be represented in the layer title as 1:1M and a 1:625 000 scale map would be represented in the layer title as 1:625k.  In the layer names we shorten this further by removing the "1:" portion so that a 1:1 000 000 scale map is represented as 1M and a 1:625 000 scale map is represented as 625k.

Additionally, if the map scale is represented in the layer title as 1:1.5M we can lose the decimal point in the layer name by using 1500k.  **Note**, you do not have to use the 1500k format over the 1.5M format, rather we offer this format as an alternative, if your server software has an issue with dots in the layer name.

Theme
^^^^^

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
^^^^^^^^^^^^^^^^^^^^

GBR BGS 1:625k Bedrock Age

FRA BRGM 1:1M Formations géologiques - France Continentale

FRA BRGM 1:1M Formations géologiques - Guyanne

Note, it is acceptable to replace the ISO country code with a more readable name in the layer title

Layer name examples
^^^^^^^^^^^^^^^^^^^

Remember that older versions of MapServer had a limit of 20 Characters for LAYER names; though this restriction no longer applies.

FRA_BRGM_1M_GeoUnits

GBR_BGS_625k_BA

World_25M_GeolUnits

Europe_BGR_5M_BLS

US-KY_KGS_24k_Faults

INSPIRE layer naming considerations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If your service falls under the INSPIRE naming conventions, then both the layer name and the layer title are fixed according to the legislation. For example the `D2.8.II.4 Data Specification on Geology–Technical Guidelines <http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_GE_v3.0.pdf>`_ tell us (section 11.1 ~ Layers to be provided by INSPIRE view services) that any layer to do with lithology or age must have the name *GE.GeologicUnit* and title *Geologic Units*.  See the `layer-naming <https://themes.jrc.ec.europa.eu/discussion/view/13952/layer-naming>`_ discussion on the INSPIRE Thematic Clusters Geology forum for fuller details.

To have a multiple layer geology service that adheres to the INSPIRE naming rules we believe the only option is for you to configure group layering. In such a situation, the layer name and title rules set out above relate to the grouped (or sub layers).  Whereas the INSPIRE name and title relate to the group (or parent) layer. If your INSPIRE service is only serving layers of one type, one way of applying group layering would be to use the WMS root layer name and title (not service name and title) as the grouping layer.

.. todo::

   I would just drop any OneGeology requirement on WMS Root Layer name but do a double check of how it appears in different clients to see if it might be helpful for some. Not used by Portal. Does this only apply to WMS as a view service? Can group layers be done in WCS and do we need them or is WCS only a download service or could it be used as a view service as well?

Summary of layer/coverage/feature metadata
------------------------------------------

For WMS layers and WCS coverages the machine readable name and human readable name should follow the conventions above. For WFS, if the data is being put out following a standard community schema then the machine readable name will be fixed according to the schema and a reasonable human readable name will probably be defined by the schema as well. If it is a simple WFS mirroring a WMS layer dataset then the names can match the WMS layer names.These go in the below places in the capabilities response.

.. todo::

   Need to mention ignoring any name prefix in machine readable name if relevant (just another constraint of software on machine readable names.

Machine readable name
^^^^^^^^^^^^^^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/Name (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:name (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/wcs:CoverageId (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Name (2.0.x)

Human readable name
^^^^^^^^^^^^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/Title (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:label (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Title (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Title (2.0.x)

.. _service_provision_onegeology_profile_layer_abstract:

Abstract
^^^^^^^^

.. todo::

   Consider whether the standard feature description in a community schema WFS is the best thing to put in the abstract or whether it should be more tailored to individual service and data set.

You must provide a description of your layer/coverage data. You may wish to include other metadata, such as information about your organization and other data you make available. You may also wish to include a statement on access constraints. For features following a standard community Schema this may not be so relevant at the feature level in that a service will be providing data for a certain data set and the abstract description of the features will be just the general description of that feature type in the schema.

* /WMS_Capabilities/Capability/Layer/Layer/Abstract (1.3.0)
* /wcs:WCS_Capabilities/wcs:ContentMetadata/wcs:CoverageOfferingBrief/wcs:description (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Abstract (2.0)
* /wfs:WFS_Capabilities/wfs:FeatureTypeList/wfs:FeatureType/wfs:Abstract (2.0.x)

.. _service_provision_onegeology_profile_layer_keywords:

Keywords
^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/KeywordList/Keyword (1.3.0)
* /WCS_Capabilities/ContentMetadata/CoverageOfferingBrief/keywords/keyword (1.0.0)
* /wcs:Capabilities/wcs:Contents/wcs:CoverageSummary/ows:Keywords/ows:Keyword (2.0.x)

The Keyword "OneGeology" must be present to be able to search for services and layers with this keyword. OneGeologyEurope participants should also include relevant keywords chosen from the keyword list created for that project and listed in `Appendix I </wmsCookbook/appendixI.html>`_. The main purpose of these keywords is to make your services discoverable by a user searching in a catalogue of services, so a clearly formed but limited list of geosciences domain specific is ideal and all OneGeology global participants may also want to consider using items from this proposed OneGeology-Europe list, which has been formed by looking at many such lists available around the world including the European GEMET thesaurus found at: `http://www.eionet.europa.eu/gemet/en/themes/ <http://www.eionet.europa.eu/gemet/en/themes/>`_.

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

To help classify your service in the portal according to the thematic keyword list (as detailed in `Appendix I </wmsCookbook/appendixI.html>`_), you should also use one or more *thematic@value keywords*.

**Please note** services using GeoSciML-Lite also require the following keyword: **Geosciml_portrayal_age_or_litho_queryable** (GeoSciML-Lite was previously called GeoSciML-Portrayal.)

For those WMS layers with an associated GeoSciML WFS that you would like to query using the OneGeology Portal thematic analysis tool, you will need to add the appropriate **GeoSciML32_wfs_age_or_litho_queryable** or **GeoSciML4_wfs_age_or_litho_queryable** keyword.

WMS Specific Metadata
---------------------

The following sections were defined for the earlier WMS only specific OneGeology profile and haven't yet been considered for updating to other service types.

.. _service_provision_onegeology_profile_layer_extent:

Extent
^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/EX_GeographicBoundingBox (1.3.0)

In WMS version 1.3.0 four elements each describing a single bounding limit (always in the order: west, east, south, north). The purpose of these extent values is to facilitate geographic searches; values may be approximate.

.. todo::

    Not sure about 2* requirement for a LatLon bounding box using EPSG:4326. Where is this used? If it isn't required for the portal then what is it important for? Does GeoNetwork catalogue use it for plotting?

    This probably is GeoNetwork related, certainly for a WMS 1.3.0 the element that is used to show the extent (<EX_GeographicBoundingBox>) is the same element as is used by GeoNetwork / ISO 19139 XML to hold extent data.

    WMS 1.1.1 has LatLonBoundingBox and WMS 1.3.0 has EX_GeographicBoundingBox, they are equivalent.  WFS 1.0.0 has LatLongBoundingBox, WFS 1.1.0 and 2.0.0 have WGS84BoundingBox. WCS 1.0.0 has lonLatEnvelope, WCS 1.1.1 and WCS 2.0.0 have WGS84BoundingBox

.. _service_provision_onegeology_profile_layer_crs:

Spatial/Coordinate reference system
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^

* /WMS_Capabilities/Capability/Layer/Layer/Style/LegendURL (1.3.0)

We require you to have some sort of legend to accompany your map data. In many cases your server software will create this for you automatically using the inbuilt SLD capability. If your WMS server is not SLD capable, or if you have a complex legend, you may add the LegendURL manually in your GetCapabilities response document.  See below :ref:`style_examples`.

.. _style_examples:

Layer styling information
^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Depending on the data you have available for each layer and depending on your WMS software, you may be able to configure what is returned in response to GetFeatureInfo requests on each layer, either to format the look of the data returned or to restrict the data attributes returned.

Ideally the response should include a field for age/lithology/lithostratigraphy as appropriate for each layer.  You may choose to include other information you consider useful but please try to exclude data fields that only have meaning internal to your organization.

Preferably it should be possible to retrieve the information in at least text/html and text/plain formats.

.. _service_provision_onegeology_profile_core_metadata:

Core TC211/ISO:19115:2003 Metadata
----------------------------------

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
