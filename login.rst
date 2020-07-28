.. note::
   This extension is under the active development even though Adobe dropped the support for Magento 1.x e-commerce platform (Jul 1st, 2020). Creativestyle will provide the necessary updates and support for this extension as long as this extension will be used by the active Amazon Pay merchants.

Login with Amazon
=================
**Login with Amazon** allows users to login to your shop using their Amazon user name and password. All available data needed for creating an account or placing an order in your Magento shop (including name, email address, and zip code) are fetched automatically from customer's Amazon account.

Requirements
------------
**Login with Amazon** service requires you to have a valid **Login and Pay with Amazon** account (refer to the :ref:`prerequisites-amazon-account-setup` if you don't have one yet), registered application for **Login with Amazon** service (refer to the :ref:`prerequisites-registering-application-for-login-with-amazon` if you don't have one yet) and Magento store with a valid SSL certificate installed and properly configured in your shop. By "installed and properly configured SSL certificate" it is meant that your webserver is configured to serve pages via HTTPS protocol, `Base URL` config option is set to the HTTPS-based URL and in :menuselection:`Web --> Secure` section of Magento settings.

`Login with Amazon` button
--------------------------
The `Login with Amazon` button appears in several places in the shop:

* on the customer login page,
* on the customer registration page.

.. image:: /images/1.7.2/login_screenshot_1.png

You can also place the `Login with Amazon` button in any place you like by including following statement in the template file:

.. code-block:: php

   <?php echo Mage::helper('amazonpayments')->getLoginWithAmazonButton(); ?>

Pressing the `Login with Amazon` button launches the Amazon authentication window, where the customer is asked for his Amazon account e-mail address and password.

.. image:: /images/1.7.2/order_step_2.png

After a successful login the customer is redirected to the user area in your shop.

.. note:: When the customer uses the `Login with Amazon` for the first time in your shop and account with the same e-mail address already exists in your shop, he will be asked to enter his shop password to match both shop and Amazon accounts. Moreover, if you require additional data from your customers which cannot be provided by Amazon (like date of birth or gender), the customer will be asked for those data in a dedicated form, that appears after the first use of `Login with Amazon` button.
