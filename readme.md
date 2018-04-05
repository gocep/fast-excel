# Laravel Fast Excel [WIP]

[![Packagist](https://img.shields.io/packagist/v/rap2hpoutre/fast-excel.svg)]()
[![Packagist](https://img.shields.io/packagist/l/rap2hpoutre/fast-excel.svg)](https://packagist.org/packages/rap2hpoutre/fast-excel)
[![Build Status](https://travis-ci.org/rap2hpoutre/fast-excel.svg?branch=master)](https://travis-ci.org/rap2hpoutre/fast-excel)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/rap2hpoutre/fast-excel/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/rap2hpoutre/fast-excel/?branch=master)

Fast Excel import/export for Laravel, thanks to Spout. See benchmarks below.

## Installation

Install via composer

```
composer require rap2hpoutre/fast-excel
```

## Quick start

Export a Model to `.xlsx` file:
 
```php
use Rap2hpoutre\FastExcel\FastExcel;
use App\User;

// Load users
$users = User::all();

// Export
(new FastExcel($users))->export('file.xlsx');
```

## Usage

### Export

You can export a Model or a **Collection**:

```php
$list = collect([
    [
        'id' => 1,
        'name' => 'Jane',
    ],
    [
        'id' => 1,
        'name' => 'John',
    ],
]);

(new FastExcel($list))->export('file.xlsx');
```

You can export `xlsx`, `ods` and `csv`:

```php
$invoices = App\Invoice::orderBy('created_at', 'DESC')->get();

(new FastExcel($invoices))->export('invoices.csv');
```

### Import

`import` returns a Collection:

```php
$collection = (new FastExcel($list))->export('file.xlsx');
```

You can import `xlsx`, `ods` and `csv`.

## Why?

Laravel *Fast* Excel is intended at being Laravel-flavoured Spout: 
a simple, but elegant wrapper around Spout with the goal of simplifying **imports and exports**. 

It could be considered as a faster (and memory friendly) alternative to Laravel Excel, with many less features.

## Benchmarks

TODO. It's ~3 times faster.