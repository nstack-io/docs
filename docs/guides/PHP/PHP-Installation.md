---
currentMenu: PHP-Installation
---

## 📦 Installation

To install this package you will need:

* PHP 7.1+

Run 

`composer require nstack/php-sdk`

or setup in composer.json

`nstack/php-sdk: 1.0.x`

## ⚙ Usage

```php
$config = new \NStack\Config('APP_ID', 'REST_KEY');
$nstack = new \NStack\NStack($config);
```