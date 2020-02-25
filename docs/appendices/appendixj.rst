=============================================================
How to create a Styled Layer Descriptor (SLD) using Arc2Earth
=============================================================

.. container::
   :name: outer_container

   .. container::
      :name: content

      .. container:: fullwidth

         .. rubric:: Appendix J: How to create a Styled Layer Descriptor
            (SLD) using Arc2Earth
            :name: appendix-j-how-to-create-a-styled-layer-descriptor-sld-using-arc2earth
            :class: technical_progress_side_menu

         Arc2Earth is a plugin for ArcGIS that is available in several
         different editions. The **Community** edition is free and
         provides access to the SLD generator. Arc2Earth is available at
         http://www.arc2earth.com/.

         #. Install the Arc2Earth plugin
         #. Open ArcMap
         #. Open the ArcMap project containing the layer or layers to
            export as SLDs
         #. Select the desired layer in the catalog tree
         #. In the Arc2Earth toolbar, click Export > Export Layer Style
            to SLD
         #. Navigate to the appropriate location
         #. Click **Export**

         After your SLD has been exported, open the .sld in any XML or
         text editor. Note that the Arc2Earth plug-in adds an outline
         (stroke) to polygon layers. If you are working with polygon
         layers, the stroke may need to be tailored or removed manually.
         Also, it may be necessary to customize the heading for your
         SLD, or change the schema location.

         **Note:** though .sld files, like any XML document, may be
         edited by a generic text editor, such as the **Notepad** or
         **Wordpad** text editors included with Windows operating
         systems, some text editors are better suited to working with
         XML documents than others. One example of a
         free-and-open-source text editor designed with XML support is
         `Notepad++ <http://notepad-plus-plus.org/>`__ (be sure to get
         the `XML tools
         plugin <http://sourceforge.net/projects/notepad-plus/forums/forum/482781/topic/3717096>`__).


.. |OneGeology logo| image:: appendixj/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
