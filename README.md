# Laravel Japanese Validation

[![Build Status](https://travis-ci.com/xzxzyzyz/laravel-japanese-validation.svg?branch=master)](https://travis-ci.com/xzxzyzyz/laravel-japanese-validation)
![Release](https://img.shields.io/github/release/xzxzyzyz/laravel-japanese-validation.svg?style=flat)
[![Packagist](https://img.shields.io/packagist/dt/xzxzyzyz/laravel-japanese-validation.svg)](https://packagist.org/packages/xzxzyzyz/laravel-japanese-validation)
![GitHub license](https://img.shields.io/github/license/xzxzyzyz/laravel-japanese-validation.svg?style=flat)

Laravelで利用する日本のバリデーションルール

Laravel 5.5+

## Installation

```bash
composer require xzxzyzyz/laravel-japanese-validation
```

## Usage

### ひらがな

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Hiragana;

$request->validate(['name' => 'ひらがなのもじれつ'], ['name' => new Hiragana]); // true


use Xzxzyzyz\Laravel\JapaneseValidation\Rules\HiraganaAndSpace;

$request->validate(['name' => 'ひらがなの もじれつ'], ['name' => HiraganaAndSpaceHiragana]); // true
```

### カタカナ

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Katakana;

$request->validate(['kana' => 'カタカナノモジレツ'], ['kana' => new Katakana]); // true

use Xzxzyzyz\Laravel\JapaneseValidation\Rules\KatakanaAndSpace;

$request->validate(['kana' => 'カタカナノ モジレツ'], ['kana' => new KatakanaAndSpace]); // true
```

### 電話番号

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Phone;

$request->validate(['phone' => '00-0000-0000'], ['phone' => new Phone]); // true
$request->validate(['phone' => '0000000000'], ['phone' => new Phone]); // true
```

### 郵便番号

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\PostalCode;

$request->validate(['zip' => '000-0000'], ['zip' => new PostalCode]); // true
$request->validate(['zip' => '0000000'], ['zip' => new PostalCode]); // true
```

### 都道府県

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Pref;

$request->validate(['pref' => '東京'], ['pref' => new Pref]); // true
```
