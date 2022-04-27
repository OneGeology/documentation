
****************
Data preparation
****************

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
====================

Scanning
--------

Your chosen paper map may look something like this one from the Dutch Geological Survey of Dutch Guyana or Suriname:

.. figure:: images/paperMap.jpg
   :width: 600
   :height: 528
   :alt: Example geological map to scan

   Example geological map to scan

Step 1
^^^^^^

It is important to find a large scanner in your city, which could cover a whole paper map.  If this scanner is not available at your survey, you may try the Topographical Survey or a large bookshop or book printer.

Step 2A
^^^^^^^

If you could use a large scanner, you can scan the whole map at one time.  But remember to scan the geological map portion into a separate file from that for the legend i.e. you will have two files one for the map and one for the legend.  Alternatively, make a copy of an original digital image of the whole map face and cut out the map from the legend.

The preferable output format should be .TIFF as this format keeps most information, but if  you have a slow Personal Computer, you could temporarily work with a JPEG copy.  The file size is than much smaller and it can be accessed and geo-referenced faster.

Good software for cropping (or cutting out) the legend or map from the whole scanned image is `IrfanView <http://www.irfanview.com/>`_, `Adobe Photoshop <http://www.adobe.com/uk/products/photoshopfamily.html>`_ or `GNU Image Manipulation Program (GIMP) <https://www.gimp.org/>`_.

Tip: This cropped map is now ready for geo-referencing.

Note, an alternative approach is to georeference the whole scanned image, then use a GIS (such as `QGIS <https://www.qgis.org/en/site/about/index.html>`_) to crop out the map sheet using a polygon mask.  You might use this technique when your original data is a scan of a old map sheet.

Step 2B
^^^^^^^

For larger maps, or if you have only a small scanner, the map should be scanned in parts and later stitched together.

.. figure:: images/scanningAMap.jpg
   :width: 414
   :height: 253
   :alt: Orientation of map for scanning

   Orientation of map for scanning


If you scan in parts always try to keep the crossings of the horizontal and vertical black lines in each of the four corners.  The straight horizontal and vertical black lines on the map are the altitude and longitude.  Then the stitching and geo-referencing will be much easier.

The output format should be .TIFF as this format keeps most pixel information available.

Step 2C
^^^^^^^

If scanners are not available, you could use a good digital camera.  Unfold the map on a well lit place without glare or light reflections.  Sometimes white sheets on the side will diffuse the light and prevent ugly reflections from the sun or from the light-bulb.  Take a picture right above the centre of the map.

Make several pictures with different lighting and shutter speed.  Choose the best colourful result.  Usually the export format is .JPG.

Step 3 ~ Stitching
^^^^^^^^^^^^^^^^^^

For the stitching of map parts many applications or free software are available, such as such as `GNU Image Manipulation Program (GIMP) <https://www.gimp.org/>`_, `OSSIM ImageLinker <http://www.ossim.org/>`_, or `QGIS <https://www.qgis.org/en/site/about/index.html>`_.

Georeferencing a scanned map
----------------------------

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
------------------------------

Although your scanned image will be rectangular in shape, nearly all mapped geographic regions will have irregularly shaped boundaries.  Thus it is preferable to make the background parts of your image transparent rather than a solid background colour which will obscure neighbouring regions.  The variety of image formats that are usable with MapServer and their various advantages and disadvantages is a complex subject which we cannot be authoritative about.

We have found 32-bit TIFF (RGB plus alpha layer) or 8-bit palette PNG with a transparent background colour work; you may wish to experiment.

See `MapServer raster data <http://www.mapserver.org/input/raster.html>`_ for more information.

The legend for the scanned map
------------------------------

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
============

GeoSciML-Lite and EarthResourceML-Lite (ERML-Lite) are simplified schemas that take the form of a flat table of attributes (conformant to OGC Simple Features Level-0 profile). These were previously called GeoSciML-Portrayal and EarthResourceML-Portrayal.

.. _service_provision_data_preparation_lite_geosciml:

GeoSciML-Lite
-------------

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
^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^

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
--------------------

EarthResourceML-Lite is a model and schema for simple map services (eg, WMS and WFS Simple Features). It is an abridged version of the full EarthResourceML model and can be used to deliver simplified views on mineral occurrences and their commodities, mines, mining activities and mine waste products.

There are six EarthResourceML-Lite views descibed in the 2.0 standard, these are:  MineView, CommodityResourceView, MineralOccurrenceView, MiningActivityView, MiningWasteView, and ProcessingPlantView.  Below we lay out what is expected of the views for those features we think that many geological survey organizations will be able to support.

