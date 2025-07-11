:original_name: UpdateSqlFilterControl.html

.. _UpdateSqlFilterControl:

Enabling or Disabling SQL Statement Concurrency Control
=======================================================

Function
--------

This API is used to enable or disable SQL Statement Concurrency Control. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

POST /v3/{project_id}/instances/{instance_id}/sql-filter/switch

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                  |
   +=================+=================+=================+==============================================================+
   | switch_status   | Yes             | String          | Whether SQL Statement Concurrency Control is enabled. Value: |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | -  **ON**: enabled                                           |
   |                 |                 |                 | -  **OFF**: disabled                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+--------+-----------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                 |
   +===========+========+=============================================================================+
   | job_id    | String | ID of the task for enabling or disabling SQL Statement Concurrency Control. |
   +-----------+--------+-----------------------------------------------------------------------------+

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

-  Enabling SQL Statement Concurrency Control

   .. code-block:: text

      POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instance/af315b8e6aaa41799bd9a31f2de15abcin07/sql-filter/switch
      {
        "switch_status" : "ON"
      }

-  Disabling SQL Statement Concurrency Control

   .. code-block:: text

      POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instance/af315b8e6aaa41799bd9a31f2de15abcin07/sql-filter/switch
      {
        "switch_status" : "OFF"
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
