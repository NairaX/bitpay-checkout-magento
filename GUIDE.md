# Using the BitPay plugin for Magento

## Prerequisites
You must have a BitPay merchant account to use this plugin.  It's free to [sign-up for a BitPay merchant account](https://bitpay.com/start).


## Server Requirements

* Last Cart Version Tested: 1.9.3.8
* [Magento CE](http://magento.com/resources/system-requirements) 1.9.0.1 or higher. Older versions might work, however this plugin has been validated to work against the 1.9.0.1 Community Edition release.
* [GMP](http://us2.php.net/gmp) or [BC Math](http://us2.php.net/manual/en/book.bc.php) PHP extensions.  GMP is preferred for performance reasons but you may have to install this as most servers do not come with it installed by default.  BC Math is commonly installed however and the plugin will fall back to this method if GMP is not found.
* [OpenSSL](http://us2.php.net/openssl) Must be compiled with PHP and is used for certain cryptographic operations.
* [PHP](http://us2.php.net/downloads.php) 5.4 or higher. This plugin will not work on PHP 5.3 and below.

## Installation

**From the Magento Market Place**

* Goto [https://marketplace.magento.com/bitpay-bitpay-core.html](https://marketplace.magento.com/bitpay-bitpay-core.html) and click the *Add to Cart* link.
* Select your shopping cart, click *Checkout* and then *Place order*
* Click *Install* and copy the access key of the latest version of the BitPay bitcoin acceptance plugin

Once you have the key, log into you Magento Store's Admin Panel and navigate to **System > Magento Connect > Magento Connect Manager**.

**NOTE:** It may ask you to log in again using the same credentials that you use to log into the Admin Panel.

All you need to do is paste the extension key and click on the *Install* button.

**WARNING:** It is good practice to backup your database before installing extensions. Please make sure you Create Backups.


**From the Releases Page:**

Visit the [Releases](https://github.com/bitpay/magento-plugin/releases) page of this repository and download the latest version. Once this is done, you can just unzip the contents and use any method you want to put them on your server. The contents will mirror the Magento directory structure.

**WARNING:** It is good practice to backup your database before installing extensions. Please make sure you Create Backups.

## Configuration

Configuration can be done using the Administrator section of your Megento store. Once Logged in, you will find the configuration settings under **System > Configuration > Sales > Payment Methods**.

![BitPay Magento Settings](https://raw.githubusercontent.com/bitpay/magento-plugin/master/docs/MagentoSettings.png "BitPay Megento Settings")

Here your will need to create a [pairing code](https://bitpay.com/api-tokens) using your BitPay merchant account. Once you have a Pairing Code, put the code in the Pairing Code field. This will take care of the rest for you.

**NOTE:** Pairing Codes are only valid for a short period of time. If it expires before you get to use it, you can always create a new one an use the new one.

**NOTE:** You will only need to do this once since each time you do this, the extension will generate public and private keys that are used to identify you when using the API.

You are also able to configure how BitPay's IPN (Instant Payment Notifications) changes the order in your Magento store.

![BitPay Invoice Settings](https://raw.githubusercontent.com/bitpay/magento-plugin/master/docs/MagentoInvoiceSettings.png "BitPay Invoice Settings")


## Usage

Once enabled, your customers will be given the option to pay with Bitcoins. Once they checkout they are redirected to a full screen BitPay invoice to pay for the order.

As a merchant, the orders in your Magento store can be treated as any other order. You may need to adjust the Invoice Settings depending on your order fulfillment.

## When Upgrading From Plugin Version 1.x to 2.x:

**Very Important:** You must complete remove any previous versions of the Bitpay Magento plugin before installing this new updated version. The plugin has been completely re-written to work with BitPay's new cryptographically secure RESTful API and will conflict with any previous plugin versions which use the old API.  To help you remove the old plugin files from your system, we have created a convenient shell script for Unix/Linux/Mac OS systems which will scan your webserver for these older files and delete them.  You may also remove these files by hand of course and the complete list of the files can be found in the source of the script for your convenience.  You can download this delete script here:  [scripts/delete.sh](https://github.com/bitpay/magento-plugin/blob/master/scripts/delete.sh).

To use this script, simply download to your server and execute the script from a shell.  You may have to mark the script executable before first use.

```sh
chmod +x delete.sh
./delete.sh
```
