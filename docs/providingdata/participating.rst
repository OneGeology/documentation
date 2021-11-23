
********************************
The aim: One service - many uses
********************************

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

******************
Map specifications
******************

Prerequisites for OneGeology involvement:

- the target scale is 1:1 000 000 but the project will be pragmatic and accept a range of scales and the best available data.
- to provide a WMS you only require a georeferenced scanned paper map or raster or vector digital GIS data.
- to provide feature and complex data queries via GeoSciML based WFS you

  - need to map from your GIS (ESRI ARCINFO, MapInfo, ORACLE etc.) data store to WFS server configuration (Geoserver or Mapserver/Cocoon).
  - need a (trained) person week, but includes getting WFS going with open source software (IT issues).
  - should note that the mapping process will be simple (small part of GeoSciML) if the themes chosen by the geological specification group are simple e.g. simple polygons with few attributes such as bedrock, lithology and age.

WMS = web map service — this is level 1, the minimum for OneGeology
WFS = web feature service, this holds more detailed data.

*****************************************
Technical specifications and requirements
*****************************************

.. figure:: /images/map_explorer.jpg
    :width: 417px
    :align: center
    :height: 249px
    :alt: Map
    :figclass: align-center

    Example of a GeoSciML downloaded map — one of the aims of OneGeology

Level 1 involvement with OneGeology web services
================================================

Geological surveys and similar institutions that wish to contribute to the OneGeology initiative at Level 1 are aiming to provide an **OGC Web Mapping Service (WMS)** from a web server within their organisation, or hosted by a neighbouring organisation, of some basic geological maps.

The maps will appear in the computer users application, which may be a web browser, in a raster or image form. Such image maps will be combinable with other spatial datasets depending on the application the user wishes to apply. If the data that is the source behind the WMS is of digital vector data form with attributes associated with those vectors e.g. information attached to a particular type polygon or boundary then the WMS will allow the display of such attributes for each polygon. If the data source behind the WMS is of a simple scanned raster type e.g. scanned from a paper map and served as a raster image, then such attributes or further informa0tion do not exist for separate polygons.


Level 2 involvement with OneGeology web services
================================================

Geological surveys and similar institutions that wish to contribute to the OneGeology initiative at Level 2 are aiming to provide an **OGC Web Feature Service (WFS)** from a web server within their organisation, or hosted by a neighbouring organisation, of some basic geological 'map' data.

These WFS will allow the user to download data in GeoSciML form resulting from queries (geographic or other attribute based) of the data over the web so that the same query could be sent to some/all of the OneGeology contributors WFS services around the world.

*********
Cookbooks
*********

What is a cookbook?
===================

A cookbook is a best practice manual 'containing a straightforward set of already tried and tested *recipe or instructions* for a specific activity'.

A series of 'cookbooks' giving best practice on using open-source, i.e. freely available, software to set up WFS will be provided by the OneGeology initiative along with guidance on how to configure a WFS using GeoSciML from the institutions' internal digital databases.

These documents will provide specific work-flow guidance notes to enable full participation of your organisation regardless of expertise, location or amount of data available.

Cookbook specification
======================

A series of OneGeology-specific branded cookbooks are available as follows:

- Online
    - `Cookbook No 1 <https://onegeology-docs.readthedocs.io/en/latest/webservices.html#wms>`_ - explains how to setup a WMS (view) service (with no GML/GeoSciML).

- PDF Download (to be moved online shortly)
    - `Cookbook No 6 <http://www.onegeology.org/docs/technical/CB6-HowToServe-a-OneGeology-WCS_v1.pdf>`_ - decribes how to set up a WCS (download) web service on your web server using open-source software.
    - `Cookbook No 7 <http://www.onegeology.org/docs/technical/GeoSciML_Cookbook_1.3.pdf>`_ - explains how we map from the backend database to the GeoSciML WFS service.
    - `Cookbook No 8 <http://www.onegeology.org/docs/technical/OneGeologyWFSCookbook_v1.4.pdf>`_- describes how to set up a WFS (download) web service on your web server using open-source software.

The aim is that multilingual versions will be available wherever possible.

****************
Support services
****************

Services which will be available to OneGeology participants to help advise and assist with serving data to the Portal include:
- This documentation including cookbooks' for step-by-step guidance.
- a support team, and `email <onegeologyhelp@bgs.ac.uk>`_.
- regional workshops to build technology capability within staff.

Work will be based on open-source technologies so all the OGC web services required software can be purchased cost free. However, a contributing survey must either have its own standard Internet server or have access to such a server through a neighbouring or regional organisation.

********************************************
Register your data or service for the Portal
********************************************

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
