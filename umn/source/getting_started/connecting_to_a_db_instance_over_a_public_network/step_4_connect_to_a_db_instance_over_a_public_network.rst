:original_name: gaussdb_02_0014.html

.. _gaussdb_02_0014:

Step 4: Connect to a DB Instance over a Public Network
======================================================

TaurusDB is fully compatible with the MySQL protocol. Therefore, you can connect to a DB instance through a common connection or an SSL connection. SSL connections are encrypted.

.. _gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_section367520762117:

Prerequisites
-------------

#. Bind an EIP to the target DB instance and configure security group rules.

   a. Bind an EIP to the target DB instance.

      For details about how to bind an EIP, see :ref:`Step 2: Bind an EIP <gaussdb_02_0015>`.

   b. .. _gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_li85977812411:

      Obtain the IP address of the local device.

   c. Configure security group rules.

      Add the IP address and port obtained in :ref:`1.b <gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_li85977812411>` to the inbound rule of the security group.

      For details about how to configure a security group rule, see :ref:`Step 3: Configure Security Group Rules <gaussdb_02_0013>`.

   d. Run the **ping** command to check the connectivity between the local device and the DB instance.

#. Use a database client to connect to the DB instance.

   You can use a database client to connect to the DB instance in the Linux or Windows OS.

   -  In the Linux OS, you need to install a MySQL client on the ECS. It is recommended that you download a MySQL client running a version later than that of the DB instance.

      For details about how to obtain and install the MySQL client, see :ref:`How Can I Install the MySQL Client? <gaussdb_faq_0011>`

   -  In the Windows OS, you can use any common database client to connect to the DB instance in a similar way.

      The database client **MySQL-Front** is used as an example in :ref:`Using MySQL-Front to Connect to a DB Instance <gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_section8112152217539>`.

.. _gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_section8112152217539:

Using MySQL-Front to Connect to a DB Instance
---------------------------------------------

#. Start MySQL-Front.

#. In the displayed dialog box, click **New**.


   .. figure:: /_static/images/en-us_image_0000001352219136.png
      :alt: **Figure 1** Connection management

      **Figure 1** Connection management

#. Enter the information of the DB instance to be connected and click **Ok**, as shown in :ref:`Figure 2 <gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_fig4664143131112>`.

   .. _gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_fig4664143131112:

   .. figure:: /_static/images/en-us_image_0000001352379040.png
      :alt: **Figure 2** Adding an account

      **Figure 2** Adding an account

   .. table:: **Table 1** Parameter description

      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                                                                                                                                                |
      +===========+============================================================================================================================================================================================================================+
      | Name      | Database connection task name. If you do not set this parameter, it will be the same as that configured for **Host** by default.                                                                                           |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Host      | EIP bound to the target DB instance. To obtain this parameter, go to the **Basic Information** page of the DB instance. The EIP can be found in the **Public IP Address (EIP)** field in the **Network Information** area. |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Port      | Private network port of the DB instance.                                                                                                                                                                                   |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User      | Name of the user who accesses the DB instance. The default user is **root**.                                                                                                                                               |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Password  | Password of the DB instance account.                                                                                                                                                                                       |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed window, select the connection that you have created in :ref:`Figure 3 <gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_fig3870144665113>` and click **Open**.

   If the connection information is correct, the DB instance is successfully connected.

   .. _gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_fig3870144665113:

   .. figure:: /_static/images/en-us_image_0000001402858861.png
      :alt: **Figure 3** Opening a session

      **Figure 3** Opening a session

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Prerequisites <gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_section367520762117>` and try again.

Using SSL to Connect to a DB Instance
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. In the **DB Instance Information** area on the **Basic Information** page, click |image2| in the **SSL** field to download the root certificate or certificate bundle.

#. Import the root certificate to the Linux OS on the ECS.

   For details, see :ref:`How Do I Import the SSL Certificate of an RDS Instance to a Windows or Linux Server? <gaussdb_faq_0010>`

#. Connect to a DB instance. The Linux OS is assumed in this example.

   **mysql -h** <*hostName*> **-P** *<port>* **-u** <*userName*> **-p** **--ssl-ca=**\ <*caName*>

   .. table:: **Table 2** Parameter description

      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Description                                                                                                                                                                                                                                      |
      +==============+==================================================================================================================================================================================================================================================+
      | <*hostName*> | Host IP address of the target DB instance to be connected. To obtain this parameter, go to the **Basic Information** page of the DB instance. The EIP can be found in the **Public IP Address (EIP)** field in the **Network Information** area. |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<port>*     | Database port. To obtain this parameter, go to the **Basic Information** page of the DB instance. The database port can be found in the **Database Port** field in the **Network Information** area.                                             |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*userName*> | Username of the TaurusDB administrator account. The default username is **root**.                                                                                                                                                                |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*caName*>   | SSL certificate file name, which should be stored in the same directory where the command is executed.                                                                                                                                           |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, to connect to a DB instance through an SSL connection as user **root**, run the following command:

   **mysql -h 10.16.0.31 -P 3306 -u root -p --ssl-ca=ca.pem**

   Enter the password of the database account as prompted:

   .. code-block::

      Enter password:

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Prerequisites <gaussdb_02_0014__en-us_topic_0172523144_en-us_topic_0154555358_en-us_topic_0153118658_section367520762117>` and try again.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352538904.png
