:original_name: DeleteSqlFilterRule.html

.. _DeleteSqlFilterRule:

Deleting Concurrency Control Rules of SQL Statements
====================================================

Function
--------

This API is used to delete concurrency control rules of SQL statements. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

DELETE /v3/{project_id}/instances/{instance_id}/sql-filter/rules

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | Instance ID.                                                               |
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

.. table:: **Table 3** Request body parameters

   +------------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Parameter        | Mandatory | Type                                                                                                                                        | Description                                            |
   +==================+===========+=============================================================================================================================================+========================================================+
   | sql_filter_rules | Yes       | Array of :ref:`DeleteNodeSqlFilterRuleInfo <deletesqlfilterrule__en-us_topic_0000001323271972_request_deletenodesqlfilterruleinfo>` objects | Concurrency control rules of SQL statements for nodes. |
   +------------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+

.. _deletesqlfilterrule__en-us_topic_0000001323271972_request_deletenodesqlfilterruleinfo:

.. table:: **Table 4** DeleteNodeSqlFilterRuleInfo

   +-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter | Mandatory | Type                                                                                                                                | Description                                  |
   +===========+===========+=====================================================================================================================================+==============================================+
   | node_id   | Yes       | String                                                                                                                              | Node ID.                                     |
   +-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | rules     | Yes       | Array of :ref:`DeleteNodeSqlFilterRule <deletesqlfilterrule__en-us_topic_0000001323271972_request_deletenodesqlfilterrule>` objects | Concurrency control rules of SQL statements. |
   +-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+

.. _deletesqlfilterrule__en-us_topic_0000001323271972_request_deletenodesqlfilterrule:

.. table:: **Table 5** DeleteNodeSqlFilterRule

   +-----------------+-----------------+------------------+----------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                  |
   +=================+=================+==================+==============================================+
   | sql_type        | Yes             | String           | SQL statement type.                          |
   |                 |                 |                  |                                              |
   |                 |                 |                  | Valid value:                                 |
   |                 |                 |                  |                                              |
   |                 |                 |                  | -  SELECT                                    |
   |                 |                 |                  | -  UPDATE                                    |
   |                 |                 |                  | -  DELETE                                    |
   +-----------------+-----------------+------------------+----------------------------------------------+
   | patterns        | Yes             | Array of strings | Concurrency control rules of SQL statements. |
   +-----------------+-----------------+------------------+----------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +-----------+--------+--------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                              |
   +===========+========+==========================================================================+
   | job_id    | String | ID of the task for deleting concurrency control rules of SQL statements. |
   +-----------+--------+--------------------------------------------------------------------------+

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

Deleting concurrency control rules of SQL statements

.. code-block::

   DELETE https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instance/af315b8e6aaa41799bd9a31f2de15abcin07/sql-filter/rules
   {
     "sql_filter_rules" : [ {
       "node_id" : "c01a5645eb2c4fb6a9373542f5366e50no07",
       "rules" : [ {
         "sql_type" : "SELECT",
         "patterns" : [ "select~from~t1", "select~from~t2" ]
       }, {
         "sql_type" : "UPDATE",
         "patterns" : [ "udpate~t3~where~id" ]
       } ]
     }, {
       "node_id" : "b234a5645eb2c4ji3b9372342f5362397no07",
       "rules" : [ {
         "sql_type" : "SELECT",
         "patterns" : [ "select~from~t1", "select~from~t2" ]
       }, {
         "sql_type" : "DELETE",
         "patterns" : [ "delete~t3~where~id" ]
       } ]
     } ]
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "aef6a470-fb63-4d5b-b644-12ead7e019b3"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
