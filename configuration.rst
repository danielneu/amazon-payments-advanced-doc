.. _configuration:

Configuration
=============
After the successful installation you can proceed to the configuration. In Magento admin go to :menuselection:`creativestyle --> Amazon Pay and Login with Amazon --> Settings` (or :menuselection:`System --> Configuration --> Amazon Payments` tab).

.. image:: /images/configuration_screenshot_1.png

Available options are grouped in following sections:

.. image:: /images/1.7.2/configuration_screenshot_10.png

Amazon Payments Account
-----------------------
In this section you can define your Amazon Payments seller account credentials.

.. image:: /images/1.7.2/configuration_screenshot_2.png

.. _configuration-credentials:

`Merchant ID, Access Key ID, Secret Access Key`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Fill out those fields with your Amazon Payments seller credentials. You can find them in the Amazon Seller Central, see: :ref:`prerequisites-where-to-find-the-required-credentials`.

.. _configuration-marketplace:

`Marketplace`
~~~~~~~~~~~~~
Select the country where you registered your seller account from the provided drop-down list. If you're unsure about this information consult your Amazon Integration Assistant.

.. _configuration-validate-account:

`Validate Amazon Payments account`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This button is designed to validate your Amazon Payments account credentials. Please use it to check whether your credentials (Merchant ID, Access Key ID, Secret Access Key and Marketplace) are valid or not.

.. warning:: Please note that the above feature will validate ANY Amazon MWS account, also such one that is not registered to Amazon Payments.

----

General Settings
----------------
In this section you can enable or disable the **Pay with Amazon** service and define basic settings of the extension.

.. image:: /images/1.7.2/configuration_screenshot_3.png

.. _configuration-enable-pay:

`Enable Pay with Amazon`
~~~~~~~~~~~~~~~~~~~~~~~~
By switching this option you can enable or disable **Pay with Amazon**. This option must be set to `Yes` if you want to provide the Pay with Amazon service to your customers.

`Sandbox mode`
~~~~~~~~~~~~~~
Sandbox mode has been designed to test the **Pay with Amazon** service. In sandbox mode the selected payment method is not charged. Refer to the **Pay with Amazon** documentation to get more information about the sandbox environment. In general, sandbox mode should be enabled for development and staging environments for testing and always has to be disabled for production environments. Never show the sandbox buttons and widgets to buyers in your live environment.

`Show Sandbox Toolbox`
~~~~~~~~~~~~~~~~~~~~~~
In sandbox mode you can simulate certain states for the different objects in the payment process. By enabling this option you get additional fields on the Amazon Checkout page that allow selecting expected payment statuses for orders, authorizations, captures and refunds returned in responses. This feature allows you to simulate different scenarios including declines in the sandbox environment.

.. _configuration-payment-action:

`Payment Action`
~~~~~~~~~~~~~~~~
You can select the desired payment action taken after an order is placed. Available options are:

* `Manual authorization` - the order reference is created only. Authorization must be requested manually by clicking `Authorize` button on the order preview page in Magento admin.
* `Authorize` (default) - order reference creation is followed by automatic authorization request. Capture must be requested manually by creating an invoice with `Capture online` option selected.
* `Authorize & capture` - order reference creation is followed by automatic authorization and capture request.
* `ERP mode` - same as `Manual authorization`, but further payment processing (authorization, capture, IPN notifications handling) is blocked in Magento. In this mode, it is assumed that after order reference creation rest of the payment processing steps will be handled by merchant's external ERP system.

.. warning:: Please do not use `ERP mode` unless your ERP system supports Amazon Payments transactions processing.

.. _configuration-authorization-processing-mode:

`Authorization Processing Mode`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This option defines mode of calling authorization request. By default `Asynchronous` mode is set, meaning that the Amazon Payments API responses immediately, but the authorization status is not known exactly and thus returned as *Pending*. This behavior requires authorization status update (either via IPN notification or cron-triggered data polling) before dispatching the order. `Synchronous` authorization returns its status immediately, but such a process takes usually few seconds more than `Asynchronous` authorization, causing your customer needs to wait longer until success page appears after `Place order` button click.

`Enable Instant Payment Notifications`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This option enables or disables handling of Instant Payment Notifications, which are used by Amazon Payments for sending feedback concerning the status of payment objects. Keep in mind that using IPN requires valid SSL certificate (issued by a trusted CA) installed on your server and correctly configured `Secure Base URL` and `Use Secure URLs in Frontend` config options (:menuselection:`System --> Configuration --> Web --> Secure` section). In case you disable IPN and want to use data polling instead you need to setup a cron for your shop.

