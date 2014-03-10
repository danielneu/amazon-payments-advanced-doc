Troubleshooting
===============

Before taking any action, please refer to the :ref:`faq` section, where many common issues have been already explained and solved.

.. _troubleshooting-logs:

Event logs
----------

The **Pay with Amazon** extension provides convenient logging system. It is disabled by default, but you can enable it in the extension settings, refer to the :ref:`configuration-logs` section for more details.

Log files location
~~~~~~~~~~~~~~~~~~

The Logger save details concerning all exceptions, all API calls and all incoming IPN notifications occured within the **Pay with Amazon** extension scope. Logs are stored in the CSV files in the following locations:

* exceptions logs:

  ``var/log/amazonpayments/apa_exception.log``

* API calls logs:

  ``var/log/amazonpayments/apa_api.log``

* IPN notifications logs:

  ``var/log/amazonpayments/apa_ipn.log``


Logs accessing
~~~~~~~~~~~~~~

In case you encouter any issues and :ref:`faq` section didn't help, you should review your logs in a next step. They can be accessed in two ways:

* Using :menuselection:`creativestyle --> Pay with Amazon --> Log preview` feature, where all logs are displayed on a convenient list with basic filtering options.

* By direct access any of the above files on your server: download the desired file (using FTP or SFTP, depending on your server configuration) and open it with any CSV-capable application. The current log files can be also downloaded by pressing `Download as CSV` button on the above logs list in the Magento admin.


Logs rotating
~~~~~~~~~~~~~

All log files are rotated as soon as they exceed the size of 8 Megabytes, the old log file is renamed then to ``var/log/amazonpayments/apa_*.log.timestamp`` and new empty file is created for storing new log entries. The old log files are still accessible by direct access (FTP, SFTP or SSH, depending on your server configuration) to ``var/log/amazonpayments`` folder on the server.


Contact support
---------------

In case neither FAQ studying nor event logs reviewing won't result in solving your issue you can submit a support ticket on http://creativeticket.de site.

.. note:: In the request ticket please describe your issue very precisely (we won't be able to do anything with the request: *Hey, it doesn't work for me, please help!*) and which extension (**Pay with Amazon**, **Checkout by Amazon**) does it concern. Some details regarding ecosystem the extension is working on (PHP version, Magento version, extension version, production or staging server) would be also very helpful. Following those advices will visibly speed up processing your request.
