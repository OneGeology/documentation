OneGeology Portal
========

The portal will collate the web services provided by member organisations.

- The portal can be accessed using most internet browsers.
- Basic map data is called a WMS (Web Map Service)
- OneGeology aims to use Free and Open Source software wherever possible.
- The data is “served” directly from the provider organisation.
- The provider organisation retains full ownership and responsibility and is able to change or modify data whenever necessary.

Using the OneGeology Portal
--------

.. todo::
   Currently taken WMS cookbook 1.4 text removing over-technical detail. Needs to have a general intro to the different kinds of service (WMS, WFS and WCS) service and what sort of things you might be able to  do with them. Probably not covering the kinds of data (traditional geol map, boreholes, minerals) in this section? Should make a generic list of the sorts of functionality a client may provide so can refer to this under each item. Need to consider whether we can actually maintain detailed instructions on more than a couple of examples. And should we? Should be able just to point to software's own documentation on using OGC services. Maybe just make a list with pointer to home page, specific documentation package may have for OGC services (should be standard stuff these days) and any gotchas/special considerations we have noticed for particular examples. The target audience for this section could include a range of levels of IT and geological knowledge and include people just using the services and service providers who also need to understand how their services can be made use of.

.. todo::

   Below introductory paragraph should probably point to some general OneGeology introduction elsewhere on www.onegeology.org to explain the range of data and purpose of OneGeology. We may need to get it written if it doesn't exist right now. We want to refer to purpose, kinds of data that are available or will be in future. This page is where the kinds of viewing, data query etc. that can be done will be introduced.

.. todo::

   List the other parts of www.onegeology.org that will link directly to here. At the moment a sidebar sub-menu "Technical detail for participants" -> "How to use a OneGeology service" and some links from other pages. Also the page http://onegeology.org/portal/portal_uses.html has links to various client pages but it all seems a bit of a repetitive anomaly and something that should be entirely replaced by content here.

OneGeology makes data from geological data providers around the world accessible to those who would like to see and use it. The majority of this data is the type that is portrayed on traditional geological maps. There are increasing amounts with different geologically related types of data such as geophysics, boreholes and hydrogeology. This data is made available by means of Open GeoSpatial Consortium `OGC <http://www.opengeospatial.org>`_ standard web services that can be accessesed by a number of free and commercial clients. Currently OneGeology makes use of three OGC standards: Web Map Service `WMS <http://www.opengeospatial.org/standards/wms>`_, Web Feature Service `WFS <http://www.opengeospatial.org/standards/wfs>`_ and Web Coverage Service `WCS <http://www.opengeospatial.org/standards/wcs>`_. These different service standards define different kinds of capability for examining the data. 

WMS provides the ability to see a map image projected to its correct geographical location in a number of map projections. This will usually be accompanied by a legend which explains the symbology used in the map. Commonly, many WMS also provide the ability to select a point on the map and get a summary in text or other format of data values for that point. The majority of OneGeology services are WMS. A small number of these WMS also provide the ability to change the symbology of the map depending on the underlying data (e.g. to highlight formations of a particular age). These are called `SLD <http://www.opengeospatial.org/standards/sld>`_ enabled WMS.

WFS provide the ability to query a service based on spatial and other criteria and return the matching data in a `GML <http://www.opengeospatial.org/standards/gml>`_ format and maybe other formats as well. It assumes the data has been structured as a collection of features with spatial and other, possibly complex properties. OneGeology is focussed on two standard formats for data exchange: `GeoSciML <http://www.geosciml.org>`_ and `ERML <http://www.earthresourceml.org/>`_. The data available from a given WFS may be visually portrayed in one or more related WMS layers.

WCS also provices the ability to return matching data based on spatial and other criteria but the data is structured as coverages where values of some fixed set of properties are defined for each point over some spatial domain. Although theoretically different kinds of division of spatial domain are possible, currently all coverages are based on regular grids. The properties are also simple whether numerical or categorical. As image formats generally specify colour values at regular grid cells then a WCS may return coverages that can be viewed as an image directly as well as data formats that need to be processed by some application.