.. note:: Trusted Certificate Authorities and other SSL requirements are listed on Amazon Payments webpage in `english <https://payments.amazon.co.uk/help/81779>`_ and `german <https://payments.amazon.de/help/81779>`_ language.

.. _configuration-ipn-endpoint-url:

`IPN endpoint URL`
~~~~~~~~~~~~~~~~~~
This auto-generated value shall be entered in the Merchant URL field of the Integration Settings in your Amazon Seller Central in case you plan to use IPN. If you use more than one store view in your Magento installation, the IPN endpoint URL will be shown after selecting appropriate store view scope.

`Data polling frequency`
~~~~~~~~~~~~~~~~~~~~~~~~
If you don’t have a valid SSL certificate in your shop or due to any other reason you don’t want to use IPN, you can set how often status of the different object shall be polled from Amazon Payments servers. Note that the cron must be setup for your shop for periodic triggering routines that poll payment data.

.. _configuration-new-order-status:

`New order status`
~~~~~~~~~~~~~~~~~~
With this option you can choose the status for newly created orders. Statuses assigned to *New* state are allowed only. Please note that this config option becomes obsolete when you use :ref:`synchronous authorization <configuration-authorization-processing-mode>`, initial order status will be set to :ref:`Order status on authorization <configuration-order-status-on-authorization>` value then.

.. _configuration-order-status-on-authorization:

`Order status on authorization`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
With this option you can change the status that will be set for an order after a successful authorization. Statuses assigned to *Processing* state are allowed only. In most cases leaving the default value seems to be a good idea.

.. warning:: Please note the difference between **state** and **status** terms in Magento. State is used by Magento internally to identify current stage of the order workflow, while status is some kind of a descriptive reflection of the state for seller purposes. Just as it is not possbile to define custom states in Magento, **it is not possible to configure the extension to use different order states** as well (*New* aka *Pending* is used for newly created orders, *Processing* - for successfully authorized orders). This rule implies that :ref:`New order status <configuration-new-order-status>` can be only changed to the status that is assigned to *New* state, while :ref:`Order status on authorization <configuration-order-status-on-authorization>` to the status assigned to *Processing* state. Any attempt to modify this behavior in the extension source code directly may lead to the inconsistency of the order workflow and may cause hard to debug issues. In case you need different than *New* state for the newly created order, consider using :ref:`synchronous authorization <configuration-authorization-processing-mode>` which gets authorization status immediately and uses :ref:`Order status on authorization <configuration-order-status-on-authorization>` straight away.

----

Login with Amazon
-----------------
In this section you can configure **Login with Amazon** service.

.. image:: /images/1.7.2/configuration_screenshot_7.png

.. _configuration-enable-login:

`Enable Login with Amazon`
~~~~~~~~~~~~~~~~~~~~~~~~~~
By switching this option you can enable or disable **Login with Amazon** feature. This service must be enabled if you want to create customer accounts in your Magento shop when order is placed and to make sure that any of the orders paid with **Pay with Amazon** will be never a guest order.

`Client ID`
~~~~~~~~~~~
The Client ID identifies your website for **Login with Amazon** service. Please refer to :ref:`prerequisites-where-to-find-the-required-credentials` section to find out how to get the value of your Client ID.

`Display Language`
~~~~~~~~~~~~~~~~~~
In this option you can select a language which will be used for displaying all elements (froms, widgets) generated by Amazon Payments. Selected language will be also used to localize emails sent by Amazon Payments to the customer after purchase. This setting applies also to **Pay with Amazon** as long as **Login with Amazon** is enabled.

`Authentication Experience`
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Select the method the authentication will be processed. By default `Pop-up` is used, meaning that after pressing `Pay` or `Login with Amazon` button, new window with Amazon login form opens, this requires the page you are placing the buttons on to be SSL-secured though. Choosing `Redirect` experience your customers will be redirected to Amazon login form in the current window after pressing `Pay` or `Login with Amazon` button. For the `Redirect` experience it is required to set `Allowed Return URLs` in the `Login with Amazon` section in your Seller Central.

.. warning:: Be aware that `Pop-up` authentication experience used by default requires the page, the button is placed on, to be in the SSL mode. This requirement is fulfilled by switching the cart page into SSL on the fly. This may lead to the unexpected results, especially if you are using some non-default Magento extensions (eg. AJAX-based adding to cart). It is always advised to test the extension in the staging environment prior to the production deployment.

----

Email Options
-------------

.. image:: /images/1.7.2/configuration_screenshot_4.png

.. _configuration-order-confirmation:

