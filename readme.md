## Laravel integration for reCAPTCHA Library

This is a Laravel integration package for https://github.com/fruitcakestudio/php-recaptcha


## Installation

Require this package with composer:

```
composer require fruitcakestudio/laravel-recaptcha
```


## Laravel integration

You can use the Laravel ServiceProvider to make use of the Laravel Configuration and Request object.

Add the ServiceProvider to your list of ServiceProviders:

```
'FruitcakeStudio\ReCaptcha\Support\Laravel\ServiceProvider',
```

Publish the Configuration and edit the sitekey, secret and language.

```
php artisan config:publish fruitcakestudio/recaptcha
```

If you want to use the Facade, add that too.

```
'ReCaptcha' => 'FruitcakeStudio\ReCaptcha\Support\Laravel\Facade',
```

This will register the ReCaptcha instance, preconfigured with your configuration and the Request object.

```php
// Using the IoC container
$captcha = App::make('recaptcha');
$captcha->getScript();

// Using the Facade
ReCaptcha::verifyRequest();
```

You can also add the ReCaptcha as a rule to the validator:

```php
$validator = Validator::make(Input::all(), array(
    'g-recaptcha-response' => 'required|recaptcha'
));
```

