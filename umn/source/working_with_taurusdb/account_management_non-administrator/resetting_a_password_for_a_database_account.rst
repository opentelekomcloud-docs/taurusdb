:original_name: gaussdbformysql_03_0133.html

.. _gaussdbformysql_03_0133:

Resetting a Password for a Database Account
===========================================

Scenarios
---------

You can reset passwords for the accounts you have created. To protect your DB instance against brute force cracking, change your password periodically, such as every three or six months.

Constraints
-----------

This operation is not allowed when another operation is being performed on your DB instance.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Databases**, click **TaurusDB**.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane, choose **Accounts**. On the displayed page, locate the target username and click **Reset Password** in the **Operation** column.

#. In the displayed dialog box, enter a new password and confirm it.

   The password must meet the following requirements:

   -  It must consist of 8 to 32 characters.

   -  It must contain at least three types of the following characters: uppercase letters, lowercase letters, digits, and special characters (``~!@#%^*-_=+?,()&$``).

   -  It must comply with the values of **validate_password** parameters.

      To check the parameter values, click a DB instance name, choose **Parameters** in the navigation pane, and search for **validate_password** in the upper right corner of the page.

   -  The password you entered in the **Confirm Password** text box must be the same as that you entered in the **New Password** text box.
   -  It cannot be the username or the username spelled backwards.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
