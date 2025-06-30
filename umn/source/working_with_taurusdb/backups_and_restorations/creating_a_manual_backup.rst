:original_name: gaussdb_03_0058.html

.. _gaussdb_03_0058:

Creating a Manual Backup
========================

Scenarios
---------

TaurusDB allows you to create manual backups for available primary nodes. You can restore data from backups to ensure data reliability.

-  When you delete a DB instance, its automated backups are also deleted but its manual backups are retained.

Method 1
--------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, locate the target DB instance and choose **More** > **Create Backup** in the **Operation** column.
#. In the displayed dialog box, enter a backup name and description. Then, click **OK**. If you want to cancel the backup creation task, click **Cancel**.

   -  The backup name must consist of 4 to 64 characters and start with a letter. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description must consist of a maximum of 256 characters and cannot contain the carriage return character or the following special characters: !<"='>&
   -  The time required for creating a manual backup depends on the data volume of the DB instance.

#. After a manual backup has been created, you can view and manage it on the **Backups** page.

Method 2
--------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. On the **Backups** page, click **Create Backup**. In the displayed dialog box, enter a backup name and a description, and click **OK**. If you want to cancel the backup creation task, click **Cancel**.

   -  The backup name must consist of 4 to 64 characters and start with a letter. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description must consist of a maximum of 256 characters and cannot contain the carriage return character or the following special characters: !<"='>&
   -  The time required for creating a manual backup depends on the data volume of the DB instance.

#. After a manual backup has been created, you can view and manage it on the **Backups** page.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352219100.png
