
Using NASA World Wind
----------------------------
.. todo::

   NASA World Wind: Check software updates (HTTP/Central/.NET version doesn't appear to have been updated, 1.4 is still latest) Java SDK version is being updated (https://github.com/NASAWorldWind/WorldWindJava/releases/), but not sure if this is something you can just install and run, rather than  use to build something. Current content http://onegeology.org/howto/1_4_4.html
   
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