For full details of the ERML-Lite schema see: http://schemas.earthresourceml.org/earthresourceml-lite/2.0/erml-lite.xsd

For full documentation of all the views see http://www.earthresourceml.org/earthresourceml-lite/2.0.1/documentation/


.. _service_provision_data_preparation_lite_mineraloccurrenceview:

MineralOccurrenceView features
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
====================

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
-----------------------------------

.. figure:: images/image001.jpg

   Figure 2: INSPIRE UML class diagram for GeologicFeature, MappedFeature, GeologicEvent and ThematicClass

.. figure:: images/image002.jpg

   Figure 3: UML context diagram for GeoSciML GeologicFeature

The INSPIRE UML class diagram for GeologicFeature, MappedFeature, GeologicEvent and ThematicClass is shown in Figure 2 and the UML of the equivalent GeoSciML classes in Figure 3.

The MappedFeature and GeologicFeature objects are at the core of GeoSciML. A MappedFeature can be considered an occurrence, such as a polygon on a geologic map, of a real world GeologicFeature the full extent of which is unknown. It is independent of geometry, so the same GeologicFeature can have different MappedFeature instances, representing mapped polygons at different scales or a modelled volume for example. Each MappedFeature, however, can be specified by only one GeologicFeature. The specification association, from MappedFeature to GeologicFeature, is required by INSPIRE. An INSPIRE service provides a collection of MappedFeatures. A OneGeology service provides a collection of MappedFeatures specified by GeologicUnit features.

GeologicFeature is the abstract parent class for GeologicUnit, GeologicStructure, GeomorphologicFeature and GeologicEvent. This section will describe those properties which apply to all GeologicFeatures, but these will always be encoded as part of one of the specialist child classes. The INSPIRE GeologicFeature class has two associations, themeClass and geologicHistory. The themeClass association should be encoded using the GeoSciML classifier association, which will be explained in section 2.6, and geologicHistory should be encoded using the GeoSciML geologicHistory property which has GeologicEvent values, explained in section 2.2.

Mapped Feature - mapping frame
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The INSPIRE inspireId
property is of type Identifier and provides the persistent identifier used for
the object by the data provider, for example the code from a stratigraphic
lexicon in the case of a GeologicUnit. In GeoSciML this should be encoded using
gml:identifier which requires both the identifier value, equivalent to
Identifier.localId, and the codespace, equivalent to Identifier.namespace,
identifying the data source (Figure 6).

Geologic Feature - name
^^^^^^^^^^^^^^^^^^^^^^^

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
------------

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
^^^^^^^^^^^^^^^^^^^^^

The INSPIRE name property
provides the name of the GeologicEvent, for example ‘Hercynian Orogeny’. Only
major events such as orogenies are likely to have names and other events should
be recorded as ‘Unnamed event’. The field should be encoded using gml:name.

Geologic Event - youngerNamedAge and olderNamedAge
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The eventProcess property
describes one or more processes that took place during the event to modify the
related GeologicFeature. For an INSPIRE service it should be encoded using
terms drawn from the EventProcessValue vocabulary (`http://inspire.ec.europa.eu/codelist/EventProcessValue <http://inspire.ec.europa.eu/codelist/EventProcessValue>`_). If it is provided for a non-INSPIRE OneGeology
service the CGI Event process vocabulary (`http://resource.geosciml.org/classifier/cgi/eventprocess <http://resource.geosciml.org/classifier/cgi/eventprocess>`_)
should be used.

Geologic Event - eventEnvironment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
--------------------------------

.. figure:: images/image004.jpg

   Figure 9: INSPIRE UML class diagram for GeologicUnit

.. figure:: images/image005.jpg

   Figure 10: UML context diagram for GeoSciML GeologicUnit

The INSPIRE UML class diagram
for GeologicUnit is shown in Figure 9 and the UML of the GeoSciML GeologicUnit package in Figure 10. GeologicUnit is a specialisation of GeologicFeature.  In INSPIRE only the geologicUnitType property is required, along with the
association to compositionPart, and as can be seen this is modelled in an
identical way in GeoSciML.

Geologic Unit - geologic unit type
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The only GeologicUnit attribute that is mandatory for
INSPIRE is geologicUnitType. This indicates the type of the geologic unit, for
example a lithostratigraphic unit or a lithologic unit. Values must be drawn
from the GeologicUnitTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/GeologicUnitTypeValue <http://inspire.ec.europa.eu/codelist/GeologicUnitTypeValue>`_). If
it is provided for a non-INSPIRE OneGeology service the CGI Geologic unit type
vocabulary (`http://resource.geosciml.org/classifier/cgi/geologicunittype <http://resource.geosciml.org/classifier/cgi/geologicunittype>`_)
should be used.

