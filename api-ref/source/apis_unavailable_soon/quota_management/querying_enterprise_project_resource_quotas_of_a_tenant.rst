:original_name: gaussdb_11_0029.html

.. _gaussdb_11_0029:

Querying Enterprise Project Resource Quotas of a Tenant
=======================================================

Function
--------

This API is used to obtain the resource quotas of a specified enterprise project. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{endpoint}/mysql/v3/{project_id}/quotas

-  Example

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/619d3e78f61b4be68bc5aa0b59edcf7b/quotas

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                    | Mandatory             | Description                                                                                                                                                                                                                           |
      +=========================+=======================+=======================================================================================================================================================================================================================================+
      | project_id              | Yes                   | Project ID of a tenant in a region.                                                                                                                                                                                                   |
      |                         |                       |                                                                                                                                                                                                                                       |
      |                         |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.                                                                                                                                                            |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                  | No                    | Index offset. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                   | No                    | Number of records to be queried. The default value is **10**. The value must be a positive integer. The minimum value is **1** and the maximum value is **100**.                                                                      |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_name | No                    | Enterprise project name.                                                                                                                                                                                                              |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                             |
   +==============+===========+========+=========================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token.                                                                                                                                                                             |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language   | No        | String | Language.                                                                                                                                                                               |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+----------------------------------------------------------------------------------------------+--------------------------+
   | Parameter   | Type                                                                                         | Description              |
   +=============+==============================================================================================+==========================+
   | quota_list  | Array of :ref:`quota <gaussdb_11_0029__en-us_topic_0000001181402752_response_quota>` objects | Quota information list.  |
   +-------------+----------------------------------------------------------------------------------------------+--------------------------+
   | total_count | Integer                                                                                      | Number of quota records. |
   +-------------+----------------------------------------------------------------------------------------------+--------------------------+

.. _gaussdb_11_0029__en-us_topic_0000001181402752_response_quota:

.. table:: **Table 4** quota

   =========================== ======= ==================================
   Parameter                   Type    Description
   =========================== ======= ==================================
   enterprise_project_id       String  Enterprise project ID.
   enterprise_project_name     String  Enterprise project name.
   instance_quota              Integer Quota of the DB instance quantity.
   vcpus_quota                 Integer Quota of vCPUs.
   ram_quota                   Integer Memory quota in GB.
   availability_instance_quota Integer Remaining quota of DB instances.
   availability_vcpus_quota    Integer Remaining quota of vCPUs.
   availability_ram_quota      Integer Remaining memory quota.
   =========================== ======= ==================================

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

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/619d3e78f61b4be68bc5aa0b59edcf7b/quotas

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
       "ram_quota" : 40,
       "availability_instance_quota" : 1,
       "availability_vcpus_quota" : 4,
       "availability_ram_quota" : 8
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
