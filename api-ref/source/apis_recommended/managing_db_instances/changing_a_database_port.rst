:original_name: UpdateGaussMySqlInstancePort.html

.. _UpdateGaussMySqlInstancePort:

Changing a Database Port
========================

Function
--------

This API is used to change the database port of a DB instance. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

PUT /v3/{project_id}/instances/{instance_id}/port

.. table:: **Table 1** URI parameters

   =========== ========= ====== =====================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== =====================================
   project_id  Yes       String Project ID of a tenant in a region.
   instance_id Yes       String Instance ID of a tenant in a project.
   =========== ========= ====== =====================================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   X-Language   No        String Language.
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameter

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                |
   +=================+=================+=================+============================================================================================+
   | port            | Yes             | Integer         | Port number.                                                                               |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Value range: 1024 to 65535, excluding 5342 to 5345, 12017, 20000, 20201, 20202, and 33062. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameter

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

.. code-block:: text

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/056538411200d4cd2f79c003c7606412/instances/096c0fc43e804757b59946b80dc27f8bin07/port

   {
     "port" : 8836
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "e0fbbfc8-1ac4-4721-b9e9-7dd685c5bdd7"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
