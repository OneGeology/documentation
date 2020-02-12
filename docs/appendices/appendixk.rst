=========================================================================
Recommend ESRI shapefile definitions for GeoSciML-Portrayal \| OneGeology
=========================================================================

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
      WMS <home.html>`__ > Recommend ESRI shapefile definitions for
      GeoSciML-Portrayal

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

         .. rubric:: Recommend ESRI shapefile definitions for
            GeoSciML-Portrayal
            :name: recommend-esri-shapefile-definitions-for-geosciml-portrayal
            :class: technical_progress_side_menu

         Because the field names in GeoSciML-Portrayal are longer than
         10 characters, you will not be able to have the full attribute
         (column) name for many of the properties if your portrayal data
         is loaded into an ESRI shapefile, which can be an issue in some
         WMS server software. To prevent truncated names, we are
         providing a recommended shapefile implementation with shorter
         field names. Field names are abbreviated to try and leave
         characters that convey the full name of the field; lower camel
         case typographic has been used, except that fields that contain
         URI’s end with ‘_uri’.

          

         .. rubric:: Table 4. Recommend shapefile definition for
            ContactView
            :name: table-4.-recommend-shapefile-definition-for-contactview

         ================== ==================== ===================
         XML field Name     Shapefile field name Shapefile data type
         ================== ==================== ===================
         identifier         identifier           String
         name               name                 String
         description        descriptio           String
         contactType        contactTyp           String
         observationMethod  obsvMethod           String
         positionalAccuracy posAccur             String
         source             source               String
         contactType_uri    conTyp_uri           String
         specification_uri  spec_uri             String
         metadata_uri       metada_uri           String
         genericSymbolizer  genericSym           String
         shape              SHAPE                ESRI geometry
         ================== ==================== ===================

          

         .. rubric:: Table 5. Recommended shapefile definition for
            ShearDisplacementStructureView
            :name: table-5.-recommended-shapefile-definition-for-sheardisplacementstructureview

         ============================ ==================== ===================
         XML field Name               Shapefile field name Shapefile data type
         ============================ ==================== ===================
         identifier                   identifier           String
         name                         name                 String
         description                  descriptio           String
         faultType                    faultType            String
         movementType                 movmntType           String
         deformationStyle             defrmStyle           String
         displacement                 displacmnt           String
         geologicHistory              geolHistry           String
         observationMethod            obsvMethod           String
         positionalAccuracy           posAccur             String
         source                       source               String
         faultType_uri                fltTyp_uri           String
         movementType_uri             movTyp_uri           String
         deformationStyle_uri         defStl_uri           String
         representativeAge_uri        repAge_uri           String
         representativeOlderAge_uri   oldAge_uri           String
         representativeYoungerAge_uri yngAge_uri           String
         specification_uri            spec_uri             String
         metadata_uri                 metada_uri           String
         genericSymbolizer            genericSym           String
         shape                        SHAPE                ESRI geometry
         ============================ ==================== ===================

          

         .. rubric:: Table 6. Recommended shapefile definition for
            GeologicUnitView
            :name: table-6.-recommended-shapefile-definition-for-geologicunitview

         ============================ ==================== ===================
         XML field Name               Shapefile field name Shapefile data type
         ============================ ==================== ===================
         identifier                   identifier           String
         name                         name                 String
         description                  descriptio           String
         geologicUnitType             geoUnitTyp           String
         rank                         rank                 String
         lithology                    lithology            String
         geologicHistory              geolHistry           String
         observationMethod            obsvMethod           String
         positionalAccuracy           posAccur             String
         source                       source               String
         geologicUnitType_uri         uniTyp_uri           String
         representativeLithology_uri  repLth_uri           String
         representativeAge_uri        repAge_uri           String
         representativeOlderAge_uri   oldAge_uri           String
         representativeYoungerAge_uri yngAge_uri           String
         specification_uri            spec_uri             String
         metadata_uri                 metada_uri           String
         genericSymbolizer            genericSym           String
         shape                        SHAPE                ESRI geometry
         ============================ ==================== ===================

         Section last modified: 12 October 2015

         `Back <appendixJ.html>`__\ \|\ `Next <home.html>`__

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

.. |OneGeology logo| image:: appendixk/1a3d7a0fc8cbefb032a4aba3fe6782e68ee5ea62.png
   :class: nob
   :name: oneGeologylogo
   :target: /home.html
