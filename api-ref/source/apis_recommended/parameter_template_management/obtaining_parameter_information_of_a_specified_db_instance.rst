:original_name: ListInstanceConfigurations.html

.. _ListInstanceConfigurations:

Obtaining Parameter Information of a Specified DB Instance
==========================================================

Function
--------

This API is used to obtain parameter information of a specified DB instance. Before calling this API:

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` it.
-  Obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

GET /v3/{project_id}/instances/{instance_id}/configurations

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

.. table:: **Table 2** Query parameters

   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                                                                               |
   +===========+===========+=========+===========================================================================================================================================================================================================================================+
   | offset    | No        | Integer | Index offset. If **offset** is set to *N*, the resource query starts from the *N*\ +1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit     | No        | Integer | Number of records to be queried. The default value is **100**. The value must be a positive integer. The minimum value is **1** and the maximum value is **100**.                                                                         |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameter

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter        | Type                                                                                                                                    | Description                              |
   +==================+=========================================================================================================================================+==========================================+
   | configurations   | :ref:`ParameterConfigurationInfo <listinstanceconfigurations__en-us_topic_0000001731567853_response_parameterconfigurationinfo>` object | Instance parameter template information. |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | total_count      | Long                                                                                                                                    | Total number of instance parameters.     |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | parameter_values | Array of :ref:`ParameterValuesInfo <listinstanceconfigurations__en-us_topic_0000001731567853_response_parametervaluesinfo>` objects     | Instance parameter information.          |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+

.. _listinstanceconfigurations__en-us_topic_0000001731567853_response_parameterconfigurationinfo:

.. table:: **Table 5** ParameterConfigurationInfo

   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                                                                                                           |
   +========================+=======================+=======================================================================================================================================================================================================+
   | datastore_version_name | String                | DB version name.                                                                                                                                                                                      |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datastore_name         | String                | DB engine name in the parameter template.                                                                                                                                                             |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | configuration_id       | String                | Parameter template ID.                                                                                                                                                                                |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created                | String                | Time when the parameter template was created. The format is "yyyy-mm-ddThh:mm:ssZ".                                                                                                                   |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated                | String                | Time when the parameter template was updated. The format is "yyyy-mm-ddThh:mm:ssZ".                                                                                                                   |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listinstanceconfigurations__en-us_topic_0000001731567853_response_parametervaluesinfo:

.. table:: **Table 6** ParameterValuesInfo

   +-----------------------+-----------------------+-------------------------------------+
   | Parameter             | Type                  | Description                         |
   +=======================+=======================+=====================================+
   | name                  | String                | Parameter name.                     |
   +-----------------------+-----------------------+-------------------------------------+
   | value                 | String                | Parameter value.                    |
   +-----------------------+-----------------------+-------------------------------------+
   | restart_required      | Boolean               | Whether a reboot is required.       |
   |                       |                       |                                     |
   |                       |                       | -  **false**: no                    |
   |                       |                       | -  **true**: yes                    |
   +-----------------------+-----------------------+-------------------------------------+
   | readonly              | Boolean               | Whether the parameter is read-only. |
   |                       |                       |                                     |
   |                       |                       | -  **false**: no                    |
   |                       |                       | -  **true**: yes                    |
   +-----------------------+-----------------------+-------------------------------------+
   | value_range           | String                | Value range.                        |
   +-----------------------+-----------------------+-------------------------------------+
   | type                  | String                | Parameter type.                     |
   |                       |                       |                                     |
   |                       |                       | -  string                           |
   |                       |                       | -  integer                          |
   |                       |                       | -  boolean                          |
   |                       |                       | -  list                             |
   |                       |                       | -  float                            |
   +-----------------------+-----------------------+-------------------------------------+
   | description           | String                | Parameter description.              |
   +-----------------------+-----------------------+-------------------------------------+

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

Obtaining parameter information of a specified DB instance

.. code-block::

   GET https://gaussdb-mysql.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/61a4ea66210545909d74a05c27a7179ein07/configurations

Example Response
----------------

**Status code: 200**

Success.

.. code-block::

   {
     "configurations" : {
       "datastore_version_name" : "2.0",
       "datastore_name" : "taurus",
       "configuration_id": "f35d2c4501944225bc96ef8d20ece2bcpr07",
       "created" : "2022-10-29T09:38:36+0000",
       "updated" : "2022-10-29T09:38:36+0000"
     },
     "total_count" : 125,
     "parameter_values" : [ {
       "name" : "auto_increment_increment",
       "value" : "1",
       "restart_required" : false,
       "readonly" : false,
       "value_range" : "1-65535",
       "type" : "integer",
       "description": auto_increment_increment and auto_increment_offset are used for master-to-master replication and to control the operations of the AUTO_INCREMENT column.
     }, {
       "name" : "auto_increment_offset",
       "value" : "1",
       "restart_required" : false,
       "readonly" : false,
       "value_range" : "1-65535",
       "type" : "integer",
       "description": auto_increment_increment and auto_increment_offset are used for master-to-master replication and to control the operations of the AUTO_INCREMENT column.
     } ]
   }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.
