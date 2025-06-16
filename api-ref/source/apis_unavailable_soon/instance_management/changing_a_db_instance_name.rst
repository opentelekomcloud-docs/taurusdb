:original_name: gaussdb_11_0018.html

.. _gaussdb_11_0018:

Changing a DB Instance Name
===========================

Function
--------

This API is used to change a DB instance name. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   PUT https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/name

-  Example

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/c3ec2c6148ad4d71b1a8411a62df0d3cin07/name

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                |
      +=================+=================+=================+============================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                        |
      |                 |                 |                 |                                                                            |
      |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | instance_id     | String          | Yes             | DB instance ID.                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================+
   | name            | Yes             | String          | Instance name.                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | Instances of the same type can have same names under the same tenant.                                                                                        |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | The value consists of 4 to 64 characters and starts with a letter. It is case-sensitive and contains only letters, digits, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameter

   ========= ====== ===============================================
   Parameter Type   Description
   ========= ====== ===============================================
   job_id    String ID of the task for changing a DB instance name.
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

Changing a DB instance name

.. code-block::

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/name

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
