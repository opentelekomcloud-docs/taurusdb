:original_name: gaussdb_01_0008.html

.. _gaussdb_01_0008:

Constraints
===========

:ref:`Table 1 <gaussdb_01_0008__en-us_topic_0171122409_table60364850123535>` shows the constraints designed to ensure the stability and security of TaurusDB.

.. _gaussdb_01_0008__en-us_topic_0171122409_table60364850123535:

.. table:: **Table 1** Function constraints

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                          | Constraint                                                                                                                                                               |
   +===================================+==========================================================================================================================================================================+
   | TaurusDB access                   | -  If TaurusDB instances are not bound with EIPs, the instances must be in the same VPC subnet as the ECSs associated with these instances.                              |
   |                                   |                                                                                                                                                                          |
   |                                   | -  Security group rules must be added to allow ECSs to access TaurusDB instances.                                                                                        |
   |                                   |                                                                                                                                                                          |
   |                                   |    By default, a TaurusDB instance cannot be accessed by an ECS in a different security group. To allow it, you must add an inbound rule to the TaurusDB security group. |
   |                                   |                                                                                                                                                                          |
   |                                   | -  The default TaurusDB instance port is **3306**. You can change it if you want to access TaurusDB through another port.                                                |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deployment                        | ECSs in which TaurusDB instances are deployed are not visible to users. You can access TaurusDB instances only over an IP address and a port.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Administrator root permission     | Only the **root** user permissions are available on the instance creation page.                                                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database parameter modification   | Most parameters can be modified on the TaurusDB console.                                                                                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data migration                    | The mysqldump tool is used to migrate data to TaurusDB.                                                                                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | TaurusDB instance reboot          | TaurusDB instances cannot be rebooted through commands. They must be rebooted on the TaurusDB console.                                                                   |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | TaurusDB backup files             | TaurusDB backup files are stored in OBS buckets and are not visible to users.                                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
