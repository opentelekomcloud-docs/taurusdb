:original_name: gaussdb_04_0001.html

.. _gaussdb_04_0001:

Querying Version Information About a DB Engine
==============================================

Function
--------

This API is used to query the version information of a specified DB engine. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/datastores/{database_name}

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                       |
   +=================+=================+=================+===================================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                               |
   |                 |                 |                 |                                                                                   |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+
   | database_name   | Yes             | String          | DB engine. The following DB engine is supported (case-insensitive): gaussdb-mysql |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   X-Language   No        String Language.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------+---------------------------------------------------------------------------------------------------+--------------+
   | Parameter  | Type                                                                                              | Description  |
   +============+===================================================================================================+==============+
   | datastores | Array of :ref:`MysqlEngineVersionInfo <gaussdb_04_0001__response_mysqlengineversioninfo>` objects | DB versions. |
   +------------+---------------------------------------------------------------------------------------------------+--------------+

.. _gaussdb_04_0001__response_mysqlengineversioninfo:

.. table:: **Table 4** MysqlEngineVersionInfo

   +-----------+--------+-------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                   |
   +===========+========+===============================================================================+
   | id        | String | DB version ID. Its value is unique.                                           |
   +-----------+--------+-------------------------------------------------------------------------------+
   | name      | String | DB version number. Only the major version number with two digits is returned. |
   +-----------+--------+-------------------------------------------------------------------------------+

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

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/datastores/gaussdb-mysql

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "datastores" : [ {
       "id" : "87620726-6802-46c0-9028-a8785e1f1921",
       "name" : "8.0"
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
