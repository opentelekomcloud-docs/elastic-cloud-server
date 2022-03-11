Why Am I Seeing An Error Message That Says The Two Computers Couldn't Be Connected in the Amount of Time Allotted When I Log In to a Windows ECS?
=================================================================================================================================================

Symptom
-------

An error message is displayed indicating that the computer cannot connect to the remote computer in the amount of time allotted.

| **Figure 1** Error message
| |image1|

Solution
--------

#. On the local computer, click on the **Start** icon, type **cmd** into the box, and run the command as an administrator.
#. Run the **netsh winsock reset** command.
#. Restart the local computer as prompted and reconnect to the ECS.



.. |image1| image:: /_static/images/en-us_image_0288997357.png
   :class: imgResize

