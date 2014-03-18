Order & payment workflow
========================

**Pay with Amazon** extension follows standard Magento order and payment workflow, and thus processing **Pay with Amazon** payments doesn't differ significantly from other payment methods available in Magento, making it easy to handle. The most important difference, comparing to the standard Magento orders, is delayed access to the billing address, which is backfilled later in the synchronization process after the succesful authorization.

All Amazon payment objects (OrderReference, Authorize, Capture and Refund) are reflected in corresponding payment transactions in Magento, which are connected with appropriate document entities provided by the Magento, (invoices for captures, credit memos for refunds).


Pay with Amazon button
----------------------

**Pay with Amazon** button appears in several places in the shop:

* on the shopping cart page,
* in the 1st step of the default One Page Checkout,
* in the sidebar cart widget.

You can also place the **Pay with Amazon** button in any place you like by including following statement in the template file:

.. code-block:: php

   <?php echo Mage::helper('amazonpayments')->getPayWithAmazonButton(); ?>

Pressing **Pay with Amazon** button launches the Amazon Payments authentication window, where the customer is asked for his Amazon account e-mail address and password. After successfull login the customer is redirected to the Amazon checkout page in your shop.

.. image:: /images/workflow_screenshot_1.png


Placing an order
----------------

**Pay with Amazon** checkout form consists of 4 steps arranged within a single page (unlike Magento default checkout, which uses accordion for showing and hiding particular steps of the checkout). These steps are: shipping address (handled by Amazon's address book widget), payment method (handled by Amazon's wallet widget), shipping method and order review (handled by default Magento checkout templates). All fields in the form (shipping address, payment method and shipping method) are pre-filled, which means that in very basic scenario customer can finish the checkout with just one click. Unfortunately, pre-filling doesn't apply to terms and conditions checkbox (if used at all) and can raise the number of required clicks, which, however, doesn't affect the easiness and quickness of the **Pay with Amazon** payment method.

.. note:: Value selected in each checkout step is saved in a separate AJAX call, also when the checkout form shows up for the first time, so depending on the connection speed rate and your server response time it may take up to few seconds until :guilabel:`Place order` button will be allowed to be clicked by the customer.

After selecting the desired shipping address, payment method, shipping method and pressing :guilabel:`Place order` button (preceded by accepting terms and conditions if needed) customer is redirected to the success page. **Pay with Amazon** uses default Magento success page, which means there's no need to add any tracking scripts or additional page layout elements that you use in default Magento checkout and want also use in Amazon checkout, all features implemented additionally on the Magento success page shall also appear on Amazon checkout success page.

.. image:: /images/workflow_screenshot_2.png

Created order will be transferred to Amazon and will appear in your Magento admin in **Pending** state.

.. note:: You may notice in the Magento admin that billing address may be incorrect at this point (as mentioned in the introduction to this chapter). That's true if billing differs from the shipping data. The only available payment object at the time of placing order is the OrderReference, which, unfortunately, doesn't provide billing data and thus shipping address must be used to meet Magento requirements concerning order data. Billing address will be updated as soon as authorization is confirmed by Amazon Payments. Keep also in mind that billing address is available only for the sellers that provided a valid VAT number in Amazon Seller Central.


Payment authorization
---------------------

Authorization can be invoked after the order data is succesfully transferred to Amazon. Depending on the value you've selected for :ref:`configuration-payment-action` option it can be processed in several ways. For `Authorize` and `Authorize & capture` actions it will be requested automatically as soon as order is placed in your shop and succesfully transferred to Amazon. The requested authorization will be therefore either confirmed or declined by Amazon either via IPN message or via data polling, see :ref:`workflow-synchronizing-order-data` to get more details. Order, for which payment authorization has been confirmed changes its state to **Processing**, order email confirmation is sent to the customer (if not disabled in the extension settings, see :ref:`configuration-order-confirmation`) and you can start the fulfilment process.

.. warning:: Never dispatch order items before authorization is confirmed. Only the confirmed authorization guarantee you will be able to capture the order amount.


Manual authorization
~~~~~~~~~~~~~~~~~~~~

In case you ship ordered items after 30 days or more you may select `Manual authorization` as a payment action. It will stop Magento from invoking authorization call automatically and let you make an authorization request manually from the Magento admin in any suitable time. To invoke authorization manually, login to the Magento admin, open the order you want authorize payment for and click the :guilabel:`Authorize payment` button placed in the top buttons rows.

.. image:: /images/workflow_screenshot_3.png

Next post-request processing (authorization confirming or declining) is carried the same way as in automatic authorization.


Declined authorizations
~~~~~~~~~~~~~~~~~~~~~~~~

If the authorization is declined by Amazon due to problem with the payment method selected, your customer will be informed about this case via e-mail and requested to visit the Amazon Payments web site and update the payment method by following the instructions on the web page. E-mail sent to the customer can be adjusted according to the :ref:`customization-email-templates` section. After the succesful payment method update, Amazon will notify Magento about the new authorization status and payment will get back on the track.

