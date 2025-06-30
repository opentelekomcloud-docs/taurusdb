:original_name: gaussdb_faq_0005.html

.. _gaussdb_faq_0005:

Does TaurusDB Support Automatic Failover?
=========================================

During the creation of a TaurusDB instance, a primary node and a read replica are both created. If the primary node fails, the system automatically fails over to a read replica with the highest priority and the original primary node is restored in the background.
