:original_name: gaussdb_02_0006.html

.. _gaussdb_02_0006:

Overview
========

Scenarios
---------

This section describes how to create a DB instance on the management console and then connect to that instance through an ECS over a private network.

If you are using TaurusDB for the first time, see :ref:`Constraints <gaussdb_01_0008>`.

Process
-------

:ref:`Figure 1 <gaussdb_02_0006__fig138110377499>` illustrates the process of connecting to a DB instance over a private network.

.. _gaussdb_02_0006__fig138110377499:

.. figure:: /_static/images/en-us_image_0000001402979149.png
   :alt: **Figure 1** Connecting to a DB instance over a private network

   **Figure 1** Connecting to a DB instance over a private network

-  :ref:`Step 1: Create a DB instance. <gaussdb_02_0004>` Confirm the specifications, network, and database account configurations of the DB instance based on service requirements.
-  :ref:`Step 2: Configure security group rules. <gaussdb_02_0008>`

   -  If the ECS and DB instance are in the same security group, they can communicate with each other by default. No security group rule needs to be configured. Go to :ref:`Step 3: Connect to a DB Instance over a Private Network <gaussdb_02_0009>`.
   -  If the ECS and DB instance are in different security groups, you need to configure security group rules for the ECS and DB instance, respectively.

      -  DB instance: Configure an inbound rule for the security group associated with the DB instance.
      -  ECS: The default security group rule allows all outgoing data packets. In this case, you do not need to configure a security group rule for the ECS. If not all outbound traffic is allowed in the security group, you need to configure an outbound rule for the ECS.

-  :ref:`Step 3: Connect to a DB instance over a private network. <gaussdb_02_0009>` You can connect to the DB instance through a common connection, or an SSL connection for enhanced security. SSL connections are encrypted.
