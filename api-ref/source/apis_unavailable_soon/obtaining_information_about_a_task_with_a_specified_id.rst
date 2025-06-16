:original_name: gaussdb_11_0032.html

.. _gaussdb_11_0032:

Obtaining Information About a Task with a Specified ID
======================================================

Function
--------

This API is used to obtain information about a TaurusDB task with a specified ID in the task center. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{endpoint}/mysql/v3/{project_id}/jobs?id={id}

-  URI example

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/jobs?id=a9767ede-fe0f-4888-9003-e843a4c90514

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | id                    | Yes                   | Task ID.                                                                   |
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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------------------+-------------------+
   | Parameter | Type                                                                                                     | Description       |
   +===========+==========================================================================================================+===================+
   | job       | :ref:`GetJobInfoDetail <gaussdb_11_0032__en-us_topic_0000001181084222_response_getjobinfodetail>` object | Task information. |
   +-----------+----------------------------------------------------------------------------------------------------------+-------------------+

.. _gaussdb_11_0032__en-us_topic_0000001181084222_response_getjobinfodetail:

.. table:: **Table 4** GetJobInfoDetail

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                     | Description                                                                                                                                     |
   +=======================+==========================================================================================================================+=================================================================================================================================================+
   | id                    | String                                                                                                                   | Task ID.                                                                                                                                        |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                                                   | Task name.                                                                                                                                      |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                                                   | Task execution status.                                                                                                                          |
   |                       |                                                                                                                          |                                                                                                                                                 |
   |                       |                                                                                                                          | Valid value:                                                                                                                                    |
   |                       |                                                                                                                          |                                                                                                                                                 |
   |                       |                                                                                                                          | -  **Running**: The task is being executed.                                                                                                     |
   |                       |                                                                                                                          | -  **Completed**: The task is successfully executed.                                                                                            |
   |                       |                                                                                                                          | -  **Failed**: The task fails to be executed.                                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | created               | String                                                                                                                   | Creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                             |
   |                       |                                                                                                                          |                                                                                                                                                 |
   |                       |                                                                                                                          | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                              |
   |                       |                                                                                                                          |                                                                                                                                                 |
   |                       |                                                                                                                          | The value is empty unless the instance creation is complete.                                                                                    |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | ended                 | String                                                                                                                   | End time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                  |
   |                       |                                                                                                                          |                                                                                                                                                 |
   |                       |                                                                                                                          | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                              |
   |                       |                                                                                                                          |                                                                                                                                                 |
   |                       |                                                                                                                          | The value is empty unless the instance creation is complete.                                                                                    |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | process               | String                                                                                                                   | Task execution progress. The execution progress (such as 60%) is displayed only when the task is being executed. Otherwise, **""** is returned. |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance              | :ref:`GetJobInstanceInfoDetail <gaussdb_11_0032__en-us_topic_0000001181084222_response_getjobinstanceinfodetail>` object | Instance information of the task with the specified ID.                                                                                         |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | :ref:`Table 6 <gaussdb_11_0032__table1014617554138>` object                                                              | Displayed information varies depending on tasks.                                                                                                |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                                                                                                                   | Task failure information.                                                                                                                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. _gaussdb_11_0032__en-us_topic_0000001181084222_response_getjobinstanceinfodetail:

.. table:: **Table 5** GetJobInstanceInfoDetail

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   id        String DB instance ID.
   name      String DB instance name.
   ========= ====== =================

.. _gaussdb_11_0032__table1014617554138:

.. table:: **Table 6** entities field data structure description

   +-----------------------+-----------------------+-----------------------------------------------------------------------+
   | Name                  | Type                  | Description                                                           |
   +=======================+=======================+=======================================================================+
   | instance              | Object                | DB instance queried in the task.                                      |
   |                       |                       |                                                                       |
   |                       |                       | For details, see :ref:`Table 7 <gaussdb_11_0032__table975183423611>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------+
   | resource_ids          | List<String>          | Resource ID involved in a task.                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------+

.. _gaussdb_11_0032__table975183423611:

.. table:: **Table 7** entities.instance field data structure description

   +-----------+--------+---------------------------------------------------------------------------------------+
   | Name      | Type   | Description                                                                           |
   +===========+========+=======================================================================================+
   | endpoint  | String | DB instance connection address.                                                       |
   +-----------+--------+---------------------------------------------------------------------------------------+
   | type      | String | DB instance type.                                                                     |
   +-----------+--------+---------------------------------------------------------------------------------------+
   | datastore | Object | DB information. For details, see :ref:`Table 8 <gaussdb_11_0032__table173094268581>`. |
   +-----------+--------+---------------------------------------------------------------------------------------+

.. _gaussdb_11_0032__table173094268581:

.. table:: **Table 8** datastore field data structure description

   ======= ====== ===========
   Name    Type   Description
   ======= ====== ===========
   type    String DB engine.
   version String DB version.
   ======= ====== ===========

.. table:: **Table 9** entities field data structure description (binding or unbinding an EIP)

   ========= ====== ==========================
   Name      Type   Description
   ========= ====== ==========================
   public_ip String EIP bound to the instance.
   ========= ====== ==========================

**Status code: 400**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Request
---------------

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/mysql/v3/0483b6b16e954cb88930a360d2c4e663/jobs?id=a9767ede-fe0f-4888-9003-e843a4c90514

Example Response
----------------

.. note::

   In the response example, some tasks in the task center are used as examples.

**Status code: 200**

Success.

.. code-block::

   {
     "job": {
       "id": "31b8ae23-c687-4d80-b7b4-42a66c9bb886",
       "name": " RestartGaussDBInstance",
       "status": "Completed",
       "created": "2018-08-06T10:41:14+0000",
       "ended": "2018-08-06T16:41:14+0000",
       "process": "",
       "instance": {
         "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
         "name": "DO-NOT-TOUCH-mgr2-taurusdb"
       },
       "entities": {}
       }
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
