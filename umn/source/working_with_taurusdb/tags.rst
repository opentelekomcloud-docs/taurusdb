:original_name: gaussdbformysql_tag.html

.. _gaussdbformysql_tag:

Tags
====

Scenarios
---------

Tag Management Service (TMS) enables you to use tags on the management console to manage resources. TMS works with other cloud services to manage tags. TMS manages tags globally, and other cloud services manage their own tags.

-  You are advised to configure predefined tags on the TMS console.
-  A tag consists of a key and value. You can add only one value for each key.
-  Each instance can have up to 20 tags.

Adding a Tag
------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. Choose **Tags** in the navigation pane and click **Add Tag**. In the displayed dialog box, enter a tag key and value, and click **OK**.

   -  The tag key must be unique and must consist of 1 to 36 characters. Only letters, digits, hyphens (-), underscores (_), and at signs (@) are allowed.
   -  The tag value can be empty or consist of 1 to 43 characters. Only letters, digits, hyphens (-), underscores (_), and at signs (@) are allowed.

#. View and manage the tag on the **Tags** page.

Editing a Tag
-------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. On the **Tags** page, locate the tag to be edited and click **Edit** in the **Operation** column. In the displayed dialog box, change the tag value and click **OK**.

   -  Only the tag value can be edited.
   -  The tag value can be empty or consist of 1 to 43 characters. Only letters, digits, hyphens (-), underscores (_), and at signs (@) are allowed.

#. View and manage the tag on the **Tags** page.

Deleting a Tag
--------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Instances** page, click the instance name.
#. On the **Tags** page, locate the tag to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.
#. View that the tag is no longer displayed on the **Tags** page.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352219100.png
.. |image3| image:: /_static/images/en-us_image_0000001352219100.png
