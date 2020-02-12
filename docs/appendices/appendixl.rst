========================================================================
Mapping OneGeology-Europe data model to GeoSciML-Portrayal \| OneGeology
========================================================================

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
      WMS <home.html>`__ > Mapping 1GE data model to GSML-P

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

         .. rubric:: Mapping OneGeology-Europe data model to
            GeoSciML-Portrayal 4.0
            :name: mapping-onegeology-europe-data-model-to-geosciml-portrayal-4.0
            :class: technical_progress_side_menu

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

         .. rubric:: Mapping OneGeology-Europe GEOLOGIC UNITS to
            GeoSciML-Portrayal GeologicUnitView features
            :name: mapping-onegeology-europe-geologic-units-to-geosciml-portrayal-geologicunitview-features

         Note that whilst many of the properties required for the
         OneGeology-Europe GEOLOGIC UNITS mapping are optional, or not
         specified by GeoSciML-Portrayal GeologicUnitView features,
         GeoSciML-Portrayal mandates other properties (that is
         properties not found in OneGeology-Europe) are defined, such as
         representativeAge_uri. Please refer to the GeoSciML-Portrayal
         `GeologicUnitView features <7_3_3.html>`__ page of the
         cookboook for more information.

         Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal
         GeologicUnitView features
         GEOLOGIC UNITS. Each feature (polygon) should have at least the
         following attributes

*featureMember/MappedFeature* for each MappedFeature (for each polygon)

A unique feature ID

M

The unique ID of the polygon is often named “fid” within a shapefile

identifier

M

Globally unique identifier for the individual feature. Recommended
practice is that this identifier be derived from the primary key for the
spatial objects in the source data in case information needs to be
transferred from the interchange format back to the source database.
This identifier is analogous to the identifier for a GeoSciML
MappedFeature.

| Observation method [urn]
| MappedFeature/observationMethod

M

Always
**urn:cgi:classifier:CGI:MappedFeatureObservationMethod:201001:compilation**

| observationMethod
| [string]

O

ObservationMethod is a convenience property to provide observation
metadata. Example values might include ‘field observation by author’,
‘compilation from published maps’, ‘air photo interpretation’. Recommend
using the CGI Feature Observation Method vocabulary.

| The positional accurancy [numerical value]
| MappedFeature/positionalAccuracy

M

It is recommended that the same, approximate, value be given for all
MappedFeatures and will generally be **250**

| positionalAccuracy
| [string]

O

accuracy may be provided, e.g. a term from a controlled vocabulary.
Vocabulary used should be described in the dataset metadata. For polygon
mapped features this is intended for use to indicate the position
uncertainty of the contact and fault features bounding the outcrop
polygon, which is only necessary if the associated line features are not
included with the polygons.

| The sampling frame [urn]
| MappedFeature/samplingFrame

M

This property should be set to
**urn:cgi:feature:CGI:EarthNaturalSurface** for the surface map and
**urn:cgi:feature:CGI:BedrockSurface** for the bedrock map

The sampling frame

-

There is no corresponding value in GeoSciML-Portrayal

| The geometry
| MappedFeature/shape

M

| shape
| [GM_Object (GM_polygon)]

M

Geometry defining the extent of the feature of interest.

| *featureMember/MappedFeature/specification/GeologicUnit*
| The following data are the attributes of the geologic unit which the
  current mappedFeature is a part of

| A unique Geologic Unit ID [Any type]
| GeologicUnit id

M

Each GeologicUnit should be given a unique identifier

| geologicUnitType
| [string]

O

Type of GeologicUnit (as defined in GeoSciML).

| The name of the geologic Unit
| GeologicUnit/name

M

Could be a simple name (text) or a urn (see the WP3 explanatory notes)

| name
| [string]

O

Display name for the GeologicUnit; this can be used to put in a geologic
unit name, or more likely an abbreviation used to label outcrops of the
unit in a map display.

| The “free text” description
| GeologicUnit/description

O

| description
| [string]

O

Text description of the GeologicUnit, typically taken from an entry on a
geological map legend.

| The geologic unit type [urn]
| GeologicUnit/geologicUnitType

M

Use the 1GE vocabulary
“\ `GeologicUnitType <../1GE/VocabXL/1GE_GeologicUnitType.xls>`__\ ”

| geologicUnitType_uri
| [string]

M

URI referring to a controlled concept from a vocabulary defining the
GeologicUnit types. Mandatory property - if no value is provided then a
URI referring to a controlled concept explaining why the value is nil
must be provided.

| The observation method [urn]
| GeologicUnit/observationMethod

M

| either
  **urn:cgi:classifier:CGI:FeatureObservationMethod:201001:data_from_single_published_description**
| where the property values are derived from a single source document,
  or
| **urn:cgi:classifier:CGI:FeatureObservationMethod:201001:synthesis_of_multiple_published_descriptions**
| where they are derived from multiple source documents.

| observationMethod
| [string]

O

ObservationMethod is a convenience property to provide observation
metadata. Example values might include ‘field observation by author’,
‘compilation from published maps’, ‘air photo interpretation’. Recommend
using the CGI Feature Observation Method vocabulary.

| The purpose
| GeologicUnit/purpose

M

For OneGeology-Europe the Purpose property should be set to:
**typical_norm**.

The purpose

-

There is no corresponding property in GeoSciML-Portrayal

| Body Morphology [urn]
| GeologicUnit/bodyMorphology

O

For dykes the GeologicUnit bodyMorphology property should always be set
to\ **urn:cgi:classifier:CGI:GeologicUnitMorphology:201001:dike** In any
other case, the value is empty.

Body Morphology

-

There is no corresponding property in GeoSciML-Portrayal

| *GeologicUnit/preferredAge/GeologicEvent*
| The following attributes describe the age of formation of the geologic
  unit

| The name (Orogenic Event) [urn]
| GeologicEvent/name

O

Only given where the Geologic Unit was formed by the orogenic event. Use
the 1GE vocabulary
“\ `OrogenicEvents <../1GE/VocabXL/1GE_Orogenic_Events.xls>`__\ ”.

The name (Orogenic Event)

-

There is no corresponding property in GeoSciML-Portrayal

| The event Age - Lower [urn]
| GeologicEvent/eventAge/.../lower

M

Use the 1GE vocabulary “\ `Ages <../1GE/VocabXL/1GE_Ages.xls>`__\ ”

| representativeOlderAge_uri
| [string]

M

URI referring to a controlled concept specifying the most
rep-resentative older value in a range of stratigraphic age intervals
for the GeologicUnit. This will be defined entirely at the discretion of
the data provider and may be a single event selected from the geologic
feature’s geological history or a value summarizing all or part of the
feature’s history.

| The event Age - Upper [urn]
| GeologicEvent/eventAge/.../upper

M

Use the 1GE vocabulary “\ `Ages <../1GE/VocabXL/1GE_Ages.xls>`__\ ”

| representativeYoungerAge_uri
| [string]

M

URI referring to a controlled concept specifying the most representative
younger value in a range of stratigraphic age intervals for the
GeologicUnit. This will be defined entirely at the discretion of the
data provider and may be a single event selected from the geologic
feature’s geological history or a value summarizing all or part of the
feature’s history.

| The event process [urn]
| GeologicEvent/eventProcess

M

Record the process that formed the Geologic Unit. Use the 1GE vocabulary
“\ `EventProcess <../1GE/VocabXL/1GE_EventProcess.xls>`__\ ”.

The event process

-

There is no corresponding property in GeoSciML-Portrayal

| The event environment [urn]
| GeologicEvent/eventEnvironment

O

Can be used to describe the environment which the Geologic Unit was
formed. Use the 1GE vocabulary
"`EventEnvironment <../1GE/VocabXL/1GE_EventEnvironment.xls>`__".

The event environment

-

There is no corresponding property in GeoSciML-Portrayal

| *GeologicUnit/geologicHistory/GeologicEvent*
| The following attributes describe a serie of geologic events that led
  to the formation of the geologic unit. To describe such a geologic
  history is *not* mandatory. But for each geologic history / geologic
  event described, one event age and at least one event process should
  be described. The rules are the same that for the preferred age. It is
  up to each data provider to describe 0 or n geologic events of the
  geologic history.

| The name (for Orogenic Event) [urn]
| GeologicEvent/name

O

Use the vocabulary
“\ `OrogenicEvents <../1GE/VocabXL/1GE_Orogenic_Events.xls>`__\ ”

The name (for Orogenic Event)

-

There is no corresponding property in GeoSciML-Portrayal

| The event Age
| GeologicEvent/eventAge

M

Can be defined as a range of urn [lower_age, upper_age], as a range of
numerical values, as a single numerical value, or as a single urn. In
the case of urns, use the 1GE vocabulary
"`Ages <../1GE/VocabXL/1GE_Ages.xls>`__"

The event Age

-

There is no corresponding property in GeoSciML-Portrayal

| The event process [urn]
| GeologicEvent/eventProcess

M

It is up to each data provider to present several event process
(therefore, several attributes with distinct names) for describing the
current geologic event of the geologic history. Use the 1GE vocabulary
“\ `EventProcess <../1GE/VocabXL/1GE_EventProcess.xls>`__\ ”.

...

O

The event process [urn]

O

| geologicHistory
| [string]

O

Text (possibly formatted with formal syntax) description of the age of
the GeologicUnit (where age is a sequence of events and may include
process and environment information).

| The event environment [urn]
| GeologicEvent/eventEnvironment

O

It is up to each data provider to present several event environment
(therefore, several attributes with distinct names) for describing the
current geologic event of the geologic history. Use the 1GE vocabulary
“\ `EventEnvironment <../1GE/VocabXL/1GE_EventEnvironment.xls>`__\ ”

...

O

The event environment [urn]

O

The event environment

-

There is no corresponding property in GeoSciML-Portrayal

| *GeologicUnit/composition/CompositionPart*
| The following attributes describe the lithology of the geologic unit.
  Some GeologicUnits will have a single CompositionPart, but others may
  have multiple CompositionParts, such as interbedded layers, each of
  which can be described with a distinct CompositionPart. Each
  CompositionPart has three properties – the lithology; the role of the
  CompositionPart in the GeologicUnit as a whole; and the proportion of
  the CompositionPart in the GeologicUnit as a whole. *For example, if
  the geologic units of a given dataset have in some cases 5 distincts
  lithology, but not more, then the database (or shapefile) will have 5
  attributes lithology, role and proportion.* the main lithology
  (proportion=all or predominant) attibute will always have a value (at
  least one lithology is mandatory), but the others will be often empty.

| Lithology [urn]
| CompositionPart/lithology

M

Use the 1GE “\ `Lithology <../1GE/VocabXL/1GE_Lithology_.xls>`__\ ”
vocabulary

| representativeLithology_uri
| [string]

M

URI referring to a controlled concept specifying the characteristic or
representative lithology of the unit. This may be a concept that defines
the super-type of all lithology values present within a GeologicUnit or
a concept defining the lithology of the dominant CompositionPart (as
defined in GeoSciML) of the unit. This identifier is intended for use as
the symbol key for a lithologic map portrayal of the geologic unit
features.

| Lithology [urn]
| CompositionPart/lithology

M

Use the 1GE “\ `Lithology <../1GE/VocabXL/1GE_Lithology_.xls>`__\ ”
vocabulary

| Lithology
| [string]

O

Text (possibly formatted with formal syntax) description of the
GeologicUnit’s lithology.

| Role [urn]
| CompositionPart/role

M

-  Where the CompositionPart is the only one in the GeologicUnit the
   role property should be set to
   **urn:cgi:classifier:CGI:GeologicUnitPartRole:200811:only_part**
-  Where the CompositionPart is one of several in the GeologicUnit the
   role property should be set to
   **urn:cgi:classifier:CGI:GeologicUnitPartRole:200811:unspecified_part_role**
-  See also the detailed explanation in the WP3 document: the
   GeologicUnitPartRole has other values in serveral cases ("Molasse",
   "Ophiolitic mélange", ...).

Role

-

There is no corresponding property in GeoSciML-Portrayal

| Proportion [urn]
| CompositionPart/proportion

M

-  Where there is only one CompositionPart is the GeologicUnit the
   Proportion property should be set to
   **urn:cgi:classifier:CGI:ProportionTerm:201001:all**.
-  Where there are multiple CompositionParts in the GeologicUnit the
   CompositionPart that comprises the single largest proportion of the
   GeologicUnit should be given a Proportion value of
   **urn:cgi:classifier:CGI:ProportionTerm:201001:predominant**.
-  All other CompositionParts should be given a Proportion value of
   **urn:cgi:classifier:CGI:ProportionTerm:201001:subordinate**.
-  Note that where there are multiple CompositionParts in the
   GeologicUnit one must be given a value of
   **urn:cgi:classifier:CGI:ProportionTerm:201001:predominant** and this
   will be the one used for portrayal of the lithology of the
   GeologicUnit.

Proportion

-

There is no corresponding property in GeoSciML-Portrayal

| GeologicUnit/metamorphicCharacter/MetamorphicDescription
| The following attributes describe the metamorphism of a geologic unit.
  It is optional. If a data provider do not wish to describe
  metamorphism for any of the geologic units, then these attributes are
  not required. Only one Metamorphic description can be given

| Metamorphic facies [urn]
| MetamorphicDescription/metamorphicFacies

O

Use of the 1GE vocabulary
“\ `MetamorphicFacies <../1GE/VocabXL/1GE_MetamorphicFacies.xls>`__\ ”.
Several Metamorphic facies can be given

...

Metamorphic facies [urn]

| Metamorphic grade [urn]
| MetamorphicDescription/metamorphicGrade

O

Use of the 1GE vocabulary
“\ `"MetamorphicGrade <../1GE/VocabXL/1GE_MetamorphicGrade.xls>`__\ ”

