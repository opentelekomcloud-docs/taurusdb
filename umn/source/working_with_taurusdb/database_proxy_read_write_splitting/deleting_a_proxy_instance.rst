:original_name: gaussdb_11_0019.html

.. _gaussdb_11_0019:

Deleting a Proxy Instance
=========================

You can delete a proxy instance as required.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Database Proxy**.
#. On the **Database Proxy** page, locate the desired proxy instance and click **Disable Database Proxy** in the **Operation** column. In the displayed dialog box, click **Yes**.

   .. note::

      If database proxy is disabled, read/write splitting is also disabled and services using the proxy address are interrupted. You need to switch your applications to the instance address.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
