:original_name: UpdateInstanceMonitor.html

.. _UpdateInstanceMonitor:

Changing the Collection Period of Monitoring by Seconds
=======================================================

Function
--------

This API is used to enable and disable Monitoring by Seconds, and change its collection period. Before calling this API, you can:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

PUT /v3/{project_id}/instances/{instance_id}/monitor-policy

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | DB instance ID.                                                            |
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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================+
   | monitor_switch  | Yes             | Boolean         | Whether to enable Monitoring by Seconds. **true** indicates that the function is enabled, and **false** indicates that the function is disabled.                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period          | No              | Integer         | Collection period. This parameter is available only when **monitor_switch** is set to **true**. The default value is **5s**. This parameter is not displayed when **monitor_switch** is set to **false**. |
   |                 |                 |                 |                                                                                                                                                                                                           |
   |                 |                 |                 | **1**: indicates that the collection period is 1s. **5**: indicates that the collection period is 5s.                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                           |
   |                 |                 |                 | Valid value:                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                           |
   |                 |                 |                 | -  **1**                                                                                                                                                                                                  |
   |                 |                 |                 | -  **5**                                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ===============================================
   Parameter Type   Description
   ========= ====== ===============================================
   job_id    String Taskflow ID for modifying Monitoring by Seconds
   ========= ====== ===============================================

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

Modifying the collection period of Monitoring by Seconds for an instance. The current collection period to 1s.

.. code-block::

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/61a4ea66210545909d74a05c27a7179ein07/monitor-policy
   {
     "monitor_switch" : true,
     "period" : 1
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "6b7dd5d4-4590-4f14-b164-a8737ce071d5"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
