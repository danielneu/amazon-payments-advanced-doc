Installation
============

Pre-installation steps
----------------------

* Create a backup of your shop before proceeding to install.
* If your shop is using compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to install.


Installation process
--------------------

* Go to :menuselection:`System --> Magento Connect --> Magento Connect Manager` and enter your admin credentials to get logged in.
* In the `Install New Extensions` section enter **Pay with Amazon** extension key obtained from Magento Connect page and click :guilabel:`Install` button.
* Installation will start and after successful install it will show a message. Optionally, you can click on :guilabel:`Refresh` button to see if **Pay with Amazon** is listed on list of the installed extensions.
* Proceed to the post-installation steps.

Post-installation steps
-----------------------

* If you're using custom design theme, refer to the Templates customization section to find out how to adjust **Pay with Amazon** templates to your needs.
* Go to :menuselection:`System --> Cache Management` and flush Magento cache storage.
* If you have disabled compiler in pre-installation stage, you can go now to :menuselection:`System --> Tools --> Compilation`, recompile and enable compiler again.

Voila! The **Pay with Amazon** extension shall be installed now. You can proceed to the :ref:`configuration` followed by :ref:`customization-frontend-templates` and :ref:`customization-email-templates` customization (if applicable).