| **MetamorphicDescription/protolithLithology/RockMaterial**
| The following attributes describe the protolith lithology of the
  metamorphic description. It is optional, and there can be several
  protolith lithology. If a protolith is given, then consolidation
  degree and lithology are mandatory

| lithology [urn]
| RockMaterial/lithology

Use the 1GE vocabulary
“\ `Lithology <../1GE/VocabXL/1GE_Lithology_.xls>`__\ ”.

| consolidation degree [urn]
| RockMaterial/consolidationDegree

If a lithology is given, then the consolidationDegree should always be
set
to\ **urn:cgi:classifier:CGI:ConsolidationDegree:200811:consolidation_not_specified**

| purpose
| RockMaterial/purpose

O

If a lithology is given, then the purpore should always be set to
**typical_norm**

Metamorphic character, description...

-

There are no corresponding properties in GeoSciML-Portrayal

**In OneGeology-Europe the only types of structure that are being used
are Faults and Contacts. Contacts are only being used to describe
Calderas, Impact Craters, and Glacial Stationary Lines.** Below we have
separated Faults from Contacts becuase in GeoSciML-Portrayal they have
different mappings.

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal ShearDisplacementStructureView features
======================================================================================================

Note that whilst many of the properties required for the
OneGeology-Europe GEOLOGIC STRUCTURES mapping are optional, or not
specified by GeoSciML-Portrayal ShearDisplacementStructureView features,
GeoSciML-Portrayal mandates other properties (that is properties not
found in OneGeology-Europe) are defined, such as movementType_uri and
deformationStyle_uri. Please refer to the GeoSciML-Portrayal
`ShearDisplacementStructureView features <7_3_2.html>`__ page of the
cookboook for more information.

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal
ShearDisplacementStructureView features

