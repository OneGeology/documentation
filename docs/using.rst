
Using OneGeology Data
======================

Data displayed on the OneGeology portal is able to be accessed via other platforms such as QGIS and ArcMap. The following pages show how you may access services using these OGC standards (including those not part of OneGeology) in a number of popular desktop software clients and web based browser applications. We concentrate first on the web based portal provided by OneGeology itself and then cover other commonly available clients.

.. todo::

   Should we expand the above WMS, WFS and WCS introductions to say generically what you could do with each in a general client before treating the specific clients? Then for each client we say: CSW yes/no -> how, WMS yes/no -> how, WFS yes/no -> how, WCS yes/no -> how. Having covered standard things like "you need the service URL" we just say where you put it, and for GetFeatureInfo how you do it in particular client etc.

.. todo::

   NASA World Wind: Check software updates (HTTP/Central/.NET version doesn't appear to have been updated, 1.4 is still latest) Java SDK version is being updated (https://github.com/NASAWorldWind/WorldWindJava/releases/), but not sure if this is something you can just install and run, rather than  use to build something. Current content http://onegeology.org/howto/1_4_4.html
   Google Earth: Check software updates and if issues still exist. Also check if same affects World Wind. Current content at http://onegeology.org/howto/1_4_6.html
   Gaia: Looks like same version as before but links changed? (http://www.thecarbonproject.com/Products/Gaia), now version 3.4.2.  Also supports version 1.1.0 WFS so perhaps worth documenting? Current content at http://onegeology.org/howto/1_4_2.html
   Dapple: This is still available (https://download.cnet.com/Dapple/3000-2379_4-75841105.html), might be worth keeping as is GeoSoft, and BGS is partnering with GeoSoft on ODA work.  Version is still the same, and still works as documented.  Only issue is on install, also needed to add DirectX End-User Runtime (https://www.microsoft.com/en-gb/download/details.aspx?id=35). Current content at http://onegeology.org/howto/1_4_5.html
   MapInfo: Can anyone check whether this is up-to-date? Current content at http://onegeology.org/howto/1_4_8.html
   uDig: Current content at http://onegeology.org/howto/1_4_9.html is pretty minimal. Is there any point maintaining a specific page?


* `Using QGIS`_
* `Using ESRI`_

  * `Using ArcCatalog`_
  * `Using ArcMap`_
  * `Using ArcPRO`_

  The documentation for the following clients has not been updated for several years so may not be up-to-date.

  * `Using NASA World Wind`_
  * `Using Google Earth <http://www.onegeology.org/howto/1_4_6.html>`_
  * `Using Gaia`_
  * `Using Dapple <http://www.onegeology.org/howto/1_4_5.html>`_
  * `Using MapInfo <http://www.onegeology.org/howto/1_4_8.html>`_
  * `Using uDig`_


Using QGIS
------------

.. todo::

   * Update screenshots to version 3 when available
   * Metasearch CSW plugin

Quantum GIS (QGIS) is a user friendly Open Source Geographic Information System (GIS) licensed under the `GNU General Public License <http://www.gnu.org/copyleft/gpl.html>`_ (http://www.gnu.org/copyleft/gpl.html). QGIS is an official project of the `Open Source Geospatial Foundation (OSGeo) <http://www.osgeo.org/>`_ (http://www.osgeo.org/). It runs on Linux, Unix, Mac OSX, and Windows and supports numerous vector, raster, and database formats and functionalities.

The current stable version of QGIS (QGIS 2.18) is available for download from https://www.qgis.org/en/site/forusers/download.html

Quantum GIS (QGIS) supports WMS versions 1.3.0 (and lower) with GetCapabilities, GetMap, GetFeatureInfo, GetLegendGraphic, layer transparency, and provides a metadata browser for the service.


Using QGIS to view WMS
^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/qgis_addWMS.png
   :alt: QGIS menu option for adding a WMS

   Figure 1 - QGIS menu option for adding a WMS

.. |wmsBtn| image:: images/qgis_btnWMS.png

To add a WMS layer from the menu, choose *Layer > Add Layer > Add WMS/WMTS Layer*. Alternatively, click on the |wmsBtn| button on the *Manage Layers Toolbar*. In the *Add Layer(s) from a WM(T)S Server* pop-up box click the *New* button, and then in the *Create a new WMS connection* pop-up add a name for your service, such as OneGeology shapefile exemplar (fcgi) using MapServer 6 and the service URL (with no parameters) as below and then click 'OK'.

We recommend using no parameters (above), so that you get the latest version of the WMS service. If you are testing your own system and you want to test a particular version you can add that version as a parameter; such as:

::

	http://ogc.bgs.ac.uk/fcgi-bin/exemplars/BGS_Bedrock_and_Superficial_Geology/wms?version=1.1.1&

.. figure:: images/qgis_addNewWMSService.png
   :alt: Adding a new WMS Service

   Figure 2 - Adding a new WMS Service

As with most other clients at this stage all you’ve done is add the WMS service to the list of available WMS services. To add a layer you need to select the WMS service from the *Add Layer(s) from a WM(T)S Server* pop-up box, and click ‘Connect’. This will show you a list of the layers being served from the WMS service.

If you are behind a firewall, you may also need to add information about your proxy server. This is done through the *Settings > Options* menu in the *Network* section.

Click on the layer you want and click ‘Add’, this will add that layer in the background, but keep the pop-up window to allow you to add another layer. Press *Ctrl* and click again on a selected layer to deselect it.

.. figure:: images/qgis_selectWMSLayers.png
   :alt: Selecting layers

   Figure 3 - Selecting layers

Note, if you select several layers (using *Ctrl* or *Shift* keys) and then click Add, QGIS will show those selected WMS layers as a single ‘derived’ layer in the GIS. In this example we have joined the bedrock lithostratigraphy and the superficial lithostratigraphy geology layers to create a single layer which we name ‘Lithostratigraphy’. Note you can rename any WMS layer to one that suits your needs, change the layer CRS, and change the layer image encoding (the default is png).

.. figure:: images/qgis_createDerivedWMSLayers.png
   :alt: Creating derived layers

   Figure 4 - Creating derived layers

If the selected layer is set to be queryable in the WMS service, you may use the identify tool to retrieve information on any feature in the map.

.. figure:: images/qgis_WMSIdentify.png
   :alt: WMS feature identification

   Figure 5 - WMS feature identification

You may right click on any layer in the layer list and go to *Properties* to get the metadata for that layer and the serivce that serves it.

.. figure:: images/qgis_WMSMetadataProperties.png
   :alt: Layer properties metadata

   Figure 6 - Layer properties metadata

.. _use_qgis_simple_wfs:

Using QGIS to access simple feature WFS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. |wfsBtn| image:: images/qgis_btnWFS.png

To add a WFS layer you need to go through a similar process as you do to add a WMS layer, that is, you must first add the WFS service by clicking on the |wfsBtn| tool on the *Manage Layers Toolbar*, then connect to the service, then select the layer you want to add. Even if the WFS service URL is the same as a WMS connection you already have listed you will need to add the WFS service URL.

.. figure:: images/qgis_addNewWFSService.png
   :alt: Adding a new WFS service

   Figure 7 - Adding a new WFS service

When you add a WFS layer you can choose to request all the features of that layer, or you may choose to request only those features that overlap the current extent, depending on whether the option *Only request features overlapping the view extent* is enabled. This will allow you to download and add to your map only the features relevant to your area of interest. However, if you change your extent by panning or zooming the map, new features will be fetched for your new view extent.


.. figure:: images/qgis_addWFSLayer.png
   :alt: Adding a new WFS service

   Figure 7 - Adding a new WFS service

Below we have zoomed to the full extent of the WFS layer, therefore all features for that layer have been returned. Individual feature attributes can be inspected by using the *Identify* tool or by opening the *Attribute Table*.

.. figure:: images/qgis_WFSIdentify.PNG
   :alt: Identifying WFS features

   Figure 8 - Identifying WFS features

When we view a WFS service, it should be noted that we actually download a representation of the data itself, not an image. We can therefore save a copy of that data for re-use elsewhere. Simple right click on the layer and go to *Save As*. Exporting formats include **ESRI Shapefile** and **GeoJSON**. Exported data can be limited to selected features or to features in the current map extent.

.. figure:: images/qgis_wfsExport.PNG
   :alt: Exporting WFS layer

   Figure 9 - Exporting WFS layer

Using QGIS to view WCS
^^^^^^^^^^^^^^^^^^^^^^^

.. |wcsBtn| image:: images/qgis_btnWCS.png

Adding a WCS layer is again a similar process than adding a WMS layer:

* Add the WCS service by clicking on the |wcsBtn| button on the *Manage Layers Toolbar*
* Connect to the service
* Select the layer you want to add

.. figure:: images/qgis_addNewWCSService.png
   :alt: Creating a connection to a WCS service

   Figure 10 - Creating a connection to a WCS service

Only one layer can be selected at a time. After selecting it, and choosing your favourite format, click 'Add'. Repeat this process if you wand to add more layers and then click 'Close'.

.. figure:: images/qgis_addNewWCSService.png
   :alt: Adding a WCS layer

   Figure 11 - Adding a WCS layer

Your layer(s) should now be displaying on the map.

.. figure:: images/qgis_displayWcsLayer.png
   :alt: Displaying a WCS layer

   Figure 12 - Displaying a WCS layer

WCS layers can be exported as rasters. To do so, right click on the layer and go to *Save As*. You can choose to crop the exported raster by specifying an extent or getting the current map extent.

.. figure:: images/qgis_exportWCSLayer.png
   :alt: Exporting a WCS layer

   Figure 13 - Exporting a WCS layer

See: https://docs.qgis.org/testing/en/docs/user_manual/working_with_ogc/ogc_client_support.html

Using ESRI
------------

The ArcGIS software package comes with several applications. Here we'll briefly show how to use **ArcCatalog** to setup OGC service connections and how to use **ArcMap** to deal with OGC layers.

The following notes are based on ESRI ArcGIS server version 10.5 (SP1).

Using ArcCatalog
^^^^^^^^^^^^^^^^

WMS Service Connection
""""""""""""""""""""""

To add a WMS service to your list of available WMS services, on the *Catalog Tree* window, you use the *GIS servers > Add WMS Server* option, and then add the Service URL (without parameters). You may select to use the default service version (which would normally be the highest version) or you may force a specified version depending on your needs.

.. figure:: images/esri_catalog_addingWms.png
   :alt: Adding a WMS service to the list of available services in ArcCatalog

   Figure 1 - Adding a WMS service to the list of available services in ArcCatalog

You will be able to preview the service layers in ArcCatalog; however, if the map service is scale layered (only visible at certain scales), you won't be able to see the map until you have zoomed in to an appropriate scale. Similarly, if the layers are queryable, you will be able to use the information tool to retrieve feature information.

You will not be able to view the legend graphics in ArcCatalog.

.. figure:: images/esri_catalog_reviewingWms.png
   :alt: Reviewing available WMS services in ArcCatalog

   Figure 2 - Reviewing available WMS services in ArcCatalog

The above screen-shot shows a number of WMS (GIS Servers) listed in the left hand menu. These are services that have previously been added to ArcCatalog. To retrieve layer name information, preview, and do GetFeatureInfo requests, you must first double-click on the layer name. This will re-query the service and retrieve only active layers at the time of your query.

WFS Service Connection
""""""""""""""""""""""

This functionality is only available with a `Data Interoperability <http://desktop.arcgis.com/en/arcmap/latest/extensions/data-interoperability/what-is-the-data-interoperability-extension-.htm>`_ license. A free alternative to get hold of the data in the WFS would be downloading the features in the WFS using QGIS and then exporting them as an ESRI Shapefile (see section *Using QGIS to view WFS*).

If you do have a Data Interoperability license, on the *Catalog Tree* window go to *Interoperability Connections > Add Interoperability Connection* to open the *Interoperability Connection* dialog. In the dialog, select WFS as format and enter the WFS url in the *Dataset* option.

.. figure:: images/esri_catalog_connectingWfs.png
   :alt: Connecting to a WFS service in ArcCatalog

   Figure 3 - Connecting to a WFS service in ArcCatalog

Before clicking *OK*, go to *Parameters* and select the *Feature Types* to download. *Feature Types* aren't selected by default, so you'll need to do this step if you want to see any layer in your WFS connection. The *WFS Parameters* dialog also allows you to set many other options, as shown in the picture below. Once you're happy with your settings click *OK* to close this dialog and *OK* again to create the WFS connection.

.. figure:: images/esri_catalog_parametersWfs.png
   :alt: WFS Parameters dialog

   Figure 4 - WFS Parameters dialog

When you create a connection, you might see that multiple versions of your layer have been created in different geometries. Refresh your connection (right click on layer and go to *Refresh*) and only the relevant geometry will be kept.

.. figure:: images/esri_catalog_allGeometriesWfs.png
   :alt: WFS connection showing all available geometries

   Figure 5 - WFS connection showing all available geometries

You can preview and identify individual features in a layer from a WFS connection by selecting the layer and going to the *Preview* tab.

.. figure:: images/esri_catalog_reviewingWfs.png
   :alt: Previewing and identifying a WFS layer

   Figure 6 - Previewing and identifying a WFS layer

WCS Service Connection
""""""""""""""""""""""

Adding a WCS service to your list of available WCS services is identical than doing it for a WMS service: on the *Catalog Tree* window go to *GIS servers > Add WMS Server* option and then add the Service URL (without parameters). You may select to use the default service version (which would normally be the highest version) or you may force a specified version depending on your needs.

.. figure:: images/esri_catalog_addingWcs.png
   :alt: Adding a WCS service to the list of available services in ArcCatalog

   Figure 7 - Adding a WCS service to the list of available services in ArcCatalog

Your WCS will now be available within the list of GIS Servers.

.. figure:: images/esri_catalog_reviewingWcs.png
   :alt: Previewing WCS layers in ArcCatalog

   Figure 7 - Previewing WCS layers in ArcCatalog

Using ArcMap
^^^^^^^^^^^^

.. |addDataBtn| image:: images/esri_map_addDataBtn.PNG

.. |addCatalogBtn| image:: images/esri_map_catalogBtn.PNG

In ArcMap you can use the *Add Data* button (|addDataBtn|) to add an WMS, WFS or WCS layer or simply drag-and-drop a layer from the *Catalog* window. This window is the equivalent to the *Catalog Tree* window in ArcCatalog and can be enabled by pressing |addCatalogBtn|. OGC service connections are usually created in ArcCatalog before the data is used in ArcMap; however, the connections can also be set at the time of adding the data.

.. figure:: images/esri_map_addingData.PNG
   :alt: Adding data to ArcMap

   Figure 8 - Adding data to ArcMap

WMS Layers
"""""""""""

WMS layers in ArcMap behave differently than other ESRI native layers. For instance, they are arranged in hierarchical entries which can't be rearranged. This tipically includes

::

	- Service name
	    - Group layer
	        - Actual layers

However there can be multiple or even nested group layers. Also, the only way to get information about feature attributes in a WMS layer is through the *Identify* tool, as shown in the previous section.

If the map is scale layered (layers are shown greyed out) you may use the *Zoom to Make Visible* option. This zooms into the layer to the scale cited in the layer below which the layer will be visible, that is you need to zoom in a little bit further using the zoom tool to be able to view the map.

If you are going to provide scale layered data, it is suggested that you also provide an outline coverage map viewable at all scales to allow users to pan around the area of interest, without needing to zoom in first.

.. figure:: images/esri_map_zoomVisibleWms.PNG
   :alt: Accessing the Zoom to make visible tool in ArcMap for scale layered data

   Figure 9 - Accessing the *Zoom to make visible* tool in ArcMap for scale layered data

There are two ways you can view the legend for any layer. First off you can use the ‘Add WMS legend to map’ option, which will overlay a large copy of the legend on top of your map window. You will probably need to move or resize this legend graphic in order to see your map.

.. figure:: images/esri_map_addLegendWms.PNG
   :alt: Adding a WMS legend to a map in ArcMap

   Figure 10 - Adding a WMS legend to a map in ArcMap

The legend will scale to the initial scale of your map and will not redraw (rescale) if you change the scale of your map view.

.. figure:: images/esri_map_lgndDisplayWms.PNG
   :alt: WMS legend displayed on the map layer in ArcMap

   Figure 11 - WMS legend displayed on the map layer in ArcMap

Alternatively, you may use the layer properties dialogue to save a copy of the legend. To do so use the *Legend URL* or right click on the legend image and go to *Save As*. If your layer presents multiple styles, they will be available in the drop down menu of this dialog.

.. figure:: images/esri_map_lgndSaveWms.PNG
   :alt: Saving a WMS legend graphic to file in ArcM

   Figure 12 - Saving a WMS legend graphic to file in ArcMap

For more information about WMS layers go to `Using WMS service layers <http://desktop.arcgis.com/en/arcmap/latest/map/web-maps-and-services/using-wms-service-layers.htm>`_

WFS Layers
"""""""""""

WFS layers behave in ArcMap like any other type of vector layer. You can, for instance, identify individual features, see feature attributes in the *Attribute Table*, join the layer to other dataset or apply symbology.

.. figure:: images/esri_map_wfs.PNG
   :alt: WFS layer displayed in ArcMap showing attributres and custom symbology

   Figure 13 - WFS layer displayed in ArcMap showing attributres and custom symbology

To export features from a WFS layer to ESRI proprietary formats, such as a **Shapefile**, right click on the layer and go to *Data > Export Data*. Note that you can export subsets of the layer by choosing only selected features or features within the view extent.

.. figure:: images/esri_map_exportProprietaryWfs.PNG
   :alt: Exporting a WFS layer to a proprietary format in ArcMap

   Figure 14 - Exporting a WFS layer to a proprietary format in ArcMap

To export features to an open format, like **GeoJSON**, you'll need to use the *Quick Export* tool, only available with the *Data Interoperability* license. If features are selected, this tool will only export selected features. You can also return feaures from a given extent by going to the tool's environments and defining an extent in the *Processing Extent* section.

.. figure:: images/esri_map_exportOpenWfs.PNG
   :alt: Exporting a WFS layer to an open format in ArcMap

   Figure 15 - Exporting a WFS layer to an open format in ArcMap

WCS Layers
"""""""""""

WCS layers operate in a similar way to other raster data but with a few less properties. For more information on available properties go to `Adding a WCS service to ArcMap <http://desktop.arcgis.com/en/arcmap/latest/map/web-maps-and-services/adding-a-wcs-service-to-arcmap.htm>`_.

.. figure:: images/esri_map_displayWcs.PNG
   :alt: Displaying WCS data in ArcMap

   Figure 16 - Displaying WCS data in ArcMap

To export a WCS layer, right click on it and go to *Data > Export Data*. The *Export WCS Data* dialog will allow you to set the extent, format or cell size of the exported data.

.. figure:: images/esri_map_exportWcs.png
   :alt: Displaying WCS data in ArcMap

   Figure 17 - Displaying WCS data in ArcMap

See: http://desktop.arcgis.com/en/arcmap/latest/map/web-maps-and-services/about-using-ogc-service-layers.htm

Using ArcPRO
^^^^^^^^^^^^

See: https://pro.arcgis.com/en/pro-app/help/data/services/ogc-services.htm

Using uDig
-----------

- Open uDig. The software can be obtained at: http://udig.refractions.net/
- Create a new map, or open an existing map to which you would like to add the web service
- On the upper menu bar, click Layer > Add...
- In the window that appears, click Web Map Server or Web Feature Server, as appropriate; click Next
- Paste the service endpoint in the URL field; click Next
- In the Resource Selection window that appears, select all layers you wish to add. When you are done, click Finish

Using Gaia
----------

Gaia: http://www.thecarbonproject.com/gaia.php

Gaia is a free desktop client provided by &#8216;The Carbon Project&#8217;; based on CarbonTools PRO; open-geospatial development tool-kit, and can access an array of geospatial sources such as the Open Geospatial Consortium (OGC) Web Mapping Service (WMS), Web Map Tile Service (WMTS), Web Coverage Service (WCS), and Web Feature Service (WFS). We note that the latest version is now 3.4.1 which adds support for WFS-T; but everything in relation to WMS mentioned below still stands.

Gaia 3.4 fully supports all WMS 1.1.1 requests and, GetCapabilities and GetMap requests for WMS 1.3.0.  It provides partial support for version 1.3.0 GetFeatureInfo requests.

Gaia is available both for Windows and Linux (using mono); here we describe using the Windows version.

To add a WMS to Gaia, use the Tools > Add Layer menu option

.. figure:: images/gaia1.jpg
   :alt: Default view of Gaia 3.4, showing menu options to add WMS services

   Default view of Gaia 3.4, showing menu options to add WMS services

.. figure:: images/gaia2.jpg
  :alt: Adding a new WMS service to the list of available services

  Adding a new WMS service to the list of available services


Select the layer icon (red plus sign)

Give the service a name, and add the service URL (with or without request parameters), select the service type (wms), and version (by default Gaia selects version 1.1.1), and click OK.

This adds the service to the list of available services but doesn't add it to your map.  To add map layers from the service you need to continue.

The service layers will now be shown in the middle window, and if the service is not scale layered, a map will be shown in the preview window.  Highlighting an individual layer from the service (click on layer name) will give a preview of that layer, to help you determine whether the WMS provides the information you require.  You may further investigate the layer metadata, by clicking on the &#8216;Open Capabilities Analyzer&#8217; button.  When you are happy you have the correct map layer, click the 'Add Layer'; button.

.. figure:: images/gaia3.jpg
  :alt: Using the Capabilities Analyzer to review WMS metadata for a map layer

  Using the Capabilities Analyzer to review WMS metadata for a map layer

Note, you can force a change in the default behaviour of the service using the Parameters form options, for example, here we are requesting the map to be served as a 24-bit png.</p>

Like the OneGeology Portal, Gaia supports all standard GIS tools (Zoom in, Zoom out, Pan, Move back and forward through previous map extents, Retrieve Feature Information).</p>

.. figure:: images/gaia4.jpg
  :alt: GetFeatureInfo request response in Gaia

  GetFeatureInfo request response in Gaia

Double-clicking on the layer in the left hand menu, will bring up the map layer properties window, which allows you to change the layer opacity (transparency), and other parameters as required.  It will also reveal the GetMap request (query) that is being used to display that map layer, at that time.  You may copy and paste that request into any browser to show that map layer.</p>

A GetMap request for a portion of the BGS bedrock lithostratigraphical data map layer. You can cut and paste this URL into any web browser and get a png format map image.

http://ogc.bgs.ac.uk/cgi-bin/BGS_Bedrock_and_Superficial_Geology/ows?REQUEST=GetMap&amp;SERVICE=WMS&amp;VERSION=1.3.0&amp;LAYERS=GBR_BGS_625k_BLS&amp;STYLES=default&amp;FORMAT=image/png;%20mode=24bit&amp;BGCOLOR=0xFFFFFF&amp;TRANSPARENT=TRUE&amp;CRS=EPSG:4326&amp;BBOX=54.0957778123079,-3.54949452254466,54.9267913615873,-2.51587849637481&amp;WIDTH=602&amp;HEIGHT=484&amp

The above parameters are specific to the version of the WMS (in this example &#8216;VERSION=1.3.0&#8217;), changing the version number alone, to review how the data might display for that version, will result in an error.</p>

Note, if you are using Gaia at work (behind a corporate firewall) or otherwise need to go through a proxy to access the web, AND don&#8217;t get any map service showing, you should check that Gaia has picked up your proxy settings; see Tools > Configuration > Proxy Settings.</p>

Using NASA World Wind
----------------------------

World Wind: http://worldwindcentral.com/wiki/Main_Page

NASA World Wind is a free client for viewing data produced by NASA.  It has two versions; a Java based version aimed at software developers for incorporating into their own software (for example Dapple) and a .NET version aimed at standard users.

Here we show you how you can use the .NET version to add and view any WMS service.

Note the .NET version of World Wind is quite picky about the graphics driver you have installed and may crash if your card is not supported, check the World Wind wiki page (above) for a list of supported graphics cards.

To add a WMS to use: Tools > Import WMS url to layer

.. figure:: images/addWMStoWorldWind.jpg
  :alt: Adding a WMS service to  the list of available WMS services in the .NET version  of NASA World Wind

  Adding a WMS service to  the list of available WMS services in the .NET version  of NASA World Wind

In the WMS Importer pop-up add the service URL into the text box and click the &#8216;Get WMS Tree&#8217; button.  You should give the output a unique name (by default it will be called wms.xml) and then click the &#8216;Save as XML&#8217; button.</p>

As with other software, this doesn&#8217;t display the WMS layer, but just adds it to the list of available layers, which are accessible through the Layer Manager.  You must select the layers in Layer Manager and then zoom to your area of interest.</p>

.. figure:: images/addWMStoWorldWind.jpg
  :alt: Adding available layers to the globe in .NET NASA World Wind

  Adding available layers to the globe in .NET NASA World Wind

Using Dapple
-------------

Dapple: http://dapple.geosoft.com/

The latest release of Dapple (v.2.1.4) supports WMS version 1.3.0.  You must use this version (or higher when they become available) if you want to view any WMS service that supports version 1.3.0. because of a bug in earlier releases.

Note, Dapple doesn't yet support GetFeatureInfo request, so you will not be able to get any information about a map at a location, by clicking on that map.

Dapple is a data explorer designed to provide an open and optimal environment for visualizing, presenting, and sharing massive quantities of geoscientific data on desktop computers.  Dapple lets you browse, discover, and display graphically rich data from global and corporate spatial servers. The Dapple project is an open-source activity sponsored by Geosoft and derived from the NASA World Wind (http://worldwind.arc.nasa.gov/) open source project.

As with other GIS software, the first step to viewing a WMS map layer in Dapple is to add the WMS service to the list of available WMS services.  To do this, select the "Servers" menu option and then "Add WMS server"

.. figure:: images/dapple1.jpg
  :alt: Adding a WMS server to the list of available WMS services in Dapple

  Adding a WMS server to the list of available WMS services in Dapple

In the pop-up window, add the GetCapabilities URL of the service without any parameters; you can supply the "service = WMS" and "request=GetCapabilitie" parameters if you want, but if you supply the version parameter it will be ignored.

For example:

http://ogc.bgs.ac.uk/cgi-bin/BGS_Bedrock_and_Superficial_Geology/wms

The intention is to always use the highest WMS version supported by the service, but the downside is that you will not be able to use Dapple to test all your service outputs.</p>

Dapple will add the service to the list of WMS servers and initially show just this new service and the data layers it can serve. If you left click on any of the layers in the Servers window, you will see the metadata associated with that layer in the Metadata window (beneath the map window).</p>

There are several ways you can add a map layer to your map view: you can use the Tools menu option, you can left click-down and drag to the Data Layers window, or you can right-click on a highlighted layer and add the layer.  In each case the result is the same the layer is added to the data layers view window, and the map is drawn.  Remember, if you drag the layer, you will need to add it to the top of the list, or you might not see it.</p>

.. figure:: images/dapple2.jpg
  :alt: Viewing map and metadata in Dapple

  Viewing map and metadata in Dapple

To view the legend of the active map layer you may click the link in the Metadata section, or you may right-click on any layer, either in the Servers view window or the Data Layers view window, and the legend will open either in browser window, or another application that is enabled to view the legend image type from a web location.</p>

.. figure:: images/dapple3.jpg
  :alt: Using the metadata legend link to view the legend information

  Using the metadata legend link to view the legend information

Using Google Earth
-------------------

Google Earth: http://earth.google.co.uk/

Requires a PC with minimum 256MB memory and 3D-capable graphics card with 16MB of VRAM.

A simple way of viewing data in Google Earth is to use a KML file exported from the OneGeology Portal. You may also add a WMS directly, using the Add menu option and then ‘Image Overlay’.

.. figure:: images/googleEarth1.jpg
  :alt: Using the image overlay option in Google Earth to add a WMS

  Using the image overlay option in Google Earth to add a WMS

Give your service a name then select the ‘Refresh’ tab, and click on the ‘WMS parameters button. In the dialogue box, add the Service URL without parameters.

For example:

http://maps.bgs.ac.uk/ArcGIS/services/BGS_Detailed_Geology/MapServer/WMSServer?

Then use the Add button to add one or more of the service layers to your image overlay (each map layer added to your image overlay will be available to be selected/turned on or off later).

The URL field is populated automatically (but note that it doesn’t add the ‘styles’ parameter, and this may cause the map layer to not display correctly (See `Google Earth Issues_`)

.. figure:: images/googleEarth2.jpg
  :alt: Selecting WMS layers in Google Earth

  Selecting WMS layers in Google Earth

When you zoom into your area of interest Google Earth will tile your map.

.. figure:: images/googleEarth3.jpg
  :alt: WMS tiling in Google Earth

  WMS tiling in Google Earth

Google Earth Issues
^^^^^^^^^^^^^^^^^^^^

Problems displaying the map layer
""""""""""""""""""""""""""""""""""

When adding a WMS layer to Google Earth, you may get a Big Red Cross instead of the map layer you were expecting. This indicates there is an error with that layer. The error may lie either with the GetMap parameters sent by Google Earth to the WMS server, or in the WMS response.

When adding any WMS using the method described above, we have noted that the parameters that Google Earth automatically populates into its form (the Edit Image Overlay Link) are missing the required ‘styles’ parameter. MapServer WMS services do not seem to be affected by this omission, that is, they will serve a map using the default style, but we have noticed that ArcGIS WMS services cannot handle this error, and you will need to add the correct style value to your link. You may look at the GetCapabilities response to get the style or styles you want to be used, or you should just be able to specify a null value, and get the default style.

.. figure:: images/googleEarth4.jpg
  :alt: Red cross showing a layer error in Google Earth

  Red cross showing a layer error in Google Earth

For example to view the BGS 50k Geology layer in Google Earth you need to use this link:

http://maps.bgs.ac.uk/ArcGIS/services/BGS_Detailed_Geology/MapServer/WMSServer?VERSION=1.1.1&REQUEST=GetMap&SRS=EPSG:4326&WIDTH=512&HEIGHT=512&LAYERS=1&TRANSPARENT=TRUE&FORMAT=image/gif&styles=

Problems displaying a map layer that spans the globe
"""""""""""""""""""""""""""""""""""""""""""""""""""""
Google Earth has a problem showing the full contents of a map layer that spans the whole globe. Specifically Google Earth seems to be unable to show coverage from such data layers at the poles and around the antimeridian (the 180th degree meridian). For example we are unable to get a map to display the whole of Russia.

The problem is illustrated below using the WORLD CGMW 1:25M Geologic Units layer. (http://mapsone.brgm.fr/1GmapserverFR/wms?map=/applications/mapserver/map%20files/Lithology_FR.map&REQUEST=GetMap&SERVICE=WMS&VERSION=1.1.1&LAYERS=WORLD_CGMW_25M_GeologicUnits&STYLES=default&FORMAT=image/png&BGCOLOR=0xFFFFFF&TRANSPARENT=TRUE&SRS=EPSG:4326&BBOX=-180,-137.242524916944,180,137.242524916944&WIDTH=602&HEIGHT=459)

There is currently no fix for this issue.

.. figure:: images/world-cgmwR.jpg
  :alt: GetMap response to the OneGeology WORLD CGMW 1:25M Geologic Units map layer showing a web map service with whole globe coverage

  GetMap response to the OneGeology WORLD CGMW 1:25M Geologic Units map layer showing a web map service with whole globe coverage

.. figure:: images/GE-hole-500.jpg
  :alt: The same OneGeology WORLD CGMW 1:25M Geologic Units map layer in Google Earth showing the display problem at the poles and the antimeridian

  The same OneGeology WORLD CGMW 1:25M Geologic Units map layer in Google Earth showing the display problem at the poles and the antimeridian

Using MapInfo Professional
--------------------------

MapInfo Professional allows you to view (GetMap) and query (GetFeatureInfo) a WMS service.  It currently doesn't support the display of legends (GetLegendGraphic)</p>

To add a WMS service to the list of available WMS services
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Select the File > Open Web Service > Open WMS menu option</p>

.. figure:: images/MIPopenWS.jpg
  :alt: Opening a Web Service in MapInfo Professional 11.5

  Opening a Web Service in MapInfo Professional 11.5

2. In the Open WMS Table dialog, select the Servers button at the top right</p>

.. figure:: images/MIPopenTabR.jpg
  :alt: Displaying existing WMS services

  Displaying existing WMS services

3. In the following WMS Servers List dialog, select the Add button at the top right of the dialog.</p>

4. From within the OneGeology Portal, copy the desired layers Service URL:</p>

.. figure:: images/MIPgetSRVurlr.jpg
  :alt: Getting the service URL from the OneGeology Portal

  Getting the service URL from the OneGeology Portal

5. Paste this Service URL into the Server URL field of the WMS Server Information dialog. The adjacent Test URL button can be used to validate this URL:</p>

.. figure:: images/MIPpasteSVurlr.jpg
  :alt: Verifying a new WMS service

  Verifying a new WMS service

6. Press the Get Description button to auto-populate the Description from the server, or enter a name manually, then press OK.</p>

.. figure:: images/MIPgetDescR.jpg
  :alt: Adding a new WMS service

  Adding a new WMS service

7. The WMS server will now appear in the Servers List. Press OK to return to the Open WMS Table dialog.</p>

.. figure:: images/MIPserversR.jpg
  :alt: Selecting an existing WMS service

  Selecting an existing WMS service

To view WMS service layers
^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Select the File > Open Web Service > Open WMS menu option.
- In the Open WMS Table dialog:
  - Ensure the desired WMS Server is selected from the drop down list</li>
  - Move the required WMS layers to the right selection window</li>
  - Choose an output name and directory for the resulting MapInfo Professional TAB file</li>
- Press OK; the data will now be opened in MapInfo Professional</li>

.. figure:: images/MIPopenWMStabR.jpg
  :alt: Selecting WMS layers

  Selecting WMS layers

.. figure:: images/MIPshowWMSr.jpg
  :alt: Viewing the WMS data

  Viewing the WMS data


To query WMS service layer
^^^^^^^^^^^^^^^^^^^^^^^^^^^

After making a WMS layer selectable (as for example "CAN CGC 1:5M Roche en place" in the above figure), the Info tool can be used. Information will be returned only from layers that are queryable. Layer that are queryable are identified by an Information icon ("i")
