:original_name: gaussdb_02_0013.html

.. _gaussdb_02_0013:

Step 3: Configure Security Group Rules
======================================

Scenarios
---------

A security group is a collection of access control rules for ECSs and DB instances that have the same security requirements and are mutually trusted in a VPC.

To ensure database security and reliability, you need to configure security group rules to allow specific IP addresses and ports to access DB instances.

When you attempt to connect to a DB instance through an EIP, you need to configure an inbound rule for the security group associated with the DB instance.

Precautions
-----------

The default security group rule allows all outgoing data packets. If an ECS and a DB instance are in the same security group, they can access each other. When a security group is created, you can configure security group rules to control access to and from DB instances in that security group.

-  By default, you can create a maximum of 500 security group rules.
-  To prevent high network latency for the first packet, you are advised to create a maximum of 50 rules for each security group.
-  To access a DB instance from resources outside the security group, you need to configure an inbound rule for the security group associated with the DB instance.

.. note::

   To ensure the security of your data and DB instances, you are advised to use the principle of least privilege for database access. Change the database port (default value: **3306**), and set the IP address to the remote server's address or an IP address on the remote server's smallest subnet so that access to the remote server is limited.

   The default value of **Source** is **0.0.0.0/0**, indicating that TaurusDB instances in the security group can be accessed from any IP address.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. Configure security group rules.

   In the **Network Information** area on the **Basic Information** page, click the security group.

#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed dialog box, set required parameters and click **OK**.

   You can click **+** to add more inbound rules.

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                             | Example Value                                                                                                                   |
      +=======================+=========================================================================================================================================================================================================================================================+=================================================================================================================================+
      | Protocol              | Network protocol.                                                                                                                                                                                                                                       | TCP                                                                                                                             |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Port and Source       | -  **Port**: specifies the port or port range over which the traffic can reach your ECS. The value ranges from 1025 to 65534, excluding 5342, 5343, 5344, 5345, 12017, 20000, 20201, 20202, 33060, 33062, and 33071, which are reserved for system use. | -  When connecting to the DB instance over a private network, enter the ECS's IP address and target DB instance's port.         |
      |                       |                                                                                                                                                                                                                                                         | -  When connecting to the DB instance over a public network, enter the local device's IP address and target DB instance's port. |
      |                       | -  **Source**: specifies the source of the security group rule. The value can be another security group, a CIDR block, or an IP address.                                                                                                                |                                                                                                                                 |
      |                       |                                                                                                                                                                                                                                                         |                                                                                                                                 |
      |                       |    xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                                                                                                    |                                                                                                                                 |
      |                       |                                                                                                                                                                                                                                                         |                                                                                                                                 |
      |                       |    xxx.xxx.xxx.0/24 (subnet)                                                                                                                                                                                                                            |                                                                                                                                 |
      |                       |                                                                                                                                                                                                                                                         |                                                                                                                                 |
      |                       |    0.0.0.0/0 (any IP address)                                                                                                                                                                                                                           |                                                                                                                                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Description           | Provides supplementary information about the security group rule. This parameter is optional.                                                                                                                                                           | ``-``                                                                                                                           |
      |                       |                                                                                                                                                                                                                                                         |                                                                                                                                 |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (<>).                                                                                                                                                         |                                                                                                                                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
