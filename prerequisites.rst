Prerequisites
=============


System requirements
-------------------

* Magento 1.5, 1.6, 1.7, 1.8
* cURL for PHP
* DOM / XML for PHP


Amazon Advanced Payments APIs account setup
-------------------------------------------


Registering an Amazon Payments Account
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Go to http://payments.amazon.de (DE merchants) or http://payments.amazon.co.uk (UK merchants)
* Click :guilabel:`Business` and choose :menuselection:`Setup options --> Advanced Payment APIs`

.. image:: /images/prerequisites_screenshot_1.png

* Click :guilabel:`Sign up`
* Go through the questionnaire to find out if you qualify for using Amazon Payments, then click :guilabel:`Sign up now`
* At the moment you cannot add your Advanced Payments APIs account to an existing Amazon merchant account. You have to register a new account specifically for the Advanced Payments APIs.
* Start registering a new account:

  * If you see the link :guilabel:`Would you like to create a new account using a different e-mail address? Click here`, please do so.
  * Enter a name for your business. In case this name is already taken, please choose a different one.
  * Enter an email address and a password. You should choose a role email address that will be read directly by the people responsible for the Amazon Payments integration. You should avoid general addresses like **info@** that are only forwarded to the general administration.
  * Choose a secure password.


.. image:: /images/prerequisites_screenshot_2.png

* Please fill in all requested information about your seller account, your contact information and your bank account or credit card data.
* Please be careful to provide exact and correct data. All information you provide will be verified by Amazon Payments, and incorrect information will delay the verification process.


.. image:: /images/prerequisites_screenshot_3.png

* After providing all information there will be an identity check on the phone, where you will be asked to enter a PIN.


.. image:: /images/prerequisites_screenshot_4.png

* Afterwards you can complete your registration

.. image:: /images/prerequisites_screenshot_5.png

* After your account is registered you will be forwarded to your Seller Central account.
* Please be aware that you cannot fully use your account yet. First you have to provide your identity data, and then the account has to go through the verification process.


Entering identity data in Seller Central
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To get the verification process started, please log in to Seller Central: https://sellercentral-europe.amazon.com/gp/homepage.html 

For a combined account (Advanced Payments APIs added to an existing account), please make sure that you have selected the :guilabel:`Amazon Payments – Production View` in the drop down menu on the top. 

.. image:: /images/prerequisites_screenshot_6.png

At :menuselection:`Settings --> Account Info` please provide the requested missing information. Especially it is crucial to provide the ID information for all relevant persons.

.. image:: /images/prerequisites_screenshot_7.png


Verification Process / Verification of all given information by Amazon Payments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After successful registration of the Amazon Payments seller account and entering the ID information Amazon Payments will check all information provided. Depending on the information provided Amazon Payments may request more information.


Creating MWS access keys
~~~~~~~~~~~~~~~~~~~~~~~~

You can generate your MWS access keys in Seller Central. Please go to :menuselection:`Integration --> MWS Access Key`

.. image:: /images/prerequisites_screenshot_8.png
.. image:: /images/prerequisites_screenshot_9.png

Log in again with your Amazon Payments account credentials

.. image:: /images/prerequisites_screenshot_10.png

Make sure that you register the MWS Access Key for your own account.

.. image:: /images/prerequisites_screenshot_11.png

Please read and accept the license agreement.

.. image:: /images/prerequisites_screenshot_12.png

The AWS Access Key and the Secret Key among with the Merchant ID, will be presented to you on the next page. You can always review the key information in Seller Central on the :menuselection:`Integration --> MWS Access Key` page.

.. image:: /images/prerequisites_screenshot_13.png


Where to find the required credentials to configure the Magento extension
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Magento extension requires you to enter information about your Amazon Payments account. You will need to enter:

* Merchant ID (aka Merchant Number, Händlernummer, Händler-ID)

.. note:: The Merchant Token **IS NOT** Merchant ID.

* AWS Access Key (aka AWS Access Key ID, AWS-Zugangsschlüssel, AWS Zugangsschlüssel-ID)
* Secret Key (aka AWS Secret Key, geheimer Schlüssel)

You can find this information in your Amazon Payments seller account in Seller Central.



.. _prerequisites-obtaining-merchant-id:

Merchant ID
'''''''''''

You can find the Merchant ID in Seller Central at :menuselection:`Setting --> Integration Settings`

.. image:: /images/prerequisites_screenshot_14.png



.. _prerequisites-obtaining-access-and-secret-key:

AWS Access Key / Secret Key
'''''''''''''''''''''''''''

You can find the AWS Access Key and the Secret Key in Seller Central at :menuselection:`Integration --> MWS Access Key`

.. image:: /images/prerequisites_screenshot_15.png



Configuration required in Seller Central
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you're planning to use IPN for the post-payment processing you need to enter a Merchant URL (IPN endpoint URL) in Seller Central. You can do this at :menuselection:`Settings --> Integration Settings`, then click the :guilabel:`Edit` button at :guilabel:`Instant Notification Settings`. IPN endpoint URL can be obtained from Magento admin at :menuselection:`System --> Configuration --> Amazon Payments`, see: :ref:`configuration-ipn-endpoint-url`.
