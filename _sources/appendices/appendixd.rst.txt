=======================================================================
Creating MapServer CLASS definitions from ArcView legends \| OneGeology
=======================================================================

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
      WMS <home.html>`__ > Creating MapServer CLASS definitions using
      QGIS

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

         .. rubric:: Appendix D: Creating MapServer CLASS definitions
            using Quantum GIS
            :name: appendix-d-creating-mapserver-class-definitions-using-quantum-gis
            :class: technical_progress_side_menu

         Quantum GIS (QGIS) is a user friendly Open Source Geographic
         Information System (GIS) licensed under the `GNU General Public
         License <http://www.gnu.org/copyleft/gpl.html>`__
         (http://www.gnu.org/copyleft/gpl.html). QGIS is an official
         project of the `Open Source Geospatial Foundation
         (OSGeo) <http://www.osgeo.org/>`__ (http://www.osgeo.org/). It
         runs on Linux, Unix, Mac OSX, and Windows and supports numerous
         vector, raster, and database formats and functionalities.

         The current stable version of QGIS (QGIS 2.12) is available for
         download from
         https://www.qgis.org/en/site/forusers/download.html

         For information on how to use QGIS to view WMS and WFS services
         see the ‘how to’ `section 1.4.7 </howto/1_4_7.html>`__

         You can use the MapServer Export QGIS plugin to create a .map
         configuration file. You will first need to enable the plugin,
         which comes bundled as part of the standard installation,
         through the Plugins menu. Select *Manage plugins* then select
         *MapServer Export* from the *QGIS Plugin Manager*.

         | |QGIS Enabling the MapServer Export plugin|
         | QGIS Enabling the MapServer Export plugin

         With the map data you wish to serve as a WMS open in QGIS,
         select *Plugins* and then *MapServer Export* to start the
         conversion process.

         | |QGIS Running the MapServer Export plugin|
         | QGIS Running the MapServer Export plugin

         You are given some options when you run the plugin (as below).
         You may use the defaults or add your own (as we have here). It
         isn’t important if you don’t know what to enter at this stage
         as you can edit the values in the .map file in any text editor.
         It may help though if add some dummy values, just so you get
         the correct structure.

         | |QGIS MapServer Export: Save project to map file|
         | QGIS MapServer Export: Save project to map file

         When you have made all the edits you want to add, click ok. If
         there are no errors, you will get a results summary window (as
         below).

         | |QGIS MapServer Export results summary|
         | QGIS MapServer Export results summary

         **Note** the URLs shown in the results summary will not work in
         the OneGeology exemplar service set-up (as detailed in this
         cookbook); you will need to follow the instructions in `Section
         4.3 <4_3.html>`__ to complete the set-up process.

         Section last modified: 19 June 2011

         `Back <appendixC_2.html>`__\ \|\ `Next <appendixE.html>`__

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

.. |OneGeology logo| image:: appendixd/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
.. |QGIS Enabling the MapServer Export plugin| image:: appendixd/da400f467b471213c167ec57a6d7c4fd39ad96a9.jpg
   :width: 700px
   :height: 612px
.. |QGIS Running the MapServer Export plugin| image:: appendixd/b3d7dde36b9b9caaec187b20ab1e5e79cc096868.jpg
   :width: 703px
   :height: 647px
.. |QGIS MapServer Export: Save project to map file| image:: appendixd/74149622023daaac436dc389b4e50f3732ddb193.jpg
   :width: 617px
   :height: 532px
.. |QGIS MapServer Export results summary| image:: appendixd/876f5c56eb15e3bc98f7fcb6c656395455cc9ba1.jpg
   :width: 685px
   :height: 352px
