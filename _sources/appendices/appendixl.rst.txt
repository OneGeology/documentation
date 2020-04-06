========================================================================
Mapping OneGeology-Europe data model to GeoSciML-Portrayal \| OneGeology
========================================================================

The following table is derived from the OneGeology-Europe WP5
and WP6 guidelines for preparing the datasets. **The table is
provided to assist those organizations that already have data
mapped to the OneGeology-Europe data model and wish to update
their services to use the same data for a GeoSciML-Portrayal
4.0 WMS service that will be INSPIRE conformant.**

When reading the table you should generally (such as excluding
headers) consider pairs of rows, where the  first row  refers
to the OneGeology-Europe data mapping (label, required status,
and description) and  the second row  is the corresponding
mapping in a GeoSciML-Portayal record. Descriptions that have a
line through them are regarded as obsolete (that is, refer to
the OneGeology-Europe data mapping that is either replaced or
not required in GeoSciML-Portrayal).

Generally you should note that URNs are deprecated and replaced
by HTTP-URIs, whether they be INSPIRE URIs, or CGI URIs.

We also provide some Excel spreadsheets (below) that map the
OneGeology-Europe URNs to their equivalent HTTP-URIs for both
the INSPIRE and CGI controlled vobabularies, that is:

`Mapping from OneGeology-Europe Lithology URNs <../docs/technical/OGEvocMap/3column-OGE-CGI-InspireURI-Mapping-LithologyREDUX.xlsx>`__ (<< link to Excel mapping spreadsheet)
   For example for mapping:
   *Lithology_1* to *representativeLithology_uri*
`Mapping from OneGeology-Europe Age URNs <../docs/technical/OGEvocMap/3column-OGE-CGI-InspireURI-Mapping-AgeREDUX-29-10-2015.xlsx>`__ (<< link to Excel mapping spreadsheet)
   For example for mapping:
   *AgeMax* or *EventAgeMax* to *representativeOlderAge_uri*,
   or
   *AgeMin* or *EventAgeMin* to *representativeYoungerAge_uri*,
   or
   *AgeMax* to *representativeAge_uri* (as BGS do in OGE
   portal)
`Mapping from OneGeology-Europe GeologicUnitType URNs <../docs/technical/OGEvocMap/2column-OGE-InspireURI-Mapping-GeologicUnitType.xlsx>`__ (<< link to Excel mapping spreadsheet)
   For example for mapping:
   *GeologicUnitType* to *geologicUnitType_uri*
`Mapping from OneGeology-Europe FaultType URNs <../docs/technical/OGEvocMap/2column-OGE-InspireURI-Mapping-FaultType.xlsx>`__ (<< link to Excel mapping spreadsheet)
   For example for mapping:
   *FaultType* to *faultType_uri*
`Mapping from OneGeology-Europe EventEnvironment URNs <../docs/technical/OGEvocMap/EventEnvironment.csv>`__ (<< link to Excel mapping spreadsheet)
   Note:
   *Not required for GeoSciML-Portrayal 4.0 conversions*
`Mapping from OneGeology-Europe EventProcess URNs <../docs/technical/OGEvocMap/EventProcess.csv>`__ (<< link to Excel mapping spreadsheet)
   Note:
   *Not required for GeoSciML-Portrayal 4.0 conversions*

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal GeologicUnitView features
-------------------------------------------------------------------------------------------

That whilst many of the properties required for the
OneGeology-Europe GEOLOGIC UNITS mapping are optional, or not
specified by GeoSciML-Portrayal GeologicUnitView features,
GeoSciML-Portrayal mandates other properties (that is
properties not found in OneGeology-Europe) are defined, such as
representativeAge_uri. Please refer to the GeoSciML-Portrayal
`GeologicUnitView features <7_3_3.html>`__ page of the
cookboook for more information.

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal GeologicUnitView features

