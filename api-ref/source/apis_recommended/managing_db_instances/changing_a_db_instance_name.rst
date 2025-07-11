:original_name: gaussdb_04_0018.html

.. _gaussdb_04_0018:

Changing a DB Instance Name
===========================

Function
--------

This API is used to change a DB instance name. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

PUT /v3/{project_id}/instances/{instance_id}/name

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

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                               |
   +===========+===========+========+===========================================================================================================================================================================================================================================================+
   | name      | Yes       | String | DB instance name. DB instances of the same type can have same names under the same tenant. The name consists of 4 to 64 characters and starts with a letter. It is case-sensitive and can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   job_id    String Task ID for changing a DB instance name.
   ========= ====== ========================================

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

Changing a DB Instance Name

.. code-block::

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/name
   {
     "name" : "taurusdb-name"
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "0f6b6a9e-bd39-4e95-9374-e4d134e5a3d1"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
