# M-PESA API Package
[![Build Status](https://travis-ci.org/Kabangi/mpesa.svg?branch=master)](https://travis-ci.org/Kabangi/mpesa)
[![Latest Stable Version](https://poser.pugx.org/kabangi/mpesa/v/stable.svg)](https://packagist.org/packages/kabangi/mpesa)
[![Latest Unstable Version](https://poser.pugx.org/kabangi/mpesa/v/unstable.svg)](https://packagist.org/packages/kabangi/mpesa)
[![License](https://poser.pugx.org/kabangi/mpesa/license.svg)](https://packagist.org/packages/kabangi/mpesa)

This is a PHP package with first class support to laravel for the Safaricom's M-Pesa REST API dubbed DARAJA API.  

It implements all the exposed endpoints by Safaricom as listed below:-

### 1. [Lipa na M-Pesa Online Payment](https://developer.safaricom.co.ke/docs#lipa-na-m-pesa-online-payment)
#### &nbsp; &nbsp; What it is?
The Lipa na M-Pesa Online Payment endpoint(STK push) allows you to request payment from your users/clients. With this endpoint all the user is required to do is input their M-PESA pin to a prompt to send a payment to you. 
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/LipaNaMpesaOnline.md).

### 2. [Lipa na M-Pesa Online Query Request](https://developer.safaricom.co.ke/docs#lipa-na-m-pesa-online-query-request)
#### &nbsp; &nbsp; What it is?
When you request payment from your users/clients via Lipa na M-Pesa Online endpoint above you might want to know the status of that request. This endpoint facilitates that. It allows you to query the status of any STK push on demand. 
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/LipaNaMpesaOnlineQuery.md).

### 3. [C2B](https://developer.safaricom.co.ke/docs#c2b-api)
#### &nbsp; &nbsp; What it is?
This endpoint enables developers to receive real time notifications when a client makes a payments to a merchant's Till number or Paybill number. It assumes the payment are made via the SIM card toolkit and as a developer you need to know when that payment hits the merchants till/paybill number for reconciliation and accounting purposes.
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/C2B.md).

### 4. [B2C](https://developer.safaricom.co.ke/docs#b2c-api)
#### &nbsp; &nbsp; What it is?
This endpoints enables merchants to pay their customers from they paybill account. Some of the use cases are but not limited to paying salaries, paying promotions to customers etc.
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/B2C.md).

### 5. [B2B](https://developer.safaricom.co.ke/docs#b2b-api)
#### &nbsp; &nbsp; What it is?
This endpoint allows merchants to transfer funds from business to business accounts. 
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/B2B.md).

### 6. [Transaction Status](https://developer.safaricom.co.ke/docs#transaction-status)
#### &nbsp; &nbsp; What it is?
This endpoint enables developers to initiate status check of a B2B, B2C and C2B transactions. It really comes in handy where one party in a transactions fails/claims not to have received an acknowledgment for a transaction.
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/TransactionStatus.md).

### 7. [Reverse API](https://developer.safaricom.co.ke/docs#reversal)
#### &nbsp; &nbsp; What it is?
This endpoint enables merchants to reverse a B2B, B2C or C2B transaction. It allows automation of reversal of erronous payment to a merchant's paybill/till number or payments to goods never delivered.
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/Reversal.md).

### 8. [Account Balance](https://developer.safaricom.co.ke/docs#account-balance-api)
#### &nbsp; &nbsp; What it is?
This endpoint enables merchants to query their Till/Paybill numbers account balance on demand.
#### &nbsp; &nbsp; How to implement it?
[Read docs here](docs/AccountBalance.md).

## Installation

This project is distributed via composer package manager and should be installed as one of your project's dependencies:

### Laravel
1. Pull the package using the command below:-
```
composer require kabangi/mpesa
```
2. Make sure `config/app.php` under `providers` array the following line exists

`Kabangi\Mpesa\Laravel\ServiceProvider::class,`
If not add it

### Raw PHP (Vanilla)
1. Modify your `composer.json` file to include:

```json
  "scripts": {
        "post-update-cmd": [
            "Kabangi\\Mpesa\\Support\\Installer::install"
        ]
  },
```
2. Run the following command
```
composer require kabangi/mpesa
```


## Configuration

### Laravel

Publish the package config file by running the following command:
   `php artisan vendor:publish`
This will add `mpesa.php` config file into config directory. 

Edit the file with the necessary values if you do not do this we will use the sandbox credentials automagically.

### Raw PHP (Vanilla)

If you followed the installation details you should have a config directory and `mpesa.php` file. 

Modify the config file where necessary to include your credentials

## Usage

### Raw PHP (Vanilla)
```
<?php
require "vendor/autoload.php";

use Kabangi\Mpesa\Native\Mpesa;

$mpesa = new Mpesa();

$response = $mpesa->STKPush([]);
header('Content-Type: application/json');
echo json_encode($response);

// $mpesa->STKStatus([]);

// $mpesa->C2BRegister([]);

// $mpesa->C2BSimulate([]);

// $mpesa->B2C([]);

// $mpesa->accountBalance([]);

// $mpesa->reversal([]);

// $mpesa->transactionStatus([]);

```

## Inspiration

This package was inspired by the work from smodav work on the following project:-
https://github.com/SmoDav/mpesa

## Contributors
Gratitudes goes to the following Ninjas for their help during my integration process and the things I had to learn along the way fom them or their code:-

| [<img src="https://avatars1.githubusercontent.com/u/8632600?s=400&u=24e47804b187e651c75c3defc65930ef4e719b79&v=4" width="100px;"/><br /><sub>Julius Kabangi</sub>](mailto::kabangijulius@gmail.com/)

## Support
Need support using this package:- 
[Send a quick message here](https://join.slack.com/t/m-pesagroup/shared_invite/enQtMjkxNjczNzQyMTc4LTFjYjE5MDIxMzJjZDUyMDAzY2RmZjlhNDI3OGY1MWVhYTFkM2YzMmI2NjQ0NGM3M2EwMGVjM2E4NGU4MmIxYjA)

## License

The M-Pesa Package is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).

