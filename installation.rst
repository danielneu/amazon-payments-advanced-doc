.. _installation:

Installation
============

Pre-installation steps
----------------------

* Create a backup of your shop before proceeding to install.
* If your shop is using compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to install.


Installation process
--------------------

.. image:: /images/1.7.2/installation_step_1.png

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.

.. image:: /images/1.7.2/installation_step_2.png

* In the `Install New Extensions` section enter **Login and Pay with Amazon** extension key obtained from `Magento Connect <http://www.magentocommerce.com/magento-connect/login-and-pay-with-amazon-advanced-payment-apis-for-europe.html>`_ and click `Install` button. Magento will display information about the extension you are about to install and after making sure this is the right version click `Proceed` button.

.. image:: /images/1.7.2/installation_step_3.png

* Installation will start and after successful install it will show a message. Optionally, you can click on `Refresh` button to see if **Login and Pay with Amazon** (identified as `Creativestyle_AmazonPayments`) is listed on list of the installed extensions.

.. image:: /images/1.7.2/installation_step_4.png

* Proceed to the post-installation steps.

Post-installation steps
-----------------------

* If you're using custom design theme, refer to the :ref:`Templates customization <customization-frontend-templates>` section to find out how to adjust **Login and Pay with Amazon** templates to your needs.
* Go to :menuselection:`System --> Cache Management` and flush Magento cache storage.
* If you have disabled compiler in pre-installation stage, you can go now to :menuselection:`System --> Tools --> Compilation`, recompile and enable compiler again.
* Logout from the Magento admin and login again.

Voila! The **Login and Pay with Amazon** extension shall be installed now. You can proceed to the :ref:`configuration` followed by :ref:`customization-frontend-templates` and :ref:`customization-email-templates` customization (if applicable).
