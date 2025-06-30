:original_name: gaussdb_11_0021.html

.. _gaussdb_11_0021:

Testing Read/Write Splitting Performance
========================================

After a proxy instance is created, you can connect your DB instance through a proxy address. You can use internal SQL commands to verify the read/write splitting performance.

Procedure
---------

#. Connect to a DB instance through a proxy address. For details, see :ref:`Creating a Proxy Instance <gaussdb_11_0017>`.

#. Run the following command to view the routing result of the previous SQL statement. The result is the private IP address of the DB instance.

   .. code-block:: text

      show last route;


   .. figure:: /_static/images/en-us_image_0000001420606766.png
      :alt: **Figure 1** Query results

      **Figure 1** Query results
