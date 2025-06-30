:original_name: quick_start.html

.. _quick_start:

Connecting to a DB Instance
===========================

You can connect a DB instance over a private or public network.

.. table:: **Table 1** Connection methods

   +-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Connect Through | Connection Address | Scenarios                                                                                                                                                                                     | Description                                                                                                                                                                                                                  |
   +=================+====================+===============================================================================================================================================================================================+==============================================================================================================================================================================================================================+
   | Private network | Private IP address | The system provides a private IP address by default.                                                                                                                                          | -  Secure and excellent performance                                                                                                                                                                                          |
   |                 |                    |                                                                                                                                                                                               | -  Recommended                                                                                                                                                                                                               |
   |                 |                    | When your applications are deployed on an ECS that is in the same region and VPC as the DB instance, you are advised to connect to the DB instance through the ECS over a private IP address. |                                                                                                                                                                                                                              |
   +-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Public network  | EIP                | If you cannot access a DB instance over a private IP address, bind an EIP to the DB instance and connect it to an ECS (or a public network host) over the EIP.                                | -  A relatively Low lower level of security compared to the other two connection modes.                                                                                                                                      |
   |                 |                    |                                                                                                                                                                                               | -  To achieve a higher data transmission rate and security level, you are advised to migrate your applications to an ECS that is in the same VPC as your DB instance and use a private IP address to access the DB instance. |
   +-----------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  VPC: indicates the Virtual Private Cloud.
   -  ECS: indicates the Elastic Cloud Server.
   -  If the ECS is in the same VPC as the DB instance, you do not need to apply for an EIP.
