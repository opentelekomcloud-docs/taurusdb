:original_name: ListInstanceTags.html

.. _ListInstanceTags:

Querying Resource Tags
======================

Function
--------

This API is used to query tags of a specified instance. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/tags

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

   +-------------+-------------------------------------------------------------------------------------------------------------------+--------------------------+
   | Parameter   | Type                                                                                                              | Description              |
   +=============+===================================================================================================================+==========================+
   | total_count | Integer                                                                                                           | Total number of records. |
   +-------------+-------------------------------------------------------------------------------------------------------------------+--------------------------+
   | tags        | Array of :ref:`ResourceTagItem <listinstancetags__en-us_topic_0000001244760821_response_resourcetagitem>` objects | Tag list.                |
   +-------------+-------------------------------------------------------------------------------------------------------------------+--------------------------+

.. _listinstancetags__en-us_topic_0000001244760821_response_resourcetagitem:

.. table:: **Table 5** ResourceTagItem

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   key       String Tag key.
   value     String Tag value.
   ========= ====== ===========

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

Querying resource tags

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/61a4ea66210545909d74a05c27a7179ein07/tags?offset=0&limit=2

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "total_count" : 2,
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value2"
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
