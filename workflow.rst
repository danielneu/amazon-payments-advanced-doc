Order & payment workflow
========================

**Pay with Amazon** extension follows standard Magento order and payment workflow, which basically means that processing **Pay with Amazon** payment after the order is placed doesn't differ significantly from other payment methods available in Magento. Most of the payments subtransactions (captures, refunds) use appropriate document entities provided by the Magento (invoices for captures, credit memos for refunds).


Pay with Amazon button
----------------------

**Pay with Amazon** button appears in several places in the shop:

* on the shopping cart page,
* in the 1st step of the default One Page Checkout,
* in the sidebar cart widget.

Moreover, you can place the **Pay with Amazon** button in any place you like by including following statement in the template file:

.. code-block:: php

   <?php echo Mage::helper('amazonpayments')->getPayWithAmazonButton(); ?>

Pressing **Pay with Amazon** button launches the Amazon Payments authentication window, where the customer is asked for his Amazon account e-mail address and password. After successfull login the customer is redirected to the Amazon checkout page in your shop.

Placing an order
----------------

.. todo:: checkout processing

Billing address will be updated as soon as authorization is confirmed by Amazon either via IPN message or via data polling. Billing address is available only for the sellers that provided valid VAT number in Amazon Seller Central.


Payment authorization
---------------------

.. todo:: authorization
.. todo:: authorization declines


Capturing payment amount
------------------------

.. todo:: capture


Refunding order items
---------------------

.. todo:: refunds
.. todo:: partial refunds 


Cancelling order
---------------------

.. todo:: cancelation
