:original_name: gaussdb_02_0008.html

.. _gaussdb_02_0008:

Step 2: Configure Security Group Rules
======================================

Scenarios
---------

A security group is a collection of access control rules for ECSs and DB instances that have the same security requirements and are mutually trusted in a VPC. To ensure database security and reliability, you need to configure security group rules to allow specific IP addresses and ports to access DB instances.

Check whether the ECS and DB instance are in the same security group.

-  If they are in the same security group, they can communicate with each other by default. No security group rule needs to be configured. Go to :ref:`Step 3: Connect to a DB Instance over a Private Network <gaussdb_02_0009>`.
-  If they are in different security groups, you need to configure security group rules for the ECS and DB instance, respectively.

   -  DB instance: Configure an inbound rule for the security group associated with the DB instance.
   -  ECS: The default security group rule allows all outgoing data packets. In this scenario, you do not need to configure a security rule for the ECS. If not all outbound traffic is allowed in the security group, you need to configure an outbound rule for the ECS.

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

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                     | Example Value                                                                              |
      +=======================+=================================================================================================================================================================+============================================================================================+
      | Protocol & Port       | Network protocol for which the security group rule takes effect.                                                                                                | TCP                                                                                        |
      |                       |                                                                                                                                                                 |                                                                                            |
      |                       | -  Currently, the value can be **All**, **TCP (All ports)**, **TCP (Custom ports)**, **UDP (All ports)**, **UDP (Custom ports)**, **ICMP**, **GRE**, or others. |                                                                                            |
      |                       | -  **All**: indicates all protocol ports are supported.                                                                                                         |                                                                                            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
      |                       | **Port**: Port or port range over which the traffic can reach your ECS.                                                                                         | When connecting to the instance through a private network, enter the port of the instance. |
      |                       |                                                                                                                                                                 |                                                                                            |
      |                       |                                                                                                                                                                 | -  Individual port: Enter a port, such as **22**.                                          |
      |                       |                                                                                                                                                                 | -  Consecutive ports: Enter a port range, such as **22-30**.                               |
      |                       |                                                                                                                                                                 | -  All ports: Leave it blank or enter **1-65535**.                                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
      | Source                | **Source**: specifies the source of the security group rule. The value can be another security group, a CIDR block, or an IP address.                           | 0.0.0.0/0                                                                                  |
      |                       |                                                                                                                                                                 |                                                                                            |
      |                       | xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                               |                                                                                            |
      |                       |                                                                                                                                                                 |                                                                                            |
      |                       | xxx.xxx.xxx.0/24 (subnet)                                                                                                                                       |                                                                                            |
      |                       |                                                                                                                                                                 |                                                                                            |
      |                       | 0.0.0.0/0 (any IP address)                                                                                                                                      |                                                                                            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
      | Description           | Provides supplementary information about the security group rule. This parameter is optional.                                                                   | ``-``                                                                                      |
      |                       |                                                                                                                                                                 |                                                                                            |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (<>).                                                                 |                                                                                            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
      | Operation             | You can copy or delete a security group rule. If there is only one security group rule, the security group rule cannot be deleted.                              | ``-``                                                                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
