:original_name: UpdateInstanceConfigurations.html

.. _UpdateInstanceConfigurations:

Modifying Parameters of a Specified Instance
============================================

Function
--------

This API is used to modify parameters of a specified instance. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

PUT /v3/{project_id}/instances/{instance_id}/configurations

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | Instance ID, which uniquely identifies an instance.                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   X-Auth-Token Yes       String User token.
   Content-Type Yes       String Content type.
   ============ ========= ====== =============

.. table:: **Table 3** Request body parameter

   +------------------+-----------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type               | Description                                                                                                                                                                                                       |
   +==================+===========+====================+===================================================================================================================================================================================================================+
   | parameter_values | Yes       | Map<String,String> | Mapping between parameter names and parameter values. You can specify parameter values based on a default parameter template. If this parameter is not specified, the original parameter information is retained. |
   +------------------+-----------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                      |
   +=======================+=======================+==================================================================+
   | job_id                | String                | ID of the task for modifying parameters of a specified instance. |
   +-----------------------+-----------------------+------------------------------------------------------------------+
   | restart_required      | Boolean               | Whether a reboot is required.                                    |
   |                       |                       |                                                                  |
   |                       |                       | -  **true**: yes                                                 |
   |                       |                       |                                                                  |
   |                       |                       | -  **false**: no                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------+

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

Modifying parameters of a specified instance

.. code-block::

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/instances/3ef58db3986540d19f95151309368d34in07/configurations

   {
     "parameter_values" : {
       "max_user_connections" : "100"
     }
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "job_id" : "e5d698a9-d8db-47d2-bf75-3c9018f72b6f",
     "restart_required" : false
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
