# Display solutions on the Laravel error page

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/laravel-error-solutions.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-error-solutions)
[![GitHub Tests Action Status](https://img.shields.io/github/actions/workflow/status/spatie/laravel-error-solutions/run-tests.yml?branch=main&label=tests&style=flat-square)](https://github.com/spatie/laravel-error-solutions/actions?query=workflow%3Arun-tests+branch%3Amain)
[![GitHub Code Style Action Status](https://img.shields.io/github/actions/workflow/status/spatie/laravel-error-solutions/fix-php-code-style-issues.yml?branch=main&label=code%20style&style=flat-square)](https://github.com/spatie/laravel-error-solutions/actions?query=workflow%3A"Fix+PHP+code+style+issues"+branch%3Amain)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/laravel-error-solutions.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-error-solutions)

This package can display solutions on the Laravel error page. Here's how it looks:

INSERT IMAGE

For some solutions, the package will display a button that will automatically run the solution. Here's how that looks when you forget to run `php artisan migrate`:

INSERT IMAGE


## Support us

[<img src="https://github-ads.s3.eu-central-1.amazonaws.com/laravel-error-solutions.jpg?t=1" width="419px" />](https://spatie.be/github-ad-click/laravel-error-solutions)

We invest a lot of resources into creating [best in class open source packages](https://spatie.be/open-source). You can support us by [buying one of our paid products](https://spatie.be/open-source/support-us).

We highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using. You'll find our address on [our contact page](https://spatie.be/about-us). We publish all received postcards on [our virtual postcard wall](https://spatie.be/open-source/postcards).

## Installation

You can install the package via composer:

```bash
composer require spatie/laravel-error-solutions
```

You can publish the config file with:

```bash
php artisan vendor:publish --tag="laravel-error-solutions-config"
```

This is the contents of the published config file:

```php
return [
    /**
     * Display solutions on the error page
     */
    'enabled' => true,

    /**
     * Enable or disable runnable solutions.
     *
     * Runnable solutions will only work in local development environments,
     * even if this flag is set to true.
     */
    'enable_runnable_solutions' => true,

    /**
     * This class is responsible for determining if a solution is runnable.
     *
     * In most cases, you can use the default implementation.
     */
    'runnable_solutions_guard' => Spatie\LaravelErrorSolutions\Support\RunnableSolutionsGuard::class,
];
```

Optionally, you can publish the views using

```bash
php artisan vendor:publish --tag="laravel-error-solutions-views"
```

## Usage

After the package installed, you'll see solutions on the error page. If you want to disable this, you can set the `enabled` key in the config file to `false`.

### Using AI to suggest solutions

The package can send your exceptions to Open AI that will attempt to automatically suggest a solution. In many cases, the suggested solutions is quite useful, but keep in mind that the solution may not be 100% correct for your context.

To generate AI powered solutions, you must first install this optional dependency.

```bash
composer require openai-php/client
```

To start sending your errors to OpenAI, you must set `ERROR_SOLUTIONS_OPEN_AI_KEY` in your `.env` file. The value should be your OpenAI key.

These bits of info will be sent to Open AI:

- the error message
- the error class
- the stack frame
- other small bits of info of context surrounding your error

It will not send the request payload or any environment variables to avoid sending sensitive data to OpenAI.

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Freek Van der Herten](https://github.com/freekmurze)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
