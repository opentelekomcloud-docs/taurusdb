:original_name: gaussdb_11_0030.html

.. _gaussdb_11_0030:

Configuring Enterprise Project Resource Quotas of a Tenant
==========================================================

Function
--------

This API is used to configure resource quotas for a specified enterprise project. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   POST https://{endpoint}/mysql/v3/{project_id}/quotas

-  Example

   POST https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/quotas

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameter

   +------------+-----------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | Parameter  | Mandatory | Type                                                                                              | Description                                                        |
   +============+===========+===================================================================================================+====================================================================+
   | quota_list | Yes       | Array of :ref:`setQuota <gaussdb_11_0030__en-us_topic_0000001181562674_request_setquota>` objects | Quota details. Up to 10 quota records can be configured at a time. |
   +------------+-----------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------+

.. _gaussdb_11_0030__en-us_topic_0000001181562674_request_setquota:

.. table:: **Table 4** setQuota

   +-----------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type    | Description                                                                                                                                                                                       |
   +=======================+===========+=========+===================================================================================================================================================================================================+
   | enterprise_project_id | Yes       | String  | Enterprise project ID.                                                                                                                                                                            |
   +-----------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_quota        | Yes       | Integer | Quota of the DB instance quantity. The value ranges from **0** to **1000**. (If there are already instances created, this parameter value must be greater than the number of existing instances.) |
   +-----------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vcpus_quota           | Yes       | Integer | Quota of vCPUs. Value: **0** to **3600000**. (If there are already instances created, this parameter value must be greater than the number of used vCPUs.)                                        |
   +-----------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ram_quota             | Yes       | Integer | Memory quota in GB. Value: **0** to **19200000**. (If there are already instances created, this parameter value must be greater than the used memory size.)                                       |
   +-----------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameter

   +------------+----------------------------------------------------------------------------------------------------+------------------------+
   | Parameter  | Type                                                                                               | Description            |
   +============+====================================================================================================+========================+
   | quota_list | Array of :ref:`setQuota <gaussdb_11_0030__en-us_topic_0000001181562674_response_setquota>` objects | Resource list objects. |
   +------------+----------------------------------------------------------------------------------------------------+------------------------+

.. _gaussdb_11_0030__en-us_topic_0000001181562674_response_setquota:

.. table:: **Table 6** setQuota

   ===================== ======= ==================================
   Parameter             Type    Description
   ===================== ======= ==================================
   enterprise_project_id String  Enterprise project ID.
   instance_quota        Integer Quota of the DB instance quantity.
   vcpus_quota           Integer Quota of vCPUs.
   ram_quota             Integer Memory quota in GB.
   ===================== ======= ==================================

Example Request
---------------

None

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "quota_list" : [ {
       "enterprise_project_id" : "0",
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
