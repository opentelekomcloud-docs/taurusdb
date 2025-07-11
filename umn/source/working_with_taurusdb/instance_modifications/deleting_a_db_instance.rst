:original_name: gaussdb_03_0047.html

.. _gaussdb_03_0047:

Deleting a DB Instance
======================

Scenarios
---------

You can manually delete a DB instance on the **Instances** page.

.. important::

   -  If you delete a DB instance, the read replicas associated with it are also deleted.
   -  Deleted DB instances cannot be recovered. Exercise caution when performing this operation.

Constraints
-----------

-  DB instances cannot be deleted when operations are being performed on them. They can be deleted only after the operations are completed.
-  If you delete a DB instance, its automated backups are also deleted and you are no longer charged for them. Manual backups are still retained and will incur additional costs.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, locate the DB instance to be deleted and click **More** > **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**. Refresh the **Instances** page later to check that the deletion is successful.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
