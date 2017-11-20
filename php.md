---
title: PHP
---
# PHP

- [Introduction](#introduction)
- [Classes](#classes)
- [Controllers](#controllers)
- [Namespacing](#namespacing)
- [Functions](#functions)
- [Variables](#variables)
- [Arrays](#arrays)
- [Docblocks](#docblocks)
- [PHPMD](#phpmd)
- [PHPCS](#phpcs)
- [Resources](#resources)

<a name="introduction"></a>
## Introduction
Here is some helpful information in addition to the PSR2 standards on how we should be using PHP.


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

Modularizing your code into pseudo packages. 

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
Docblocks should state the return type and paremeters, as this can help the IDE flag up when you are trying to use the wrong return type or parameter.

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

<a name="phpmd"></a>
## PHPMD - PHP Mess Detection
Also as much as possible try to following the best practices set out in [PHPMD](https://phpmd.org/).

We have a custom ruleset which can be downloaded <a href="https://raw.githubusercontent.com/sysflowdev/coding-standards/master/_resources/phpmd.xml" target="_blank">here</a>.

> Set up PHPStorm to alert you to problems in your code.
> File > Settings > Editor > Inspections > PHP > PHP Mess Detector validation

<a name="phpcs"></a>
## PHPCS - PHP Code Sniffer

We have a custom PHPCS ruleset which can be downloaded <a href="https://raw.githubusercontent.com/sysflowdev/coding-standards/master/_resources/phpcs.xml" target="_blank">here</a>.

> Set up PHPStorm to alert you to problems in your code.
> File > Settings > Editor > Inspections > PHP > PHP Code Sniffer validation

<a name="resources"></a>
## Resources
- [PHP : The Right Way](http://www.phptherightway.com/)
- [PHP.net](http://www.php.net/)
- [Laracasts](https://laracasts.com/)
- [Laravel Docs 4.2](https://laravel.com/docs/4.2)
- [Laravel API 4.2](https://laravel.com/api/4.2)
- [Laravel Docs 5.5](https://laravel.com/docs/5.5)
- [Laravel API 5.5](https://laravel.com/api/5.5)
- [OOP Principles](https://anampiu.github.io/blog/OOP-principles/)
- [Object Calisthenics](http://williamdurand.fr/2013/06/03/object-calisthenics/)  
