:original_name: gaussdb_08_0112.html

.. _gaussdb_08_0112:

Modifying a Parameter Template
==============================

You can modify parameters in a custom parameter template to optimize TaurusDB database performance.

You can change parameter values in custom parameter templates only, but cannot change parameter values in default parameter templates. When you change parameter values in a custom parameter template, the changes take effect for all DB instances to which the parameter template applies.

.. note::

   Though parameter values in a default template cannot be changed, you can view details about a default parameter template. If a custom parameter template is set incorrectly and causes a database reboot to fail, you can re-configure the custom parameter template according to the configurations of the default parameter template.

Modifying Parameter Template Parameters
---------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. In the navigation pane on the left, choose **Parameter Templates**. On the **Custom Templates** page, click the parameter template you want to view.

#. Modify parameters as required.

   Available operations are as follows:

   .. important::

      After you modify parameters in a parameter template, some modifications immediately take effect for the DB instance to which the parameter template applies. Exercise caution when performing this operation.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After the parameters have been modified, you can click **Change History** to view the modification details.

   .. important::

      The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <gaussdb_05_0018>`.

   -  After modifying some parameters of a DB instance, you may need to reboot the DB instance for the modifications to take effect.
   -  After modifying some parameters of a read replica, you may need to reboot the read replica for the modifications to take effect.

Modifying Instance Parameters
-----------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   Available operations are as follows:

   .. important::

      Check the value in the **Effective upon Reboot** column.

      -  If the value is **Yes** and the DB instance status on the **Instances** page is **Pending reboot**, you must reboot the DB instance for the modifications of this parameter to take effect.
      -  If the value is **No**, the modification of this parameter takes effect immediately.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

   After parameters are modified, you can click **Change History** to view parameter modification details.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352219100.png
