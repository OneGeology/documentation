=======================================================================================
Considerations for converting a MapServer based OneGeology-Europe service \| OneGeology
=======================================================================================

.. container::
   :name: outer_container

   .. container::
      :name: content

      .. container:: fullwidth

         .. rubric:: Considerations for converting a MapServer based
            OneGeology-Europe service
            :name: considerations-for-converting-a-mapserver-based-onegeology-europe-service
            :class: technical_progress_side_menu

         .. rubric:: Adding INSPIRE extended capabilities
            :name: adding-inspire-extended-capabilities

         When converting a MapServer (+ 1GE Connector) OneGeology-Europe
         service to an INSPIRE compliant GeoSciML-Portrayal WMS (without
         the 1GE Connector) the first thing you will need to do is
         upgrade your MapServer version to 6.2.0 (or above) to ensure
         you get the Extended Capabilities section.

         To update/upgrade your MapServer (on Windows) installation you
         have several options. The current tested option for 64-bit
         Windows, Apache 2.4, and MapServer 6.4.1 is to use the
         `GISInternals <http://www.gisinternals.com/release.php>`__
         supplied binaries, see `section 4.4.3 <4_4_3.html>`__ for
         details of how to install and configure such a service. The
         original method for installing a MapServer for Windows (MS4W)
         service for OneGeology services has recently been significantly
         updated but we have not yet had an opportunity to check that it
         installs and is configured it in the same way as described in
         the cookbook for earlier versions. See http://www.ms4w.com/ for
         further details. Another option is to install MapServer by
         using the OSGeo4W binary distribution, see
         http://trac.osgeo.org/osgeo4w/ for further details.

         For example to add a scenario 1 INSPIRE extended capabilities
         section (where you have an external XML document or service
         that provides such a document containing metadata for your WMS
         service) you would use the following parameters in your SERVICE
         > WEB > METADATA:

         ::

                        "WMS_LANGUAGES" "eng"
                        "WMS_INSPIRE_CAPABILITIES" "URL"
                        "WMS_INSPIRE_METADATAURL_FORMAT" "application/xml"
                        "WMS_INSPIRE_METADATAURL_HREF" 
                        "http://metadata.bgs.ac.uk/geonetwork/srv/en/csw?SERVICE=CSW&REQUEST=GetRecordById&
                        ID=7822e848-822d-45a5-8584-56d352fd2170&elementSetName=full&OutputSchema=csw:IsoRecord&"

         Which would create:

         ::

            <inspire_vs:ExtendedCapabilities>
                <inspire_common:MetadataUrl xsi:type="inspire_common:resourceLocatorType">
                    <inspire_common:URL>http://metadata.bgs.ac.uk/geonetwork/srv/en/csw?SERVICE=CSW
                    &REQUEST=GetRecordById&ID=7822e848-822d-45a5-8584-56d352fd2170&elementSetName=full&OutputSchema=csw:IsoRecord&
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

         Or to add a scenario 2 INSPIRE extended capabilities section
         (where you have no external metadata document for your WMS
         service) you could add the following parameters:

         ::

            #==================================================================================#
            # INSPIRE extended capabilities
            # Requires MapServer 6.2.0 and above, or the values are ignored
            #==================================================================================#
                        "WMS_LANGUAGES" "eng"
                        "WMS_INSPIRE_CAPABILITIES" "embed"
                        "WMS_INSPIRE_KEYWORD" "infoMapAccessService"
                        "WMS_INSPIRE_MPOC_EMAIL" "enqiries@bgs.ac.uk"
                        "WMS_INSPIRE_MPOC_NAME" "Mr Matthew Harrison"
                        "WMS_INSPIRE_METADATADATE" "2014-03-28"
                        "WMS_INSPIRE_RESOURCELOCATOR" "http://ogc.bgs.ac.uk/cgi-bin/TFL-PSI/ows?"
                        "WMS_INSPIRE_TEMPORAL_REFERENCE" "2014-06-06"

         Which would create:

         ::

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

         .. rubric:: Group layering
            :name: group-layering

         To conform to INSPIRE naming requirements for view services you
         will probably need to group your layers; for example if you
         have bedrock and surface geology layers in your 1GE service you
         will need to do this, or if you have different layers for
         surface age and surface lithology. See `section
         4.5 <4_5.html>`__ of this cookbook for details of how to
         configure group layering.

         When giving a name to your layers one suggestion is prepending
         the INSPIRE MappedFeature group name to the individual layer
         names (which should follow the OneGeology WMS profile naming
         conventions), so for example if you have a number of layers for
         geologic units (e.g. layers representing bedrock age, bedrock
         lithology, surface age, and surface lithology) these would
         according to INSPIRE naming rules need to be part of a layer
         (e.g. within a grouped layer) called *GE.GeologicUnit*. The
         OneGeology naming conventions for a layer (see `section
         2.5 <2_5.html>`__ for details) would suggest a name for the
         surface age layer like *GBR_BGS_EN_1M_Surface_Age*, so
         combining these we would get an INSPIRE plus OneGeology layer
         name of *GE.GeologicUnit_GBR_BGS_EN_1M_Surface_Age*. This
         convention is OK if you are intending to publish a WMS only
         service, however if you also intend to publish a
         GeoSciML-Portrayal WFS using the same configuration, you will
         find that there is an issue with the Feature Identifiers that
         is, your identifier will have a structure like
         *GE.GeologicUnit_GBR_BGS_EN_1M_Surface_Age.10*, and such a
         structure (with two or more dots) causes an error when doing a
         GetFeature request by ID; as MapServer seems to regard
         everything after the first dot as the feature identifier.

         For example a request like:

         ``http://.../BGS_OGE_Bedrock_and_Surface_Geology/ows?service=WFS&request=GetFeature&version=1.1.0&FeatureID=GE.GeologicFault_BGS_EN_1M_Surface.10&``
         Results in the following error:

         ::

            <?xml version="1.0" encoding="ISO-8859-1"?>
            <ows:ExceptionReport xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ows="http://www.opengis.net/ows" version="1.1.0" 
            language="en-US" xsi:schemaLocation="http://www.opengis.net/ows http://schemas.opengis.net/ows/1.0.0/owsExceptionReport.xsd">
              <ows:Exception exceptionCode="InvalidParameterValue" locator="featureid">
                <ows:ExceptionText>msWFSGetFeature(): WFS server error. Invalid FeatureId in GetFeature. Expecting layername.value : (null)</ows:ExceptionText>
              </ows:Exception>
            </ows:ExceptionReport>

         If you are also publishing a GeoSciML-Portrayal WFS using the
         same configuration, then you must either substitute underscores
         for the dot in the INSPIRE name (*GE.GeologicUnit* becomes
         *GE_GeologicUnit*) or omit the INSPIRE component completely.

         .. rubric:: Updating the class files and data
            :name: updating-the-class-files-and-data

         If your OneGeology-Europe service was based on a database, then
         you will just need to use an INNER JOIN in the relevant
         database tables using the mapping tables supplied in Appendix
         L; that is you just need to add some new columns into the
         database, using the GeoSciML-Portrayal names as the field
         names. You can keep the original LAYER > CLASSes in your map
         file and be able to show both the original OneGeology symbology
         (the default style), and also be able to provide different
         portrayals through the application of an external SLD, such as
         through the OneGeology portal.

         If your OneGeology-Europe service was based on a shapefile, you
         may need to create new classes (you can keep the old classes
         and have these serve a different (original) symbology if
         desired). You may need to create new classes for a service
         based on a shapefile because a shapefile can only have field
         names up to 10 characters long and GeoSciML-Portrayal requires
         some field names up to 28 chararaters, (and the standard SLD
         files such as those used by the portal expect the full
         GeoSciML-Portrayal names). It is possible that you can get
         around this restriction by using the GML aliasing ability (see
         the WFS considerations section below for examples), but we have
         not tested this for a GeoSciML-Portrayal WMS.

         .. rubric:: Handing fields for which you have no data
            :name: handing-fields-for-which-you-have-no-data

         As GeoSciML-Portrayal requires data (or URIs pointing to null
         value reasons) for data that was not required in the
         OneGeology-Europe services, you have a few options with
         MapServer if you don't have the required data (for example a
         specification_uri for all features). Option 1 would be to
         create a column in the data source and populate the rows with
         null value URIs (such as for example with the value
         http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unknown/).
         Option 2 would be to populate the missing values within the
         GetFetaureInfo request template, such as below:

         ::

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
                <!-- Here we supply a link to our Feature (using our Simple Fetaure GeoSciML-Portrayal WFS).  
                This information isn't in the database and we can update to a full GeoSciML response when available 
                In the actual template we have this as a link -->
                <dd>http://ogc2.bgs.ac.uk/cgi-bin/BGS_OGE_Bedrock_and_Surface_Geology_in3/ows?service=WFS&
                request=GetFeature&version=1.1.0&&FeatureID=GBR_BGS_EN_1M_Surface_Fault.[OBJECTID]&</dt>
                <!-- Here we supply a link to some metadata for our datasource that isn't in the database 
                In the actual template we have this as a link -->
                <dd>http://metadata.bgs.ac.uk/geonetwork/srv/en/iso19139.xml?id=6075</dd>
            </dl>

         Another option would be to configure some GML constants, see
         the below section on WFS considerations for the configuration
         details.

         .. rubric:: GeoSciML-Portrayal (simple feature ~ GML SF-0) WFS
            considerations
            :name: geosciml-portrayal-simple-feature-gml-sf-0-wfs-considerations

         Whilst configuring a WFS is outside of the scope of this WMS
         cookbook, the following section is included to help you migrate
         your OneGeology-Europe (WMS+WFS) service to a
         GeoSciML-Portrayal (WMS + WFS) service; it should be noted
         however that such a simple feature WFS would not meet the
         requirements for an INSPIRE compliant download service - a full
         GeoSciML 4.0 complex property WFS is required for INSPIRE.

         In the MAP > WEB > METADATA section you can set the default WFS
         language, and also configure a namespace prefix and uri
         GeoSciML-Portrayal for like:

         ::

                        "WFS_LANGUAGES" "eng"
                        "WFS_NAMESPACE_PREFIX" "gmlsp"
                        "WFS_NAMESPACE_URI" "http://xmlns.geosciml.org/geosciml-portrayal/4.0"

         In any LAYER > METADATA section you can define any number of
         GML constants. You can use this mecahnism as a way to add nil
         values or other constant information that is missing from your
         data source but required by the GeoSciML-Portrayal schema, or
         simply because you wish to supply it.

         In this example (below) we have used this mechanism to populate
         specification_uri and metadata_uri which were required with
         GeoSciML-Portrayal version 2; in the current version 4.0 these
         propreties are now optional.

         ::

                        "GML_CONSTANTS" "specification_uri,metadata_uri"
                        "GML_metadata_uri_TYPE" "string"
                        "GML_metadata_uri_VALUE" "http://metadata.bgs.ac.uk/geonetwork/srv/en/iso19139.xml?id=6074"
                        "GML_specification_uri_TYPE" "string"
                        "GML_specification_uri_VALUE" "http://inspire.ec.europa.eu/codelist/VoidReasonValue/Unpopulated/"

         Once a constant has been defined for a layer, the constant can
         be access in a template using the standard notation.

         In any LAYER > METADATA section you can specify which items in
         your datasource to include (or exclude) in your Feature
         response, so in this below example we are saying effectively
         include everything (GML_INCLUDE_ITEMS) except
         (GML_EXCLUDE_ITEMS).

         ::

              
                        "GML_INCLUDE_ITEMS" "all"
                        "GML_EXCLUDE_ITEMS" "AgeMax,AgeMin,EventEnvironment,EventProcess,Lithology_1,ProportionTerms_1,GeologicUnitPartRole_1,Lithology_2,
                        ProportionTerms_2,GeologicUnitPartRole_2,Lithology_3,ProportionTerms_3,GeologicUnitPartRole_3,Lithology_4,ProportionTerms_4,
                        GeologicUnitPartRole_4,Lithology_5,ProportionTerms_5,GeologicUnitPartRole_5,MetamorphicGrade,NameIndex,BodyMorphology,
                        SamplingFrame,GUObservationMethod,GUPurpose,SHAPE_Length,SHAPE_Area,RELEASED,gu_id,mf_id"

         In any LAYER > METADATA section you can specify an alias to be
         used in your feature response, so for example if your feature
         identifier is called *OBJECTID* in your database you can alias
         it to the required *identifier*, or if you want to change the
         case of a field (or property) from *Name* to *name* you would
         use:

         ::

                        "GML_OBJECTID_ALIAS" "identifier"
                        "GML_Name_ALIAS" "name"

         You can specify your own grouping of the properties (and the
         order in which they appear) within a feature and give this
         grouping a name like below. If you have used any aliases you
         must reference the original name and not the alias value in the
         grouping, though the alias will appear in the output.

         ::

                        "GML_GROUPS" "ShearDisplacementStructureView"
                        "GML_ShearDisplacementStructureView_GROUP" "OBJECTID,Name,faultType,observationMethod,positionalAccuracy,faultType_uri,
                        movementType_uri,deformationStyle_uri,representativeAge_uri,representativeOlderAge_uri,representativeYoungerAge_uri,
                        specification_uri,metadata_uri"

         Section last modified: 10 December 2015

         `Back <appendixL.html>`__ \| `Next <home.html>`__