GEOLOGIC STRUCTURES. Each feature should have at least the following
attributes

*featureMember/MappedFeature* for each MappedFeature

A unique feature ID

M

This unique ID is often named “fid” within a shapefile

identifier

M

Globally unique identifier for the individual feature. Recommended
practice is that this identifier be derived from the primary key for the
spatial objects in the source data in case information needs to be
transferred from the interchange format back to the source database.
This identifier is analogous to the identifier for a GeoSciML
MappedFeature.

| Observation method [urn]
| MappedFeature/observationMethod

?

Always
“urn:cgi:classifier:CGI:MappedFeatureObservationMethod:201001:compilation”,
therefore not required in the database or within the shapefile: can be
directly encoded in the GeoSciML response.

| observationMethod
| [string]

O

ObservationMethod is a convenience property that provides a quick and
dirty approach to observation metadata when data are reported using a
feature view (as opposed to observation view).

| The positional accurancy [numerical value]
| MappedFeature/positionalAccuracy

M

It is recommended that the same, approximate, value be given for all
MappedFeatures and will generally be around 250m for a 1:1 million scale
map.

| positionalAccuracy
| [string]

O

Preferred use is a quantitative value defining the radius of an
uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of
100 m for a line feature defines a buffer polygon of total width 200 m
centered on the line. Some other text description that quantifies
position accuracy may be provided, e.g. a term from a controlled
vocabulary. Vocabulary used should be described in the dataset metadata.

