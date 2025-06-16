:original_name: ListGaussMySqlSlowLog.html

.. _ListGaussMySqlSlowLog:

Querying Database Slow Logs
===========================

Function
--------

This API is used to query database slow logs. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/slowlog?start_date={start_date}&end_date={end_date}&node_id={node_id}

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
   |                 |                 |                 | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset.                                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_date        | Yes             | String          | End time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | Only error logs generated within the last month can be queried.                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Index offset. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of records to be queried. The default value is **100**. The value must be a positive integer. The minimum value is **1** and the maximum value is **100**.                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Statement type. The default value **All**. If this parameter is left empty, all statement types are queried. Valid value:                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | -  ALL                                                                                                                                                                                                                                |
   |                 |                 |                 | -  INSERT                                                                                                                                                                                                                             |
   |                 |                 |                 | -  UPDATE                                                                                                                                                                                                                             |
   |                 |                 |                 | -  SELECT                                                                                                                                                                                                                             |
   |                 |                 |                 | -  DELETE                                                                                                                                                                                                                             |
   |                 |                 |                 | -  CREATE                                                                                                                                                                                                                             |
   |                 |                 |                 | -  DROP                                                                                                                                                                                                                               |
   |                 |                 |                 | -  ALTER                                                                                                                                                                                                                              |
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

   +-----------------+---------------------------------------------------------------------------------------------+---------------------------+
   | Parameter       | Type                                                                                        | Description               |
   +=================+=============================================================================================+===========================+
   | slow_log_list   | Array of :ref:`MysqlSlowLogList <listgaussmysqlslowlog__response_mysqlslowloglist>` objects | Error log details.        |
   +-----------------+---------------------------------------------------------------------------------------------+---------------------------+
   | long_query_time | String                                                                                      | Slow query log threshold. |
   +-----------------+---------------------------------------------------------------------------------------------+---------------------------+
   | total_record    | Integer                                                                                     | Total number of records.  |
   +-----------------+---------------------------------------------------------------------------------------------+---------------------------+

.. _listgaussmysqlslowlog__response_mysqlslowloglist:

.. table:: **Table 5** MysqlSlowLogList

   ============= ====== ===================================
   Parameter     Type   Description
   ============= ====== ===================================
   node_id       String Node ID.
   count         String Number of executions.
   time          String Execution time.
   lock_time     String Lock wait time.
   rows_sent     String Number of sent rows.
   rows_examined String Number of scanned rows.
   database      String Database which slow logs belong to.
   users         String Account.
   query_sample  String Execution syntax.
   type          String Statement type.
   start_time    String Start time in the UTC format.
   client_ip     String IP address.
   ============= ====== ===================================

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

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/096c0fc43e804757b59946b80dc27f8bin07/slowlog?offset=0&limit=1&start_date=2022-07-10T00:00:00+0800&end_date=2022-07-19T00:00:00+0800&node_id=cc07c60e94ec4575989840e648fb4f66no07&type=INSERT

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "slow_log_list" : [ {
       "node_id" : "cc07c60e94ec4575989840e648fb4f66no07",
       "count" : 1,
       "time" : "1.04899 s",
       "lock_time" : "0.00003 s",
       "rows_sent" : 0,
       "rows_examined" : 0,
       "database" : "gaussdb-mysql",
       "users" : "root",
       "query_sample" : "INSERT INTO time_zone_name (Name, Time_zone_id) VALUES (N @time_zone_id);",
       "type" : "INSERT",
       "start_time" : "2022-07-11T00:00:00+0800",
       "client_ip" : "192.*.*.1"
     } ],
     "long_query_time" : 10,
     "total_record" : 1
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
