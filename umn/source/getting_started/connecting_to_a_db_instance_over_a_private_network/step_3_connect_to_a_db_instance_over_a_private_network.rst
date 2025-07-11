:original_name: gaussdb_02_0009.html

.. _gaussdb_02_0009:

Step 3: Connect to a DB Instance over a Private Network
=======================================================

TaurusDB is fully compatible with the MySQL protocol. You can connect to a DB instance through either a common connection or an SSL connection. SSL connections are encrypted.

Prerequisites
-------------

#. Log in to the ECS.

   -  For details on how to create and log in to an ECS, see "Creating an ECS" and "Logging In an ECS" in the *Elastic Cloud Server User Guide*.

   -  To connect to a DB instance through an ECS, you must ensure that:

      -  The ECS and DB instance are in the same VPC.
      -  The ECS must be allowed by the security group to access DB instances.

         -  If the security group with which the target DB instance associated is the default security group, you do not need to configure security group rules.

         -  If the security group with which the target DB instance associated is not the default security group, check whether the security group rules allow the ECS to connect to the DB instance. For details, see :ref:`Step 2: Configure Security Group Rules <gaussdb_02_0008>`.

            If the security group rules allow the access from the ECS, the ECS can connect to the DB instance.

            If the security group rules do not allow the access from the ECS, you need to add a security group rule. The ECS must be allowed by the security group to access DB instances.

#. Use a database client to connect to the target DB instance.

   You can use a database client to connect to the DB instance in the Linux or Windows OS.

   -  In the Linux OS, install the MySQL client on the device that can access TaurusDB. It is recommended that you download a MySQL client running a version later than that of the DB instance.

      For details about how to obtain and install the MySQL client, see :ref:`How Can I Install the MySQL Client? <gaussdb_faq_0011>`

   -  In the Windows OS, you can use any common database client to connect to the DB instance in a similar way.

      The database client **MySQL-Front** is used as an example in :ref:`Using MySQL-Front to Connect to a DB Instance <gaussdb_02_0009__en-us_topic_0171122303_section103301531245>`.

.. _gaussdb_02_0009__en-us_topic_0171122303_section103301531245:

Using MySQL-Front to Connect to a DB Instance
---------------------------------------------

#. Start MySQL-Front.

#. In the displayed dialog box, click **New**.


   .. figure:: /_static/images/en-us_image_0000001352219096.png
      :alt: **Figure 1** Connection management

      **Figure 1** Connection management

#. Enter the information of the DB instance to be connected and click **Ok**, as shown in :ref:`Figure 2 <gaussdb_02_0009__en-us_topic_0171122303_fig4664143131112>`.

   .. _gaussdb_02_0009__en-us_topic_0171122303_fig4664143131112:

   .. figure:: /_static/images/en-us_image_0000001352379004.png
      :alt: **Figure 2** Adding an account

      **Figure 2** Adding an account

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                 |
      +===================================+=============================================================================================================================================+
      | Name                              | Database connection task name. If you do not set this parameter, it will be the same as that configured for **Host** by default.            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Host                              | Private IP address for write of the target DB instance. To view the private address of the target DB instance, perform the following steps: |
      |                                   |                                                                                                                                             |
      |                                   | a. Log in to the TaurusDB console.                                                                                                          |
      |                                   | b. Select the region in which the DB instance is located.                                                                                   |
      |                                   | c. Click the target DB instance to go to the **Basic Information** page.                                                                    |
      |                                   | d. In the **Network Information** area, view the private IP address for write.                                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Port                              | Private network port of the DB instance.                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | User                              | Name of the user who accesses the DB instance. The default user is **root**.                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Password                          | Password of the DB instance account.                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed window, select the connection that you have created and click **Open**. If the connection information is correct, the DB instance is successfully connected.


   .. figure:: /_static/images/en-us_image_0000001402858817.png
      :alt: **Figure 3** Opening a session

      **Figure 3** Opening a session

SSL Connection
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. In the **DB Instance Information** area on the **Basic Information** page, click |image2| in the **SSL** field to download the root certificate or certificate bundle.

#. Import the root certificate to the Linux OS on the ECS.

   For details, see :ref:`How Do I Import the SSL Certificate of an RDS Instance to a Windows or Linux Server? <gaussdb_faq_0010>`

#. Connect to a DB instance. The Linux OS is assumed in this example.

   **mysql -h** <*hostName*> **-P** *<port>* **-u** <*userName*> **-p** **--ssl-ca=**\ <*caName*>

   .. table:: **Table 2** Parameter description

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                      |
      +===================================+==================================================================================================================================================================+
      | <*hostName*>                      | Private IP address for write.                                                                                                                                    |
      |                                   |                                                                                                                                                                  |
      |                                   | To obtain this parameter, go to the **Basic Information** page of the DB instance and view the private IP address for write in the **Network Information** area. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<port>*                          | Database port. By default, the value is **3306**.                                                                                                                |
      |                                   |                                                                                                                                                                  |
      |                                   | To obtain this parameter, go to the **Basic Information** page of the DB instance and view the database port in the **Network Information** area.                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*userName*>                      | Username of the TaurusDB administrator account. The default username is **root**.                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*caName*>                        | SSL certificate file name, which should be stored in the same directory where the command is executed.                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, to connect to a DB instance through an SSL connection as user **root**, run the following command:

   **mysql -h 172.16.0.31 -P 3306 -u root -p --ssl-ca=ca.pem**

   Enter the password of the database account as prompted:

   .. code-block::

      Enter password:

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001402979157.png