Geologic Unit - composition
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The composition association from GeologicUnit to
CompositionPart provides the means for describing the lithology of the
GeologicUnit. In INSPIRE a GeologicUnit must have at least one CompositionPart,
but can have several where the GeologicUnit is composed of several different
lithologies. For each CompositionPart values for three attributes must be
provided: role, material and proportion. The requirements are the same for a
OneGeology service.

Composition Part - role
^^^^^^^^^^^^^^^^^^^^^^^

Role
defines the relationship of the compositionPart to the GeologicUnit as a whole,
e.g. vein, interbedded constituent, layers, dominant constituent. Values should
be drawn from the CompositionPartRoleValue vocabulary (`http://inspire.ec.europa.eu/codelist/CompositionPartRoleValue <http://inspire.ec.europa.eu/codelist/CompositionPartRoleValue>`_). If it is
provided for a non-INSPIRE OneGeology service the CGI Geologic unit part role
vocabulary (`http://resource.geosciml.org/classifier/cgi/geologicunitpartrole <http://resource.geosciml.org/classifier/cgi/geologicunitpartrole>`_)
should be used.

Composition Part - proportion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The material attribute provides
the lithology of the CompositionPart and is of type LithologyValue (a codelist)
in INSPIRE (Figure 9) whereas in GeoSciML it is modelled as a CompoundMaterial (Figure 12). CompoundMaterial is a specialisation of EarthMaterial and the parent class of RockMaterial. The RockMaterial.lithology property is the equivalent of
INSPIRE CompositionPart.material.

.. figure:: images/image007.png

   Figure 12: UML context diagram for GeoSciML RockMaterial

Rock Material -lithology
^^^^^^^^^^^^^^^^^^^^^^^^

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
------------------

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The faultType property
describes the type of ShearDispacementStructure and should be populated with a
value drawn from the FaultTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/FaultTypeValue <http://inspire.ec.europa.eu/codelist/FaultTypeValue>`_). For a non-INSPIRE OneGeology service the CGI Fault
Type vocabulary (`http://resource.geosciml.org/classifier/cgi/faulttype <http://resource.geosciml.org/classifier/cgi/faulttype>`_)
should be used.

Fold - profileType
^^^^^^^^^^^^^^^^^^

The profileType property describes
the type of fold defined according to its geometry and the younging direction
of the strata. It should be populated using values from the
FoldProfileTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/FoldProfileTypeValue <http://inspire.ec.europa.eu/codelist/FoldProfileTypeValue>`_). There isn’t currently an equivalent CGI vocabulary.

.. todo:: 

   As far as I can see there is still no CGI vocabulary for this property. Again not sure why previous version of cookbook didn’t even bother to say “there is no CGI version”?

Geomorphologic Feature
----------------------

Figure 16 shows the INSPIRE UML class diagram for geomorphology, and Figure 17 the equivalent GeoSciML modeling. As can be seen
these are modeled in an identical way. GeomorphologicFeature is an abstract
specialization of GeologicFeature with two sub-types, AnthropogenicGeomorphologicFeature
and NaturalGeomorphologicFeature.

.. figure:: images/image011.jpg

   Figure 16: INSPIRE UML class diagram for GeomorphologicFeature

.. figure:: images/image012.jpg

   Figure 17: UML context diagram for GeoSciML GeomorphologicFeature

Natural Geomorphologic Feature - NaturalGeomorphologicFeatureType
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. todo::

   For this and next two properties should I explicitly note that there is no current CGI vocabulary?

The
NaturalGeomorphologicFeatureType property describes the type of
NaturalGeomorphologicFeature and should be populated with a value drawn from
the NaturalGeomorphologicFeatureTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/NaturalGeomorphologicFeatureTypeValue <http://inspire.ec.europa.eu/codelist/NaturalGeomorphologicFeatureTypeValue>`_). There isn’t currently an equivalent CGI vocabulary.

Natural Geomorphologic Feature - activity
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The activity property
describes the level of activity of a NaturalGeomorphologicFeature and should be
populated with a value from the GeomorphologicActivityValue vocabulary (`http://inspire.ec.europa.eu/codelist/GeomorphologicActivityValue <http://inspire.ec.europa.eu/codelist/GeomorphologicActivityValue>`_). There isn’t currently an equivalent CGI vocabulary.

