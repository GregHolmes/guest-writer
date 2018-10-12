---
layout: post
title: "Top PHP libraries you should know"
description: ""
date: "2018-10-12 08:30"
author:
  name: "Greg Holmes"
  url: "https://twitter.com/greg__holmes"
  mail: "iam@gregholmes.co.uk"
  avatar: "https://avatars0.githubusercontent.com/u/2411269?s=460&v=4"
related:
- 2017-11-15-an-example-of-all-possible-elements
---

**TL;DR:** Briefly describe what this article is about and what the reader will achieve/learn after reading it. Please,
also provide the link to a GitHub repository that contains code related to this article.

### What is PHP?

PHP - Hypertext Preprocessor (AKA PHP) is a server-side scripting language. Created by Rasmus Lerdorf in 1994 and built upon / improved vastly in the time between then and now. Originally PHP's name was Personal Home Page, however this has evolved into the recursive acronym it is now.

The PHP language is a very popular programming language, developed in and supported by developers worldwide. Due to the coverage the language has worldwide, there are a vast number of libraries developed and maintained, created for various specific purposes.

### The libraries

##### Faker (Test data)

[Faker by Fzaninotto is a PHP library](https://github.com/fzaninotto/Faker) that allows you to generate fake data to be used throughout your development environment. This is a great tool that can be used to bootstrap your database to make use as a fully functioning service.

In order to make use of this library, a simple composer command is required:

```bash
composer require fzaninotto/faker
```

Basic usage (Along side several possible examples):

```php
$faker = Faker\Factory::create();

// Names
$faker->name
$faker->titleMale
$faker->firstNameFemale
$faker->lastName

// DateTime
$faker->dateTime($max = 'now', $timezone = null)
$faker->date($format = 'Y-m-d', $max = 'now')
$faker->dayOfWeek($max = 'now')
$faker->timezone

// Internet
$faker->email
$faker->safeEmail
$faker->freeEmail
$faker->url
$faker->ipv4

// Payment
$faker->creditCardType
$faker->creditCardNumber
$faker->creditCardDetails
```

There are a vast number of different bits of data that can be faked with this library. To view this list, the URL can be found here: [https://github.com/fzaninotto/Faker](https://github.com/fzaninotto/Faker)

#### PHPUnit (testing)
#### Email Validator (validation)

Email validation can very difficult to ensure that you've covered all aspects of ensuring the e-mail is valid in both syntax and whether the domain for example actually has email addresses.

With the use of the [Email Validator](https://github.com/egulias/EmailValidator), which is active and maintained, it can be a matter of minutes to implement into a project and be used to ensure the e-mail is valid.

In order to make use of this library, a simple composer command is required:

```bash
composer require egulias/email-validator "~2.1"
```

There is coverage for a multiple possibilities to check the validation for. These are:

* RFCValidation
* NoRFCWarningsValidation
* DNSCheckValidation
* SpoofCheckValidation

For example, using RFC validation, you could use the following code, which would return isValid() as a boolean:

```php
use Egulias\EmailValidator\EmailValidator;
use Egulias\EmailValidator\Validation\RFCValidation;

$validator = new EmailValidator();
$validator->isValid("example@example.com", new RFCValidation());
```

If you wished to use more than one validation option, for example, you wanted to use all 4 validations then you would use the `MultipleValidationWithAnd` with:

```php
use Egulias\EmailValidator\EmailValidator;
use Egulias\EmailValidator\Validation\DNSCheckValidation;
use Egulias\EmailValidator\Validation\MultipleValidationWithAnd;
use Egulias\EmailValidator\Validation\RFCValidation;

$validator = new EmailValidator();
$multipleValidations = new MultipleValidationWithAnd([
    new RFCValidation(),
    new NoRFCWarningsValidation(),
    new DNSCheckValidation(),
    new SpoofCheckValidation()
]);
$validator->isValid("example@example.com", $multipleValidations);
```

#### Guzzle (http/async)

[Guzzle's PHP HTTP client](https://github.com/guzzle/guzzle) is a library that makes it simple to send HTTP requests, improving functionality and reducing implementation time for requests between the project and third party API's.

This PHP client provides a simple interface that can be used for building RESTful requests, streaming large uploads and downloads, making use of HTTP cookies, and uploading JSON data, among others.

The library can send both synchronous and asynchronous requests whilst using the same interface.

In order to make use of this library, a simple composer command is required:

```bash
composer require guzzlehttp/guzzle
```

An example of sending a GET request to StarWars API can be found here:

```php
$client = new GuzzleHttp\Client();
$res = $client->request('GET', 'https://swapi.co/api/starships/9/');
echo $res->getStatusCode();
// "200"
echo $res->getHeader('content-type');
// 'application/json; charset=utf8'
echo $res->getBody();
// {"name": "Death Star",...
```
#### Serializer (serialize objects)
#### Doctrine2 (orm)
#### Assetic (asset management)
#### Carbon (datetime handling)
#### Monolog (logging)
#### Swift (email send)
