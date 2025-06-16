:original_name: gaussdb_04_0020.html

.. _gaussdb_04_0020:

Changing DB Instance Specifications
===================================

Function
--------

This API is used to change DB instance specifications. Before using this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

POST /v3/{project_id}/instances/{instance_id}/action

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | DB instance ID, which is compliant with the UUID format.                   |
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

   +---------------+-----------+------------------------------------------------------------------------------+-----------------------------------+
   | Parameter     | Mandatory | Type                                                                         | Description                       |
   +===============+===========+==============================================================================+===================================+
   | resize_flavor | Yes       | :ref:`MysqlResizeFlavor <gaussdb_04_0020__request_mysqlresizeflavor>` object | Specification change information. |
   +---------------+-----------+------------------------------------------------------------------------------+-----------------------------------+

.. _gaussdb_04_0020__request_mysqlresizeflavor:

.. table:: **Table 4** MysqlResizeFlavor

   ========= ========= ====== ===================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================
   spec_code Yes       String Specification code.
   ========= ========= ====== ===================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ========= ====== ===============================================
   Parameter Type   Description
   ========= ====== ===============================================
   job_id    String Job ID for changing DB instance specifications.
   ========= ====== ===============================================

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

Changing instance specifications

.. code-block::

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/ba62a0b83a1b42bfab275829d86ac0fdin07/action
   {
     "resize_flavor" : {
       "spec_code" : "gaussdb.mysql.xlarge.x86.8"
     }
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "dff1d289-4d03-4942-8b9f-463ea07c000d"
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
