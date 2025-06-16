:original_name: gaussdb_11_0024.html

.. _gaussdb_11_0024:

Querying an Automated Backup Policy
===================================

Function
--------

This API is used to query an automated backup policy. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/backups/policy

-  Example

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/c3ec2c6148ad4d71b1a8411a62df0d3cin07/backups/policy

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                |
      +=================+=================+=================+============================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                        |
      |                 |                 |                 |                                                                            |
      |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | instance_id     | String          | Yes             | DB instance ID.                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                             |
   +==============+===========+========+=========================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token.                                                                                                                                                                             |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language   | No        | String | Language.                                                                                                                                                                               |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +---------------+--------------------------------------------------------------------------------------------------+----------------------------+
   | Parameter     | Type                                                                                             | Description                |
   +===============+==================================================================================================+============================+
   | backup_policy | :ref:`BackupPolicy <gaussdb_11_0024__en-us_topic_0000001226563879_response_backuppolicy>` object | Backup policy information. |
   +---------------+--------------------------------------------------------------------------------------------------+----------------------------+

.. _gaussdb_11_0024__en-us_topic_0000001226563879_response_backuppolicy:

.. table:: **Table 4** BackupPolicy

   +------------+---------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type    | Description                                                                                       |
   +============+=========+===================================================================================================+
   | keep_days  | Integer | Backup retention days.                                                                            |
   +------------+---------+---------------------------------------------------------------------------------------------------+
   | start_time | String  | Backup time window. Automated backups will be triggered during the backup time window.            |
   +------------+---------+---------------------------------------------------------------------------------------------------+
   | period     | String  | Backup cycle configuration. Data will be automatically backed up on the selected days every week. |
   +------------+---------+---------------------------------------------------------------------------------------------------+

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

.. code-block::

   get https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/backups/policy

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
