:original_name: gaussdb_06_0006.html

.. _gaussdb_06_0006:

Modifying an Automated Backup Policy
====================================

Function
--------

This API is used to modify an automated backup policy. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

PUT /v3/{project_id}/instances/{instance_id}/backups/policy/update

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | DB instance ID, which is compliant with the UUID format.                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   X-Language   No        String Language.
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +---------------+-----------+------------------------------------------------------------------------------+-----------------------+
   | Parameter     | Mandatory | Type                                                                         | Description           |
   +===============+===========+==============================================================================+=======================+
   | backup_policy | Yes       | :ref:`MysqlBackupPolicy <gaussdb_06_0006__request_mysqlbackuppolicy>` object | Database information. |
   +---------------+-----------+------------------------------------------------------------------------------+-----------------------+

.. _gaussdb_06_0006__request_mysqlbackuppolicy:

.. table:: **Table 4** MysqlBackupPolicy

   +------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory       | Type            | Description                                                                                                                                                                                                                 |
   +==============================+=================+=================+=============================================================================================================================================================================================================================+
   | start_time                   | Yes             | String          | Backup time window. Automated backups will be triggered during the backup time window.                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                                                                                                     |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                                                                                                |
   |                              |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to **00**.                                                                                                                                              |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | Example value:                                                                                                                                                                                                              |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | 21:00-22:00                                                                                                                                                                                                                 |
   +------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keep_days                    | Yes             | Integer         | Backup retention days.                                                                                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | Value: **1** to **732**                                                                                                                                                                                                     |
   +------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period                       | Yes             | String          | Backup cycle configuration. Data will be automatically backed up on the selected days every week.                                                                                                                           |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | Value range: The value is a number separated by commas (,), indicating the days of the week.                                                                                                                                |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | For example, the value **1,2,3,4** indicates that the backup period is Monday, Tuesday, Wednesday, and Thursday.                                                                                                            |
   +------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | retention_num_backup_level-1 | No              | Integer         | Number of retained level-1 backups. The default value is **0**. This parameter is mandatory when the level-1 backup function is enabled. This parameter is unavailable when the level-1 backup function is disabled. Value: |
   |                              |                 |                 |                                                                                                                                                                                                                             |
   |                              |                 |                 | -  0                                                                                                                                                                                                                        |
   |                              |                 |                 | -  1                                                                                                                                                                                                                        |
   +------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+-------------------------------------------+
   | Parameter             | Type                  | Description                               |
   +=======================+=======================+===========================================+
   | status                | String                | Backup status. Value:                     |
   |                       |                       |                                           |
   |                       |                       | -  **BUILDING**: modification in progress |
   |                       |                       | -  **COMPLETED**: modification completed  |
   |                       |                       | -  **FAILED**: modification failed        |
   +-----------------------+-----------------------+-------------------------------------------+
   | instance_id           | String                | DB instance ID.                           |
   +-----------------------+-----------------------+-------------------------------------------+
   | instance_name         | String                | DB instance name.                         |
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

Modifying a backup policy

.. code-block::

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/backups/policy/update
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
     "instance_name" : "TaurusDB"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
