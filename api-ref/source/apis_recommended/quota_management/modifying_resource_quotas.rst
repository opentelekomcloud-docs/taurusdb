:original_name: gaussdb_04_0013.html

.. _gaussdb_04_0013:

Modifying Resource Quotas
=========================

Function
--------

This API is used to modify the resource quota of a specified enterprise project.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

Precautions
-----------

Before using this API, ensure that the enterprise project has been enabled and you have the **gaussdb:quota:modify** permission.

URI
---

PUT /v3/{project_id}/quotas

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
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

   +------------+-----------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type                                                                 | Description                                                                                        |
   +============+===========+======================================================================+====================================================================================================+
   | quota_list | Yes       | Array of :ref:`setQuota <gaussdb_04_0013__request_setquota>` objects | Enterprise project resource quotas to be updated. A maximum of 10 quotas can be updated at a time. |
   +------------+-----------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+

.. _gaussdb_04_0013__request_setquota:

.. table:: **Table 4** setQuota

   +-------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory | Type    | Description                                                                                                                                                                          |
   +=========================+===========+=========+======================================================================================================================================================================================+
   | enterprise_project_id   | Yes       | String  | Enterprise project ID.                                                                                                                                                               |
   +-------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_name | Yes       | String  | Enterprise project name.                                                                                                                                                             |
   +-------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_quota          | Yes       | Integer | Quota of the DB instance quantity. Value: **0** to **100000**. (If there are already instances created, this parameter value must be greater than the number of existing instances.) |
   +-------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vcpus_quota             | Yes       | Integer | Quota of vCPUs. Value: **0** to **2147483646**. (If there are already instances created, this parameter value must be greater than the number of used vCPUs.)                        |
   +-------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ram_quota               | Yes       | Integer | Memory quota in GB. Value: **0** to **2147483646**. (If there are already instances created, this parameter value must be greater than the used memory size.)                        |
   +-------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +------------+-----------------------------------------------------------------------+-------------------------------+
   | Parameter  | Type                                                                  | Description                   |
   +============+=======================================================================+===============================+
   | quota_list | Array of :ref:`setQuota <gaussdb_04_0013__response_setquota>` objects | Configured quota information. |
   +------------+-----------------------------------------------------------------------+-------------------------------+

.. _gaussdb_04_0013__response_setquota:

.. table:: **Table 6** setQuota

   ======================= ======= ==================================
   Parameter               Type    Description
   ======================= ======= ==================================
   enterprise_project_id   String  Enterprise project ID.
   enterprise_project_name String  Enterprise project name.
   instance_quota          Integer Quota of the DB instance quantity.
   vcpus_quota             Integer Quota of vCPUs.
   ram_quota               Integer Memory quota in GB.
   ======================= ======= ==================================

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

.. code-block::

   PUT https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/quotas
   {
     "quota_list" : [ {
       "enterprise_project_id" : "0",
       "enterprise_project_name" : "default",
       "instance_quota" : 20,
       "vcpus_quota" : 20,
       "ram_quota" : 40
     } ]
   }

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "quota_list" : [ {
       "enterprise_project_id" : "0",
       "enterprise_project_name" : "default",
       "instance_quota" : 20,
       "vcpus_quota" : 20,
       "ram_quota" : 40
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
