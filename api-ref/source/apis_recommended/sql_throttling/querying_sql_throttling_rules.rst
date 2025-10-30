:original_name: ShowSqlFilterRule.html

.. _ShowSqlFilterRule:

Querying SQL Throttling Rules
=============================

Function
--------

This API is used to query SQL throttling rules. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/sql-filter/rules

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

.. table:: **Table 2** Query parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                        |
   +===========+===========+========+====================================================================================================================================================================================================+
   | node_id   | Yes       | String | Node ID.                                                                                                                                                                                           |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sql_type  | No        | String | SQL statements. The value can be **SELECT**, **UPDATE**, **DELETE**, or **INSERT** (case-insensitive). If this parameter is not specified, SQL throttling rules of all the statements are queried. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameter

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter        | Type                                                                                                           | Description           |
   +==================+================================================================================================================+=======================+
   | node_id          | String                                                                                                         | Node ID.              |
   +------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | sql_filter_rules | Array of :ref:`SqlFilterRule <showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrule>` objects | SQL throttling rules. |
   +------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+

.. _showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrule:

.. table:: **Table 5** SqlFilterRule

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Type                                                                                                                         | Description           |
   +=======================+==============================================================================================================================+=======================+
   | sql_type              | String                                                                                                                       | SQL statement type.   |
   |                       |                                                                                                                              |                       |
   |                       |                                                                                                                              | Valid value:          |
   |                       |                                                                                                                              |                       |
   |                       |                                                                                                                              | -  SELECT             |
   |                       |                                                                                                                              | -  UPDATE             |
   |                       |                                                                                                                              | -  DELETE             |
   |                       |                                                                                                                              | -  INSERT             |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | patterns              | Array of :ref:`SqlFilterRulePattern <showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrulepattern>` objects | SQL throttling rules. |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. _showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrulepattern:

.. table:: **Table 6** SqlFilterRulePattern

   =============== ======= ============================================
   Parameter       Type    Description
   =============== ======= ============================================
   pattern         String  SQL throttling rule.
   max_concurrency Integer Maximum number of concurrent SQL statements.
   cur_concurrency Integer Current number of concurrent requests.
   cur_reject      Integer Current number of interceptions.
   create_at       Long    Time when a SQL throttling rule was created.
   expire_at       Long    Time when a SQL throttling rule expires.
   =============== ======= ============================================

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

Querying SQL throttling rules

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instance/af315b8e6aaa41799bd9a31f2de15abcin07/sql-filter/rules?node_id=c01a5645eb2c4fb6a9373542f5366e50no07

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "node_id" : "c01a5645eb2c4fb6a9373542f5366e50no07",
     "sql_filter_rules" : [ {
       "sql_type" : "SELECT",
       "patterns" : [ {
         "pattern" : "select~from~t1",
         "max_concurrency" : 0,
         "cur_concurrency" : 0,
         "cur_reject" : 0,
         "create_at" : 1753254394,
         "expire_at" : 9223372036854775807
       }, {
         "pattern" : "select~from~t2~where~id",
         "max_concurrency" : 10,
         "cur_concurrency" : 0,
         "cur_reject" : 0,
         "create_at" : 1753254394,
         "expire_at" : 9223372036854775807
       } ]
     }, {
       "sql_type" : "UPDATE",
       "patterns" : [ {
         "pattern" : "update~t1",
         "max_concurrency" : 0,
         "cur_concurrency" : 0,
         "cur_reject" : 0,
         "create_at" : 1753254394,
         "expire_at" : 9223372036854775807
       }, {
         "pattern" : "update~t2~where~id",
         "max_concurrency" : 10,
         "cur_concurrency" : 0,
         "cur_reject" : 0,
         "create_at" : 1753254394,
         "expire_at" : 9223372036854775807
       } ]
     }, {
       "sql_type" : "DELETE",
       "patterns" : [ {
         "pattern" : "delete~from",
         "max_concurrency" : 0,
         "cur_concurrency" : 0,
         "cur_reject" : 0,
         "create_at" : 1753254394,
         "expire_at" : 9223372036854775807
       } ]
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
