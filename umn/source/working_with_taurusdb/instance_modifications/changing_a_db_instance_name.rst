:original_name: gaussdb_03_0032.html

.. _gaussdb_03_0032:

Changing a DB Instance Name
===========================

Scenarios
---------

You can change the name of a TaurusDB instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, locate the instance name and click |image2| in the **Name/ID** column to edit the instance name.

   -  The DB instance name must start with a letter and consist of 4 to 64 characters. Only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_) are allowed.
   -  When changing the instance name, you can determine whether to select **Change node names synchronously** as required. If this option is selected, the names of the corresponding nodes are changed when the instance name is changed. If this option is not selected, only the instance name is changed, and the corresponding node names are not changed.
   -  If you want to submit the change, click **OK**. If you want to cancel the change, click **Cancel**.

#. View the result of the change on the **Basic Information** page.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001402858869.png
