:original_name: ShowGaussMySqlProjectQuotas.html

.. _ShowGaussMySqlProjectQuotas:

Querying the DB Instance Quotas of a Tenant
===========================================

Function
--------

This API is used to obtain the resource quotas of a specified tenant. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/project-quotas

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | type            | No              | String          | Resource type used to filter quotas. Its value can be **instance**. |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | Valid value:                                                        |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **instance**                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------------------+------------------------------------+
   | Parameter | Type                                                                                | Description                        |
   +===========+=====================================================================================+====================================+
   | quotas    | :ref:`project-quotas <showgaussmysqlprojectquotas__response_project-quotas>` object | Tenant instance quota information. |
   +-----------+-------------------------------------------------------------------------------------+------------------------------------+

.. _showgaussmysqlprojectquotas__response_project-quotas:

.. table:: **Table 5** project-quotas

   +-----------+-----------------------------------------------------------------------------------+------------------------+
   | Parameter | Type                                                                              | Description            |
   +===========+===================================================================================+========================+
   | resources | Array of :ref:`resource <showgaussmysqlprojectquotas__response_resource>` objects | Resource list objects. |
   +-----------+-----------------------------------------------------------------------------------+------------------------+

.. _showgaussmysqlprojectquotas__response_resource:

.. table:: **Table 6** resource

   +-----------------------+-----------------------+---------------------------------------------------+
   | Parameter             | Type                  | Description                                       |
   +=======================+=======================+===================================================+
   | type                  | String                | Quota of a specified type.                        |
   |                       |                       |                                                   |
   |                       |                       | -  **instance**: indicates the DB instance quota. |
   |                       |                       |                                                   |
   |                       |                       | Valid value:                                      |
   |                       |                       |                                                   |
   |                       |                       | -  **instance**                                   |
   +-----------------------+-----------------------+---------------------------------------------------+
   | used                  | Integer               | Number of created resources.                      |
   +-----------------------+-----------------------+---------------------------------------------------+
   | quota                 | Integer               | Maximum resource quota.                           |
   +-----------------------+-----------------------+---------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Request
---------------

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/project-quotas?type=instance

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "quotas" : {
       "resources" : [ {
         "type" : "instance,",
         "used" : "4,",
         "quota" : 50
       } ]
     }
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
