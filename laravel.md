---
title: Laravel
---
# Laravel

- [Introduction](#introduction)
- [Routes](#routes)
- [Recommended Packages](#packages)

<a name="introduction"></a>
## Introduction
Here is some helpful information around the conventions we employ when building Laravel projects.


<a name="routes"></a>
## Routes

Wherever possible, routes in Laravel should be named.

Named routes may use a combination of 'dot' notation, and kebab-case.

For example:

```php
route('admin.product-type.index');
```

Route names should follow resourceful naming wherever possible: `index`, `create`, `store` etc, and should be singular.


<a name="packages"></a>
## Recommended Packages

Below is a list of a few packages which we are familier with, and recommend you consider.

> Of course, this is not an exhaustive list, and may not apply to all projects.

- [Laravel Permissions](https://github.com/spatie/laravel-permission)