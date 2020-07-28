.. note::
   This extension is under the active development even though Adobe dropped the support for Magento 1.x e-commerce platform (Jul 1st, 2020). Creativestyle will provide the necessary updates and support for this extension as long as this extension will be used by the active Amazon Pay merchants.

Troubleshooting
===============

Before taking any action, please refer to the :ref:`faq` section, where many common issues have been already explained and solved.

.. _troubleshooting-logs:

Event logs
----------

The **Pay with Amazon** extension provides a convenient logging system. It is disabled by default, but you can enable it in the extension settings, refer to the :ref:`configuration-logs` section for more details.

Log files location
~~~~~~~~~~~~~~~~~~

The Logger saves details concerning all exceptions, all API calls and all incoming IPN notifications that occurred within the **Pay with Amazon** extension scope. Logs are stored in CSV files in the following locations:

* exceptions logs:

  ``var/log/amazonpayments/apa_exception.log``

* API calls logs:

  ``var/log/amazonpayments/apa_api.log``

* IPN notifications logs:

  ``var/log/amazonpayments/apa_ipn.log``


Logs accessing
~~~~~~~~~~~~~~

In case you encounter any issues and :ref:`faq` section didn't help, you should review your logs in the next step. Logs can be accessed in two ways:

* Using :menuselection:`creativestyle --> Pay with Amazon --> Log preview` feature, where all logs are displayed on a convenient list with basic filtering options.

* By directly accessing (using FTP, SFTP or SSH, depending on your server configuration) the above files on your server. After the download you can open them with any CSV-capable application. The current log files can be also downloaded by pressing `Download as CSV` button on the logs list :menuselection:`creativestyle --> Pay with Amazon --> Log preview` in the Magento admin.


Logs rotating
~~~~~~~~~~~~~

All log files are rotated as soon as they exceed the size of 8 Megabytes, the old log file is renamed then to ``var/log/amazonpayments/apa_*.log.timestamp`` and a new empty file is created for storing the new log entries. The old log files are still accessible by direct access (FTP, SFTP or SSH) to ``var/log/amazonpayments`` folder on the server.


Contact support
---------------

In case neither studying the FAQ nor the event logs reviewing resulted in solving your issue you can submit a support ticket on http://creativeticket.de site.

.. note:: In the request ticket tell us please which extension (**Advanced Payment APIs**, **Checkout by Amazon**) does your issue concern and describe it very precisely. Some details regarding ecosystem the extension is working within (PHP version, Magento version, extension version, production or staging server) would be also very helpful. Following those advices will visibly speed up processing your request.
