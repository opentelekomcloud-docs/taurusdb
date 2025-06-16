:original_name: ShowInstanceMonitorExtend.html

.. _ShowInstanceMonitorExtend:

Querying the Collection Period of Monitoring by Seconds
=======================================================

Function
--------

This API is used to query the collection period of Monitoring by Seconds. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/monitor-policy

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================+
   | monitor_switch        | Boolean               | Whether to enable Monitoring by Seconds. **true** indicates that the function is enabled, and **false** indicates that the function is disabled. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | period                | Integer               | Collection period. This parameter is returned only when **monitor_switch** is set to **true**.                                                   |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | -  **1**: The collection period is 1s.                                                                                                           |
   |                       |                       | -  **5**: The collection period is 5s.                                                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Request
---------------

Querying the collection period of Monitoring by Seconds for an instance

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/61a4ea66210545909d74a05c27a7179ein07/monitor-policy

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "monitor_switch" : true,
     "period" : "1"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