| The sampling frame [urn]
| MappedFeature/samplingFrame

M

This property should be set to
**urn:cgi:feature:CGI:EarthNaturalSurface** for the surface map
and\ **urn:cgi:feature:CGI:BedrockSurface** for the bedrock map

The sampling frame

-

There is no corresponding property in GeoSciML-Portrayal

| The geometry
| MappedFeature/shape

M

| shape
| [GM_Object (GM_curve)]

M

Geometry defining the extent of the feature of interest.

| FAULT:
  *featureMember/MappedFeature/specification/ShearDisplacementStructure*
| the following data are the attributes of the geologic structure which
  the current mappedFeature is a part of

| A unique Geologic Structure ID [Any type]
| ShearDisplacementStructure

M

Each GeologicStructure should be given a unique identifier.

A unique Geologic Structure ID

-

There is no corresponding property in GeoSciML-Portrayal

| The name of the geologic Structure
| ShearDisplacementStructure/name

O

Could be a simple name (text) or a urn (see the WP3 explanatory notes)

| name
| [string]

O

Display name for the ShearDisplacementStructure. This may be a generic
fault type, e.g. ‘thrust fault’, ‘strike-slip fault’, or a particular
fault name, e.g. ‘Moine thrust’, ‘san Andreas Fault’.

