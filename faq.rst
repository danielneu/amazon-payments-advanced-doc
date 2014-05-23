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
