:original_name: gaussdb_02_0015.html

.. _gaussdb_02_0015:

Step 2: Bind an EIP
===================

Scenarios
---------

You can bind an EIP to a DB instance for public access and can unbind the EIP from the DB instance if needed.

Precautions
-----------

-  Public accessibility reduces the security of DB instances. Therefore, exercise caution when enabling this function. To achieve a higher transmission rate and security level, you are advised to migrate your applications to the ECS that is in the same region as your DB instance.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. In the **Network Information** area, click **Bind** next to Private IP Address.

#. In the displayed dialog box, select an EIP and click **OK**.

   If no available EIPs are displayed, click **View EIP** and obtain an EIP.

   .. important::

      You need to configure security group rules and enable specific IP addresses and ports to access the target DB instance. For details, see :ref:`Step 3: Configure Security Group Rules <gaussdb_02_0013>`.

#. On the **EIPs** page, view the EIP that has been bound to the DB instance.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
