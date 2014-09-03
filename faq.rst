.. _faq:

Frequently Asked Questions
==========================


Installation
------------

**I have successfully installed Pay with Amazon extension, but when I try to go to the configuration page** :menuselection:`System --> Configuration --> Amazon Payments` **I am getting: 404 Not Found error.**

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

In case you are sure you have :ref:`Merchant ID <configuration-credentials>` and :ref:`configuration-marketplace` correctly set, check if any of the following extensions are installed and enabled in your shop and follow the instructions:

* Mxperts_NoRegion

This extension replaces default `checkout.cart` block with own one. The replaced block doesn't include checkout buttons defined previously. To bring the **Pay with Amazon** button back, find ``noregion.xml`` file in your theme folder (or in the default theme folder) and modify `checkout.cart.methods` block by adding following code:

    .. code-block:: xml

       <block name="checkout.cart.methods" as="methods" type="core/text_list" translate="label">
           ...
            <block type="amazonpayments/pay_button" name="checkout.cart.methods.amazonpayments_pay.bottom" before="-">
                <action method="setIdSuffix"><value>div</value></action>
                <action method="setEnableOr"><value>1</value></action>
            </block>
       </block>
