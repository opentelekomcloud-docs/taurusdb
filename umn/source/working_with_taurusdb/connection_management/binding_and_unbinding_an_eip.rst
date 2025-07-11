:original_name: gaussdb_03_0011.html

.. _gaussdb_03_0011:

Binding and Unbinding an EIP
============================

Scenarios
---------

By default, a TaurusDB instance is not publicly accessible (not bound with an EIP) after being created. You can bind an EIP to the instance for public accessibility and can unbind the EIP from the instance as required.

.. important::

   To ensure that the database can be accessed, the security group used by the database must have the permission to access the database port. For example, if the database port is **3306**, ensure that the security group has the permission to access port **3306**.

Prerequisites
-------------

-  You have assigned an EIP on the VPC console.
-  If a DB instance has already been bound with an EIP, you must unbind the EIP from the DB instance first before binding a new EIP to it.

.. _gaussdb_03_0011__en-us_topic_0171122283_section3199593620428:

Binding an EIP
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. In the **Network Information** area, click **Bind** in the **Public IP Address (EIP)** field.

#. In the displayed dialog box, select an EIP and click **OK**.

   If no available EIPs are displayed, click **View EIP** and obtain an EIP.

   .. important::

      You need to configure security group rules and enable specific IP addresses and ports to access the target DB instance.

#. On the **EIPs** page, view the EIP that has been bound to the DB instance.

   To unbind the EIP from the DB instance, see :ref:`Unbinding an EIP <gaussdb_03_0011__en-us_topic_0171122283_section186511510267>`.

.. _gaussdb_03_0011__en-us_topic_0171122283_section186511510267:

Unbinding an EIP
----------------

#. On the **Instance Management** page, click the DB instance that has been bound with an EIP. The **Basic Information** page is displayed.
#. In the **Network Information** area, click **Unbind** in the **Public IP Address (EIP)** field.
#. In the displayed dialog box, click **Yes**.
#. To bind an EIP to the DB instance again, see :ref:`Binding an EIP <gaussdb_03_0011__en-us_topic_0171122283_section3199593620428>`.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
