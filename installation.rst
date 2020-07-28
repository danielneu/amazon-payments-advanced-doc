.. note::
   This extension is under the active development even though Adobe dropped the support for Magento 1.x e-commerce platform (Jul 1st, 2020). Creativestyle will provide the necessary updates and support for this extension as long as this extension will be used by the active Amazon Pay merchants.

.. note::
   If you are looking for the information on how to migrate from the dropped Magento Connect / Marketplace please refer to :ref:`migrating-from-magento-connect` section.

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

.. _installation-magento-connect-manager:

Installation via Magento Connect Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.

.. image:: /images/1.7.2/installation_step_1.png

.. image:: /images/1.7.2/installation_step_2.png

* In the :guilabel:`Install New Extensions` section paste the following extension key:

.. centered:: `http://connect.creativestyle.de/Creativestyle_AmazonPayments`

and click :guilabel:`Install` button. Magento Connect Manager will validate the key and check the extension dependencies and will display a pre-installation summary. Click :guilabel:`Proceed` button to start the installation.

.. image:: /images/1.7.2/installation_step_3.png

* After the successful installation, please click on :guilabel:`Refresh` button to refresh the list of the installed extensions and assure that **Login and Pay with Amazon** (identified as `Creativestyle_AmazonPayments`) is listed on that list.

.. image:: /images/1.7.2/installation_step_4.png

* Proceed to the :ref:`post-installation-steps`.

Manual installation
~~~~~~~~~~~~~~~~~~~

* Go to `Creativestyle Magento 1.x connect channel <https://connect.creativestyle.de/Creativestyle_AmazonPayments>`_ and download the recent installation package of the extension. Unpack the downloaded file to your Magento root directory.

.. note::
   If you are using any VCS (git, svn, mercurial) for versioning your shop basecode, you can also commit the content of the downloaded file to the VCS repository and next deploy it to your shop.

* Proceed to the :ref:`post-installation-steps`.

.. _post-installation-steps:

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

1. Create a backup of your shop before proceeding to upgrade.
2. If your shop utilises compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to upgrade.

.. _migrating-from-magento-connect:

Migrating from Magento Connect / Marketplace
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: **In a nutshell**: You have to uninstall the previous plugin version first. Then install the most recent version with a new extension key: `http://connect.creativestyle.de/Creativestyle_AmazonPayments`.

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.

.. image:: /images/1.7.2/installation_step_1.png

.. image:: /images/1.7.2/installation_step_2.png

* On the list of the installed extensions please find `Creativestyle_AmazonPayments`, select :guilabel:`Uninstall` in the corresponding action dropdown list and click :guilabel:`Commit changes` button.
* After the successful uninstallation from the previous source, install it from the `Creativestyle Magento 1.x connect channel <https://connect.creativestyle.de/Creativestyle_AmazonPayments>`_ as described in the :ref:`installation-magento-connect-manager` section.


Upgrade process
~~~~~~~~~~~~~~~

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.

.. image:: /images/1.7.2/installation_step_1.png

.. image:: /images/1.7.2/installation_step_2.png

* Click :guilabel:`Check for Upgrades` button in the :guilabel:`Manage Existing Extensions` section. If the newest version of Amazon Pay is available, the Creativestyle_AmazonPayments extension on the list will be highlighted with the yellow color. In the corresponding action dropdown list please select :guilabel:`Upgrade to X.X.X (stable)` option and click :guilabel:`Commit changes` button.

* After the successful upgrade, please click on :guilabel:`Refresh` button to refresh the list of the installed extensions and assure that **Login and Pay with Amazon** (identified as `Creativestyle_AmazonPayments`) was upgraded to the desired version.

* Proceed to the :ref:`post-upgrade-steps` section.

.. _post-upgrade-steps:

Post-upgrade steps
~~~~~~~~~~~~~~~~~~

Version 3.0.2 comes with a significant change to the payment processing workflow (comparing to versions 1.x and 2.x). Prior to version 3.x the payment authorization was requested during placing the order (i.e. right after clicking :guilabel:`Save order` button in the checkout), thus in synchronous and optimized authorization mode (assuming there wasn't transaction timed out error), the order ended up with the immediate authorization result.

Since the Strong Customer Authentication (derived from the PSD2 directive) was introduced in version 3.0.2, the authorization is requested after the order is actually placed. Thus, it may happen that the order payment remains unauthorized for a longer time unless the buyer finishes his Multi-Factor Authentication challenge. This change has to be considered for passing the order to the fulfillment process, to avoid fulfilling the orders that haven't been actually paid. As stated in :ref:`workflow-authorization` section, it is always advised to start fulfilling the order after the authorization is confirmed, which, in the default configuration, is reflected by the "Processing" order status.


Upgrade to 3.x troubleshooting
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**After upgrade to 3.x, when the buyer clicks Amazon Pay button in the cart, he is redirected to the customer dashboard instead of the checkout.**

1. Please make sure that your webserver serves the most recent version of the `js/creativestyle/amazonpayments.min.js` file. Some webservers (as well as CDNs) are caching static assets, so it may happen that your shop serves an outdated version of the frontend JS application.

2. If you are using custom layout or template files for Amazon Pay, make sure that your customizations are compliant with the recent changes in the extension. The easiest way to check is your customization is the case is to delete following files as after refreshing Magento cache, see if this resolves your issue:

* app/design/frontend/CUSTOMPACKAGE/CUSTOMTHEME/layout/amazonpayments.xml
* app/design/frontend/CUSTOMPACKAGE/CUSTOMTHEME/template/creativestyle/amazonpayments/js.phtml
* app/design/frontend/CUSTOMPACKAGE/CUSTOMTHEME/template/creativestyle/amazonpayments/login/redirect.phtml