In simple terms, currently WFS are used for spatial data stored in some vector format and WCS for data stored in a raster gridded format.

.. todo::

   Should we also mention the CSW for searching metadata about the services in the above list?

The Portal has the following functions:

- Zoom
- Pan
- Get Information tool
- Help menu
- multi-layer map view,
- opacity selection,
- legend viewer, 
- details of provider organisation / geological survey
- web link URL to the provider survey
- brief description of the data layer
- conditions of use information for each layer

Using the data from OneGeology on other platforms
------------

The following pages show how you may access services using these OGC standards (including those not part of OneGeology) in a number of popular desktop software clients and web based browser applications. We concentrate first on the web based portal provided by OneGeology itself and then cover other commonly available clients.

.. todo::

   Should we expand the above WMS, WFS and WCS introductions to say generically what you could do with each in a general client before treating the specific clients? Then for each client we say: CSW yes/no -> how, WMS yes/no -> how, WFS yes/no -> how, WCS yes/no -> how. Having covered standard things like "you need the service URL" we just say where you put it, and for GetFeatureInfo how you do it in particular client etc.

.. toctree::
   :maxdepth: 1

   portal
   qgis
   esri

The documentation for the following clients has not been updated for several years so may not be up-to-date.

* `Using NASA World Wind </howto/1_4_4.html>`_
* `Using Google Earth </howto/1_4_6.html>`_
* `Using Gaia </howto/1_4_2.html>`_
* `Using Dapple </howto/1_4_5.html>`_
* `Using MapInfo </howto/1_4_8.html>`_
* `Using uDig </howto/1_4_9.html>`_

.. todo::

   NASA World Wind: Check software updates (HTTP/Central/.NET version doesn't appear to have been updated, 1.4 is still latest) Java SDK version is being updated (https://github.com/NASAWorldWind/WorldWindJava/releases/), but not sure if this is something you can just install and run, rather than  use to build something. Current content http://onegeology.org/howto/1_4_4.html
   Google Earth: Check software updates and if issues still exist. Also check if same affects World Wind. Current content at http://onegeology.org/howto/1_4_6.html
   Gaia: Looks like same version as before but links changed? (http://www.thecarbonproject.com/Products/Gaia), now version 3.4.2.  Also supports version 1.1.0 WFS so perhaps worth documenting? Current content at http://onegeology.org/howto/1_4_2.html
   Dapple: This is still available (https://download.cnet.com/Dapple/3000-2379_4-75841105.html), might be worth keeping as is GeoSoft, and BGS is partnering with GeoSoft on ODA work.  Version is still the same, and still works as documented.  Only issue is on install, also needed to add DirectX End-User Runtime (https://www.microsoft.com/en-gb/download/details.aspx?id=35). Current content at http://onegeology.org/howto/1_4_5.html
   MapInfo: Can anyone check whether this is up-to-date? Current content at http://onegeology.org/howto/1_4_8.html
   uDig: Current content at http://onegeology.org/howto/1_4_9.html is pretty minimal. Is there any point maintaining a specific page?


* `Using QGIS <https://github.com/OneGeology/OneGeology_Docs/blob/master/PORTAL.rst#qgis>`_
* Using ESRI

  * `Using ArcMap <https://github.com/OneGeology/OneGeology_Docs/blob/master/PORTAL.rst#ArcMap>`_
  * `Using ArcPRO <https://github.com/OneGeology/OneGeology_Docs/blob/master/PORTAL.rst#ArcPRO>`_
  
QGIS
^^^^^^^^^^^^

See: https://docs.qgis.org/testing/en/docs/user_manual/working_with_ogc/ogc_client_support.html
  
ArcMap
^^^^^^^^^^^^
  
See: http://desktop.arcgis.com/en/arcmap/latest/map/web-maps-and-services/about-using-ogc-service-layers.htm
  
ArcPRO
^^^^^^^^^^^^
  
See: https://pro.arcgis.com/en/pro-app/help/data/services/ogc-services.htm
