===========================================================
Recommend ESRI shapefile definitions for GeoSciML-Portrayal
===========================================================

.. container::
   :name: outer_container

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
