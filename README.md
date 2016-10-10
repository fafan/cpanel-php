# CPanel/WHM API for PHP library

NOTE: This library is modified from original code of gufy/cpanel-php

I rewrite runQuery() function to use cURL instead of GuzzleHttp


## Contents
- [Installation](#installation)
- [Usage](#usage)
- [Functions](#functions)
- [Credits](#credits)

### Installation

To install this package, you can run this code via your terminal
```shell
	composer require fafan/cpanel-php
```

Or update your `composer.json` by adding this line
```json
	"fafan/cpanel-php":"^0.1"
```

Then, run this code
```shell
	composer update
```

### Usage

For example, if you would like to get list accounts of your whm server, you can do this.

```php
  <?php
  $cpanel = new \Fafan\CpanelPhp\Cpanel([
      'host'        =>  'https://123.456.789.123:2087', // ip or domain complete with its protocol and port
      'username'    =>  'root', // username of your server, it usually root.
      'auth_type'   =>  'hash', // set 'hash' or 'password'
      'password'    =>  'password', // long hash or your user's password
  ]);

  $accounts = $cpanel->listaccts(); // it will returned as array

```

### Functions

This is the example when you want to define your configuration while creating new object

```php
  <?php
  $cpanel = new \Fafan\CpanelPhp\Cpanel([
      'host'        =>  'https://123.456.789.123:2087', // required
      'username'    =>  'root', // required
      'auth_type'   =>  'hash', // optional, default 'hash'
      'password'    =>  'password', // required
  ]);
```

Somehow, you want to override your current configuration. To do this, here is the code

```php
  <?php
  // change username andd (password or hash)
  $cpanel->setAuthorization($username, $password);

  // change host
  $cpanel->setHost($host);

  // change authentication type
  $cpanel->setAuthType($auth_type);
```

#### Get defined configuration
After you define some of your configuration, you can get it again by calling this functions

```php
  <?php
  // get username
  $cpanel->getUsername();

  // get password
  $cpanel->getPassword();

  // get authentication type
  $cpanel->getAuthType();

  // get host
  $cpanel->getHost();
```

#### Credits

Original code: gufy/cpanel-php, version 1.0

By Mochamad Gufron <mgufronefendi@gmail.com>