.. raw :: html

   <table class="cadre">
   <caption>Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal GeologicUnitView features</caption>
   <tr class="title"><td colspan="3">GEOLOGIC UNITS. Each feature (polygon) should have at least the following attributes</td></tr>
   <tr class="subtitle"><td colspan="3" class="obs"><i>featureMember/MappedFeature</i> for each MappedFeature (for each polygon)</td></tr>
   <tr><td class="label">A unique feature ID</td><td>M</td><td class="obs">The unique ID of the polygon is often named &#8220;fid&#8221; within a shapefile</td></tr>
   <tr><td class="label2">identifier</td><td>M</td><td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td></tr>
   <tr style="background:#EFEFEF"><td>Observation method [urn]<br /><span class="geosciml">MappedFeature/observationMethod</span></td><td class="obs">M</td><td class="obs">Always <b>urn:cgi:classifier:CGI:MappedFeatureObservationMethod:201001:compilation</b></td></tr>
   <tr><td>observationMethod<br />[string]</td><td>O</td><td>ObservationMethod is a convenience property to provide observation metadata. Example values might include &#8216;field observation by author&#8217;, &#8216;compilation from published maps&#8217;, &#8216;air photo interpretation&#8217;. Recommend using the CGI Feature Observation Method vocabulary.</td></tr>
   <tr><td class="label">The positional accurancy [numerical value]<br /><span class="geosciml">MappedFeature/positionalAccuracy</span></td><td class="obs">M</td><td class="obs">It is recommended that the same, approximate, value be given for all MappedFeatures and will generally be <b>250</b></td></tr>
   <tr><td class="label2">positionalAccuracy<br />[string]</td><td>O</td><td>accuracy may be provided, e.g. a term from a controlled vocabulary. Vocabulary used should be described in the dataset metadata. For polygon mapped features this is intended for use to indicate the position uncertainty of the contact and fault features bounding the outcrop polygon, which is only necessary if the associated line features are not included with the polygons.</td></tr>
   <tr style="background:#EFEFEF"><td>The sampling frame [urn]<br /><span class="geosciml">MappedFeature/samplingFrame</span></td><td class="obs">M</td><td class="obs">This property should be set to <b>urn:cgi:feature:CGI:EarthNaturalSurface</b> for the surface map and <b>urn:cgi:feature:CGI:BedrockSurface</b> for the bedrock map</td></tr>
   <tr><td>The sampling frame</td><td>-</td><td>There is no corresponding value in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The geometry<br /><span class="geosciml">MappedFeature/shape</span></td><td>M</td><td></td></tr>
   <tr><td class="label2">shape<br />[GM_Object (GM_polygon)]</td><td>M</td><td>Geometry defining the extent of the feature of interest.</td></tr>
   <tr class="subtitle"><td colspan="3" class="obs"><i>featureMember/MappedFeature/specification/GeologicUnit</i><br />The following data are the attributes of the geologic unit which the current mappedFeature is a part of</td></tr>
   <tr><td class="label">A unique Geologic Unit ID [Any type]<br /><span class="geosciml">GeologicUnit id</span></td><td class="obs">M</td><td class="obs">Each GeologicUnit should be given a unique identifier</td></tr>
   <tr><td class="label2">geologicUnitType<br />[string]</td><td>O</td><td>Type of GeologicUnit (as defined in GeoSciML).</td></tr>
   <tr><td class="label">The name of the geologic Unit<br /><span class="geosciml">GeologicUnit/name</span></td><td class="obs">M</td><td class="obs">Could be a simple name (text) or a urn (see the WP3 explanatory notes)</td></tr>
   <tr><td class="label2">name<br />[string]</td><td>O</td><td>Display name for the GeologicUnit; this can be used to put in a geologic unit name, or more likely an abbreviation used to label outcrops of the unit in a map display.</td></tr>
   <tr><td class="label">The &#8220;free text&#8221; description<br /><span class="geosciml">GeologicUnit/description</span></td><td>O</td><td></td></tr>
   <tr><td class="label2">description<br />[string]</td><td>O</td><td>Text description of the GeologicUnit, typically taken from an entry on a geological map legend.</td></tr>
   <tr><td class="label">The geologic unit type [urn]<br /><span class="geosciml">GeologicUnit/geologicUnitType</span></td><td class="obs">M</td><td class="obs">Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_GeologicUnitType.xls" target="download">GeologicUnitType</a>&#8221;</td></tr>
   <tr><td class="label2">geologicUnitType_uri<br />[string]</td><td>M</td><td>URI referring to a controlled concept from a vocabulary defining the GeologicUnit types. Mandatory property - if no value is provided then a URI referring to a controlled concept explaining why the value is nil must be provided.</td></tr>
   <tr style="background:#EFEFEF"><td>The observation method [urn]<br /><span class="geosciml">GeologicUnit/observationMethod</span></td><td class="obs">M</td><td class="obs">either <b>urn:cgi:classifier:CGI:FeatureObservationMethod:201001:data_from_single_published_description</b><br />where the property values are derived from a single source document, or<br /><b>urn:cgi:classifier:CGI:FeatureObservationMethod:201001:synthesis_of_multiple_published_descriptions</b><br />where they are derived from multiple source documents.</td></tr>
   <tr><td>observationMethod<br />[string]</td><td>O</td><td>ObservationMethod is a convenience property to provide observation metadata. Example values might include &#8216;field observation by author&#8217;, &#8216;compilation from published maps&#8217;, &#8216;air photo interpretation&#8217;. Recommend using the CGI Feature Observation Method vocabulary.</td></tr>
   <tr style="background:#EFEFEF"><td>The purpose<br /><span class="geosciml">GeologicUnit/purpose</span></td><td class="obs">M</td><td class="obs">For OneGeology-Europe the Purpose property should be set to: <b>typical_norm</b>.</td></tr>
   <tr><td>The purpose</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">Body Morphology [urn]<br /><span class="geosciml">GeologicUnit/bodyMorphology</span></td><td class="obs">O</td><td class="obs">For dykes the GeologicUnit bodyMorphology property should always be set to<b>urn:cgi:classifier:CGI:GeologicUnitMorphology:201001:dike</b> In any other case, the value is empty.</td></tr>
   <tr><td class="label2">Body Morphology</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr class="subtitle2"><td colspan="3" class="obs"><i>GeologicUnit/preferredAge/GeologicEvent</i><br />The following attributes describe the age of formation of the geologic unit</td></tr>
   <tr><td class="label">The name (Orogenic Event) [urn]<br /><span class="geosciml">GeologicEvent/name</span></td><td class="obs">O</td><td class="obs">Only given where the Geologic Unit was formed by the orogenic event. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_Orogenic_Events.xls" target="download">OrogenicEvents</a>&#8221;.</td></tr>
   <tr><td class="label2">The name (Orogenic Event)</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The event Age - Lower [urn]<br /><span class="geosciml">GeologicEvent/eventAge/.../lower</span></td><td class="obs">M</td><td class="obs">Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_Ages.xls" target="download">Ages</a>&#8221;</td></tr>
   <tr><td class="label2">representativeOlderAge_uri<br />[string]</td><td>M</td><td>URI referring to a controlled concept specifying the most rep-resentative older value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing all or part of the feature&#8217;s history.</td></tr>
   <tr><td class="label">The event Age - Upper [urn]<br /><span class="geosciml">GeologicEvent/eventAge/.../upper</span></td><td class="obs">M</td><td class="obs">Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_Ages.xls" target="download">Ages</a>&#8221;</td></tr>
   <tr><td class="label2">representativeYoungerAge_uri<br />[string]</td><td>M</td><td>URI referring to a controlled concept specifying the most representative younger value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing all or part of the feature&#8217;s history.</td></tr>
   <tr><td class="label">The event process [urn]<br /><span class="geosciml">GeologicEvent/eventProcess</span></td><td class="obs">M</td><td class="obs">Record the process that formed the Geologic Unit. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_EventProcess.xls" target="download">EventProcess</a>&#8221;.</td></tr>
   <tr><td class="label2">The event process</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The event environment [urn]<br /><span class="geosciml">GeologicEvent/eventEnvironment</span></td><td class="obs">O</td><td class="obs">Can be used to describe the environment which the Geologic Unit was formed. Use the 1GE vocabulary "<a href="../1GE/VocabXL/1GE_EventEnvironment.xls" target="download">EventEnvironment</a>".</td></tr>
   <tr><td class="label2">The event environment</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr class="subtitle2"><td colspan="3" class="obs"><i>GeologicUnit/geologicHistory/GeologicEvent</i> <br />The following attributes describe a serie of geologic events that led to the formation of the geologic unit. To describe such a geologic history is <i>not</i> mandatory. But for each geologic history / geologic event described, one event age and at least one event process should be described. The rules are the same that for the preferred age. It is up to each data provider to describe 0 or n geologic events of the geologic history.</td></tr>
   <tr><td class="label">The name (for Orogenic Event) [urn]<br /><span class="geosciml">GeologicEvent/name</span></td><td class="obs">O</td><td class="obs">Use the vocabulary &#8220;<a href="../1GE/VocabXL/1GE_Orogenic_Events.xls" target="download">OrogenicEvents</a>&#8221;</td></tr>
   <tr><td class="label2">The name (for Orogenic Event)</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The event Age<br /><span class="geosciml">GeologicEvent/eventAge</span></td><td class="obs">M</td><td class="obs">Can be defined as a range of urn [lower_age, upper_age], as a range of numerical values, as a single numerical value, or as a single urn. In the case of urns, use the 1GE vocabulary "<a href="../1GE/VocabXL/1GE_Ages.xls" target="download">Ages</a>"</td></tr>
   <tr><td class="label2">The event Age</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The event process [urn]<br /><span class="geosciml">GeologicEvent/eventProcess</span></td><td class="obs">M</td><td rowspan="3" class="obs">It is up to each data provider to present several event process (therefore, several attributes with distinct names) for describing the current geologic event of the geologic history. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_EventProcess.xls" target="download">EventProcess</a>&#8221;.</td></tr>
   <tr><td class="label">...</td><td class="obs">O</td></tr>
   <tr><td class="label">The event process [urn]</td><td class="obs">O</td></tr>
   <tr><td class="label2">geologicHistory<br />[string]</td><td>O</td><td>Text (possibly formatted with formal syntax) description of the age of the GeologicUnit (where age is a sequence of events and may include process and environment information).</td></tr>
   <tr><td class="label">The event environment [urn]<br /><span class="geosciml">GeologicEvent/eventEnvironment</span></td><td class="obs">O</td><td rowspan="3" class="obs">It is up to each data provider to present several event environment (therefore, several attributes with distinct names) for describing the current geologic event of the geologic history. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_EventEnvironment.xls" target="download">EventEnvironment</a>&#8221;</td></tr>
   <tr><td class="label">...</td><td class="obs">O</td></tr>
   <tr><td class="label">The event environment [urn]</td><td class="obs">O</td></tr>
   <tr><td class="label2">The event environment</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr class="subtitle2"><td colspan="3" class="obs"><i>GeologicUnit/composition/CompositionPart</i><br />The following attributes describe the lithology of the geologic unit. Some GeologicUnits will have a single CompositionPart, but others may have multiple CompositionParts, such as interbedded layers, each of which can be described with a distinct CompositionPart. Each CompositionPart has three properties – the lithology; the role of the CompositionPart in the GeologicUnit as a whole; and the proportion of the CompositionPart in the GeologicUnit as a whole. <i>For example, if the geologic units of a given dataset have in some cases 5 distincts lithology, but not more, then the database (or shapefile) will have 5 attributes lithology, role and proportion.</i> the main lithology (proportion=all or predominant) attibute will always have a value (at least one lithology is mandatory), but the others will be often empty.</td></tr>
   <tr><td class="label">Lithology [urn]<br /><span class="geosciml">CompositionPart/lithology</span></td><td class="obs">M</td><td class="obs">Use the 1GE &#8220;<a href="../1GE/VocabXL/1GE_Lithology_.xls" target="download">Lithology</a>&#8221; vocabulary</td></tr>
   <tr><td class="label2">representativeLithology_uri<br />[string]</td><td>M</td><td>URI referring to a controlled concept specifying the characteristic or representative lithology of the unit. This may be a concept that defines the super-type of all lithology values present within a GeologicUnit or a concept defining the lithology of the dominant CompositionPart (as defined in GeoSciML) of the unit. This identifier is intended for use as the symbol key for a lithologic map portrayal of the geologic unit features.</td></tr>
   <tr><td class="label">Lithology [urn]<br /><span class="geosciml">CompositionPart/lithology</span></td><td class="obs">M</td><td class="obs">Use the 1GE &#8220;<a href="../1GE/VocabXL/1GE_Lithology_.xls" target="download">Lithology</a>&#8221; vocabulary</td></tr>
   <tr><td class="label2">Lithology<br />[string]</td><td>O</td><td>Text (possibly formatted with formal syntax) description of the GeologicUnit&#8217;s lithology.</td></tr>
   <tr style="background:#EFEFEF"><td>Role [urn]<br /><span class="geosciml">CompositionPart/role</span></td><td class="obs">M</td><td class="obs"> 
   <ul>
   <li>Where the CompositionPart is the only one in the GeologicUnit the role property should be set to <b>urn:cgi:classifier:CGI:GeologicUnitPartRole:200811:only_part</b></li>
   <li>Where the CompositionPart is one of several in the GeologicUnit the role property should be set to <b>urn:cgi:classifier:CGI:GeologicUnitPartRole:200811:unspecified_part_role</b></li>
   <li>See also the detailed explanation in the WP3 document: the GeologicUnitPartRole has other values in serveral cases  ("Molasse", "Ophiolitic mélange", ...).</li>
   </ul></td></tr>
   <tr><td>Role</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr style="background:#EFEFEF"><td>Proportion [urn]<br /><span class="geosciml">CompositionPart/proportion</span></td><td class="obs">M</td>
   <td class="obs"><ul>
   <li>Where there is only one CompositionPart is the GeologicUnit the Proportion property should be set to <b>urn:cgi:classifier:CGI:ProportionTerm:201001:all</b>.</li>
   <li>Where there are multiple CompositionParts in the GeologicUnit the CompositionPart that comprises the single largest proportion of the GeologicUnit should be given a Proportion value of <b>urn:cgi:classifier:CGI:ProportionTerm:201001:predominant</b>.</li>
   <li>All other CompositionParts should be given a Proportion value of <b>urn:cgi:classifier:CGI:ProportionTerm:201001:subordinate</b>.</li>
   <li>Note that where there are multiple CompositionParts in the GeologicUnit one must be given a value of <b>urn:cgi:classifier:CGI:ProportionTerm:201001:predominant</b> and this will be the one used for portrayal of the lithology of the GeologicUnit.</li>
   </ul></td></tr>
   <tr><td>Proportion</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr class="subtitle2"><td colspan="3" class="obs">GeologicUnit/metamorphicCharacter/MetamorphicDescription<br />The following attributes describe the metamorphism of a geologic unit. It is optional. If a data provider do not wish to describe metamorphism for any of the geologic units, then these attributes are not required. Only one Metamorphic description can be given</td></tr>
   <tr><td class="label">Metamorphic facies [urn]<br /><span class="geosciml">MetamorphicDescription/metamorphicFacies</span></td><td class="obs">O</td><td rowspan="3" class="obs">Use of the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_MetamorphicFacies.xls" target="download">MetamorphicFacies</a>&#8221;. Several Metamorphic facies can be given</td></tr>
   <tr><td class="label">...</td><td></td></tr>
   <tr><td class="label">Metamorphic facies [urn]</td><td></td></tr>
   <tr><td class="label">Metamorphic grade [urn]<br /><span class="geosciml">MetamorphicDescription/metamorphicGrade</span></td><td class="obs">O</td><td class="obs">Use of the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_MetamorphicGrade.xls" target="download">"MetamorphicGrade</a>&#8221;</td></tr>
   <tr><td colspan="3" class="obs"><i><b>MetamorphicDescription/protolithLithology/RockMaterial</b></i><br />The following attributes describe the protolith lithology of the metamorphic description. It is optional, and there can be several protolith lithology. If a protolith is given, then consolidation degree and lithology are mandatory</td></tr>
   <tr><td class="label">lithology [urn]<br /><span class="geosciml">RockMaterial/lithology</span></td><td></td><td class="obs">Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_Lithology_.xls" target="download">Lithology</a>&#8221;.</td></tr>
   <tr style="background:#EFEFEF"><td>consolidation degree [urn]<br /><span class="geosciml">RockMaterial/consolidationDegree</span></td><td></td><td class="obs">If a lithology is given, then the consolidationDegree should always be set to<b>urn:cgi:classifier:CGI:ConsolidationDegree:200811:consolidation_not_specified</b></td></tr>
   <tr style="background:#EFEFEF"><td>purpose<br /><span class="geosciml">RockMaterial/purpose</span></td><td class="obs">O</td><td class="obs">If a lithology is given, then the purpore should always be set to <b>typical_norm</b></td></tr>
   <tr><td class="label2">Metamorphic character, description...</td><td>-</td><td>There are no corresponding properties in GeoSciML-Portrayal</td></tr>
   </table>


