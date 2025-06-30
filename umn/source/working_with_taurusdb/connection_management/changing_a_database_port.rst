:original_name: gaussdb_03_0012.html

.. _gaussdb_03_0012:

Changing a Database Port
========================

Scenarios
---------

You can change the database port of a TaurusDB instance. The change applies to the ports of the primary node and read replicas, and may affect services intermittently.

Constraints
-----------

Changing the database port of a DB instance will only affect access through its IP address. If a DB instance is accessed through a proxy instance, the database port of the proxy instance cannot be changed, which defaults to **3306**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. In the **Network Information** area, click |image2| in the **Database Port** field.

   The database port of a TaurusDB instance ranges from 1025 to 65534, excluding 5342, 5343, 5344, 5345, 12017, 20000, 20201, 20202, 33060, 33062, and 33071, which are reserved for system use.

   -  To submit the change, click |image3|.

      -  In the dialog box, click **Yes**.

         a. If you change the database port of a DB instance, the ports of the primary node and read replicas are also changed accordingly and all of them are rebooted.
         b. This process takes about 1-5 minutes.

   -  To cancel the change, click |image4|.

#. View the result of the change on the **Basic Information** page.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352378996.png
.. |image3| image:: /_static/images/en-us_image_0000001352538852.png
.. |image4| image:: /_static/images/en-us_image_0000001403138693.png
