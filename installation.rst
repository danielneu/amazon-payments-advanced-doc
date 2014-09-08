.. _installation:

Installation
============

.. warning:: Be aware that after installing **Login and Pay with Amazon** extension your cart page will be automatically switched into SSL mode. It is always advised to test the extension in some staging environment prior to deploy to the production, especially in case you expect any issues caused by enabling SSL on the cart page.


Pre-installation steps
----------------------

* Create a backup of your shop before proceeding to install.
* If your shop is using compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to install.


Installation process
--------------------

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.
* In the `Install New Extensions` section enter **Login and Pay with Amazon** extension key obtained from `Magento Connect <http://www.magentocommerce.com/magento-connect/pay-with-amazon-advanced-payment-apis-for-europe.html/>`_ and click :guilabel:`Install` button.
* Installation will start and after successful install it will show a message. Optionally, you can click on :guilabel:`Refresh` button to see if **Login and Pay with Amazon** (identified as `Creativestyle_AmazonPayments`) is listed on list of the installed extensions.
* Proceed to the post-installation steps.

Post-installation steps
-----------------------

* If you're using custom design theme, refer to the :ref:`Templates customization <customization-frontend-templates>` section to find out how to adjust **Login and Pay with Amazon** templates to your needs.
* Go to :menuselection:`System --> Cache Management` and flush Magento cache storage.
* If you have disabled compiler in pre-installation stage, you can go now to :menuselection:`System --> Tools --> Compilation`, recompile and enable compiler again.

Voila! The **Login and Pay with Amazon** extension shall be installed now. You can proceed to the :ref:`configuration` followed by :ref:`customization-frontend-templates` and :ref:`customization-email-templates` customization (if applicable).
