# Laravel Japanese Validation

[![phpunit](https://github.com/xzxzyzyz/laravel-japanese-validation/actions/workflows/ci.yml/badge.svg)](https://github.com/xzxzyzyz/laravel-japanese-validation/actions/workflows/ci.yml)
![Release](https://img.shields.io/github/release/xzxzyzyz/laravel-japanese-validation.svg?style=flat)
[![Packagist](https://img.shields.io/packagist/dt/xzxzyzyz/laravel-japanese-validation.svg)](https://packagist.org/packages/xzxzyzyz/laravel-japanese-validation)
![GitHub license](https://img.shields.io/github/license/xzxzyzyz/laravel-japanese-validation.svg?style=flat)

Laravelで利用する日本のバリデーションルール

## Installation

```bash
composer require xzxzyzyz/laravel-japanese-validation
```

## Usage

### ひらがな

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Hiragana;

Validator::make(['name' => 'ひらがなのもじれつ'], ['name' => new Hiragana])->passes(); // true


use Xzxzyzyz\Laravel\JapaneseValidation\Rules\HiraganaAndSpace;

Validator::make(['name' => 'ひらがなの もじれつ'], ['name' => new HiraganaAndSpace])->passes(); // true
```

### カタカナ

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Katakana;

Validator::make(['kana' => 'カタカナノモジレツ'], ['kana' => new Katakana])->passes(); // true

use Xzxzyzyz\Laravel\JapaneseValidation\Rules\KatakanaAndSpace;

Validator::make(['kana' => 'カタカナノ モジレツ'], ['kana' => new KatakanaAndSpace])->passes(); // true
```

### 半角英数字

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Alpha;

Validator::make(['alpha' => 'ABC'], ['alpha' => new Alpha])->passes(); // true
Validator::make(['alpha' => 'ＡＢＣ'], ['alpha' => new Alpha])->passes(); // false

use Xzxzyzyz\Laravel\JapaneseValidation\Rules\AlphaDash;

Validator::make(['alpha_dash' => 'ABC-_'], ['alpha_dash' => new AlphaDash])->passes(); // true
Validator::make(['alpha_dash' => 'ＡＢＣー'], ['alpha_dash' => new AlphaDash])->passes(); // false

use Xzxzyzyz\Laravel\JapaneseValidation\Rules\AlphaNumber;

Validator::make(['alpha_num' => 'ABC123'], ['alpha_num' => new AlphaNumber])->passes(); // true
Validator::make(['alpha_num' => 'ＡＢＣ１２３'], ['alpha_num' => new AlphaNumber])->passes(); // false
```

### 電話番号

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Phone;

Validator::make(['phone' => '00-0000-0000'], ['phone' => new Phone])->passes(); // true
Validator::make(['phone' => '0000000000'], ['phone' => new Phone])->passes(); // true
```

### 携帯電話番号

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\MobilePhone;

Validator::make(['phone' => '090-1111-2222'], ['phone' => new MobilePhone])->passes(); // true
Validator::make(['phone' => '09011112222'], ['phone' => new MobilePhone])->passes(); // true
```

### 郵便番号

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\PostalCode;

Validator::make(['zip' => '000-0000'], ['zip' => new PostalCode])->passes(); // true
Validator::make(['zip' => '0000000'], ['zip' => new PostalCode])->passes(); // true
```

### 都道府県

```php
use Xzxzyzyz\Laravel\JapaneseValidation\Rules\Pref;

Validator::make(['pref' => '東京'], ['pref' => new Pref])->passes(); // true
```
