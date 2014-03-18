.. _configuration:

Configuration
=============

After succesful installation you can proceed to the configuration. In the Magento admin go to :menuselection:`System --> Configuration --> Amazon Payments` tab. 

.. image:: /images/configuration_screenshot_1.png

Available options are grouped within the following tabs:

Amazon Payments Account
-----------------------

In this section you can define your Amazon Payments seller account credentials.

.. image:: /images/configuration_screenshot_2.png

:guilabel:`Merchant ID, Access Key ID, Secret Access Key`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Fill out those fields with your Amazon Payments seller credentials, you can find them in Amazon Seller Central, see: :ref:`prerequisites-obtaining-merchant-id` and :ref:`prerequisites-obtaining-access-and-secret-key`.

:guilabel:`Marketplace`
~~~~~~~~~~~~~~~~~~~~~~~
Select a marketplace you're selling your products on from the provided dropdown list. If you're unsure about this information consult your Amazon Integration Assistant.

General Settings
----------------

In this section you can enable or disable **Pay with Amazon** service and define basic settings of the extension.

.. image:: /images/configuration_screenshot_3.png

:guilabel:`Enable Pay with Amazon`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
By switching this option you can enable or disable **Pay with Amazon**. This option must be set to "Yes" if you want to provide Pay with Amazon service to your customers.

:guilabel:`Sandbox mode`
~~~~~~~~~~~~~~~~~~~~~~~~
Sandbox mode has been designed to test **Pay with Amazon** service. In sanbox mode credit cards are not charged. Refer to the **Pay with Amazon** documentation to get more information about sandbox. In principle, sandbox mode should be enabled for development and staging enviroments and always disabled for production environment.

:guilabel:`Show Sandbox Toolbox`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In sandbox mode you can simulate certain payment states. By enabling this option you get additional fields on the Amazon Checkout page that allow selecting expected payment status given in a response.

.. _configuration-payment-action:

:guilabel:`Payment Action`
~~~~~~~~~~~~~~~~~~~~~~~~~~
You can select desired payment action taken after order is placed. By default authorization is made automatically and capture must be triggered by the seler by creating an invoice in Magento admin (Authorize method). By selecting `Authorize & capture` method order amount will be captured immediately, which means that authorization will be followed by immediate capture call. If you want to use this setting it is mandatory that you have to be whitelisted for this feature by Amazon Payments first.

.. warning:: Please use `Authorize & capture` action only in case you're shipping goods same day they are ordered.

:guilabel:`Enable Instant Payment Notifications`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This option enable or disable handling of Instant Payment Notifications, which are used by Amazon for sending feedback concerning payment status. Keep in mind that using IPN requires having a valid SSL (issued by a trusted CA) installed on your server and correctly configured Secure Base URL (:menuselection:`System --> Configuration --> Web`). In case you disable IPN and want to use data polling instead you need to setup a cron for your shop.

.. _configuration-ipn-endpoint-url:

:guilabel:`IPN endpoint URL`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This auto-generated value shall be entered in the Merchant URL field of the Integration Settings in your Amazon Seller Central in case you plan to use IPN.

:guilabel:`Data polling frequency`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If you don’t have a valid SSL certificate in your shop or due to any other reason you don’t want to use IPN, you can set the how often payment status shall be polled from Amazon servers. Note that cron must be setup for your shop for periodic triggering routines that poll payment data.

:guilabel:`Order status on authorization`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
With this option you can change a status to which order will be set after successful authorization. In most cases leaving the default value seems to be a good idea.


Email Options
-------------

.. image:: /images/configuration_screenshot_4.png

.. _configuration-order-confirmation:

:guilabel:`Send order confirmation`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This option allows you to select whether an email confirmation for newly placed orders shall be sent by the shop. Note that, regardless this setting, payment confirmation will be always sent by Amazon.

.. _configuration-declined-payment-email:

:guilabel:`Declined Payment Email Template`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In this option you can select email template which will be used for notifying customer about declined authorization. Refer to the :ref:`customization-email-templates` section to find out how to customize email templates.

:guilabel:`Declined Payment Email Sender`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
With this option you can define the sender of the `Authorization declined` email notification. Sender can be selected from within pre-defined Magento email contacts (:menuselection:`System --> Configuration --> Store Email Addresses`).


.. _configuration-appearance-settings:

Appearance Settings
-------------------

In this section you can set basic design options for the Amazon widgets.

.. image:: /images/configuration_screenshot_5.png


Developer options
-----------------

.. image:: /images/configuration_screenshot_6.png

:guilabel:`Allowed IPs (comma separated)`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
For the testing or debugging purposes you can restrict access to **Pay with Amazon** checkout in your shop to certain IP numbers only. **Pay with Amazon** buton will be shown then only for the visitors comming from allowed IPs. You can set more than one allowed IP, enter them separated with comma.

.. _configuration-logs:

:guilabel:`Enable logging`
~~~~~~~~~~~~~~~~~~~~~~~~~~
Pay with Amazon extension comes with dedicated logging mechanism. Any exception, API call or IPN request will be saved to the var/log/amazonpayments folder in your Magento installation. For your convenience logs are also accessible via :menuselection:`creativestyle --> Amazon Payments --> Log preview` in Magento admin. Refer to the :ref:`troubleshooting-logs` section to get more details concerning the logging feature.
