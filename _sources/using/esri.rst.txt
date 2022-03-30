
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