.. important ::
   In OneGeology-Europe the only types of structure that are being used are Faults and Contacts. Contacts are only being used to describe Calderas, Impact Craters, and Glacial Stationary Lines. Below we have separated Faults from Contacts becuase in GeoSciML-Portrayal they have different mappings.

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal ShearDisplacementStructureView features
-------------------------------------------------------------------------------------------------------

.. note ::
   Note that whilst many of the properties required for the OneGeology-Europe GEOLOGIC STRUCTURES mapping are optional, or not specified by GeoSciML-Portrayal ShearDisplacementStructureView features, GeoSciML-Portrayal mandates other properties (that is properties not found in OneGeology-Europe) are defined, such as movementType_uri and deformationStyle_uri. Please refer to the GeoSciML-Portrayal ShearDisplacementStructureView features page of the cookboook for more information.

.. raw :: html

   <table class="cadre">
   <caption>Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal ShearDisplacementStructureView features</caption>
   <tr class="title"><td colspan="3">GEOLOGIC STRUCTURES. Each feature should have at least the following attributes</td></tr>
   <tr class="subtitle"><td colspan="3" class="obs"><i>featureMember/MappedFeature</i> for each MappedFeature</td></tr>
   <tr><td class="label">A unique feature ID</td><td>M</td><td class="obs">This unique ID is often named &#8220;fid&#8221; within a shapefile</td></tr>
   <tr><td class="label2">identifier</td><td>M</td><td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td></tr>
   <tr style="background:#EFEFEF"><td>Observation method [urn]<br /><span class="geosciml">MappedFeature/observationMethod</span></td><td>?</td><td class="obs">Always &#8220;urn:cgi:classifier:CGI:MappedFeatureObservationMethod:201001:compilation&#8221;, therefore not required in the database or within the shapefile: can be directly encoded in the GeoSciML response.</td></tr>
   <tr><td>observationMethod<br />[string]</td><td>O</td><td>ObservationMethod is a convenience property that provides a quick and dirty approach to observation metadata when data are reported using a feature view (as opposed to observation view).</td></tr>
   <tr><td class="label">The positional accurancy [numerical value]<br /><span class="geosciml">MappedFeature/positionalAccuracy</span></td><td class="obs">M</td><td class="obs">It is recommended that the same, approximate, value be given for all MappedFeatures and will generally be around 250m for a 1:1 million scale map.</td></tr>
   <tr><td class="label2">positionalAccuracy<br />[string]</td><td>O</td><td>Preferred use is a quantitative value defining the radius of an uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of 100 m for a line feature defines a buffer polygon of total width 200 m centered on the line. Some other text description that quantifies position accuracy may be provided, e.g. a term from a controlled vocabulary. Vocabulary used should be described in the dataset metadata.</td></tr>
   <tr style="background:#EFEFEF"><td>The sampling frame [urn]<br /><span class="geosciml">MappedFeature/samplingFrame</span></td><td class="obs">M</td><td class="obs">This property should be set to <b>urn:cgi:feature:CGI:EarthNaturalSurface</b> for the surface map and<b>urn:cgi:feature:CGI:BedrockSurface</b> for the bedrock map</td></tr>
   <tr><td>The sampling frame</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The geometry<br /><span class="geosciml">MappedFeature/shape</span></td><td>M</td><td></td></tr>
   <tr><td class="label2">shape<br />[GM_Object (GM_curve)]</td><td>M</td><td>Geometry defining the extent of the feature of interest.</td></tr>
   <tr class="subtitle"><td colspan="3" class="obs">FAULT: <i>featureMember/MappedFeature/specification/ShearDisplacementStructure</i><br />the following data are the attributes of the geologic structure which the current mappedFeature is a part of</td></tr>
   <tr><td class="label">A unique Geologic Structure ID [Any type]<br /><span class="geosciml">ShearDisplacementStructure</span></td><td class="obs">M</td><td class="obs">Each GeologicStructure should be given a unique identifier.</td></tr>
   <tr><td class="label2">A unique Geologic Structure ID</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The name of the geologic Structure<br /><span class="geosciml">ShearDisplacementStructure/name</span></td><td>O</td><td class="obs">Could be a simple name (text) or a urn (see the WP3 explanatory notes)</td></tr>
   <tr><td class="label2">name<br />[string]</td><td>O</td><td>Display name for the ShearDisplacementStructure. This may be a generic fault type, e.g. &#8216;thrust fault&#8217;, &#8216;strike-slip fault&#8217;, or a particular fault name, e.g. &#8216;Moine thrust&#8217;, &#8216;san Andreas Fault&#8217;.</td></tr>
   <tr style="background:#EFEFEF"><td>The observation method [urn]<br /><span class="geosciml">ShearDisplacementStructure/observationMethod</span></td><td class="obs">M</td><td class="obs">either <b>urn:cgi:classifier:CGI:FeatureObservationMethod:201001:data_from_single_published_description</b><br />where the property values are derived from a single source document, or <br /><b>urn:cgi:classifier:CGI:FeatureObservationMethod:201001:synthesis_of_multiple_published_descriptions</b><br />where they are derived from multiple source documents.</td></tr>
   <tr><td>observationMethod<br />[string]</td><td>O</td><td>Metadata snippet indicating how the spatial extent of the feature was determined. ObservationMethod is a convenience property that provides a quick and dirty approach to observation metadata when data are reported using a feature view (as opposed to observation view).</td></tr>
   <tr style="background:#EFEFEF"><td>The purpose<br /><span class="geosciml">ShearDisplacementStructure/purpose</span></td><td>?</td><td class="obs">For OneGeology-Europe the Purpose property should be set to : <b>typical_norm</b>.</td></tr>
   <tr><td>The purpose</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr class="subtitle2"><td colspan="3"><b>FAULT TYPE</b></td></tr>
   <tr><td class="label">Fault Type [urn]<br /><span class="geosciml">ShearDisplacementStructure/faultType</span></td><td>?</td><td class="obs"><b>For all Faults the property faultType must be populated</b> with the URN of one of the concepts described in the vocabulary &#8220;<a href="../1GE/VocabXL/1GE_FaultType.xls" target="download">FaultType</a>&#8221;.</td></tr>
   <tr><td class="label2">faultType<br />[string]</td><td>O</td><td>Type of ShearDisplacementStructure (as defined in GeoSciML).</td></tr>
   <tr><td class="label">Fault Type [urn]<br /><span class="geosciml">ShearDisplacementStructure/faultType</span></td><td>?</td><td class="obs"><b>For all Faults the property faultType must be populated</b> with the URN of one of the concepts described in the vocabulary &#8220;<a href="../1GE/VocabXL/1GE_FaultType.xls" target="download">FaultType</a>&#8221;.</td></tr>
   <tr><td class="label2">faultType_uri<br />[string]</td><td>M</td><td>URI referring to a controlled concept from a vocabulary defining the fault (ShearDisplacementStructure) type. Mandatory property - if no value is provided then a URI referring to a controlled concept explaining why the value is nil must be provided.</td></tr>
   <tr class="subtitle2"><td colspan="3" class="obs"><i>Contact/preferredAge/GeologicEvent </i> <br />An age as &#8220;preferredAge&#8221; can be optionally provided for glacial stationary lines</td></tr>
   <tr><td class="label">The event Age<br /><span class="geosciml"></span>GeologicEvent/eventAge</td><td>M</td><td class="obs">The eventAge field should be populated as a numeric range (two attributes) or as a single numeric value (one attribute). The age recorded as a negative number (e.g. -250)</td></tr>
   <tr><td class="label2">representativeAge_uri<br/>[string]</td><td>M</td><td>URI referring to a controlled concept specifying the most representative stratigraphic age interval for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing the all or part of the feature&#8217;s history.</td></tr>
   <tr><td class="label">The event Age<br /><span class="geosciml"></span>GeologicEvent/eventAge</td><td>M</td><td class="obs">The eventAge field should be populated as a numeric range (two attributes) or as a single numeric value (one attribute). The age recorded as a negative number (e.g. -250)</td></tr>
   <tr><td class="label2">representativeOlderAge_uri<br/>[string]</td><td>M</td><td>URI referring to a controlled concept specifying the most representative older value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing the all or part of the feature&#8217;s history.</td></tr>
   <tr><td class="label">The event Age<br /><span class="geosciml"></span>GeologicEvent/eventAge</td><td>M</td><td class="obs">The eventAge field should be populated as a numeric range (two attributes) or as a single numeric value (one attribute). The age recorded as a negative number (e.g. -250)</td></tr>
   <tr><td class="label2">representativeYoungerAge_uri<br/>[string]</td><td>M</td><td>URI referring to a controlled concept specifying the most representative younger value in a range of stratigraphic age intervals for the GeologicUnit. This will be defined entirely at the discretion of the data provider and may be a single event selected from the geologic feature&#8217;s geological history or a value summarizing the all or part of the feature&#8217;s history.</td></tr>
   <tr><td class="label">The event process [urn]<br /><span class="geosciml">GeologicEvent/eventProcess</span></td><td class="obs">M</td><td rowspan="3" class="obs">It is up to each data provider to present several event process (therefore, several attributes with distinct names) for describing the process that formed the geologic structure. Use the 1GE vocabulary "<a href="../1GE/VocabXL/1GE_EventProcess.xls" target="download">EventProcess</a>".</td></tr>
   <tr><td class="label">...</td><td class="obs">O</td></tr>
   <tr><td class="label">The event process [urn]</td><td class="obs">O</td></tr>
   <tr><td class="label2">geologicHistory<br />[string]</td><td class="obs">O</td><td>Text (possibly formatted with formal syntax) description of the sequence of events that formed and have affected the ShearDisplacementStructure. Events include process and optional environment information.</td></tr>
   <tr><td class="label">The event environment [urn]<br /><span class="geosciml">GeologicEvent/eventEnvironment</span></td><td class="obs">O</td><td rowspan="3" class="obs">It is up to each data provider to present zero or several event environment (therefore, several attributes with distinct names) for describing the environment in which theGeologicStructure was formed. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_EventEnvironment.xls" target="download">EventEnvironment</a>&#8221;</td></tr>
   <tr><td class="label">...</td><td class="obs">O</td></tr>
   <tr><td class="label">The event environment [urn]</td><td class="obs">O</td></tr>
   <tr><td class="label">The event environment</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   </table>

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal ContactView features
------------------------------------------------------------------------------------

