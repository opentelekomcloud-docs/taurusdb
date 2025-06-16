:original_name: gaussdb_04_0002.html

.. _gaussdb_04_0002:

Querying Database Specifications
================================

Function
--------

This API is used to query the database specifications of a specified DB engine version. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/flavors/{database_name}?availability_zone_mode={availability_zone_mode}

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | database_name   | Yes             | String          | DB engine.                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                                                                                           |
   +========================+=================+=================+=======================================================================================================================+
   | version_name           | No              | String          | DB version number. To obtain this value, see :ref:`Querying Version Information About a DB Engine <gaussdb_04_0001>`. |
   |                        |                 |                 |                                                                                                                       |
   |                        |                 |                 | Currently, only MySQL 8.0 is supported.                                                                               |
   +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | availability_zone_mode | Yes             | String          | AZ mode. Its value can be **single** or **multi** and is case-insensitive.                                            |
   +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | spec_code              | No              | String          | Specification code.                                                                                                   |
   +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   X-Language   No        String Language.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------+-----------------------------+
   | Parameter | Type                                                                                  | Description                 |
   +===========+=======================================================================================+=============================+
   | flavors   | Array of :ref:`MysqlFlavorsInfo <gaussdb_04_0002__response_mysqlflavorsinfo>` objects | DB instance specifications. |
   +-----------+---------------------------------------------------------------------------------------+-----------------------------+

.. _gaussdb_04_0002__response_mysqlflavorsinfo:

.. table:: **Table 5** MysqlFlavorsInfo

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                             |
   +=======================+=======================+=========================================================================================================================+
   | vcpus                 | String                | Number of vCPUs. For example, the value **1** indicates 1 vCPU.                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | ram                   | String                | Memory size in GB.                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Specification type. The value is **x86**.                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specification ID. The value must be unique.                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | spec_code             | String                | Resource specification code. Its value is same as the value of **flavor_ref**. Example: **gaussdb.mysql.xlarge.x86.8**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | version_name          | String                | DB version number.                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | instance_mode         | String                | DB instance type. Currently, its value can only be **Cluster**.                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | az_status             | Map<String,String>    | Specification status in an AZ.                                                                                          |
   |                       |                       |                                                                                                                         |
   |                       |                       | -  **normal**: The specifications are available.                                                                        |
   |                       |                       | -  **unsupported**: The specifications are not supported.                                                               |
   |                       |                       | -  **sellout**: The specifications are sold out.                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

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

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/flavors/gaussdb-mysql?version_name=8.0&spec_code=gaussdb.mysql.xlarge.x86.8&availability_zone_mode=single

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "flavors" : [ {
       "vcpus" : "4",
       "ram" : "32",
       "type" : "x86",
       "id" : "3169caaf-6c2f-41d5-aadd-c8fc3d83597e",
       "spec_code" : "gaussdb.mysql.xlarge.x86.8",
       "instance_mode" : "Cluster",
       "version_name" : "8.0",
       "az_status" : {
         "eu-de-01" : "normal",
         "eu-de-02" : "normal"
       }
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
