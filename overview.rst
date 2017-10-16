Overview
========

This extension provides an official integration of your Magento store with **Login and Pay with Amazon** services. They help your customers shop quickly, safely and securely. Your customers can pay on your website without re-entering their payment and address details. All Amazon transactions are protected by Amazon's A-to-z Guarantee.

The extension is a pure payment solution. No item level is communicated to Amazon Payments and it allows you to manage your orders directly from Magento.


Extension features
------------------

* `Pay with Amazon` button in the shopping cart and in the 1st step of OnePage checkout
* `Login with Amazon` button on the customer login and registration page
* Customization of **Login and Pay with Amazon** widgets from within Magento admin
* Support for payment authorizations, captures and refunds (also partial refunds)
* Support for synchronous and asynchronous authorization
* Supports Amazon Instant Payment Notifications
* Live & sandbox modes available
* Toolbox for simulating payment states in sandbox mode
* CSV-based event logger
* Multilanguage, available languages: en, de, fr, es, it

Getting the extension
---------------------

In your browser, open the `Magento Marketplace <https://marketplace.magento.com/creativestyle-creativestyle-amazonpayments.html>`_ page, add it to your cart, and go to checkout (this will be free of charge). On the order confirmation page click on `Install` to receive the access key (you may need to log in with your Magento account). Copy the access key.

Refer to the :ref:`installation` section to get more details concerning installation procedure.


Changelog
---------

Version 1.7.8
~~~~~~~~~~~~~

Improvements
''''''''''''

* Implemented simplified partial capture

Changes
'''''''

* Updated Amazon Payments SDK library

Fixes
'''''

* Added missing declined payment email templates for FR, IT and ES
* Fixed several issues for hard declined authorizations in synchronous mode

Version 1.7.6
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added support for custom SSL CA bundle file
* Implemented automatic authentication experience
* Disable `Pay with Amazon` availability for zero-total orders
* Retrieving billing address during the checkout
* Added exception handling for missing amazon_user_id attribute

Fixes
'''''

* Added support for SUPEE-6285 patch
* Added support for SUPEE-6788 patch
* Fixed calls to deprecated iconv functions in SDK library
* Fixed display errors for Magento RWD theme

Version 1.7.4.1
~~~~~~~~~~~~~~~

Fixes
'''''

* Fixed incorrect billing address issue for `Auth & capture` payment action

Version 1.7.4
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added missing payment cancellation functions
* Added Login with Amazon button on the customer registration page
* Added retrieving shipping address during the checkout
* Disabled Amazon button for virtual orders when Login is disabled

Fixes
'''''
* Fixed issue with placing virtual orders in sandbox mode
* Fixed closing order reference on completed capture

Version 1.7.2
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented multilanguage feature for Login with Amazon

Improvements
''''''''''''

* Implemented re-authorization after the first authorization expires
* Putting order on hold for some kinds of closed authorization
* Added reason code of the transaction status directly to the order comments
* Added store name to SetOrderReferenceDetails call

Changes
'''''''

* Updated Amazon Payments SDK library to 1.0.14


Fixes
'''''

* Fixed Firefox redirect experience issue
* Fixed issues in the splitting full customer name helper function

Version 1.6.4
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented redirect authentication experience

Improvements
''''''''''''

* Added links to the seller credentials in Amazon Seller Central on extension settings page
* Added Amazon Seller Central order link on order preview page in Magento admin
* Added invoice cancellation on declined capture
* Modified way of identifying `Place order` button in the checkout based on button ID instead of container class name

Fixes
'''''

* Removed button tooltip for mobile devices
* Fixed missing re-authorization on declined authorization in `Auth & capture` payment mode

Version 1.6.2
~~~~~~~~~~~~~

Fixes
'''''

* Fixed bugs in the refactored payment method model
* Fixed IPN processing bugs in v.1.6.0
* Fixed 404 error when customer press `Cancel` on Amazon login form

Version 1.6.0
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented synchronous authorization

Improvements
''''''''''''

* Made initial order status configurable
* Refactored payment method model

Version 1.3.4
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added gift messages support
* Improved customer address handling for Germany and Austria (extracting company name from the address)

Changes
'''''''

* Switched IPN endpoint URL to non-secure mode if sandbox is enabled

Fixes
'''''

* Fixed missing `original_price` and `base_original_price` item's attributes after order is placed
* Fixed state of `Place order` button which was enabled even the payment method is not selected
* Fixed state of `Place order` button which was disabled for virtual orders

Version 1.3.2
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented asynchronous way of loading Amazon Payments JS libraries

Improvements
''''''''''''

* Added cURL error handling for Login with Amazon API calls

Changes
'''''''

* Using deminified JS when sandbox mode is on for easier debugging
* Modified `Pay with Amazon` button tooltip text for virtual orders
* Refactored Amazon Payments SDK library to fix autoloader issues

Fixes
'''''

* Fixed wrong shipping cost when additional fees (acting as additional items in total section) are applied
* Fixed issue with `Merge JS` option enabled
* Closing OrderReference transaction after succesful capture

Version 1.2.6
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented responsive Amazon Payments widgets in the checkout

Fixes
'''''

* Fixed error when accessing extension settings page on Magento lower than 1.7.0.1
* Fixed issues with Magento compiler

Version 1.2.4
~~~~~~~~~~~~~

Fixes
'''''

* Fixed `Pay with Amazon` button appearing twice when Login with Amazon feature is enabled

Version 1.2.2
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Added **Login with Amazon** service

Improvements
''''''''''''

* Added helper methods for generating Pay or Login with Amazon buttons

Changes
'''''''

* Changed frontend template files structure
* Changed `Pay with Amazon` button in the 1st step of OPC to `Login with Amazon`

Fixes
'''''

* Clean orderReferenceId session data after successful order
* Fixed issue with permanently disabled `Place order` button when there is more than one layer with `buttons-set` class used
* Fixed using of invalid Amazon account credentials when cancelling an order in non-default store of multi-store installations


Extension vendor
----------------

This extension has been developed by creativestyle GmbH in cooperation with Amazon Payments Europe S.C.A.

Creativestyle is an interactive agency with years of experience and origins in Germany. Our company is present in the e-commerce market since 2001. We focus on development and implementation of various Internet projects.

| **creativestyle GmbH**
| Ganghoferstr. 68 a
| 80339 München
| Germany
| +49 89 5480 7604
| http://www.creativestyle.de
|
