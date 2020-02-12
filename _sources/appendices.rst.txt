===========================
Appendices
===========================

Appendix I: OneGeology English keyword dictionary picklist
===========================================================

To help classify your service in the portal with respect these thematic keywords you can use one or more of the optional thematic\@value style keywords in your layer metadata.

Note, terms like Geology shown in bold help to classify the terms for ease of reading, but don't imply any hierarchy.  These terms are also part of the picklist of terms.


.. table:: keywords
    :widths: auto
    :align: left

    ==================================  ====================
    Term                                Definition
    ==================================  ====================
    **Economic geology**                Geologic bodies and materials that can be utilized profitably by man
    Exploration                         ~
    Mining                              ~
    Metals                              Metal resources
    Minerals                            Mineral resources
    Energy                              Energy resources
    Coal                                ~
    Peat                                ~
    Oil                                 ~
    Oil shale                           ~
    Gas                                 ~
    Ore                                 ~
    Metallic ore                        ~
    **Engineering geology**             Geologic factors affecting the location, design, construction, operation, and maintenance of engineering works
    Geotechnics                         ~
    Rock mechanics                      ~
    Soil mechanics                      ~
    Land heave                          ~
    Land subsidence                     ~
    **Environmental geology**           Human interactions with the geological environment
    Geologic hazards                    Geological conditions capable of causing damage or loss of property and life
    Avalanche                           ~
    Cavity caving                       ~
    Collapse of metastable sediments    ~
    Earthquake                          ~
    Flood                               ~
    Landslide                           ~
    Mud and debris flow                 ~
    Off-shore landslides and collapses  ~
    Quick clay                          ~
    Rockfall                            ~
    Tsunami                             ~
    Volcanism                           ~
    Pollution                           Human pollution (contamination) of the geological environment
    Acid drainage                       ~
    Groundwater pollution               ~
    Diffuse pollution                   ~
    Point-source pollution              ~
    Reclamation                         ~
    Soil pollution                      ~
    Climate change                      Geological conditions as they effect climate change
    Emission of climate gas             ~
    Global warming                      ~
    Methane exhalation                  ~
    Sea level rise                      ~
    Carbon capture and storage          ~
    Waste                               Unwanted or unusable materials
    Medical geology                     Geological conditions as they effect human, animal, and plant health
    Airborne dust exposure              ~
    Arsenic exposure                    ~
    Asbestos exposure                   ~
    Heavy metal exposure                ~
    Radon exposure                      ~
    **Geology**                         Earth's history and its life as recorded in the rocks; includes the study of geologic features of an area, such as the geometry of rock formations, weathering and erosion, and sedimentation
    Bedrock                             Consolidated rock
    Superficial deposits                Unconsolidated or quaternary geological deposits
    Surface geology                     Superficial deposits and bedrock which occurs at the Earth's surface
    Borehole                            Boreholes or data surveyed in boreholes
    Geochronology                       Absolute ages of rocks, fossils, and sediments, within a certain degree of uncertainty inherent to the method used
    Radiometry                          In optics, radiometry is a set of techniques for measuring electromagnetic radiation, including visible light
    Absolute age                        The geologic age of a fossil, or a geologic event or structure expressed in units of time, usually years
    Stratigraphy                        Rock and sediment layers and layering (stratification)
    Biostratigraphy                     The branch of stratigraphy which focuses on correlating and assigning relative ages of rock strata by using the fossil assemblages contained within them
    Chronostratigraphy                  The branch of stratigraphy that studies the age of rock strata in relation to time
    Structural geology                  Three-dimensional distribution of rock units with respect to their deformational histories
    Tectonics                           ~
    Neotectonics                        ~
    Structure                           ~
    Fault                               ~
    Fold                                ~
    Petrology                           Origin, occurrence, structure, and history of rocks
    Lithology                           ~
    Igneous rock                        ~
    Metamorphic rock                    ~
    Sedimentary rock                    ~
    Mineralogy                          ~
    Geochemistry                        Distribution and amounts of the chemical elements in minerals, ores, rocks, soils, and water
    Hydrogeochemistry                   ~
    Lithogeochemistry                   ~
    Organic geochemistry                ~
    Pedology                            Soil morphology, genesis, and classification
    Soil                                ~
    Permafrost                          ~
    Sedimentology                       Description, classification, origin, and interpretation of sediments and sedimentary rocks
    Deposition                          ~
    Erosion                             ~
    Marine submersion                   ~
    Mudflow                             ~
    Geomorphology                       Landforms on the Earth's surface and the processes that shape them
    Conservation                        ~
    Geological trail                    ~
    Geopark                             ~
    Geosite                             ~
    Geotourism                          ~
    Preservation                        ~
    Artificial ground                   Man-made deposits, mineral workings, re-modelled or altered ground
    Marine Geology                      Investigations of the ocean floor and coastal margins
    Seafloor type                       ~
    Shallow gas                         ~
    Bathymetry                          ~
    Miscellaneous                       ~
    Education                           ~
    Mathematical geology                ~
    Popular geology                     ~
    Harmonized geology                  ~
    Harmonized age                      ~
    Harmonized genesis                  ~
    Harmonized data                     ~
    Harmonized structure                ~
    **Geophysics**                      Measurements and interpolations of geophysical parameters
    Gravimetry                          Measurement of the strength of a gravitational field
    Geomagnetism                        Measurements of the Earth's magnetic field
    Paleomagnetism                      The record of the Earth's magnetic field preserved in various magnetic minerals through time
    Geoelectricity                      Measurements of the Earth's natural electric fields and phenomena
    Radioactivity                       Measurements of the Earth's radioactive elements
    Seismology                          Earthquakes and the propagation of elastic waves through the Earth
    Geothermics                         Study of the thermal state of the interior of the solid Earth and of the thermal properties of Earth materials
    **Hydrogeology**                    Distribution and movement of groundwater in the soil and rocks of the Earth's crust
    Aquifer                             ~
    Groundwater                         ~
    Groundwater abstraction             ~
    Groundwater level                   ~
    Infiltration                        ~
    Spring                              ~
    Water quality                       ~
    Water well                          ~
    Groundwater body                    Principal reporting unit with hydraulically coherent entities
    ==================================  ====================


