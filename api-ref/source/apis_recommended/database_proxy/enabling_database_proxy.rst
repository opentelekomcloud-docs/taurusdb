:original_name: CreateGaussMySqlProxy.html

.. _CreateGaussMySqlProxy:

Enabling Database Proxy
=======================

Function
--------

This API is used to enable database proxy in ELB mode. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

POST /v3/{project_id}/instances/{instance_id}/proxy

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

   +-------------------+-----------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type                                                                             | Description                                                                                                                                                                                                                                                  |
   +===================+=================+==================================================================================+==============================================================================================================================================================================================================================================================+
   | flavor_ref        | Yes             | String                                                                           | Proxy specification code.                                                                                                                                                                                                                                    |
   +-------------------+-----------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_num          | Yes             | Integer                                                                          | Number of proxy instance nodes. The value is an integer from 2 to 32.                                                                                                                                                                                        |
   +-------------------+-----------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | proxy_name        | No              | String                                                                           | Proxy instance name. DB instances of the same type can have same names under the same tenant. The name consists of 4 to 64 characters and starts with a letter. It is case-sensitive and can contain only letters, digits, hyphens (-), and underscores (_). |
   +-------------------+-----------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | proxy_mode        | No              | String                                                                           | Proxy instance type. The default type is **readwrite**.                                                                                                                                                                                                      |
   |                   |                 |                                                                                  |                                                                                                                                                                                                                                                              |
   |                   |                 |                                                                                  | Valid value:                                                                                                                                                                                                                                                 |
   |                   |                 |                                                                                  |                                                                                                                                                                                                                                                              |
   |                   |                 |                                                                                  | -  **readwrite**                                                                                                                                                                                                                                             |
   |                   |                 |                                                                                  | -  **readonly**                                                                                                                                                                                                                                              |
   +-------------------+-----------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | nodes_read_weight | No              | Array of :ref:`NodesWeight <creategaussmysqlproxy__request_nodesweight>` objects | Read weight of the node.                                                                                                                                                                                                                                     |
   |                   |                 |                                                                                  |                                                                                                                                                                                                                                                              |
   |                   |                 |                                                                                  | If **proxy_mode** is set to **readonly**, you can assign weights only for read replicas.                                                                                                                                                                     |
   +-------------------+-----------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _creategaussmysqlproxy__request_nodesweight:

.. table:: **Table 4** NodesWeight

   +-----------+-----------+---------+--------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                            |
   +===========+===========+=========+========================================================+
   | id        | No        | String  | Node ID.                                               |
   +-----------+-----------+---------+--------------------------------------------------------+
   | weight    | No        | Integer | Weight assigned to the node. Value: **0** to **1000**. |
   +-----------+-----------+---------+--------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

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

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/43e4feaab48f11e89039fa163ebaa7e4br01/proxy
   {
     "flavor_ref" : "gaussdb.mysql.large.x86.4",
     "node_num" : 2,
     "proxy_name" : "taurusdb-proxy",
     "proxy_mode" : "readonly",
     "nodes_read_weight" : [ {
       "id" : "45021bf73a244312a3f2af95092feeecno07",
       "weight" : 50
     }, {
       "id" : "d78a65690cea4af5ad14585e110ff89bno07",
       "weight" : 400
     } ]
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
