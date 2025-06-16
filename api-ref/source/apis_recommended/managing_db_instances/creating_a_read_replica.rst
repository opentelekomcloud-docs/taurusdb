:original_name: gaussdb_04_0015.html

.. _gaussdb_04_0015:

Creating a Read Replica
=======================

Function
--------

This API is used to create a read replica. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

POST /v3/{project_id}/instances/{instance_id}/nodes/enlarge

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

   +------------+-----------+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type              | Description                                                                                                                                                                                                                                                                                                                                          |
   +============+===========+===================+======================================================================================================================================================================================================================================================================================================================================================+
   | priorities | Yes       | Array of integers | Failover priority of a read replica. Failover priority ranges from 1 for the first priority to 16 for the last priority. This priority determines the order in which read replicas are promoted when recovering from a primary node failure. Read replicas with the same priority have a same probability of being promoted to the new primary node. |
   +------------+-----------+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                 |
   +=======================+=======================+=============================================================================+
   | instance_id           | String                | DB instance ID.                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | node_names            | Array of strings      | Node name list                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | job_id                | String                | Read replica creation task ID.                                              |
   |                       |                       |                                                                             |
   |                       |                       | This parameter is returned only when a pay-per-use read replica is created. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+

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

Creating a read replica

.. code-block::

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/nodes/enlarge
   {
     "priorities" : [ 1, 2 ]
   }

Example Response
----------------

**Status code: 201**

Success.

.. code-block::

   {
     "instance_id" : "ba62a0b83a1b42bfab275829d86ac0fdin07",
     "node_names" : [ "taurusdb-ccf5_node03" ],
     "job_id" : "dff1d289-4d03-4942-8b9f-463ea07c000d"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
