:original_name: DeleteGaussMySqlBackup.html

.. _DeleteGaussMySqlBackup:

Deleting a Manual Backup
========================

Function
--------

This API is used to delete a manual backup. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

DELETE /v3/{project_id}/backups/{backup_id}

.. table:: **Table 1** URI parameters

   ========== ========= ====== ===================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================================
   project_id Yes       String Project ID of a tenant in a region.
   backup_id  Yes       String Backup file ID.
   ========== ========= ====== ===================================

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

.. table:: **Table 3** Response body parameter

   =========== ====== ============
   Parameter   Type   Description
   =========== ====== ============
   backup_id   String Backup ID.
   backup_name String Backup name.
   =========== ====== ============

**Status code: 400**

.. table:: **Table 4** Response body parameter

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 5** Response body parameter

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Request
---------------

.. code-block:: text

   DELETE https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/backups/1fe4feaab48f11e6654hfa163eba87e4b66

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "backup_id" : "b1182ccdda034f2b9535f3dca5c47e71br07",
     "backup_name" : "backup-f3c1"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
