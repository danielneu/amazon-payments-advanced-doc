Overview
========

This extension provides an official integration of your Magento store with **Login and Pay with Amazon** services. They help your customers shop quickly, safely and securely. Your customers can pay on your website without re-entering their payment and address details. All Amazon transactions are protected by Amazon's A-to-z Guarantee.

The extension is a pure payment solution. No item level is communicated to Amazon Payments and it allows you to manage your orders directly from Magento.


Getting the extension
---------------------

In your browser, open the `Magento Marketplace <https://marketplace.magento.com/creativestyle-creativestyle-amazonpayments.html>`_ page, add it to your cart, and go to checkout (this will be free of charge). On the order confirmation page click on `Install` to receive the access key (you may need to log in with your Magento account). Copy the access key.

Refer to the :ref:`installation` section to get more details concerning installation procedure.


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

Changelog
---------

Version 3.0.8
~~~~~~~~~~~~~

Improvements & changes
''''''''''''''''''''''

* Implemented JS versioning
* Added support for newsletter subscription in the checkout

Version 3.0.6
~~~~~~~~~~~~~

Fixes
'''''

* Fixed redirect URL issues for the redirect authentication experience

Version 3.0.2
~~~~~~~~~~~~~

Improvements & changes
''''''''''''''''''''''

* Implemented Amazon Pay Strong Customer Authentication (PSD2 compliance)

Version 2.0.28
~~~~~~~~~~~~~~

Improvements & changes
''''''''''''''''''''''

* Improved button tooltip handling on mobile devices
* Explicitly set environment params for login JS application
* Re-structure settings page

Fixes
'''''

* Fixed reference to the closed cURL resource in Amazon Pay SDK lib
* Add support for form key validation in One Page Checkout

Version 2.0.26
~~~~~~~~~~~~~~

Changes
'''''''

* Stop keeping order reference ID and access token in the session data
* Force transaction data re-fetch on incoming IPN notification
* Re-implement Amazon Pay API requests logging

Fixes
'''''

* Add shipping rates recollecting after saving shipping address (fixes shipping costs issue)


Version 2.0.24
~~~~~~~~~~~~~~

Fixes
'''''

* Fixed shipping address processing during the checkout

Version 2.0.22
~~~~~~~~~~~~~~

Changes
'''''''

* Revert APA deprecation (Make Client ID config option optional)

Version 2.0.20
~~~~~~~~~~~~~~

Changes
'''''''

* Make Client ID config option mandatory (APA deprecation)

Fixes
'''''

* Fixed non-working Amazon Pay button on the product page when Login is disabled

Version 2.0.18
~~~~~~~~~~~~~~

Changes
'''''''

* Splitted Eurozone region

Changes
'''''''

* Wrap execution of external JS on checkout page in try-catch block

Fixes
'''''

* Fixed automatic invoice creation for auth & capture payment action
* Fixed typos in config options paths

Version 2.0.16.1
~~~~~~~~~~~~~~~~

Fixes
'''''

* Fixed saving access key and secret key options issue

Version 2.0.16
~~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented support for One Page Checkout

Improvements
''''''''''''

* Added support for SetOrderAttributes API call

Changes
'''''''

* Updated Amazon Payments SDK library

Version 2.0.14
~~~~~~~~~~~~~~

Improvements
''''''''''''

* Enabled support for multi currency globally

Fixes
'''''

* Skip declined payment email sending for synchronous authorizations
* Fix JS to dispose security warning in Magento malware scanner

Version 2.0.12
~~~~~~~~~~~~~~

Fixes
'''''

* Added missing translations for custom order statuses settings (#131)
* Re-authorization after InvalidPaymentMethod follows payment action settings (#133)
* Added order reference cancellation for asynchronous TransactionTimedOut authorization (#134)

Version 2.0.10
~~~~~~~~~~~~~~

Improvements
''''''''''''

* Added configurable order statuses for declined authorizations (#129)
* Implemented basic support for custom fields in the checkout

Fixes
'''''

* Fixed invoice status update on successful capture notification (#128)

Version 2.0.8
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added configurable multi currency

Fixes
'''''

* Fixed missing `Refund online` button for invoices created automatically for CaptureNow options (#127)
* Fixed TransactionTimedOut and AmazonRejected auth declines handling in synchronous mode

Version 2.0.6
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added support for soft descriptor in authorization call (#115)
* Added `Amazon Pay` button tooltip (#121)
* Implemented automatic order reference closing on successful capture (#126)
* Ignore authorization IPNs for synchronous mode (#120)

Fixes
'''''

* Fixed double invoice bug for manual capture (#122)

Version 2.0.4
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added `Amazon Pay` button on product view page

Fixes
'''''

* Fixed non-working Login for new customers

Version 2.0.2
~~~~~~~~~~~~~

Fixes
'''''

* Fix issues with wallet re-render for declined auth

Version 2.0.0
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented omni-chronous authorization

Changes
'''''''

* Refactored order post-processing
* Changed IPN endpoint URL
* Changed frontend layout and templates (no backward compatibility)
* Simplified frontend JS application

Version 1.8.6
~~~~~~~~~~~~~

Improvements
''''''''''''

* Added coupon code handling in Amazon checkout review
* Added possibility to disconnect customer account from Amazon account

Changes
'''''''

* Removed password form for account matching when customer is logged-in
* Updated Amazon Pay logos in Magento admin

Fixes
'''''

* Fixed PHP versions in Magento Connect package.xml file

Version 1.8.4
~~~~~~~~~~~~~

Improvements
''''''''''''

* Support for France, Italy and Spain
* Support for PHP 7
* Configurable store name in API calls

Changes
'''''''

* `Amazon Payments` re-branding

Fixes
'''''

* Fixed legacy payment method bug when trying to list all payment methods
* Fixed missing `original_price` and `base_original_price` item's attributes after order is placed
* Added missing return statement to the IPN controller

Version 1.8.2
~~~~~~~~~~~~~

Major Highlights
''''''''''''''''

* Implemented Quick Configuration (Simple Path)

Improvements
''''''''''''

* Added verbosity to error messages on frontend in sandbox mode
* Set payment method as soon as Amazon checkout is started

Fixes
'''''

* Fixed call to member function on null $quote variable in payment method model

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

Creativestyle is an award-winning, pioneering e-commerce agency with more than 15 years of experience. Since 2001, they have been developing expertise in the field of technology and software solutions. With a 50 person team of experts consisting of certified specialists in the fields of design, development and management of innovative projects, they can guarantee a full range of services from consulting and planning, through concept and design, to technical implementation and subsequent project support.

| **creativestyle GmbH**
| Erika-Mann-Straße 53
| 80636 München
| Germany
| http://www.creativestyle.de
|
