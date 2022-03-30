
Using MapInfo Professional
--------------------------

.. todo::

   MapInfo: Can anyone check whether this is up-to-date? Current content at http://onegeology.org/howto/1_4_8.html

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