:original_name: gaussdbformysql_03_0134.html

.. _gaussdbformysql_03_0134:

Changing Permissions for a Database Account
===========================================

Scenarios
---------

You can authorize database users you have created to specific databases or revoke permissions from authorized database users.

Constraints
-----------

This operation is not allowed when another operation is being performed on your DB instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane, choose **Accounts**. On the displayed page, locate the target username and click **Change Permission** in the **Operation** column.
#. In the displayed dialog box, select one or more unauthorized databases and authorize their permissions to the account. To delete a selected database, locate the database and click **x** in the **Operation** column.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