.. raw :: html

   <table class="cadre">
   <caption>Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal ContactView features</caption>
   <tr class="title"><td colspan="3">GEOLOGIC STRUCTURES. Each feature should have at least the following attributes</td></tr>
   <tr class="subtitle"><td colspan="3" class="obs"><i>featureMember/MappedFeature</i> For each MappedFeature</td></tr>
   <tr><td class="label">A unique feature ID</td><td>M</td><td class="obs">This unique ID is often named &#8220;fid&#8221; within a shapefile</td></tr>
   <tr><td class="label2">identifier</td><td>M</td><td>Globally unique identifier for the individual feature. Recommended practice is that this identifier be derived from the primary key for the spatial objects in the source data in case information needs to be transferred from the interchange format back to the source database. This identifier is analogous to the identifier for a GeoSciML MappedFeature.</td></tr>
   <tr style="background:#EFEFEF"><td>Observation method [urn]<br /><span class="geosciml">MappedFeature/observationMethod</span></td><td>?</td><td class="obs">Always &#8220;urn:cgi:classifier:CGI:MappedFeatureObservationMethod:201001:compilation", therefore not required in the database or within the shapefile: can be directly encoded in the GeoSciML response.</td></tr>
   <tr><td>observationMethod<br />[string]</td><td>O</td><td>Metadata snippet indicating how the spatial extent of the feature was determined. ObservationMethod is a convenience property that provides a quick and dirty approach to observation metadata.</td></tr>
   <tr><td class="label">The positional accurancy [numerical value]<br /><span class="geosciml">MappedFeature/positionalAccuracy</span></td><td class="obs">M</td><td class="obs">It is recommended that the same, approximate, value be given for all MappedFeatures and will generally be around 250m for a 1:1 million scale map.</td></tr>
   <tr><td class="label2">positionalAccuracy<br />[string]</td><td>O</td><td>Preferred use is a quantitative value defining the radius of an uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of 100 m for a line feature defines a buffer polygon of total width 200 m centered on the line. Some other text description that quantifies position accuracy may be provided, e.g. a term from a controlled vocabulary. Vocabulary used should be described in the dataset metadata.</td></tr>
   <tr style="background:#EFEFEF"><td>The sampling frame [urn]<br /><span class="geosciml">MappedFeature/samplingFrame</span></td><td class="obs">M</td><td class="obs">This property should be set to <b>urn:cgi:feature:CGI:EarthNaturalSurface</b><br/>for the surface map and <b>urn:cgi:feature:CGI:BedrockSurface</b> for the bedrock map</td></tr>
   <tr><td>The sampling frame</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The geometry<br /><span class="geosciml">MappedFeature/shape</span></td><td>M</td><td></td></tr>
   <tr><td class="label2">shape<br />[GM_Object]</td><td>M</td><td>Geometry defining the extent of the feature of interest. This is the only element with complex content, and must contain a GML geome-try that is valid for the Geography Markup Language (GML) simple features profile (OGC 06-049r1.). The shape value will generally be provided by GIS software, and will need no user input.</td></tr>
   <tr class="subtitle"><td colspan="3" class="obs">CONTACT: <i>featureMember/MappedFeature/specification/Contact</i><br />The following data are the attributes of the geologic structure which the current mappedFeature is a part of</td></tr>
   <tr><td class="label">A unique Geologic Structure ID [Any type]<br /><span class="geosciml">Contact id</span></td><td class="obs">M</td><td class="obs">Each GeologicStructure should be given a unique identifier.</td></tr>
   <tr><td class="label2">A unique Geologic Structure ID</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr><td class="label">The name of the geologic Structure<br /><span class="geosciml">Contact/name</span></td><td>O</td><td class="obs">Could be a simple name (text) or a urn (see the WP3 explanatory notes)</td></tr>
   <tr><td class="label2">name<br />[string]</td><td>O</td><td>Display name for the Contact. Examples: &#8216;depositional contact&#8217;, &#8216;unconformity&#8217;, &#8216;Martin-Escabrosa contact&#8217;</td></tr>
   <tr style="background:#EFEFEF"><td>The observation method [urn]<br /><span class="geosciml">Contact/observationMethod</span></td><td class="obs">M</td><td class="obs">either <b>urn:cgi:classifier:CGI:FeatureObservationMethod:201001:data_from_single_published_description</b><br />where the property values are derived from a single source document, or <br /><b>urn:cgi:classifier:CGI:FeatureObservationMethod:201001:synthesis_of_multiple_published_descriptions</b><br />where they are derived from multiple source documents.</td></tr>
   <tr><td>observationMethod<br />[string]</td><td>O</td><td>Metadata snippet indicating how the spatial extent of the feature was determined. ObservationMethod is a convenience property that provides a quick and dirty approach to observation metadata.</td></tr>
   <tr style="background:#EFEFEF"><td>The purpose<br /><span class="geosciml">Contact/purpose</span></td><td>?</td><td class="obs">For OneGeology-Europe the Purpose property should be set to : <b>typical_norm</b>.</td></tr>
   <tr><td>The purpose</td><td>-</td><td>There is no corresponding property in GeoSciML-Portrayal</td></tr>
   <tr class="subtitle2"><td colspan="3"><b>CONTACT TYPE</b></td></tr>
   <tr><td class="label">Contact Type [urn]<br /><span class="geosciml">Contact/contactType</span></td><td>?</td><td class="obs">In OneGeology-Europe Contacts are only being used to describe the linear features delimiting impact craters and calderas. Impact craters and calderas are not defined as polygons and the material within these structures should be described using GeologicUnit.  
   <ul>
   <li>For impact craters the Contact contactType property should be set to<br /><b>urn:cgi:classifier:CGI:ContactType:201001:impact_structure_boundary</b></li>
   <li>For calderas the Contact contactType property should be set to<br /><b>urn:cgi:classifier:CGI:ContactType:201001:volcanic_subsidence_zone_boundary</b></li>
   <li>For glacial stationary lines the Contact contactType property should be set to<br /><b>urn:cgi:classifier:CGI:ContactType:201001:glacial_stationary_line</b></li>
   <li>You may also wish to give the glacial stationary line a name (see WP3 Explanatory notes)</li>
   </ul></td></tr>
   <tr><td class="label2">contactType_uri<br />[string]</td><td>M</td><td>URI referring to a controlled concept from a vocabulary defining the Contact types. Mandatory property - if no value is provided then a URI referring to a controlled concept explaining why the value is nil must be provided.</td></tr>
   <tr><td class="label">Contact Type [urn]<br /><span class="geosciml">Contact/contactType</span></td><td>?</td><td class="obs">In OneGeology-Europe Contacts are only being used to describe the linear features delimiting impact craters and calderas. Impact craters and calderas are not defined as polygons and the material within these structures should be described using GeologicUnit.  
   <ul>
   <li>For impact craters the Contact contactType property should be set to<br /><b>urn:cgi:classifier:CGI:ContactType:201001:impact_structure_boundary</b></li>
   <li>For calderas the Contact contactType property should be set to<br /><b>urn:cgi:classifier:CGI:ContactType:201001:volcanic_subsidence_zone_boundary</b></li>
   <li>For glacial stationary lines the Contact contactType property should be set to<br /><b>urn:cgi:classifier:CGI:ContactType:201001:glacial_stationary_line</b></li>
   <li>You may also wish to give the glacial stationary line a name (see WP3 Explanatory notes)</li>
   </ul></td></tr>
   <tr><td class="label2">contactType<br />[string]</td><td>O</td><td>Text label specifying the kind of surface separating two geologic units including primary boundaries such as depositional contacts, all kinds of unconformities, intrusive contacts, and gradational contacts, as well as faults that separate geologic units. Ideally this would be the preferred label for the concept identified by contactType_uri</td></tr>
   <tr class="subtitle2"><td colspan="3" class="obs"><i>Contact/preferredAge/GeologicEvent</i><br />An age as “preferredAge” can be optionally provided for glacial stationary lines</td></tr>
   <tr><td class="label">The event Age<br /><span class="geosciml"></span>GeologicEvent/eventAge</td><td class="obs">M</td><td class="obs">The eventAge field should be populated as a numeric range (two attributes) or as a single numeric value (one attribute). The age recorded as a negative number (e.g. -250)</td></tr>
   <tr><td class="label">The event process [urn]<br /><span class="geosciml">GeologicEvent/eventProcess</span></td><td class="obs">M</td><td rowspan="3" class="obs">It is up to each data provider to present several event process (therefore, several attributes with distinct names) for describing the process that formed the geologic structure. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_EventProcess.xls" target="download">EventProcess</a>&#8221;.</td></tr>
   <tr><td class="label">...</td><td class="obs">O</td></tr>
   <tr><td class="label">The event process [urn]</td><td class="obs">O</td></tr>
   <tr><td class="label">The event environment [urn]<br /><span class="geosciml">GeologicEvent/eventEnvironment</span></td><td class="obs">O</td><td rowspan="3" class="obs">It is up to each data provider to present zero or several event environment (therefore, several attributes with distinct names) for describing the environment in which theGeologicStructure was formed. Use the 1GE vocabulary &#8220;<a href="../1GE/VocabXL/1GE_EventEnvironment.xls" target="download">EventEnvironment</a>&#8221;</td></tr>
   <tr><td class="label">...</td><td class="obs">O</td></tr>
   <tr><td class="label">The event environment [urn]</td><td class="obs">O</td></tr>
   <tr><td class="label2">event age, process, and environment</td><td class="obs">-</td><td>There are no corresponding properties in GeoSciML-Portrayal</td></tr>
   </table>

Section last modified: 22 March 2016

`Back <appendixK.html>`__\ \|\ `Next <appendixL_1.html>`__

.. |OneGeology logo| image:: appendixl/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
