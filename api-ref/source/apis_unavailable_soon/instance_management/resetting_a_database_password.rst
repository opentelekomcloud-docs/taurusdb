:original_name: gaussdb_11_0019.html

.. _gaussdb_11_0019:

Resetting a Database Password
=============================

Function
--------

This API is used to reset a database password. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   POST https://{endpoint}/mysql/v3/{project_id}/instances/{instance_id}/password

-  Example

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/c3ec2c6148ad4d71b1a8411a62df0d3cin07/password

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

.. table:: **Table 3** Request body parameter

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================================================+
   | password        | Yes             | String          | Database password.                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                         |
   |                 |                 |                 | Valid value:                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                         |
   |                 |                 |                 | The password consists of 8 to 32 characters and contains at least three types of the following: uppercase letters, lowercase letters, digits, and special characters (``~!@#$%^*-_=+?,()&``).                           |
   |                 |                 |                 |                                                                                                                                                                                                                         |
   |                 |                 |                 | You are advised to enter a strong password to improve security and prevent security risks such as brute force cracking. If you enter a weak password, the system automatically determines that the password is invalid. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

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

Resetting a database password

.. code-block:: text

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/password
   {
     "password" : "Test_345612"
   }

Example Response
----------------

{}

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
