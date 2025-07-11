:original_name: gaussdb_03_0087.html

.. _gaussdb_03_0087:

Setting Alarm Rules
===================

Scenarios
---------

You can set alarm rules for TaurusDB to customize the monitored objects and notification policies and stay aware of the TaurusDB operating status.

The TaurusDB alarm rules include alarm rule names, services, dimensions, monitored objects, metrics, alarm thresholds, monitoring period, and whether to send notifications.

Procedure
---------

#. Log in to the management console.

#. Under **Management & Deployment**, click **Cloud Eye**.

#. In the navigation pane on the left, choose **Cloud Service Monitoring** > **TaurusDB**.

#. Locate the DB instance for which you want to create an alarm rule and click |image1| on the left, and then click **Create Alarm Rule** in the **Operation** column.

#. On the displayed page, set parameters as required.

   .. table:: **Table 1** Parameter description

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Parameter description                                                                                                                                    |
      +===================================+==========================================================================================================================================================+
      | Name                              | Alarm rule name. The system generates a random name, which you can modify.                                                                               |
      |                                   |                                                                                                                                                          |
      |                                   | Example value: **alarm-b6al**                                                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | (Optional) Supplementary information about the alarm rule.                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Method                            | There are two options: **Use existing template**, and **Configure manually**.                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Template                          | Template to be used.                                                                                                                                     |
      |                                   |                                                                                                                                                          |
      |                                   | You can select a default alarm template or create a custom template.                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Alarm Notification                | Whether to notify users when alarms are triggered. Notifications can be sent by email, text message, or HTTP/HTTPS message.                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Notification Object               | Object that receives alarm notifications. You can select the account contact or a topic.                                                                 |
      |                                   |                                                                                                                                                          |
      |                                   | -  Account contact is the mobile phone number and email address of the registered account.                                                               |
      |                                   | -  Topic is used to publish messages and subscribe to notifications. If the required topic is unavailable, create one first and add subscriptions to it. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**. The alarm rule is created.

   For operation details, see the *Cloud Eye User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001403218685.png
