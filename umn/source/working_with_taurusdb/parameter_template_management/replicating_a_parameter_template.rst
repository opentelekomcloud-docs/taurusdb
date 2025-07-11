:original_name: gaussdb_08_0014.html

.. _gaussdb_08_0014:

Replicating a Parameter Template
================================

Scenarios
---------

You can replicate a parameter template you have created. When you have already created a parameter template and want to include most of the custom parameters and values from that template in a new parameter template, you can replicate that parameter template.

After the parameter template is replicated, you should wait at least 5 minutes before using it to create a DB instance.

Default parameter templates cannot be replicated. You can create parameter templates based on the default ones.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Parameter Templates** page, click **Custom Templates**. Locate the target parameter template and click **Replicate** in the **Operation** column.

   Alternatively, click the target DB instance on the **Instances** page. On the **Parameters** page, click **Export** to generate a new parameter template for future use.

#. In the displayed dialog box, configure required details and click **OK**.

   -  The template name consists of 1 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
   -  The template description consists of a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=

   After the parameter template is replicated, a new template is generated in the list in the **Customer Templates** tab of the **Parameter Templates** page.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
