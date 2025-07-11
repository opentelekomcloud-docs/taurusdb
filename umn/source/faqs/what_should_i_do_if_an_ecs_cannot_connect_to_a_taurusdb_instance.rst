:original_name: gaussdb_faq_0009.html

.. _gaussdb_faq_0009:

What Should I Do If an ECS Cannot Connect to a TaurusDB Instance?
=================================================================

Perform the following steps to identify the problem:

#. Check whether the ECS and DB instance are located in the same VPC.

   -  If they are in the same VPC, go to :ref:`2 <gaussdb_faq_0009__en-us_topic_0192953749_l76760374fb794a8d9b961321c13f386d>`.
   -  If they are in different VPCs, create an ECS in the VPC where the DB instance is located.

#. .. _gaussdb_faq_0009__en-us_topic_0192953749_l76760374fb794a8d9b961321c13f386d:

   Check whether a security group has been created for the ECS.

   -  If a security group has been created, check whether its configuration rules are suitable.

      For details, see security group description in :ref:`Step 1: Create a DB Instance <gaussdb_02_0004>`. Then, go to :ref:`3 <gaussdb_faq_0009__en-us_topic_0192953749_lbdf6c75fe0be4c37879e3354bc192d36>`.

   -  If no security group has been created, go to the VPC console from the ECS details page and create a security group.

#. .. _gaussdb_faq_0009__en-us_topic_0192953749_lbdf6c75fe0be4c37879e3354bc192d36:

   Check whether the ECS can connect to the DB instance over the instance port.

   The default port of the DB instance is **3306**.

   .. code-block::

      telnet <IP address> {Port number}

   -  If the ECS can connect to the DB instance port, the network between the ECS and the DB instance is normal.
   -  If the ECS cannot connect to the DB instance port, contact technical support.
