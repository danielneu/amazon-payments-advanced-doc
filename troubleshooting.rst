Troubleshooting
===============

Before taking any action, please refer to the :ref:`faq` section, where many common issues have been already explained and solved.

.. _troubleshooting-logs:

Event logs
----------

The **Pay with Amazon** extension provides convenient logging system. It is disabled by default, but you can enable it in the extension settings, refer to the :ref:`configuration-logs` section for more details.

Log files location
~~~~~~~~~~~~~~~~~~

The Logger saves details concerning all exceptions, all API calls and all incoming IPN notifications occured within the **Pay with Amazon** extension scope. Logs are stored in the CSV files in the following locations:

* exceptions logs:

  ``var/log/amazonpayments/apa_exception.log``

* API calls logs:

  ``var/log/amazonpayments/apa_api.log``

* IPN notifications logs:

  ``var/log/amazonpayments/apa_ipn.log``


Logs accessing
~~~~~~~~~~~~~~

In case you encouter any issues and :ref:`faq` section didn't help, you should review your logs in the next step. Logs can be accessed in two ways:

* Using :menuselection:`creativestyle --> Pay with Amazon --> Log preview` feature, where all logs are displayed on a convenient list with basic filtering options.

* By direct access (using FTP, SFTP or SSH, depending on your server configuration) above files on your server, after download you can open them with any CSV-capable application. The current log files can be also downloaded by pressing `Download as CSV` button on the logs list :menuselection:`creativestyle --> Pay with Amazon --> Log preview` in the Magento admin.


Logs rotating
~~~~~~~~~~~~~

All log files are rotated as soon as they exceed the size of 8 Megabytes, the old log file is renamed then to ``var/log/amazonpayments/apa_*.log.timestamp`` and new empty file is created for storing new log entries. The old log files are still accessible by direct access (FTP, SFTP or SSH) to ``var/log/amazonpayments`` folder on the server.


Contact support
---------------

In case neither FAQ studying nor event logs reviewing won't result in solving your issue you can submit a support ticket on http://creativeticket.de site.

.. note:: In the request ticket tell us please which extension (**Pay with Amazon**, **Checkout by Amazon**) does your issue concern and describe it very precisely. Some details regarding ecosystem the extension is working within (PHP version, Magento version, extension version, production or staging server) would be also very helpful. Following those advices will visibly speed up processing your request.
