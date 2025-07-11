:original_name: gaussdbformysql_03_0121.html

.. _gaussdbformysql_03_0121:

Creating a Database
===================

Scenarios
---------

After your TaurusDB instance is created, you can create databases on it.

Constraints
-----------

-  This operation is not allowed when another operation is being performed on your DB instance.
-  After a database is created, its name cannot be changed.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane, choose **Databases**. On the displayed page, click **Create Database**. In the displayed dialog box, enter a database name, select a character set, and authorize permissions for users. Then, click **OK**.

   .. table:: **Table 1** Parameter description

      +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter     | Description                                                                                                                                                                         |
      +===============+=====================================================================================================================================================================================+
      | Database Name | The database name can consist of up to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed. The total number of hyphens (-) cannot exceed 10.         |
      +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Character Set | Select a character set as required.                                                                                                                                                 |
      +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User          | You can select one or more unauthorized users. If there are no unauthorized users, you can create one by referring to :ref:`Creating a Database Account <gaussdbformysql_03_0131>`. |
      +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description   | The description can consist of up to 512 characters. It cannot contain carriage returns or any of the following special characters: !<"='>&                                         |
      +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After the database is created, authorize or delete it on the **Databases** page. You can search for the desired database by character set and database name.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
