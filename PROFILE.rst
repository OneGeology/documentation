.. contents::

.. _service_provision_onegeology_profile:

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

