:original_name: gaussdb_11_0016.html

.. _gaussdb_11_0016:

Deleting a Read Replica
=======================

Function
--------

This API is used to delete a read replica. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   DELETE https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/nodes/{node_id}

-  Example

   DELETE https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/nodes/d11ae66fsfdsaer3w3ino9

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | instance_id           | Yes                   | DB instance ID, which is compliant with the UUID format.                   |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | node_id               | Yes                   | Read-only node ID, which is compliant with the UUID format.                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                             |
   +==============+===========+========+=========================================================================================================================================================================================+
   | X-Auth-Token | No        | String | User token.                                                                                                                                                                             |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language   | No        | String | Language.                                                                                                                                                                               |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   ========= ====== ===========================================
   Parameter Type   Description
   ========= ====== ===========================================
   job_id    String ID of the task for deleting a read replica.
   ========= ====== ===========================================

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

.. code-block:: text

   DELETE https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/instances/3d39c18788b54a919bab633874c159dfin01/nodes/ss62c18799854a919bab633874c159dfin55

Example Response
----------------

**Status code: 500**

Server error.

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
