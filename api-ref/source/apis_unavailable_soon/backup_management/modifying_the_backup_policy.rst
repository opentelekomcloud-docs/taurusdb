:original_name: gaussdb_11_0025.html

.. _gaussdb_11_0025:

Modifying the Backup Policy
===========================

Function
--------

This API is used to modify the backup policy. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   PUT https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/backups/policy/update

-  Example

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/c3ec2c6148ad4d71b1a8411a62df0d3cin07/backups/policy/update

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                |
      +=================+=================+=================+============================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                        |
      |                 |                 |                 |                                                                            |
      |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | instance_id     | String          | No              | DB instance ID.                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                             |
   +==============+===========+========+=========================================================================================================================================================================================+
   | X-Auth-Token | No        | String | User token.                                                                                                                                                                             |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language   | No        | String | Language.                                                                                                                                                                               |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +---------------+-----------+-----------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter     | Mandatory | Type                                                                                                      | Description           |
   +===============+===========+===========================================================================================================+=======================+
   | backup_policy | Yes       | :ref:`MysqlBackupPolicy <gaussdb_11_0025__en-us_topic_0000001181402750_request_mysqlbackuppolicy>` object | Database information. |
   +---------------+-----------+-----------------------------------------------------------------------------------------------------------+-----------------------+

.. _gaussdb_11_0025__en-us_topic_0000001181402750_request_mysqlbackuppolicy:

.. table:: **Table 4** MysqlBackupPolicy

   +-----------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                   | Mandatory       | Type            | Description                                                                                                                                       |
   +=============================+=================+=================+===================================================================================================================================================+
   | start_time                  | Yes             | String          | Backup time window. Automated backups will be triggered during the backup time window.                                                            |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                           |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                      |
   |                             |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to **00**.                                                                    |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | Example value:                                                                                                                                    |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | **21:00-22:00**                                                                                                                                   |
   +-----------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | keep_days                   | Yes             | Integer         | Backup retention days.                                                                                                                            |
   +-----------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | period                      | Yes             | String          | Backup cycle configuration. Data will be automatically backed up on the selected days every week.                                                 |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | Value range: The value is a number separated by commas (,), indicating the days of the week.                                                      |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | For example, the value **1,2,3,4** indicates that the backup period is Monday, Tuesday, Wednesday, and Thursday.                                  |
   +-----------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | retention_num_backup_level1 | No              | Integer         | Number of retained level-1 backups. The default value is **0**. This parameter is valid when the level-1 backup function is enabled. Valid value: |
   |                             |                 |                 |                                                                                                                                                   |
   |                             |                 |                 | -  **0**                                                                                                                                          |
   |                             |                 |                 | -  **1**                                                                                                                                          |
   +-----------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+-------------------------------------------+
   | Parameter             | Type                  | Description                               |
   +=======================+=======================+===========================================+
   | status                | String                | Backup status. Value:                     |
   |                       |                       |                                           |
   |                       |                       | -  **BUILDING**: Modification in progress |
   |                       |                       | -  **COMPLETED**: Modification completed  |
   |                       |                       | -  **FAILED**: Modification failed        |
   +-----------------------+-----------------------+-------------------------------------------+
   | instance_id           | String                | Instance ID.                              |
   +-----------------------+-----------------------+-------------------------------------------+
   | instance_name         | String                | Instance name.                            |
   +-----------------------+-----------------------+-------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Request
---------------

Modifying the backup policy

.. code-block::

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/054e292c9880d4992f02c0196d3ea468/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/backups/policy/update

   {
     "backup_policy" : {
       "keep_days" : 7,
       "start_time" : "19:00-20:00",
       "period" : "1,2,3,4,5"
     }
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "status" : "COMPLETED",
     "instance_id" : "ef25188419f941309882d2986b2210b9in07",
     "instance_name" : "taurusdb"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
