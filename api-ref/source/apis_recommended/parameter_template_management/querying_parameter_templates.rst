:original_name: gaussdb_04_0009.html

.. _gaussdb_04_0009:

Querying Parameter Templates
============================

Function
--------

This API is used to obtain parameter templates, including all databases' default and custom parameter templates. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/configurations

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                                                                           |
   +===========+===========+=========+=======================================================================================================================================================================================================================================+
   | offset    | No        | Integer | Index offset. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit     | No        | Integer | Number of records to be queried. The default value is **100**. The value must be a positive integer. The minimum value is **1** and the maximum value is **100**.                                                                     |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +----------------+-----------------------------------------------------------------------------------------------+--------------------------------------+
   | Parameter      | Type                                                                                          | Description                          |
   +================+===============================================================================================+======================================+
   | configurations | Array of :ref:`ConfigurationSummary <gaussdb_04_0009__response_configurationsummary>` objects | Parameter template information.      |
   +----------------+-----------------------------------------------------------------------------------------------+--------------------------------------+
   | total_count    | Integer                                                                                       | Total number of parameter templates. |
   +----------------+-----------------------------------------------------------------------------------------------+--------------------------------------+

.. _gaussdb_04_0009__response_configurationsummary:

.. table:: **Table 5** ConfigurationSummary

   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                        |
   +========================+=======================+====================================================================================================================+
   | id                     | String                | Parameter template ID.                                                                                             |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Parameter template name.                                                                                           |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | description            | String                | Parameter template description.                                                                                    |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | datastore_version_name | String                | Engine version                                                                                                     |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | datastore_name         | String                | Engine name.                                                                                                       |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | created                | String                | Creation time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                |
   |                        |                       |                                                                                                                    |
   |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | updated                | String                | Update time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                  |
   |                        |                       |                                                                                                                    |
   |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
   | user_defined           | Boolean               | Whether the parameter template is a custom template.                                                               |
   |                        |                       |                                                                                                                    |
   |                        |                       | -  **false**: The parameter template is a default template.                                                        |
   |                        |                       | -  **true**: The parameter template is a custom template.                                                          |
   +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

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

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/configurations

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "total_count" : 1,
     "configurations" : [ {
       "id" : "887ea0d1bb0843c49e8d8e5a09a95652pr07",
       "name" : "configuration_test",
       "description" : "configuration_test",
       "datastore_version_name" : "8.0",
       "datastore_name" : "GaussDB(for MySQL)",
       "created" : "2019-05-15T11:53:34+0000",
       "updated" : "2019-05-15T11:53:34+0000",
       "user_defined" : true
     }, {
       "id" : "3bc1e9cc0d34404b9225ed7a58fb284epr07",
       "name" : "Default-TaurusDB V2.0",
       "description" : "Default parameter template for TaurusDB",
       "datastore_version_name" : "8.0",
       "datastore_name" : "GaussDB(for MySQL)",
       "created" : "2019-05-27T03:38:51+0000",
       "updated" : "2019-05-27T03:38:51+0000",
       "user_defined" : false
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