| The observation method [urn]
| ShearDisplacementStructure/observationMethod

M

| either
  **urn:cgi:classifier:CGI:FeatureObservationMethod:201001:data_from_single_published_description**
| where the property values are derived from a single source document,
  or
| **urn:cgi:classifier:CGI:FeatureObservationMethod:201001:synthesis_of_multiple_published_descriptions**
| where they are derived from multiple source documents.

| observationMethod
| [string]

O

Metadata snippet indicating how the spatial extent of the feature was
determined. ObservationMethod is a convenience property that provides a
quick and dirty approach to observation metadata when data are reported
using a feature view (as opposed to observation view).

| The purpose
| ShearDisplacementStructure/purpose

?

For OneGeology-Europe the Purpose property should be set to :
**typical_norm**.

The purpose

-

There is no corresponding property in GeoSciML-Portrayal

**FAULT TYPE**

| Fault Type [urn]
| ShearDisplacementStructure/faultType

?

**For all Faults the property faultType must be populated** with the URN
of one of the concepts described in the vocabulary
“\ `FaultType <../1GE/VocabXL/1GE_FaultType.xls>`__\ ”.

| faultType
| [string]

O

Type of ShearDisplacementStructure (as defined in GeoSciML).

| Fault Type [urn]
| ShearDisplacementStructure/faultType

?

**For all Faults the property faultType must be populated** with the URN
of one of the concepts described in the vocabulary
“\ `FaultType <../1GE/VocabXL/1GE_FaultType.xls>`__\ ”.

| faultType_uri
| [string]

M

URI referring to a controlled concept from a vocabulary defining the
fault (ShearDisplacementStructure) type. Mandatory property - if no
value is provided then a URI referring to a controlled concept
explaining why the value is nil must be provided.

| *Contact/preferredAge/GeologicEvent*
| An age as “preferredAge” can be optionally provided for glacial
  stationary lines

| The event Age
| GeologicEvent/eventAge

M

The eventAge field should be populated as a numeric range (two
attributes) or as a single numeric value (one attribute). The age
recorded as a negative number (e.g. -250)

| representativeAge_uri
| [string]

M

URI referring to a controlled concept specifying the most representative
stratigraphic age interval for the GeologicUnit. This will be defined
entirely at the discretion of the data provider and may be a single
event selected from the geologic feature’s geological history or a value
summarizing the all or part of the feature’s history.

| The event Age
| GeologicEvent/eventAge

M

The eventAge field should be populated as a numeric range (two
attributes) or as a single numeric value (one attribute). The age
recorded as a negative number (e.g. -250)

| representativeOlderAge_uri
| [string]

M

URI referring to a controlled concept specifying the most representative
older value in a range of stratigraphic age intervals for the
GeologicUnit. This will be defined entirely at the discretion of the
data provider and may be a single event selected from the geologic
feature’s geological history or a value summarizing the all or part of
the feature’s history.

| The event Age
| GeologicEvent/eventAge

M

The eventAge field should be populated as a numeric range (two
attributes) or as a single numeric value (one attribute). The age
recorded as a negative number (e.g. -250)

| representativeYoungerAge_uri
| [string]

M

