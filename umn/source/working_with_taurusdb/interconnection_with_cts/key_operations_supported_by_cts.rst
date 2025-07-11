:original_name: gaussdb_03_0014.html

.. _gaussdb_03_0014:

Key Operations Supported by CTS
===============================

Cloud Trace Service (CTS) records operations related to TaurusDB for further querying, auditing, and backtracking. :ref:`Table 1 <gaussdb_03_0014__table81771041193510>` lists the supported operations.

.. _gaussdb_03_0014__table81771041193510:

.. table:: **Table 1** TaurusDB operations recorded by CTS

   +----------------------------------------------+----------------+-----------------------+
   | Operation                                    | Resource Type  | Trace Name            |
   +==============================================+================+=======================+
   | Creating a DB instance                       | instance       | createInstance        |
   +----------------------------------------------+----------------+-----------------------+
   | Creating a read replica                      | instance       | addNodes              |
   +----------------------------------------------+----------------+-----------------------+
   | Deleting a read replica                      | instance       | deleteNode            |
   +----------------------------------------------+----------------+-----------------------+
   | Rebooting a DB instance                      | instance       | restartInstance       |
   +----------------------------------------------+----------------+-----------------------+
   | Changing a database port                     | instance       | changeInstancePort    |
   +----------------------------------------------+----------------+-----------------------+
   | Changing a security group                    | instance       | modifySecurityGroup   |
   +----------------------------------------------+----------------+-----------------------+
   | Promoting a read replica to the primary node | instance       | instanceSwitchOver    |
   +----------------------------------------------+----------------+-----------------------+
   | Binding or unbinding an EIP                  | instance       | setOrResetPublicIP    |
   +----------------------------------------------+----------------+-----------------------+
   | Deleting a DB instance                       | instance       | deleteInstance        |
   +----------------------------------------------+----------------+-----------------------+
   | Renaming a DB instance                       | instance       | renameInstance        |
   +----------------------------------------------+----------------+-----------------------+
   | Changing a failover priority                 | instance       | modifyPriority        |
   +----------------------------------------------+----------------+-----------------------+
   | Modifying specifications                     | instance       | instanceAction        |
   +----------------------------------------------+----------------+-----------------------+
   | Resetting a password                         | instance       | resetPassword         |
   +----------------------------------------------+----------------+-----------------------+
   | Restoring data to a new DB instance          | instance       | restoreInstance       |
   +----------------------------------------------+----------------+-----------------------+
   | Creating a backup                            | backup         | createManualSnapshot  |
   +----------------------------------------------+----------------+-----------------------+
   | Deleting a backup                            | backup         | deleteManualSnapshot  |
   +----------------------------------------------+----------------+-----------------------+
   | Creating a parameter template                | parameterGroup | createParameterGroup  |
   +----------------------------------------------+----------------+-----------------------+
   | Modifying parameters in a parameter template | parameterGroup | updateParameterGroup  |
   +----------------------------------------------+----------------+-----------------------+
   | Deleting a parameter template                | parameterGroup | deleteParameterGroup  |
   +----------------------------------------------+----------------+-----------------------+
   | Replicating a parameter template             | parameterGroup | copyParameterGroup    |
   +----------------------------------------------+----------------+-----------------------+
   | Resetting a parameter template               | parameterGroup | resetParameterGroup   |
   +----------------------------------------------+----------------+-----------------------+
   | Comparing parameter templates                | parameterGroup | compareParameterGroup |
   +----------------------------------------------+----------------+-----------------------+
   | Applying a parameter template                | parameterGroup | applyParameterGroup   |
   +----------------------------------------------+----------------+-----------------------+
   | Deleting a task from the task center         | job            | deleteTaskCenterJob   |
   +----------------------------------------------+----------------+-----------------------+
