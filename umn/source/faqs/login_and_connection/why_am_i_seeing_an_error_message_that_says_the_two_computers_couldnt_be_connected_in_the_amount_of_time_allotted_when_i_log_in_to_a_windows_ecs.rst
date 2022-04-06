.. _en-us_topic_0264235947:

Why Am I Seeing An Error Message That Says The Two Computers Couldn't Be Connected in the Amount of Time Allotted When I Log In to a Windows ECS?
=================================================================================================================================================



.. _en-us_topic_0264235947__en-us_topic_0173599485_section472713533172:

Symptom
-------

An error message is displayed indicating that the computer cannot connect to the remote computer in the amount of time allotted.



.. _en-us_topic_0264235947__en-us_topic_0173599485_en-us_topic_0120795668_fig1256612592310:

.. figure:: /_static/images/en-us_image_0288997357.png
   :alt: Click to enlarge
   :figclass: imgResize


   **Figure 1** Error message



.. _en-us_topic_0264235947__en-us_topic_0173599485_section2388160183:

Solution
--------

#. On the local computer, click on the **Start** icon, type **cmd** into the box, and run the command as an administrator.
#. Run the **netsh winsock reset** command.
#. Restart the local computer as prompted and reconnect to the ECS.