Appendix K - Recommend ESRI shapefile definitions for GeoSciML-Portrayal
=========================================================================

Because the field names in GeoSciML-Portrayal are longer than 10 characters, you will not be able to have the full attribute (column) name for many of the properties if your portrayal data is loaded into an ESRI shapefile, which can be an issue in some WMS server software. To prevent truncated names, we are providing a recommended shapefile implementation with shorter field names. Field names are abbreviated to try and leave characters that convey the full name of the field; lower camel case typographic has been used, except that fields that contain URI’s end with ‘_uri’.


Table 4. Recommend shapefile definition for ContactView

================== ==================== ===================
XML field Name     Shapefile field name Shapefile data type
================== ==================== ===================
identifier         identifier           String
name               name                 String
description        descriptio           String
contactType        contactTyp           String
observationMethod  obsvMethod           String
positionalAccuracy posAccur             String
source             source               String
contactType_uri    conTyp_uri           String
specification_uri  spec_uri             String
metadata_uri       metada_uri           String
genericSymbolizer  genericSym           String
shape              SHAPE                ESRI geometry
================== ==================== ===================

Table 5. Recommended shapefile definition for ShearDisplacementStructureView

============================ ==================== ===================
XML field Name               Shapefile field name Shapefile data type
============================ ==================== ===================
identifier                   identifier           String
name                         name                 String
description                  descriptio           String
faultType                    faultType            String
movementType                 movmntType           String
deformationStyle             defrmStyle           String
displacement                 displacmnt           String
geologicHistory              geolHistry           String
observationMethod            obsvMethod           String
positionalAccuracy           posAccur             String
source                       source               String
faultType_uri                fltTyp_uri           String
movementType_uri             movTyp_uri           String
deformationStyle_uri         defStl_uri           String
representativeAge_uri        repAge_uri           String
representativeOlderAge_uri   oldAge_uri           String
representativeYoungerAge_uri yngAge_uri           String
specification_uri            spec_uri             String
metadata_uri                 metada_uri           String
genericSymbolizer            genericSym           String
shape                        SHAPE                ESRI geometry
============================ ==================== ===================

Table 6. Recommended shapefile definition for GeologicUnitView

============================ ==================== ===================
XML field Name               Shapefile field name Shapefile data type
============================ ==================== ===================
identifier                   identifier           String
name                         name                 String
description                  descriptio           String
geologicUnitType             geoUnitTyp           String
rank                         rank                 String
lithology                    lithology            String
geologicHistory              geolHistry           String
observationMethod            obsvMethod           String
positionalAccuracy           posAccur             String
source                       source               String
geologicUnitType_uri         uniTyp_uri           String
representativeLithology_uri  repLth_uri           String
representativeAge_uri        repAge_uri           String
representativeOlderAge_uri   oldAge_uri           String
representativeYoungerAge_uri yngAge_uri           String
specification_uri            spec_uri             String
metadata_uri                 metada_uri           String
genericSymbolizer            genericSym           String
shape                        SHAPE                ESRI geometry
============================ ==================== ===================

Appendix F - WMS 1.3.0 GetCapabilities response from the BGS OneGeology exemplar service
=========================================================================================

.. container:: fullwidth

   .. rubric:: Appendix F: WMS 1.3.0 GetCapabilities response from the
      BGS OneGeology exemplar service
      :name: appendix-f-wms-1.3.0-getcapabilities-response-from-the-bgs-onegeology-exemplar-service
      :class: technical_progress_side_menu

   Below is the GetCapabilities response returned by the BGS OneGeology
   service as configured by the MapServer map file shown in `Appendix
   E`_. This response document may be obtained using the following
   requests, that is, either as a `request without version parameter`_
   like:

   ::

      http://ogc.bgs.ac.uk/cgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/ows?
        service=WMS&
        request=GetCapabilities&

   or as a `request with version parameter`_ like:
   ::

      http://ogc.bgs.ac.uk/cgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/ows?
        service=WMS&
        request=GetCapabilities&
        version=1.3.0&

   That is, the version parameter is omittable because the default
   service is always the highest version supported by the WMS server.

   -  `View the generated XML`_

.. _request without version parameter: http://ogc.bgs.ac.uk/cgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/ows?service=WMS&request=GetCapabilities&
.. _request with version parameter: http://ogc.bgs.ac.uk/cgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/ows?service=WMS&request=GetCapabilities&version=1.3.0&
.. _View the generated XML: http://www.onegeology.org/wmsCookbook/BGS_Bedrock_and_Superficial_Geology-1.3.0.xml
