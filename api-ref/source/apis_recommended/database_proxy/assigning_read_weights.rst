:original_name: SetGaussMySqlProxyWeight.html

.. _SetGaussMySqlProxyWeight:

Assigning Read Weights
======================

Function
--------

This API is used to assign read weights for nodes. Being using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

PUT /v3/{project_id}/instances/{instance_id}/proxy/{proxy_id}/weight

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+-------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                 |
   +=============+===========+========+=============================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region.                         |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | instance_id | Yes       | String | DB instance ID, which is compliant with the UUID format.    |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | proxy_id    | Yes       | String | Database proxy ID, which is compliant with the UUID format. |
   +-------------+-----------+--------+-------------------------------------------------------------+

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

   +----------------+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter      | Mandatory | Type                                                                                                                                                             | Description                              |
   +================+===========+==================================================================================================================================================================+==========================================+
   | master_weight  | No        | Integer                                                                                                                                                          | Weight of the primary node.              |
   +----------------+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | readonly_nodes | No        | Array of :ref:`TaurusModifyProxyWeightReadonlyNode <setgaussmysqlproxyweight__en-us_topic_0000001362641517_request_taurusmodifyproxyweightreadonlynode>` objects | Weight information of the read replicas. |
   +----------------+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+

.. _setgaussmysqlproxyweight__en-us_topic_0000001362641517_request_taurusmodifyproxyweightreadonlynode:

.. table:: **Table 4** TaurusModifyProxyWeightReadonlyNode

   ========= ========= ======= ===========================
   Parameter Mandatory Type    Description
   ========= ========= ======= ===========================
   id        No        String  Read replica ID.
   weight    No        Integer Weight of the read replica.
   ========= ========= ======= ===========================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

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

.. code-block::

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/e73893ef73754465a8bd2e0857bbf13ein07/proxy/e87088f0b6a345e79db19d57c41fde15po01/weight
   {
     "master_weight" : 100
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "04efe8e2-9255-44ae-a98b-d87c11411890"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
