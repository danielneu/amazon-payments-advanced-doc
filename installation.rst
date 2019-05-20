.. _installation:

Installation
============

Pre-installation steps
----------------------

* Create a backup of your shop before proceeding to install.
* If your shop is using compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to install.


.. _installation-process:

Installation process
--------------------

* In your browser, open the `Magento Marketplace <https://marketplace.magento.com/creativestyle-creativestyle-amazonpayments.html>`_ page, add it to your cart, and go to checkout (this will be free of charge). On the order confirmation page click on :guilabel:`Install` to receive the access key (you may need to log in with your Magento account). Copy the access key.

.. image:: /images/1.7.2/installation_step_1.png

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.

.. image:: /images/1.7.2/installation_step_2.png

* In the `Install New Extensions` section enter **Login and Pay with Amazon** extension key obtained from `Magento Marketplace <https://marketplace.magento.com/creativestyle-creativestyle-amazonpayments.html>`_ page and click :guilabel:`Install` button. Magento will display information about the extension you are about to install and after making sure this is the right version click `Proceed` button.

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


Upgrade
-------

Pre-upgrade steps
~~~~~~~~~~~~~~~~~

1. Create a backup of your shop before proceeding to install.
2. If your shop is using compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to install.


Plugin version 2.0.x (installed after September 2017) to 3.x
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: In a nutshell: You can simply use Magento connect to upgrade to the most recent plugin version.

**Required steps:**

1. Log in to the admin area of your Magento 1 shop.
2. Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.
3. Click on :guilabel:`Check for Upgrades` within the :guilabel:`Extensions` tab.
4. For the module `creativestyle+Creativestyle_AmazonPayments` select the most recent version and click on :guilabel:`Commit changes`.
5. After installation go back to admin area (link on top :guilabel:`Return to Admin`).
6. Go to :menuselection:`System --> Cache Management`.
7. Click on the button :guilabel:`Flush Magento Cache` (top right).
8. Click on the button :guilabel:`Flush JavaScript/ CSS Cache` (bottom left).
9. If you have disabled compiler in pre-installation stage, you can go now to :menuselection:`System --> Tools --> Compilation`, recompile and enable compiler again.
10. Logout from the Magento admin and login again.
11. Test if you can place an order with Amazon Pay. If you have any trouble please contact our support.

Plugin version 1.x (installed before September 2017, including version 2.0.0) to 3.x
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: In a nutshell: You have to uninstall the previous plugin version first. Then install the most recent version with a new extension key obtained from Magento Marketplace.

**Required steps:**

1. Log in to the admin area of your Magento 1 shop.
2. Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.
3. Search the package `creativestyle+Creativestyle_AmazonPayments`, select :guilabel:`Uninstall` as action, then click on the :guilabel:`Commit changes` button below.
4. Install the most recent version according to our installation guide: :ref:`installation-process`.
5. Test if you can place an order with Amazon Pay. If you have any trouble please contact our support.


Post-upgrade steps
~~~~~~~~~~~~~~~~~~

.. attention:: The following instruction concerns the shops that rely on the order workflow (eg. 3rd party ERP implementation, etc.) and upgrades the extension from version either 1.x or 2.x to 3.x. Version 3.0.2 does not bring any changes to the templates or layout definitions. The only frontend related change has been introduced in the main JS application `js/creativestyle/amazonpayments.min.js` file.

Version 3.0.2 comes with a significant change to the payment processing workflow. Prior to version 3.x the payment authorization was requested during placing the order (i.e. right after clicking :guilabel:`Save order` button in the checkout), thus in synchronous and optimized (when there wasn't transaction timed out decline) authorization mode, the order ended up with the immediate authorization result.

Since the Strong Customer Authentication (derived from the PSD2 directive) was introduced in version 3.0.2, the authorization is requested after the order is actually placed. Thus, it may happen that the order payment remains unauthorized for a longer time unless the buyer finishes his Multi-Factor Authentication challenge. This change has to be considered for passing the order to the fulfillment process, to avoid fulfilling the orders that haven't been actually paid. As stated in :ref:`workflow-authorization` section, it is always advised to start fulfilling the order after the authorization is confirmed, which, in the default configuration, is reflected by the "Processing" order status.