URI referring to a controlled concept specifying the most representative
younger value in a range of stratigraphic age intervals for the
GeologicUnit. This will be defined entirely at the discretion of the
data provider and may be a single event selected from the geologic
feature’s geological history or a value summarizing the all or part of
the feature’s history.

| The event process [urn]
| GeologicEvent/eventProcess

M

It is up to each data provider to present several event process
(therefore, several attributes with distinct names) for describing the
process that formed the geologic structure. Use the 1GE vocabulary
"`EventProcess <../1GE/VocabXL/1GE_EventProcess.xls>`__".

...

O

The event process [urn]

O

| geologicHistory
| [string]

O

Text (possibly formatted with formal syntax) description of the sequence
of events that formed and have affected the ShearDisplacementStructure.
Events include process and optional environment information.

| The event environment [urn]
| GeologicEvent/eventEnvironment

O

It is up to each data provider to present zero or several event
environment (therefore, several attributes with distinct names) for
describing the environment in which theGeologicStructure was formed. Use
the 1GE vocabulary
“\ `EventEnvironment <../1GE/VocabXL/1GE_EventEnvironment.xls>`__\ ”

...

O

The event environment [urn]

O

The event environment

-

There is no corresponding property in GeoSciML-Portrayal

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal ContactView features
===================================================================================

Mapping OneGeology-Europe GEOLOGIC UNITS to GeoSciML-Portrayal
ContactView features

GEOLOGIC STRUCTURES. Each feature should have at least the following
attributes

*featureMember/MappedFeature* For each MappedFeature

A unique feature ID

M

This unique ID is often named “fid” within a shapefile

identifier

M

Globally unique identifier for the individual feature. Recommended
practice is that this identifier be derived from the primary key for the
spatial objects in the source data in case information needs to be
transferred from the interchange format back to the source database.
This identifier is analogous to the identifier for a GeoSciML
MappedFeature.

| Observation method [urn]
| MappedFeature/observationMethod

?

Always
“urn:cgi:classifier:CGI:MappedFeatureObservationMethod:201001:compilation",
therefore not required in the database or within the shapefile: can be
directly encoded in the GeoSciML response.

| observationMethod
| [string]

O

Metadata snippet indicating how the spatial extent of the feature was
determined. ObservationMethod is a convenience property that provides a
quick and dirty approach to observation metadata.

| The positional accurancy [numerical value]
| MappedFeature/positionalAccuracy

M

It is recommended that the same, approximate, value be given for all
MappedFeatures and will generally be around 250m for a 1:1 million scale
map.

| positionalAccuracy
| [string]

O

Preferred use is a quantitative value defining the radius of an
uncertainty buffer around a MappedFeature, e.g. a positionAccuracy of
100 m for a line feature defines a buffer polygon of total width 200 m
centered on the line. Some other text description that quantifies
position accuracy may be provided, e.g. a term from a controlled
vocabulary. Vocabulary used should be described in the dataset metadata.

| The sampling frame [urn]
| MappedFeature/samplingFrame

M

| This property should be set to
  **urn:cgi:feature:CGI:EarthNaturalSurface**
| for the surface map and **urn:cgi:feature:CGI:BedrockSurface** for the
  bedrock map

The sampling frame

-

There is no corresponding property in GeoSciML-Portrayal

| The geometry
| MappedFeature/shape

M

| shape
| [GM_Object]

M

Geometry defining the extent of the feature of interest. This is the
only element with complex content, and must contain a GML geome-try that
is valid for the Geography Markup Language (GML) simple features profile
(OGC 06-049r1.). The shape value will generally be provided by GIS
software, and will need no user input.

| CONTACT: *featureMember/MappedFeature/specification/Contact*
| The following data are the attributes of the geologic structure which
  the current mappedFeature is a part of

| A unique Geologic Structure ID [Any type]
| Contact id

M

Each GeologicStructure should be given a unique identifier.

A unique Geologic Structure ID

-

There is no corresponding property in GeoSciML-Portrayal

| The name of the geologic Structure
| Contact/name

O

Could be a simple name (text) or a urn (see the WP3 explanatory notes)

| name
| [string]

O

Display name for the Contact. Examples: ‘depositional contact’,
‘unconformity’, ‘Martin-Escabrosa contact’

| The observation method [urn]
| Contact/observationMethod

M

| either
  **urn:cgi:classifier:CGI:FeatureObservationMethod:201001:data_from_single_published_description**
