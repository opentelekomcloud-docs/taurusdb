:original_name: gaussdb_03_0072.html

.. _gaussdb_03_0072:

Creating a Parameter Template
=============================

You can use database parameter templates to manage DB engine configurations. A database parameter template acts as a container for engine configuration values that can be applied to one or more DB instances.

.. important::

   Not all DB engine parameters can be changed in a custom parameter template.

If you want to use your custom parameter template, you simply create a parameter template and select it when you create a DB instance or apply it to an existing DB instance following the instructions provided in :ref:`Applying a Parameter Template <gaussdb_05_0018>`.

When you have already created a parameter template and want to include most of the custom parameters and values from that template in a new parameter template, you can replicate that parameter template following the instructions provided in :ref:`Replicating a Parameter Template <gaussdb_08_0014>`.

The following are the key points you should know when using parameters:

-  When you change a dynamic parameter value in a parameter template and save the change, the change takes effect immediately. When you change a static parameter value in a parameter template and save the change, the change will take effect only after you manually reboot the DB instances to which the parameter template applies.
-  Improper parameter settings may have unintended adverse effects, including degraded performance and system instability. Exercise caution when modifying database parameters and you need to back up data before modifying parameters in a parameter template. Before applying parameter template changes to a production DB instance, you should try out these changes on a test DB instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **TaurusDB**.
#. On the **Parameter Templates** page, click **Create Parameter Template**.
#. In the displayed dialog box, configure required information and click **OK**.

   -  Select a DB engine for the parameter template.
   -  The template name must consist of 1 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
   -  The description consists of a maximum of 256 characters and cannot contain the carriage return character or the following special characters: >!<"&'=

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
