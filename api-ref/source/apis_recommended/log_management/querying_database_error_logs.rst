:original_name: ListGaussMySqlErrorLog.html

.. _ListGaussMySqlErrorLog:

Querying Database Error Logs
============================

Function
--------

This API is used to query database error logs. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/errorlog?start_date={start_date}&end_date={end_date}&node_id={node_id}

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

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================================================================+
   | start_date      | Yes             | String          | Start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_date        | Yes             | String          | End time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | Only error logs generated within the last month can be queried.                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Index offset. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of records to be queried. The default value is **100**. The value must be a positive integer. The minimum value is **1** and the maximum value is **100**.                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | level           | No              | String          | Log level. The default value is **ALL**. Valid value:                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | -  ALL                                                                                                                                                                                                                                |
   |                 |                 |                 | -  INFO                                                                                                                                                                                                                               |
   |                 |                 |                 | -  WARNING                                                                                                                                                                                                                            |
   |                 |                 |                 | -  ERROR                                                                                                                                                                                                                              |
   |                 |                 |                 | -  FATAL                                                                                                                                                                                                                              |
   |                 |                 |                 | -  NOTE                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_id         | Yes             | String          | Node ID.                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +----------------+------------------------------------------------------------------------------------------------+--------------------------+
   | Parameter      | Type                                                                                           | Description              |
   +================+================================================================================================+==========================+
   | error_log_list | Array of :ref:`MysqlErrorLogList <listgaussmysqlerrorlog__response_mysqlerrorloglist>` objects | Error log details.       |
   +----------------+------------------------------------------------------------------------------------------------+--------------------------+
   | total_record   | Integer                                                                                        | Total number of records. |
   +----------------+------------------------------------------------------------------------------------------------+--------------------------+

.. _listgaussmysqlerrorlog__response_mysqlerrorloglist:

.. table:: **Table 5** MysqlErrorLogList

   +-----------------------+-----------------------+-------------------------+
   | Parameter             | Type                  | Description             |
   +=======================+=======================+=========================+
   | node_id               | String                | Node ID.                |
   +-----------------------+-----------------------+-------------------------+
   | time                  | String                | Time in the UTC format. |
   +-----------------------+-----------------------+-------------------------+
   | level                 | String                | Log level.              |
   |                       |                       |                         |
   |                       |                       | -  ALL                  |
   |                       |                       | -  INFO                 |
   |                       |                       | -  WARNING              |
   |                       |                       | -  ERROR                |
   |                       |                       | -  FATAL                |
   |                       |                       | -  NOTE                 |
   +-----------------------+-----------------------+-------------------------+
   | content               | String                | Error log content.      |
   +-----------------------+-----------------------+-------------------------+

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

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/096c0fc43e804757b59946b80dc27f8bin07/errorlog?offset=0&limit=1&level=ERROR&start_date=2022-07-10T00:00:00+0800&end_date=2022-07-19T00:00:00+0800&node_id=cc07c60e94ec4575989840e648fb4f66no07

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "error_log_list" : [ {
       "node_id" : "cc07c60e94ec4575989840e648fb4f66no07",
       "time" : "2022-07-17T07:34:33",
       "level" : "ERROR",
       "content" : "[MY013508] [Repl] do failed: 1"
     } ],
    "total_record":1
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
