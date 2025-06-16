:original_name: BatchTagAction.html

.. _BatchTagAction:

Adding or Deleting Tags in Batches
==================================

Function
--------

This API is used to add tags to or delete tags from a specified DB instance in batches. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

POST /v3/{project_id}/instances/{instance_id}/tags/action

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------------------------+-----------------+
   | Parameter       | Mandatory       | Type                                                                                           | Description     |
   +=================+=================+================================================================================================+=================+
   | action          | Yes             | String                                                                                         | Action. Value:  |
   |                 |                 |                                                                                                |                 |
   |                 |                 |                                                                                                | -  **create**   |
   |                 |                 |                                                                                                | -  **delete**   |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+-----------------+
   | tags            | Yes             | Array of :ref:`TagItem <batchtagaction__en-us_topic_0000001200000942_request_tagitem>` objects | Tag list.       |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+-----------------+

.. _batchtagaction__en-us_topic_0000001200000942_request_tagitem:

.. table:: **Table 4** TagItem

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================+
   | key             | Yes             | String          | Tag key. It contains a maximum of 36 Unicode characters and cannot be null, an empty string, or a space. Only digits, uppercase letters, lowercase letters, underscores (_), and hyphens (-) are allowed.                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Tag value. It contains a maximum of 43 Unicode characters. It can be an empty string but cannot be a space. Only digits, uppercase letters, lowercase letters, underscores (_), periods (.), and hyphens (-) are allowed. |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | -  If **action** is set to **create**, this parameter is mandatory.                                                                                                                                                       |
   |                 |                 |                 | -  If **action** is set to **delete** and **value** is specified, tags are deleted by key and value. If **value** is not specified, tags are deleted by key.                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

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

-  Adding tags

   .. code-block::

      POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/61a4ea66210545909d74a05c27a7179ein07/tags/action
      {
        "action" : "create",
        "tags" : [ {
          "key" : "key1",
          "value" : "value1"
        }, {
          "key" : "key2",
          "value" : "value2"
        } ]
      }

-  Deleting tags

   .. code-block::

      POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/61a4ea66210545909d74a05c27a7179ein07/tags/action
      {
        "action" : "delete",
        "tags" : [ {
          "key" : "key1"
        }, {
          "key" : "key2",
          "value" : "value2"
        } ]
      }

Example Response
----------------

**Status code: 200**

Success.

None

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
