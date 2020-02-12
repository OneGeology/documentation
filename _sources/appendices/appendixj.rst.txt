===========================================================================
How to create a Styled Layer Descriptor (SLD) using Arc2Earth \| OneGeology
===========================================================================

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
      WMS <home.html>`__ > How to create a Styled Layer Descriptor (SLD)
      using Arc2Earth

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

         Section last modified: 15 February 2013

         `Back <appendixI.html>`__\ \|\ `Next <6.html>`__

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
   Survey <http://www.bgs.ac.uk/hosted.html>`__ but responsibility for
   the content of the site lies with OneGeology not with the British
   Geological Survey. Questions, suggestions, or comments regarding the
   contents of this site should be directed to `the OneGeology
   administration <mailto:onegeology@bgs.ac.uk>`__.

.. |OneGeology logo| image:: appendixj/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
