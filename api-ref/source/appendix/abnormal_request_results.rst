:original_name: gaussdb_10_0001.html

.. _gaussdb_10_0001:

Abnormal Request Results
========================

-  Abnormal response description

   .. table:: **Table 1** Abnormal response description

      +------------+--------+---------------------------------------------------------------------------------------------------------------------+
      | Name       | Type   | Description                                                                                                         |
      +============+========+=====================================================================================================================+
      | error_code | String | Returned error code when a task submission exception occurs. For details, see :ref:`Error Codes <gaussdb_10_0003>`. |
      +------------+--------+---------------------------------------------------------------------------------------------------------------------+
      | error_msg  | String | Returned error description when a task submission exception occurs.                                                 |
      +------------+--------+---------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      {
          "error_code": "DBS.280234",
          "error_msg": "Invalid DB instance name."
      }
