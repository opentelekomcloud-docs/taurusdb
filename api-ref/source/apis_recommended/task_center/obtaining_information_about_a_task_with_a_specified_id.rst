:original_name: ShowGaussMySqlJobInfo.html

.. _ShowGaussMySqlJobInfo:

Obtaining Information About a Task with a Specified ID
======================================================

Function
--------

This API is used to obtain information about a TaurusDB task with a specified ID in the task center. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

Constraints
-----------

-  This API is used to query asynchronous tasks of the last one month in the task center.
-  After a job is generated, it takes several seconds to query the job ID.

URI
---

GET /v3/{project_id}/jobs?id={id}

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                |
   +=================+=================+=================+============================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region.                                        |
   |                 |                 |                 |                                                                            |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   id        Yes       String Task ID.
   ========= ========= ====== ===========

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

.. table:: **Table 4** Response body parameter

   +-----------+-----------------------------------------------------------------------------------+-------------------+
   | Parameter | Type                                                                              | Description       |
   +===========+===================================================================================+===================+
   | job       | :ref:`GetJobInfoDetail <showgaussmysqljobinfo__response_getjobinfodetail>` object | Task information. |
   +-----------+-----------------------------------------------------------------------------------+-------------------+

.. _showgaussmysqljobinfo__response_getjobinfodetail:

.. table:: **Table 5** GetJobInfoDetail

   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                              | Description                                                                                                                                                            |
   +=======================+===================================================================================================+========================================================================================================================================================================+
   | id                    | String                                                                                            | Task ID.                                                                                                                                                               |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                            | Task name.                                                                                                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                            | Task execution status.                                                                                                                                                 |
   |                       |                                                                                                   |                                                                                                                                                                        |
   |                       |                                                                                                   | Value:                                                                                                                                                                 |
   |                       |                                                                                                   |                                                                                                                                                                        |
   |                       |                                                                                                   | -  **Running**: The task is being executed.                                                                                                                            |
   |                       |                                                                                                   | -  **Completed**: The task is successfully executed.                                                                                                                   |
   |                       |                                                                                                   | -  **Failed**: The task fails to be executed.                                                                                                                          |
   |                       |                                                                                                   |                                                                                                                                                                        |
   |                       |                                                                                                   | Valid value:                                                                                                                                                           |
   |                       |                                                                                                   |                                                                                                                                                                        |
   |                       |                                                                                                   | -  **Running**                                                                                                                                                         |
   |                       |                                                                                                   | -  **Completed**                                                                                                                                                       |
   |                       |                                                                                                   | -  **Failed**                                                                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created               | String                                                                                            | Creation time in the "yyyy-mm-ddThh:mm:ssZ" format. **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
   |                       |                                                                                                   |                                                                                                                                                                        |
   |                       |                                                                                                   | The value is empty unless the DB instance creation is complete.                                                                                                        |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ended                 | String                                                                                            | End time in the "yyyy-mm-ddThh:mm:ssZ" format. **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.      |
   |                       |                                                                                                   |                                                                                                                                                                        |
   |                       |                                                                                                   | The value is empty unless the DB instance creation is complete.                                                                                                        |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | process               | String                                                                                            | Task execution progress. The execution progress (such as 60%) is displayed only when the task is being executed. Otherwise, **""** is returned.                        |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance              | :ref:`GetJobInstanceInfoDetail <showgaussmysqljobinfo__response_getjobinstanceinfodetail>` object | DB instance information of the task with the specified ID.                                                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                                                                                            | Displayed information varies depending on tasks.                                                                                                                       |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                                                                                            | Task failure information.                                                                                                                                              |
   +-----------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showgaussmysqljobinfo__response_getjobinstanceinfodetail:

.. table:: **Table 6** GetJobInstanceInfoDetail

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   id        String DB instance ID.
   name      String DB instance name.
   ========= ====== =================

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

.. code-block:: text

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/jobs?id=a9767ede-fe0f-4888-9003-e843a4c90514

Example Response
----------------

**Status code: 200**

.. note::

   In the response example, some tasks in the task center are used as examples.

Success.

.. code-block::

   {
     "job" : {
       "id" : "a9767ede-fe0f-4888-9003-e843a4c90514",
       "name" : "CreateMysqlInstance",
       "status" : "Completed",
       "created" : "2018-08-06T10:41:14+0800",
       "ended" : "2018-08-06T16:41:14+0000",
       "process" : "",
       "instance" : {
         "id" : "a48e43ff268f4c0e879652d65e63d0fbin07",
         "name" : "DO-NOT-TOUCH-mgr2-mysql-single"
       },
       "entities" : {
         "instance" : {
           "endpoint" : "192.168.1.203:3306",
           "type" : "Cluster",
           "datastore" : {
             "type" : "gaussdb-mysql",
             "version" : "8.0"
           }
         },
         "resource_ids" : [ "a48e43ff268f4c0e879652d65e63d0fbin07.vm", "a48e43ff268f4c0e879652d65e63d0fbin07.volume" ]
       }
     }
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
