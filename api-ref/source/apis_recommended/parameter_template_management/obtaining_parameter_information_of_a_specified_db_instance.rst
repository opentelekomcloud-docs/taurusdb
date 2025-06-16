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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                         |
   +=================+=================+=================+=====================================================================================================+
   | project_id      | Yes             | String          | **Explanation**:                                                                                    |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | Project ID of a tenant in a region.                                                                 |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.                          |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | **Constraints**:                                                                                    |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | None                                                                                                |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | **Value range**:                                                                                    |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | The value can contain 32 characters. Only letters and digits are allowed.                           |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | **Default value**:                                                                                  |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | None                                                                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | **Explanation**:                                                                                    |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | Instance ID, which uniquely identifies an instance.                                                 |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | **Constraints**:                                                                                    |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | None                                                                                                |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | **Value range**:                                                                                    |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | The value can contain 36 characters with a suffix of **in07**. Only letters and digits are allowed. |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | **Default value**:                                                                                  |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | None                                                                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                           |
   +=================+=================+=================+=======================================================================================+
   | offset          | No              | Integer         | **Explanation**:                                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | Index offset. The query starts from the next piece of data indexed by this parameter. |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | **Constraints**:                                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | The value must be an integer and cannot be a negative number.                         |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | **Value range**:                                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | >=0                                                                                   |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | **Default value**:                                                                    |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | 0                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | **Explanation**:                                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | Number of records to be queried.                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | **Constraints**:                                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | The value must be an integer and cannot be a negative number.                         |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | **Value range**:                                                                      |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | 1-100                                                                                 |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | **Default value**:                                                                    |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | 100                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | **Explanation**:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | User token.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | To obtain this value, call the IAM API for `obtaining a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | The value of **X-Subject-Token** in the response header is the token value.                                                                       |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | **Constraints**:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | None                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | **Value range**:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | None                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | **Default value**:                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | None                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language      | No              | String          | **Explanation**:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Request language type.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | **Constraints**:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | None                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | **Value range**:                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  en-us                                                                                                                                          |
   |                 |                 |                 | -  zh-cn                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | **Default value**:                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | en-us                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter             | Type                                                                                                                                    | Description                              |
   +=======================+=========================================================================================================================================+==========================================+
   | configurations        | :ref:`ParameterConfigurationInfo <listinstanceconfigurations__en-us_topic_0000001731567853_response_parameterconfigurationinfo>` object | **Explanation**:                         |
   |                       |                                                                                                                                         |                                          |
   |                       |                                                                                                                                         | Instance parameter template information. |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | total_count           | Long                                                                                                                                    | **Explanation**:                         |
   |                       |                                                                                                                                         |                                          |
   |                       |                                                                                                                                         | Total number of instance parameters.     |
   |                       |                                                                                                                                         |                                          |
   |                       |                                                                                                                                         | **Value range**:                         |
   |                       |                                                                                                                                         |                                          |
   |                       |                                                                                                                                         | >=0                                      |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | parameter_values      | Array of :ref:`ParameterValuesInfo <listinstanceconfigurations__en-us_topic_0000001731567853_response_parametervaluesinfo>` objects     | **Explanation**:                         |
   |                       |                                                                                                                                         |                                          |
   |                       |                                                                                                                                         | Instance parameter information.          |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+

.. _listinstanceconfigurations__en-us_topic_0000001731567853_response_parameterconfigurationinfo:

.. table:: **Table 5** ParameterConfigurationInfo

   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                                                                                                           |
   +========================+=======================+=======================================================================================================================================================================================================+
   | datastore_version_name | String                | **Explanation**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | DB version name.                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **Value range**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | 2.0                                                                                                                                                                                                   |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datastore_name         | String                | **Explanation**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | DB engine name in the parameter template.                                                                                                                                                             |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **Value range**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | taurus                                                                                                                                                                                                |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created                | String                | **Explanation**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | Time when the parameter template was created. The format is "yyyy-mm-ddThh:mm:ssZ".                                                                                                                   |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **Value range**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | None                                                                                                                                                                                                  |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated                | String                | **Explanation**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | Time when the parameter template was updated. The format is "yyyy-mm-ddThh:mm:ssZ".                                                                                                                   |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | **Value range**:                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                       |
   |                        |                       | None                                                                                                                                                                                                  |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listinstanceconfigurations__en-us_topic_0000001731567853_response_parametervaluesinfo:

.. table:: **Table 6** ParameterValuesInfo

   +-----------------------+-----------------------+-------------------------------------+
   | Parameter             | Type                  | Description                         |
   +=======================+=======================+=====================================+
   | name                  | String                | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Parameter name.                     |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | None                                |
   +-----------------------+-----------------------+-------------------------------------+
   | value                 | String                | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Parameter value.                    |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | None                                |
   +-----------------------+-----------------------+-------------------------------------+
   | restart_required      | Boolean               | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Whether a reboot is required.       |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | -  **false**: No                    |
   |                       |                       | -  **true**: Yes                    |
   +-----------------------+-----------------------+-------------------------------------+
   | readonly              | Boolean               | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Whether the parameter is read-only. |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | -  **false**: No                    |
   |                       |                       | -  **true**: Yes                    |
   +-----------------------+-----------------------+-------------------------------------+
   | value_range           | String                | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Value range.                        |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | None                                |
   +-----------------------+-----------------------+-------------------------------------+
   | type                  | String                | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Parameter type.                     |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | -  string                           |
   |                       |                       | -  integer                          |
   |                       |                       | -  boolean                          |
   |                       |                       | -  list                             |
   |                       |                       | -  float                            |
   +-----------------------+-----------------------+-------------------------------------+
   | description           | String                | **Explanation**:                    |
   |                       |                       |                                     |
   |                       |                       | Parameter description.              |
   |                       |                       |                                     |
   |                       |                       | **Value range**:                    |
   |                       |                       |                                     |
   |                       |                       | None                                |
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
