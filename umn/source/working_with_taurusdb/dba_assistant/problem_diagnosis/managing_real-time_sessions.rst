:original_name: en-us_topic_0000002521502463.html

.. _en-us_topic_0000002521502463:

Managing Real-Time Sessions
===========================

Scenarios
---------

You can view current session statistics of your instance and kill abnormal sessions.

Constraints
-----------

Killing a session may cause the application to disconnect from the instance. Your application should be able to reconnect to the instance.

Setting a Slow Session Threshold
--------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Click |image2| in the upper left corner of the page and choose **Databases** > **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.

#. Click the **Sessions** tab to view current session statistics by user, access host, and database.

#. In the session list, select the abnormal session you want to kill and click **Kill Session** to recover the database.

   A maximum of 20 sessions can be killed at once.

   To kill sessions automatically, see :ref:`Using Auto Kill Sessions <en-us_topic_0000002489182682>`.

.. |image1| image:: /_static/images/en-us_image_0000002518409421.png
.. |image2| image:: /_static/images/en-us_image_0000002486209558.png
