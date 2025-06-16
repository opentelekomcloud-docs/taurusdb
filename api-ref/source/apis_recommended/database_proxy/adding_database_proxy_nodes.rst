:original_name: ExpandGaussMySqlProxy.html

.. _ExpandGaussMySqlProxy:

Adding Database Proxy Nodes
===========================

Function
--------

This API is used to add database proxy nodes.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.
-  Database proxy is unavailable for DB instances in a DeC.

URI
---

POST /v3/{project_id}/instances/{instance_id}/proxy/enlarge

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

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                  |
   +===========+===========+=========+==============================================================================================================================================================================+
   | node_num  | Yes       | Integer | The number of proxy nodes to be added. The value is an integer from 1 to 30. Restrictions: The total number of proxy nodes for an instance is no more than 32.               |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | proxy_id  | No        | String  | ID of the proxy instance. If only one proxy instance is created, this parameter is not required. If multiple proxy instances are created, you must configure this parameter. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

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

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/61a4ea66210545909d74a05c27a7179ein07/proxy/enlarge
   {
     "node_num" : 2,
     "proxy_id" : "151c14381ac14ecfb9703a745b992677po01"
   }

Example Response
----------------

**Status code: 201**

Success.

.. code-block::

   {
     "job_id" : "04efe8e2-9255-44ae-a98b-d87cae411890"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
