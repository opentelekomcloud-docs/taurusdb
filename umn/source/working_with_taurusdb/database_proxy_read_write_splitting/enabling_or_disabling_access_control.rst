:original_name: gaussdb_11_0025.html

.. _gaussdb_11_0025:

Enabling or Disabling Access Control
====================================

If load balancing is enabled for a database proxy instance, the security group associated with the proxy instance does not apply. You need to use access control to grant access from specific IP addresses.

Enabling Access Control
-----------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. On the **Database Proxy** page, enable access control.

   Locate the target proxy instance and click |image2| next to the **Access Control** area.

#. Click **Configure**. In the displayed dialog box, configure the access control mode and IP addresses or CIDR blocks.

   -  **Access Control**: The blacklist and whitelist cannot be configured at the same time. If you switch between lists, your previously entered settings will be lost. IP addresses or CIDR blocks in the blacklist are not allowed to access proxy instances.
   -  **IP Address or CIDR Block**: Enter valid IP addresses or CIDR blocks that meet the following requirements:

      -  Each line contains an IP address or a CIDR block and ends with a line break.
      -  Each IP address or CIDR block can include a description separated by a vertical bar symbol (|), for example, **192.168.10.10|TaurusDB01**. The description can include up to 50 characters but cannot contain angle brackets (<>).
      -  Up to 300 IP addresses or CIDR blocks can be added.

Disabling Access Control
------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. On the **Database Proxy** page, disable access control.

   Locate the target proxy instance and click |image4| next to the **Access Control** area.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001405277053.png
.. |image3| image:: /_static/images/en-us_image_0000001352219100.png
.. |image4| image:: /_static/images/en-us_image_0000001405262769.png