`Send order confirmation`
~~~~~~~~~~~~~~~~~~~~~~~~~
This option allows you to select whether a confirmation email for newly placed orders shall be sent by the shop. Note that, regardless this setting, a payment confirmation will be always sent by Amazon Payments.

.. note:: Order confirmation emails are not sent unless authorization is confirmed. If the emails are not sent, even you have above option enabled, it is very likely that Amazon Payments transactions are not updated. In such a case please make sure your shop accepts IPN notifications or polls transaction data in the cronjob.

.. _configuration-declined-payment-email:

`Declined Payment Email Template`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In this option you can select an email template which will be used for notifying customers about declined authorizations. Refer to the :ref:`customization-email-templates` section to find out how to customize email templates.

`Declined Payment Email Sender`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
With this option you can define the sender of the `Authorization declined` email notification. The sender can be selected from the pre-defined Magento email contacts (:menuselection:`System --> Configuration --> Store Email Addresses`).

----

.. _configuration-common-appearance-settings:

Common Appearance Settings
--------------------------
In this section you can set size (width and height) of Amazon widgets used in the checkout process.

.. image:: /images/1.7.2/configuration_screenshot_5.png

.. _configuration-use-responsive-widgets:

`Use responsive widgets`
~~~~~~~~~~~~~~~~~~~~~~~~
With this option you can decide if Amazon widgets used in the checkout (address book, wallet) will adapt to the layout by filling whole container area. This behavior allows to set widget size by defining size of its container in the external CSS file, making Amazon checkout compatible and easy to use with responsive layouts. Disabling this option will change the widgets to use explicit sizes defined in the next config options of this section.

`Address widget width, Address widget height`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In this option you can set size in pixels (width and height) of Amazon address book widget for disabled :ref:`configuration-use-responsive-widgets` option.

`Wallet widget width, Wallet widget height`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In this option you can set size in pixels (width and height) of Amazon wallet widget for disabled :ref:`configuration-use-responsive-widgets` option.

----

.. _configuration-pay-alexa-notifications:

Alexa Delivery Notifications
--------------------------------------------------
Alexa delivery notifications for Amazon Pay merchants allow you to pro-actively inform your customers if their order is on its way or has arrived.
After enabling the feature, generate or upload an existing key pair into the configuration fields `Private Key` and `Public Key`. If you are having trouble with the automatic generation inside the Magento admin, please follow this `guide <https://developer.amazon.com/de/docs/amazon-pay-automatic/delivery-notifications.html>`_.

You will need to reach out to Amazon Pay in order to receive your `Public Key ID` at this time. Please use the `contact` link and simply send the pre-defined email. You should recieve your `Public Key ID` within 1-2 business days. Once received, add the `Public Key ID` into the corresponding field.

.. image:: /images/configuration_screenshot_10.png

Configure your carriers using the `Carrier codes` form by selecting your available carriers and assign them to the matching one in the Amazon Pay carrier list.

.. image:: /images/configuration_screenshot_11.gif
----


.. _configuration-login-appearance-settings:

Appearance Settings for Login and Pay with Amazon
-------------------------------------------------
These settings apply to the design (type, size and color) of the buttons, both `Pay with Amazon` and `Login with Amazon`, when :ref:`configuration-enable-login` option is set to `Yes`, therefore they become irrelevant if you don't use **Login with Amazon** service, you may be interested then in :ref:`configuration-pay-appearance-settings`.

.. image:: /images/1.7.2/configuration_screenshot_8.png

----

.. _configuration-pay-appearance-settings:

Appearance Settings for standalone Pay with Amazon
--------------------------------------------------
These settings apply to the design (size and color) of the `Pay with Amazon` button when :ref:`configuration-enable-login` option is set to `No`, therefore they become irrelevant if you use **Login with Amazon** service, :ref:`configuration-login-appearance-settings` are applied then.

.. image:: /images/1.7.2/configuration_screenshot_9.png

----

Developer options
-----------------

.. image:: /images/1.7.2/configuration_screenshot_6.png

`Allowed IPs (comma separated)`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
For testing or debugging purposes you can restrict access to **Pay with Amazon** checkout in your shop to certain IP numbers only. **Pay with Amazon** button will be shown only for the visitors coming from allowed IPs. You can set more than one allowed IP separated with commas.

.. _configuration-logs:

`Enable logging`
~~~~~~~~~~~~~~~~
The Pay with Amazon extension comes with a dedicated logging mechanism. Any exception, API call or IPN notification will be saved to the var/log/amazonpayments folder in your Magento installation. For your convenience logs are also accessible via :menuselection:`creativestyle --> Login and Pay with Amazon --> Log preview` in Magento admin. Refer to the :ref:`troubleshooting-logs` section to get more details concerning the logging feature.