Anthropogenic Geomorphologic Feature - AnthropogenicGeomorphologicFeatureType
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The
AnthopogenicGeomorphologicFeatureType property describes the type of
AnthropogenicGeomorphologicFeature and should be populated with a value drawn
from the AnthropogenicGeomorphologicFeatureTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/AnthropogenicGeomorphologicFeatureTypeValue <http://inspire.ec.europa.eu/codelist/AnthropogenicGeomorphologicFeatureTypeValue>`_). There isn’t currently an equivalent CGI vocabulary.

Thematic Class
--------------

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
--------

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
^^^^^^^^^^^^^^^^^^^^

The INSPIRE inspireId
property is of type Identifier and provides the persistent identifier used for
the borehole by the data provider. In GeoSciML this should be encoded using
gml:identifier which requires both the identifier value, equivalent to
Identifier.localId, and the codespace, equivalent to Identifier.namespace,
identifying the data source (Figure 6).

Borehole - sampledFeature
^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^

.. todo::

   Again note no CGI vocabulary?

The purpose property
describes the purpose for which the Borehole was drilled and should be
populated with a value from the BoreholePurposeValue vocabulary (`http://inspire.ec.europa.eu/codelist/BoreholePurposeValue <http://inspire.ec.europa.eu/codelist/BoreholePurposeValue>`_). In GeoSciML this property is inside
indexData/BoreholeDetails. There isn’t currently an equivalent CGI vocabulary.

Borehole - boreholeLength
^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The BoreholeInterval in
GeoSciML v4.1 does not have a mappingFrame / samplingFrame property as this
will always be the borehole to which it belongs. Thus, although in the INSPIRE
geology theme Schema the property is encoded by referencing the gml:id of the
borehole, for GeoSciML nothing needs specifying explicitly.

BoreholeInterval - geometry (shape)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A BoreholeInterval is
specified by a GeologicFeature in exactly the same way as described in section
2.1 for MappedFeature. The encoding of a GeologicFeature specifying a
MappedInterval is therefore identical to that described above for
MappedFeatures and won’t be repeated here.

BoreholeInterval - mappedIntervalBegin & mappedIntervalEnd
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
-------------------

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The INSPIRE inspireId
property is of type Identifier and provides the persistent identifier used for
the GeologicCollection by the data provider. In GeoSciML this should be encoded
using gml:identifier which requires both the identifier value, equivalent to Identifier.localId,
and the codespace, equivalent to Identifier.namespace, identifying the data
source (Figure 28).

GeologicCollection - name
^^^^^^^^^^^^^^^^^^^^^^^^^

The INSPIRE name property
provides the name of the GeologicCollection. It should be encoded using
gml:name (Figure 28).

Geologic Collection - collectionType
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. todo::

   A CGI vocab based on the INSPIRE code list is a CGI draft schema. Need to check when this gets published.

The collectionType
property describes the type of collection and should be populated with a value
from the CollectionTypeValue vocabulary (`http://inspire.ec.europa.eu/codelist/CollectionTypeValue <http://inspire.ec.europa.eu/codelist/CollectionTypeValue>`_) (Figure 28). At the time of writing an equivalent CGI vocabulary has been drafted but not yet published.

Geologic Collection - member
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In INSPIRE there are four
types of feature which can be members of a GeologicCollection: MappedFeature;
Borehole; GeophObject; and GeophObjectSet (Figure 26). GeophObject and GeophObjectSet are features in the geophysics application schema and won’t be discussed further here. In GeoSciML the member
association from GSML to GSMLItem allows the members of a GSML collection to be
any of the types in the GSMLItem union class. The types of member of an INSPIRE
GeologicCollection can be mapped to these: MappedFeature maps to mappedItem and
Borehole to samplingFeatureItem (Figure 28). Figure 27 shows the encoding of a MappedFeature as a member of a GSML collection.

MD_Metadata - contact
^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Although the
MD_DataIdentification abstract property is not required by INSPIRE it is
mandatory for MD_DataIdentification. It should be populated with a text description
of the GeologicCollection (Figure 34).

MD_DataIdentification - language
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Although the
MD_DataIdentification language property is not required by INSPIRE it is
mandatory for MD_DataIdentification. It identifies the language(s) used in the
GeologicCollection and should be encoded using the language codes defined in
ISO639-2 (Figure 34).

If the dataset has no natural
language the special code of "zxx" of the ISO 639-2/B reserved for
"no linguistic content; not applicable" shall be used.

MD_DataIdentification - topicCategory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
