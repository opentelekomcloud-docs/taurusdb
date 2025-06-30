:original_name: gaussdb_faq_0010.html

.. _gaussdb_faq_0010:

How Do I Import the SSL Certificate of an RDS Instance to a Windows or Linux Server?
====================================================================================

Importing the Certificate to a Windows Server
---------------------------------------------

#. Click **Start** and choose **Run**. In the displayed **Run** dialog box, enter **MMC** and press **Enter**.
#. On the displayed console, choose **File** > **Add/Remove Snap-in**.
#. In the left **Available snap-ins** pane of the displayed **Add or Remove Snap-ins** dialog box, select **Certificates** and click **Add**.
#. In the displayed **Certificates snap-in** dialog box, select **Computer account** and click **Next**.
#. In the displayed **Select Computer** dialog box, click **Finish**.
#. In the **Add or Remove Snap-ins** dialog box, click **OK**.
#. On the console, double-click **Certificates**.
#. Right-click **Trusted Root Certification Authorities** and choose **All Tasks** > **Import**.
#. In the displayed **Certificate Import Wizard** dialog box, click **Next**.
#. Click **Browse** to change the file type to **All Files (*.*)**.
#. Locate the downloaded root certificate ca.pem file and click **Open**. Then, click **Next**.

   .. important::

      You must change the file type to **All Files (*.*)** because **.pem** is not a standard certificate extension name.

#. Click **Next**.
#. Click **Finish**.
#. Click **OK** to complete the import of the root certificate.

Importing the Certificate to a Linux Server
-------------------------------------------

You can use a connection tool (such as WinSCP or PuTTY) to upload the certificate to any directory on a Linux server.

Example:


.. figure:: /_static/images/en-us_image_0000001460761526.png
   :alt: **Figure 1** Importing a certificate

   **Figure 1** Importing a certificate
