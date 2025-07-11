:original_name: ShowSqlFilterRule.html

.. _ShowSqlFilterRule:

Querying Concurrency Control Rules of SQL Statements
====================================================

Function
--------

This API is used to query concurrency control rules of SQL statements. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/sql-filter/rules?node_id={node_id}

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

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                           |
   +===========+===========+========+=======================================================================================================================================================================================================+
   | node_id   | Yes       | String | Node ID.                                                                                                                                                                                              |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type      | No        | String | SQL statement type. The value can be **SELECT**, **UPDATE**, and **DELETE** (case-insensitive). If this parameter is not specified, concurrency control rules of all types of statements are queried. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +------------------+----------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter        | Type                                                                                                           | Description                                  |
   +==================+================================================================================================================+==============================================+
   | node_id          | String                                                                                                         | Node ID.                                     |
   +------------------+----------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | sql_filter_rules | Array of :ref:`SqlFilterRule <showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrule>` objects | Concurrency control rules of SQL statements. |
   +------------------+----------------------------------------------------------------------------------------------------------------+----------------------------------------------+

.. _showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrule:

.. table:: **Table 5** SqlFilterRule

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter             | Type                                                                                                                         | Description                                  |
   +=======================+==============================================================================================================================+==============================================+
   | sql_type              | String                                                                                                                       | SQL statement type.                          |
   |                       |                                                                                                                              |                                              |
   |                       |                                                                                                                              | Valid value:                                 |
   |                       |                                                                                                                              |                                              |
   |                       |                                                                                                                              | -  SELECT                                    |
   |                       |                                                                                                                              | -  UPDATE                                    |
   |                       |                                                                                                                              | -  DELETE                                    |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | patterns              | Array of :ref:`SqlFilterRulePattern <showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrulepattern>` objects | Concurrency control rules of SQL statements. |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+

.. _showsqlfilterrule__en-us_topic_0000001323591588_response_sqlfilterrulepattern:

.. table:: **Table 6** SqlFilterRulePattern

   =============== ======= =============================================
   Parameter       Type    Description
   =============== ======= =============================================
   pattern         String  A concurrency control rule of SQL statements.
   max_concurrency Integer Maximum number of concurrent SQL statements.
   =============== ======= =============================================

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

Querying concurrency control rules of SQL statements

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
         "max_concurrency" : 0
       }, {
         "pattern" : "select~from~t2~where~id",
         "max_concurrency" : 10
       } ]
     }, {
       "sql_type" : "UDPATE",
       "patterns" : [ {
         "pattern" : "update~t1",
         "max_concurrency" : 0
       }, {
         "pattern" : "update~t2~where~id",
         "max_concurrency" : 10
       } ]
     }, {
       "sql_type" : "DELETE",
       "patterns" : [ {
         "pattern" : "delete~from",
         "max_concurrency" : 0
       } ]
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
