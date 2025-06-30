:original_name: gaussdb_11_0031.html

.. _gaussdb_11_0031:

Changing a Proxy Address
========================

Scenarios
---------

You can change the IP address of a proxy instance.

Precautions
-----------

Changing a proxy address will interrupt database connections and services. Perform the operation during off-peak hours or when services are stopped.

Constraints
-----------

The new IP address is not in use and must be in the same subnet as the TaurusDB instance.

Procedure
---------

You can change the proxy address for a TaurusDB instance with read/write splitting enabled.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the target instance.

#. In the navigation pane on the left, choose **Database Proxy**.

   Click the desired proxy instance. In the **Proxy Instance Information** area, click **Change** next to the **Proxy Address** field.

#. In the displayed dialog box, enter a new IP address and click **OK**.

   In-use IP addresses cannot be used.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
