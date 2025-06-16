:original_name: ShowGaussMySqlProxyFlavors.html

.. _ShowGaussMySqlProxyFlavors:

Querying Database Proxy Specifications
======================================

Function
--------

This API is used to query database proxy specifications. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.
-  Database proxy is unavailable for DB instances in a DeC.

URI
---

GET /v3/{project_id}/instances/{instance_id}/proxy/flavors

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | DB instance ID.                                                            |
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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +---------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------+
   | Parameter           | Type                                                                                                         | Description                      |
   +=====================+==============================================================================================================+==================================+
   | proxy_flavor_groups | Array of :ref:`MysqlProxyFlavorGroups <showgaussmysqlproxyflavors__response_mysqlproxyflavorgroups>` objects | Specification group information. |
   +---------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------+

.. _showgaussmysqlproxyflavors__response_mysqlproxyflavorgroups:

.. table:: **Table 4** MysqlProxyFlavorGroups

   +---------------+----------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter     | Type                                                                                                           | Description                                  |
   +===============+================================================================================================================+==============================================+
   | group_type    | String                                                                                                         | Specification group type. It can be **x86**. |
   +---------------+----------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | proxy_flavors | Array of :ref:`MysqlProxyComputeFlavor <showgaussmysqlproxyflavors__response_mysqlproxycomputeflavor>` objects | Proxy specifications.                        |
   +---------------+----------------------------------------------------------------------------------------------------------------+----------------------------------------------+

.. _showgaussmysqlproxyflavors__response_mysqlproxycomputeflavor:

.. table:: **Table 5** MysqlProxyComputeFlavor

   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                                |
   +===========+========+============================================================================================================================================================================+
   | vcpus     | String | Number of vCPUs. For example, the value **1** indicates 1 vCPU.                                                                                                            |
   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ram       | String | Memory size in GB.                                                                                                                                                         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | db_type   | String | Database type.                                                                                                                                                             |
   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id        | String | Proxy specification ID.                                                                                                                                                    |
   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | spec_code | String | Proxy specification code.                                                                                                                                                  |
   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | az_status | Object | AZ status. **key** indicates the AZ ID and **value** indicates the status of the AZ where the proxy specifications reside. The value can be **normal** or **unsupported**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/096c0fc43e804757b59946b80dc27f8bin07/proxy/flavors

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "proxy_flavor_groups" : {
       "group_type" : "X86",
       "proxy_flavors" : {
         "id" : "19be4c5d-d363-3342-bdbc-0dd9dbf7fafe",
         "spec_code" : "gaussdb.proxy.large.x86.2",
         "vcpus" : 2,
         "ram" : 4,
         "db_type" : "Proxy",
         "az_status" : {
           "az1" : "normal"
         },
         "region_status" : "normal"
       }
     }
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