In case the authorization has been declined due to any other reason than problems with selected payment method, the notification email will be sent to shop administrator and apropriate action will be undetaken according to the Amazon Payments Integration Guide.


Capturing payment amount
------------------------

After succesful authorization you can capture funds against the authorization. Capture, similar to authorization, can be requested in two modes: manual and automatic. By default you should capture order amount manually as soon as you shipped the order items. You are allowed to enable automatic capture only if you sell digital goods or you ship items same day they are ordered, moreover you have to be whitelisted by Amazon Payments.

:ref:`configuration-payment-action` option in the extension settings allows to switch between manual and automatic capture mode. For `Manual authorization` & `Authorization` actions capture must be requested manually in the Magento admin. For `Authorize & capture` action capture is requested automatically as soon as authorization is confirmed by Amazon Payments.


Manual capture
~~~~~~~~~~~~~~

To capture order amount you must create an invoice first. To create an invoice login to the Magento admin, open the order which you want capture amount for and click the :guilabel:`Invoice` button located in the top buttons rows. Please make sure that order you want to process has been succesfuly authorized, which basically means that it is in **Processing** state.

.. image:: /images/workflow_screenshot_4.png

After clicking the :guilabel:`Invoice` button, new invoice form will appear with most of the crucial data (like products quantity) already filled in. You can adjust some invoice fields if needed. At this point you can create a shipment as well, by checking :guilabel:`Create Shipment` checkbox and adding tracking number if needed. Before submitting the form, please **make absolutely sure** that :guilabel:`Amount` selectbox is set to `Capture online` and press :guilabel:`Submit Invoice` button. New invoice and new shipment (if checked :guilabel:`Create Shipment` checkbox) will be created for the order and capture will be requested at Amazon Payments gateway.

.. image:: /images/workflow_screenshot_5.png

.. warning:: To collect the funds that were reserved, you must capture them within 30 days of a successful authorization (two days in Sandbox mode). We strongly recommend that you capture funds within seven days of authorization to reduce the likelihood of declines. In case your fulfilment process exceeds time of 30 days consider using `Manual authorization` as the payment action and authorize the payment later in any suitable time before the shipping.

.. note:: Partial captures are not supported by the extension at this moment.

Capture status, similar to authorization, will be updated either via IPN message or via data polling, see :ref:`workflow-synchronizing-order-data` for more details.


Automatic capture
~~~~~~~~~~~~~~~~~

In this mode capture is requested automatically after the succesful authorization. Also the invoice that covers all order items is created automatically. Post-request processing (capture status synchronization) is carried the same way as in capture invoked manually from Magento backend.


Refunding order items
---------------------

Order, which payment has been captured for, can be refunded either fully or partially. Refunds are made against the invoices and thus having a paid invoice assigned to the order is a necessary condition that has to be met to refund any order item. Refunds in Magento are recorded as credit memos, so for requesting refund at Amazon Payments gateway you should create a credit memo first. To create a credit memo login to the Magento admin, open the order you want refund, click :guilabel:`Invoices` tab on the right, select an invoice you want to refund and click on it.

.. image:: /images/workflow_screenshot_6.png

Preview of the selected invoice will appear. Make sure that you are on the single invoice preview page and click the :guilabel:`Credit Memo` button.

.. image:: /images/workflow_screenshot_7.png

New credit memo form will appear with most of the crucial data (like products quantity to be refunded) already filled in. If you want to refund the invoice partially (i.e. only few of the invoiced items) adjust products quantity to be refunded (set 0 for items that shall not be refunded) and click :guilabel:`Update Qty's` button to update refund totals. You can also set refunded items back to stock by checking :guilabel:`Return to Stock` checkbox. Next choose if you want to refund shipping costs or apply any refunds adjustment and fill in apropriate fields. Next before submitting the credit memo form, double check that you have :guilabel:`Refund` button available and click it. Credit memo will be created and refund will be requested at Amazon Payments gateway. Its status will be updated either via IPN or data polling, depending on the update method selected in the extension settings.

.. image:: /images/workflow_screenshot_8.png

.. warning:: For the sucessful refund (recorded in Magento and requested (!) at Amazon Payments gateway) always use :guilabel:`Refund` button available on the new credit memo form invoked from the single invoice preview page. If you click :guilabel:`Credit Memo` button directly on the order page you will be redirected to the new credit memo form with :guilabel:`Refund offline` button only, which admittedly will record credit memo in Magento, but surely won't call refund request at Amazon Payments gateway. If in any case you will get a credit memo with :guilabel:`Refund offline` button only then surely something had to go wrong and you should break the refund process immediately and start it from the beginning following the above guideline.


Cancelling order
----------------

.. todo:: Cancelling order


.. _workflow-synchronizing-order-data:

Synchronizing order data
------------------------

.. todo:: Synchronizing order data
