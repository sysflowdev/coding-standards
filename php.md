---
title: PHP
---
# PHP

- [Introduction](#introduction)
- [Filenames](#filenames)
- [Classes](#classes)
- [Controllers](#controllers)
- [Namespacing](#namespacing)
- [Functions](#functions)
- [Variables](#variables)
- [Arrays](#arrays)
- [Docblocks](#docblocks)
- [StyleCI](#styleci)
- [PHPMD](#phpmd)
- [PHPCS](#phpcs)
- [Laravel](#laravel)
- [Resources](#resources)

<a name="introduction"></a>
## Introduction
Here is some helpful information in addition to the PSR2 standards on how we should be using PHP.

<a name="filenames"></a>
## Filenames

Except classes, filenames should be kebab-case (All lowercase with - separating words) e.g. this-is-my-view.blade.php

Classes are different, these should be PascalCase e.g. ThisIsMyClass.php, ThisIsMyClass.js

<a name="classes"></a>
## Classes

File names and class names should be Studly case.

Examples of names:
<dl class="dl-horizontal">
    <dt>Model</dt>
    <dd>Task</dd>    
    <dt>Controller</dt>
    <dd>TaskController</dd>   
    <dt>Composer</dt>
    <dd>TaskComposer</dd>    
    <dt>Factory</dt>
    <dd>TaskFactory</dd>
</dl>

<a name="controllers"></a>
## Controllers
Each controller should ideally only contain the following public methods. These are all optional methods.

- Index
- Create
- Store
- Edit 
- Update
- Show
- Destroy

If you are to add other methods, here is an example of when not to add to the existing controller.
- getNotes()
- storeNotes()

These should ideally be in their own controller as:
- index
- store

<a name="namespacing"></a>
## Namespacing

Modularizing your code into pseudo packages (&quot;package by feature instead of layer&quot;).

**Examples (Holiday)**
- Sysflow/Holiday/Commands
- Sysflow/Holiday/Http/Admin/Controllers
- Sysflow/Holiday/Http/Frontend/Controllers
- Sysflow/Holiday/Models
- resources/views/holiday

**Examples (Task)**
- Sysflow/Task/Commands
- Sysflow/Task/Http/Admin/Controllers
- Sysflow/Task/Http/Frontend/Controllers
- Sysflow/Task/Models
- resources/views/task

<a name="functions"></a>
## Functions
Should always be descriptive e.g.
- isExportable()
- export()

Functions should be written in camelCase. With the exception of global helper functions and tests. 

<a name="variables"></a>
## Variables
<div class="alert alert-warning">And the winner is camelCase</div>

```php
$invoice->vat_total = $vatTotal;
$vatTotal = $invoice->vat_total;
```

<a name="arrays"></a>
## Arrays
- Array keys should be snake case.
- Arrays should be written in the new format using square brackets [].

```php
$array = [
    'some_array_key' => 'some_value'
];
```

## Docblocks
Docblocks should state the return type and parameters, as this can help the IDE flag up when you are trying to use the wrong return type or parameter.

Also usage of PHP return types where appropriate (e.g. when they serve a benefit, if you require an integer then force it to be one).

```php
/**
 * Description (optional?)
 *  
 * @param $name
 *
 * @return string
 */
```

<a name="styleci"></a>
## Style CI
We typically use the [Laravel Preset](https://docs.styleci.io/presets#laravel) in StyleCI for our PHPCSFixer baseline.

However, below are the settings that we recommend changing for readability.

```
enabled:
    - align_equals
    - concat_with_spaces
    - align_double_arrow_minimal
disabled:
    - unalign_equals
    - concat_without_spaces
```

### align_equals (enabled)
Align equals symbols in consecutive lines. This is for readability.

> :bulb This fixer cannot be enabled at the same time as the align_equals_minimal or unalign_equals fixers.

### concat_with_spaces (enabled)
Concatenation should be used with at least one whitespace around. This is for readability.

> :bulb This fixer cannot be enabled at the same time as the concat_without_spaces fixer.

### align_double_arrows_minimal (enabled)
Minimally align double arrow symbols in consecutive lines. This is again for readability.

> :bulb This fixer cannot be enabled at the same time as the align_double_arrow or unalign_double_arrow fixers.


<a name="phpmd"></a>
## PHPMD - PHP Mess Detection
Also as much as possible try to following the best practices set out in [PHPMD](https://phpmd.org/).

We have a custom ruleset which can be downloaded <a href="https://raw.githubusercontent.com/sysflowdev/coding-standards/master/assets/files/phpmd.xml" target="_blank">here</a>.

> Set up PHPStorm to alert you to problems in your code.
> File > Settings > Editor > Inspections > PHP > PHP Mess Detector validation

<a name="phpcs"></a>
## PHPCS - PHP Code Sniffer

We have a custom PHPCS ruleset which can be downloaded <a href="https://raw.githubusercontent.com/sysflowdev/coding-standards/master/assets/files/phpcs.xml" target="_blank">here</a>.

> Set up PHPStorm to alert you to problems in your code.
> File > Settings > Editor > Inspections > PHP > PHP Code Sniffer validation

<a name="laravel"></a>
## Routes
Wherever possible, routes in Laravel should be named.

Named routes should use a combination of 'dot' notation, and kebab-case.

```
route('admin.product-type.index');
```

Route names should follow resourceful naming wherever possible: index, create, store etc, and should not be pluralised.

<a name="resources"></a>
## Resources
- [PHP : The Right Way](http://www.phptherightway.com/)
- [PHP.net](http://www.php.net/)
- [Laracasts](https://laracasts.com/)
- [Laravel Docs](https://laravel.com/docs)
- [OOP Principles](https://anampiu.github.io/blog/OOP-principles/)
- [Object Calisthenics](http://williamdurand.fr/2013/06/03/object-calisthenics/)  
