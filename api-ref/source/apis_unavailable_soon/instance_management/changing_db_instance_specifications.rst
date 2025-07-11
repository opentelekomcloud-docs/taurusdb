:original_name: gaussdb_11_0020.html

.. _gaussdb_11_0020:

Changing DB Instance Specifications
===================================

Function
--------

This API is used to change DB instance specifications. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   POST https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/action

-  Example

   POST https://gaussdb-mysql.eu-de.otc.t-systems.commysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/c3ec2c6148ad4d71b1a8411a62df0d3cin07/action

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                |
      +=================+=================+=================+============================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                        |
      |                 |                 |                 |                                                                            |
      |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | instance_id     | String          | No              | DB instance ID.                                                            |
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

   +---------------+-----------+-----------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter     | Mandatory | Type                                                                                                      | Description                       |
   +===============+===========+===========================================================================================================+===================================+
   | resize_flavor | Yes       | :ref:`MysqlResizeFlavor <gaussdb_11_0020__en-us_topic_0000001181084216_request_mysqlresizeflavor>` object | Specification change information. |
   +---------------+-----------+-----------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _gaussdb_11_0020__en-us_topic_0000001181084216_request_mysqlresizeflavor:

.. table:: **Table 4** MysqlResizeFlavor

   ========= ========= ====== ===================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================
   spec_code Yes       String Specification code.
   ========= ========= ====== ===================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                          |
   +===========+========+======================================================================================================================================================+
   | job_id    | String | Job ID for changing DB instance specifications. This parameter is returned only when you change the specifications of a pay-per-use DB instance.     |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | order_id  | String | Order ID for changing DB instance specifications. This parameter is returned only when you change the specification of a yearly/monthly DB instance. |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Changing instance specifications

.. code-block::

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/action

   {
     "resize_flavor" : {
       "spec_code" : "gaussdb.mysql.xlarge.x86.8"
     }
   }

Example Response
----------------

None

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
