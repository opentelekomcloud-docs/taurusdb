:original_name: gaussdb_05_0018.html

.. _gaussdb_05_0018:

Applying a Parameter Template
=============================

Scenarios
---------

Modifications to parameters in a custom parameter template take effect only after you apply this parameter template to target DB instances.

-  The parameter **innodb_buffer_pool_size** is determined by the memory. DB instances of different specifications have different value ranges. If this parameter value is out of range of the DB instance to which the parameter template applies, the maximum value within the range is used.
-  A parameter template can be applied only to DB instances of the same DB engine version.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Parameter Templates** page, you can apply a default template or a custom template to a target DB instance:

   -  To apply a default template, click **Default Templates**, locate the target parameter template, and in the **Operation** column, click **Apply**.
   -  To apply a custom template, click **Custom Templates**, locate the target parameter template, and in the **Operation** column, choose **More** > **Apply**.

   A parameter template can be applied to one or more DB instances.

#. In the displayed dialog box, select one or more DB instances to which the parameter template will apply and click **OK**.

   After the parameter template applies to DB instances successfully, you can view the application records by referring to :ref:`Viewing Application Records of a Parameter Template <gaussdb_05_0098>`.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
