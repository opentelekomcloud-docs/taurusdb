:original_name: gaussdb_03_0114.html

.. _gaussdb_03_0114:

Deleting a Read Replica
=======================

Scenarios
---------

You can manually delete read replicas on the **Instances** page.

.. important::

   Deleted read replicas cannot be restored. Exercise caution when performing this operation.

Constraints
-----------

-  You can only delete a read replica when the DB instance has two or more read replicas.
-  DB instances cannot be deleted when operations are being performed on them. They can be deleted only after the operations are completed.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. At the bottom of the **Basic Information** page, locate the read replica to be deleted and choose **More** > **Delete** in the **Operation** column.

   For high availability reasons, the system reserves an available read replica. The read replica cannot be deleted until the associated DB instance is deleted.

#. In the displayed dialog box, click **Yes**. Refresh the **Instances** page later to check that the deletion is successful.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