| where the property values are derived from a single source document,
  or
| **urn:cgi:classifier:CGI:FeatureObservationMethod:201001:synthesis_of_multiple_published_descriptions**
| where they are derived from multiple source documents.

| observationMethod
| [string]

O

Metadata snippet indicating how the spatial extent of the feature was
determined. ObservationMethod is a convenience property that provides a
quick and dirty approach to observation metadata.

| The purpose
| Contact/purpose

?

For OneGeology-Europe the Purpose property should be set to :
**typical_norm**.

The purpose

-

There is no corresponding property in GeoSciML-Portrayal

**CONTACT TYPE**

| Contact Type [urn]
| Contact/contactType

?

In OneGeology-Europe Contacts are only being used to describe the linear
features delimiting impact craters and calderas. Impact craters and
calderas are not defined as polygons and the material within these
structures should be described using GeologicUnit.

-  For impact craters the Contact contactType property should be set to
   **urn:cgi:classifier:CGI:ContactType:201001:impact_structure_boundary**
-  For calderas the Contact contactType property should be set to
   **urn:cgi:classifier:CGI:ContactType:201001:volcanic_subsidence_zone_boundary**
-  For glacial stationary lines the Contact contactType property should
   be set to
   **urn:cgi:classifier:CGI:ContactType:201001:glacial_stationary_line**
-  You may also wish to give the glacial stationary line a name (see WP3
   Explanatory notes)

| contactType_uri
| [string]

M

URI referring to a controlled concept from a vocabulary defining the
Contact types. Mandatory property - if no value is provided then a URI
referring to a controlled concept explaining why the value is nil must
be provided.

| Contact Type [urn]
| Contact/contactType

?

In OneGeology-Europe Contacts are only being used to describe the linear
features delimiting impact craters and calderas. Impact craters and
calderas are not defined as polygons and the material within these
structures should be described using GeologicUnit.

-  For impact craters the Contact contactType property should be set to
   **urn:cgi:classifier:CGI:ContactType:201001:impact_structure_boundary**
-  For calderas the Contact contactType property should be set to
   **urn:cgi:classifier:CGI:ContactType:201001:volcanic_subsidence_zone_boundary**
-  For glacial stationary lines the Contact contactType property should
   be set to
   **urn:cgi:classifier:CGI:ContactType:201001:glacial_stationary_line**
-  You may also wish to give the glacial stationary line a name (see WP3
   Explanatory notes)

| contactType
| [string]

O

Text label specifying the kind of surface separating two geologic units
including primary boundaries such as depositional contacts, all kinds of
unconformities, intrusive contacts, and gradational contacts, as well as
faults that separate geologic units. Ideally this would be the preferred
label for the concept identified by contactType_uri

| *Contact/preferredAge/GeologicEvent*
| An age as “preferredAge” can be optionally provided for glacial
  stationary lines

| The event Age
| GeologicEvent/eventAge

M

The eventAge field should be populated as a numeric range (two
attributes) or as a single numeric value (one attribute). The age
recorded as a negative number (e.g. -250)

| The event process [urn]
| GeologicEvent/eventProcess

M

It is up to each data provider to present several event process
(therefore, several attributes with distinct names) for describing the
process that formed the geologic structure. Use the 1GE vocabulary
“\ `EventProcess <../1GE/VocabXL/1GE_EventProcess.xls>`__\ ”.

...

O

The event process [urn]

O

| The event environment [urn]
| GeologicEvent/eventEnvironment

O

It is up to each data provider to present zero or several event
environment (therefore, several attributes with distinct names) for
describing the environment in which theGeologicStructure was formed. Use
the 1GE vocabulary
“\ `EventEnvironment <../1GE/VocabXL/1GE_EventEnvironment.xls>`__\ ”

...

O

The event environment [urn]

O

event age, process, and environment

-

There are no corresponding properties in GeoSciML-Portrayal

Section last modified: 22 March 2016

`Back <appendixK.html>`__\ \|\ `Next <appendixL_1.html>`__

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
Survey <http://www.bgs.ac.uk/hosted.html>`__ but responsibility for the
content of the site lies with OneGeology not with the British Geological
Survey. Questions, suggestions, or comments regarding the contents of
this site should be directed to `the OneGeology
administration <mailto:onegeology@bgs.ac.uk>`__.

.. |OneGeology logo| image:: appendixl/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
