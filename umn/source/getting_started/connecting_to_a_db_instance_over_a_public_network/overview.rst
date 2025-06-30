:original_name: gaussdb_02_0016.html

.. _gaussdb_02_0016:

Overview
========

Scenarios
---------

This section describes how to create a DB instance on the management console and bind an EIP to the DB instance to make the instance publicly accessible.

If you are using TaurusDB for the first time, see :ref:`Constraints <gaussdb_01_0008>`.

Process
-------

:ref:`Figure 1 <gaussdb_02_0016__fig138110377499>` illustrates the process of connecting to a DB instance over a public network.

.. _gaussdb_02_0016__fig138110377499:

.. figure:: /_static/images/en-us_image_0000001352379000.png
   :alt: **Figure 1** Connecting to a DB instance over a public network

   **Figure 1** Connecting to a DB instance over a public network

-  :ref:`Step 1: Create a DB instance. <gaussdb_02_0012>` Confirm the specifications, network, and database account configurations of the DB instance based on service requirements.
-  :ref:`Step 2: Bind an EIP. <gaussdb_02_0015>` The Elastic IP service provides independent public IP addresses and bandwidth for public access. You can apply for an EIP on the VPC console and bind the EIP to the DB instance.
-  :ref:`Step 3: Configure security group rules. <gaussdb_02_0013>` To access a DB instance from resources outside the security group, you need to configure an inbound rule for the security group associated with the DB instance.
-  :ref:`Step 4: Connect to a DB instance over a public network. <gaussdb_02_0014>` You can connect to a DB instance through a common connection, or an SSL connection for enhanced security. SSL connections are encrypted.
