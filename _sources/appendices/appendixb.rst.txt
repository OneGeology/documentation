=========================================================
Creating MapServer CLASS definitions from ArcView legends
=========================================================

.. container::
   :name: outer_container

   .. container::
      :name: content

      .. container:: fullwidth

         .. rubric:: Appendix B: Creating MapServer CLASS definitions
            from ArcView legends
            :name: appendix-b-creating-mapserver-class-definitions-from-arcview-legends
            :class: technical_progress_side_menu

         The Gix Export Tool can help you create the CLASS sections of
         your map file from an ESRI ArcView 3.x .apr file. This tool
         converts ESRI ArcView 3.x (NOT ArcMap) projects to common open
         source alternatives including a MapServer map file. (Please
         note that this tool has only been used to convert simple
         symbology e.g. geology polygons symbolized by a solid colour
         according to its lithology value. Its ability to convert more
         complex symbology has not been tested.) Download the `Gix
         Export Tool <http://gix.sourceforge.net/>`__
         (http://gix.sourceforge.net/). Run the executable and follow
         the instructions to install the tool as an ArcView 3.x
         extension. Having installed the Gix Export Tool, create or open
         an ArcView project containing your symbolized data.

         | |ArcView map view showing symbolized data|
         | ArcView map view showing symbolized data

         | |Loading the Gix ArcView extension|
         | Loading the Gix ArcView extension

         Load the Gix Export Tool Extension (File — Extensions, tick
         required extension, click OK).

         | |Loading the Gix ArcView extension|
         | Loading the Gix ArcView extension

         Complete the following steps to convert your project to a
         MapServer map file.

         #. Select View — Export View.

            | |ArcView, Exporting your View|
            | ArcView, Exporting your View

         #. The first screen asks you to select your output file format
            — choose MapServer map file (.map) and click next.

            | |Gix export tool, selecting output format|
            | Gix export tool, selecting output format

         #. The next screen asks you to select a version (choose
            default) and output file. The output file generated will be
            a temporary file from which you will cut the CLASS
            components and paste them into the master map file you have
            been creating elsewhere. Select a location for your output
            file and click next.

            | |Gix export tool, selecting output file|
            | Gix export tool, selecting output file

         #. The next screen asks for details of the main and reference
            map. You won’t use these sections so accept the defaults and
            click next.

            | |Gix export tool, details for the main, and reference
              maps|
            | Gix export tool, details for the main, and reference maps

         #. The next screen asks for details of the legend. Again, you
            won’t use these sections so accept the defaults and click
            next.

            | |Gix export tool, details for the legend|
            | Gix export tool, details for the legend

         #. The next screen asks for details of the scale bar. Again,
            you won’t use these sections so accept the defaults and
            click next.

            | |Gix export tool, details for the scale bar|
            | Gix export tool, details for the scale bar

         #. The next screen asks for details of the OGC metadata. Again,
            you won’t use these sections so accept the defaults and
            click next.

            | |Gix export tool, OGC metadata details|
            | Gix export tool, OGC metadata details

         #. The next screen asks for details of final options. Again,
            you won’t use these sections so accept the defaults.

            | |Gix export tool, character set encoding and symbology
              options|
            | Gix export tool, character set encoding and symbology
              options

         #. Click Finish to create your map file.

         Open up the map file you created in a text editor and complete
         the following steps for each layer in your map file:

         #. Navigate to the line beginning CLASSITEM
         #. Highlight from here down to the END #CLASS line associated
            with that layer
         #. Copy and paste the selected lines to an empty text file
         #. Delete all TEMPLATE ’ template.html’ lines (one for each
            class)
         #. Paste the remaining content into your master map file within
            the section for the layer you are dealing with. A good
            position is after the END line which closes the METADATA for
            that layer.

         If your symbolization in ArcView had polygon boundaries you
         will need to remove these from the MapServer symbolization.
         This may be easier to do by deleting all the ‘OUTLINECOLOR’
         lines from the generated map file than by altering your ArcView
         symbolization.



.. |OneGeology logo| image:: appendixb/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
.. |ArcView map view showing symbolized data| image:: /images/wmsCookbook/ArcView1.jpg
   :width: 600px
   :height: 466px
.. |Loading the Gix ArcView extension| image:: /images/wmsCookbook/ArcView2.jpg
   :width: 600px
   :height: 490px
.. |Loading the Gix ArcView extension| image:: /images/wmsCookbook/ArcView3.jpg
   :width: 600px
   :height: 501px
.. |ArcView, Exporting your View| image:: /images/wmsCookbook/ArcView4.jpg
   :width: 600px
   :height: 543px
.. |Gix export tool, selecting output format| image:: /images/wmsCookbook/ArcView5.jpg
   :height: 242px
.. |Gix export tool, selecting output file| image:: /images/wmsCookbook/ArcView6.jpg
   :height: 242px
.. |Gix export tool, details for the main, and reference maps| image:: /images/wmsCookbook/ArcView7.jpg
   :height: 242px
.. |Gix export tool, details for the legend| image:: /images/wmsCookbook/ArcView8.jpg
   :height: 242px
.. |Gix export tool, details for the scale bar| image:: /images/wmsCookbook/ArcView9.jpg
   :height: 242px
.. |Gix export tool, OGC metadata details| image:: /images/wmsCookbook/ArcView10.jpg
   :height: 242px
.. |Gix export tool, character set encoding and symbology options| image:: /images/wmsCookbook/ArcView11.jpg
   :height: 242px
