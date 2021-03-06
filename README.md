# Types checker

[![Latest Stable Version](https://img.shields.io/packagist/v/kubawerlos/types-checker.svg)](https://packagist.org/packages/kubawerlos/types-checker)
[![PHP version](https://img.shields.io/packagist/php-v/kubawerlos/types-checker.svg)](https://php.net)
[![CI Status](https://github.com/kubawerlos/types-checker/workflows/CI/badge.svg?branch=main&event=push)](https://github.com/kubawerlos/types-checker/actions)
[![Code coverage](https://img.shields.io/coveralls/github/kubawerlos/types-checker/main.svg)](https://coveralls.io/github/kubawerlos/types-checker?branch=main)
[![Psalm type coverage](https://shepherd.dev/github/kubawerlos/types-checker/coverage.svg)](https://shepherd.dev/github/kubawerlos/types-checker)

A tool to find missing type declarations in PHP 7 code.


## Installation

```bash
composer require --dev kubawerlos/types-checker
```


## Usage

```bash
vendor/bin/types-checker src tests
```

## Configuration

| Option                | Description                                   |
| --------------------- | --------------------------------------------- |
| `--autoloader`        | Add custom autoloader file                    |
| `--exclude`           | Exclude class, interface or trait from report |
| `--skip-return-types` | Do not report missing return types            |

## Example

```php
<?php

interface Foo
{
    public function baz();
}

class Bar
{
    public function baz($x): array
    {
    }

    public function qux(bool $b, $x)
    {
    }
}
```

```bash
Types checker - 2 items checked:
 - 1 class
 - 1 interface

Issues found:
 - Interface Foo:
   - baz:
     - missing return type
 - Class Bar:
   - baz:
     - parameter $x is missing type
   - qux:
     - missing return type
     - parameter $x is missing type

  4 issues
```
