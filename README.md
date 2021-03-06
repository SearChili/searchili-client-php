# searchili-client-php
PHP client for SearChili API

[![Build Status](https://travis-ci.com/SearChili/searchili-client-php.svg?branch=main)](https://travis-ci.com/github/SearChili/searchili-client-php)
[![Packagist](https://img.shields.io/packagist/v/SearChili/searchili-client-php.svg?style=flat-square)](https://github.com/searchili/searchili-client-php)
[![Latest Stable Version](https://poser.pugx.org/searchili/searchili-client-php/v)](https://packagist.org/packages/searchili/searchili-client-php)
[![License](https://poser.pugx.org/searchili/searchili-client-php/license)](https://packagist.org/packages/searchili/searchili-client-php)

> ### Requirements

- PHP 5.6+
- Autoloader compatible with PSR-4
- PHP must be compiled with lib-curl

> ### Installation

To install the library just add it via [composer](https://getcomposer.org/download/)

```composer
composer require SearChili/searchili-client-php
```

Or in composer.json

```json
{
    "SearChili/searchili-client-php": "^1.0"
}
```

> ### Tests

We can use the composer to run the tests:

```composer
composer test
```

> ### How to Use
To use this library, you must first register on [SearChili](https://searchi.li).
After the registration, an apiKey and apiSecret will be available to access the API.

The API methods that can be invoked:
- Site info
- Entity search
- Entity sayt
- Entity store
- Entity delete

The following is a small example of how this library can be used.


> #### Alice
> ##### Search

```php
<?php

require_once "vendor/autoload.php";

use SearChili\Alice\Client as SearChiliAliceClient;

$client = new SearChiliAliceClient('<apiKey>');

$entities = $client->entity->search('query');
print_r($entities);
```


> #### Bob
> ##### Get authenticated site info

```php
<?php

require_once "vendor/autoload.php";

use SearChili\Bob\Client as SearChiliBobClient;

$client = new SearChiliBobClient('<apiSecret>');

$response = $client->site->get();
print_r($response->toArray());
```

> ##### Store

```php
$result = $aliceClient->entity->store(
    1, // ID
    'Example Title', // Title
    'http://domain.com/article-1', // Link
    'This is excerpt', // Excerpt
    'This will be the long body of this amazing article.' // Body
);
print_r($result);
```

> ##### Delete

```php
$result = $aliceClient->entity->delete(1);
var_dump($result);
```

> ### License

This library follows the terms of use of [MIT](https://github.com/SearChili/searchili-client-php/blob/main/LICENSE)
