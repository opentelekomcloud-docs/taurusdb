:original_name: gaussdb_06_0005.html

.. _gaussdb_06_0005:

Querying an Automated Backup Policy
===================================

Function
--------

This API is used to query an automated backup policy. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/backups/policy

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +---------------+---------------------------------------------------------------------+----------------------------+
   | Parameter     | Type                                                                | Description                |
   +===============+=====================================================================+============================+
   | backup_policy | :ref:`BackupPolicy <gaussdb_06_0005__response_backuppolicy>` object | Backup policy information. |
   +---------------+---------------------------------------------------------------------+----------------------------+

.. _gaussdb_06_0005__response_backuppolicy:

.. table:: **Table 4** BackupPolicy

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                         |
   +=======================+=======================+=====================================================================================================+
   | keep_days             | Integer               | Backup retention days. Value: **1** to **732**                                                      |
   |                       |                       |                                                                                                     |
   |                       |                       | Minimum value: **1**                                                                                |
   |                       |                       |                                                                                                     |
   |                       |                       | Maximum value: **732**                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | start_time            | String                | Backup time window. Automated backups will be triggered during the backup time window.              |
   |                       |                       |                                                                                                     |
   |                       |                       | The value must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | period                | String                | Backup cycle configuration. Data will be automatically backed up on the selected days every week.   |
   |                       |                       |                                                                                                     |
   |                       |                       | Value range: The value is a number separated by commas (,), indicating the days of the week.        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Request
---------------

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/61a4ea66210545909d74a05c27a7179ein07/backups/policy

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "backup_policy" : {
       "keep_days" : "7,",
       "start_time" : "19:00-20:00",
       "period" : "1,2"
      }
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
