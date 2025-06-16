:original_name: gaussdb_11_0015.html

.. _gaussdb_11_0015:

Creating a Read Replica
=======================

Function
--------

This API is used to create a read replica. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   POST https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/nodes/enlarge

-  Example

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/nodes/enlarge

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | instance_id           | Yes                   | Instance ID, which is compliant with the UUID format.                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameters

   +------------+-----------+-------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type              | Description                                                                                                              |
   +============+===========+===================+==========================================================================================================================+
   | priorities | Yes       | Array of integers | Read replica failover priority ranging from 1 to 16. The total number of the primary node and read replicas is up to 16. |
   +------------+-----------+-------------------+--------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                          |
   +=======================+=======================+======================================================================================+
   | instance_id           | String                | DB instance ID.                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | node_names            | Array of strings      | Node name list                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | job_id                | String                | ID of the task for creating a DB instance.                                           |
   |                       |                       |                                                                                      |
   |                       |                       | This parameter is returned only when pay-per-use DB instances are created.           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | order_id              | String                | Order ID. This parameter is returned only when yearly/monthly instances are created. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

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

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/nodes/enlarge

   {
     "priorities" : [ 1, 2 ]
   }

Example Response
----------------

**Status code: 201**

Success.

.. code-block::

   {
     "instance_id" : "f381d0b539e644df8f5b0d3a62129515in07",
     "node_names" : [ "taurusdb-ccf5_node03" ],
     "job_id" : "dff1d289-4d03-4942-8b9f-463ea07c000d"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
