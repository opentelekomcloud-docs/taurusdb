:original_name: gaussdb_faq_0011.html

.. _gaussdb_faq_0011:

How Can I Install the MySQL Client?
===================================

MySQL provides client installation packages for different OSs on its official website. Click `here <https://dev.mysql.com/downloads/mysql/8.0.html#downloads>`__ to download the MySQL 8.0 client installation package or click `here <http://downloads.mysql.com/archives/community/>`__ to download the packages of other versions. The following uses Red Hat Linux as an example to show how to obtain the required installation package and install it.

Procedure
---------

#. Obtain the installation package.

   Find the `link <https://dev.mysql.com/downloads/file/?id=496982>`__ to the required version on the download page. The mysql-community-client-8.0.21-1.el6.x86_64 is used as an example in the following.


   .. figure:: /_static/images/en-us_image_0000001352379056.png
      :alt: **Figure 1** Download

      **Figure 1** Download

   .. note::

      Click `No thanks, just start my download. <http://dev.mysql.com/get/Downloads/MySQL-8.0/mysql-community-client-8.0.21-1.el6.x86_64.rpm>`__ to download the installation package.

#. Upload the installation package to the ECS.

   .. note::

      When you create an ECS, select an OS, such as Red Hat 6.6, and bind an EIP to it. Then, upload the installation package to the ECS using a remote connection tool, and use PuTTY to connect to the ECS.

#. Run the following command to install the MySQL client:

   .. code-block::

      sudo rpm -ivh mysql-community-client-8.0.21-1.el6.x86_64.rpm

   .. note::

      -  If any conflicts occur during the installation, add the **replacefiles** parameter to the command and try to install the client again. Example:

         .. code-block::

            rpm -ivh --replacefiles mysql-community-client-8.0.21-1.el6.x86_64.rpm

      -  If a message is displayed prompting you to install a dependency package, you can add the **nodeps** parameter to the command and install the client again. Example:

         .. code-block::

            rpm -ivh --nodeps mysql-community-client-8.0.21-1.el6.x86_64.rpm
