.. note::
   This extension is under the active development even though Adobe dropped the support for Magento 1.x e-commerce platform (Jul 1st, 2020). Creativestyle will provide the necessary updates and support for this extension as long as this extension will be used by the active Amazon Pay merchants.

.. _faq:

Frequently Asked Questions
==========================


Installation
------------

**I have successfully installed Login and Pay with Amazon extension, but when I try to go to the configuration page** :menuselection:`System --> Configuration --> Amazon Payments` **I am getting: 404 Not Found error.**

It's a Magento bug, the ACL list is not reloaded after the new extension is installed. To solve this issue please logout from the Magento admin and next login again.

----

.. _faq-magento15:

**It is stated that the extension is compatible with Magento 1.5, but when I try to place an order I am getting an exception: Invalid method Mage_Sales_Model_Order_Payment::lookupTransaction().**

Magento 1.5 doesn't provide public wrapper for _lookupTransaction() method of order payment model, which is commonly used by **Pay with Amazon** extension. To fix this issue we have prepared a compatibility pack that rewrites current sales/order_payment model. You can install it via Magento Connect, to do so go to :menuselection:`System --> Magento Connect --> Magento Connect Manager`, enter your admin credentials to get logged in, in the `Install New Extensions` section enter `http://connect20.creativetest.de/Creativestyle_AmazonPaymentsCompatibilityPack` key and click :guilabel:`Install` button.


.. warning:: Keep in mind that if any other 3rd party extension rewrites the sales/order_payment model as well, installing Magento 1.5 Compatibility Pack may lead to a rewrite conflict resulting in misfunction of one or more extensions. It is always advised to test it on a staging system prior to deploy to the production.


Frontend
--------

.. _faq-product-exclude:

**How can I disable Pay with Amazon for certain products?**

There are few extensions available for disabling payment methods on-the-fly based on the desired conditions. We recommend to install and use Rico Neitzel's `PaymentFilter for Products and Customer Groups <http://www.magentocommerce.com/magento-connect/paymentfilter-for-products-and-customer-groups.html>`_, which **Pay with Amazon** has been successfully tested against.

----

.. _faq-no-button:

**Pay with Amazon button doesn't show up in the cart after the extension is installed and set up.**

Lack of **Pay with Amazon** button in the cart is usually caused by one of the following reasons:

* incorrect :ref:`Merchant ID <configuration-credentials>` set (double check if you don't have any whitespaces in your :ref:`Merchant ID <configuration-credentials>`),
* incorrect :ref:`configuration-marketplace` set,
* your Amazon seller account is either blocked or not activated (you can check status of your account in Amazon Seller Central).

You can check validity of the provided Amazon Payments credentials using :ref:`configuration-validate-account` button available in the extension settings. In case you are sure you have :ref:`Merchant ID <configuration-credentials>` and :ref:`configuration-marketplace` correctly set, check if any of the following extensions is installed and enabled in your shop and follow the instructions:

* Mxperts_NoRegion
* FME_Ajaxaddtocart

Those extensions replace default `checkout.cart` block with own ones. The replaced block doesn't include checkout buttons defined previously. To bring the **Pay with Amazon** button back, find appropriate layout file:

* ``noregion.xml`` for Mxperts_NoRegion extension,
* ``ajaxaddtocart.xml`` for FME_Ajaxaddtocart extension

in your theme folder (or in the default theme folder) and modify `checkout.cart.methods` and / or `checkout.cart.top_methods` blocks by adding following code:

    .. code-block:: xml

        <block name="checkout.cart.methods" as="methods" type="core/text_list" translate="label">
            (...)
            <block type="amazonpayments/pay_button" name="checkout.cart.methods.amazonpayments_pay.bottom" before="-">
                <action method="setIdSuffix"><value>div</value></action>
                <action method="setEnableOr"><value>1</value></action>
            </block>
        </block>
        (...)
        <block name="checkout.cart.top_methods" as="top_methods" type="core/text_list" translate="label">
            (...)
            <block type="amazonpayments/pay_button" name="checkout.cart.methods.amazonpayments_pay.top" before="-">
                <action method="setIdSuffix"><value>top</value></action>
                <action method="setEnableOr"><value>1</value></action>
            </block>
        </block>

----

**After upgrade to 3.x, when the buyer clicks Amazon Pay button in the cart, he is redirected to the customer dashboard instead of the checkout.**

1. Please make sure that your webserver serves the most recent version of the `js/creativestyle/amazonpayments.min.js` file. Some webservers (as well as CDNs) are caching static assets, so it may happen that your shop serves an outdated version of the frontend JS application.

2. If you are using custom layout or template files for Amazon Pay, make sure that your customizations are compliant with the recent changes in the extension. The easiest way to check is your customization is the case is to delete following files as after refreshing Magento cache, see if this resolves your issue:

* app/design/frontend/CUSTOMPACKAGE/CUSTOMTHEME/layout/amazonpayments.xml
* app/design/frontend/CUSTOMPACKAGE/CUSTOMTHEME/template/creativestyle/amazonpayments/js.phtml
* app/design/frontend/CUSTOMPACKAGE/CUSTOMTHEME/template/creativestyle/amazonpayments/login/redirect.phtml

