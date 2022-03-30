
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
