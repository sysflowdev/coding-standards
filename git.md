---
title: Git
---
# Git

- [Introduction (@todo)](#introduction)
- [.gitignore](#gitignore)
- [Branch naming](#branch-naming)
- [Deployments](#deployments)

<a name="introduction"></a>
# Introduction
This section is a WIP.

<a name="gitignore"></a>
# .gitignore
Here is a list of files and variables that should ***never*** be committed.
- .env files
- API keys
- Private keys
- Tokens
- Uploaded documents
- node_modules folder
- vendor folder
- IDE specific folders (.idea)

### Dotenv

If you are working on a non-Laravel 5 project, it is highly recommended you install the <a href="https://github.com/vlucas/phpdotenv" target="_blank">Dotenv package</a>, which allows you to easliy load .env files into your project to store these details.

You may also wish to grab a copy of the <a href="https://github.com/laravel/framework/blob/master/src/Illuminate/Support/helpers.php#L595" target="_blank">Laravel 5 `env()` helper method</a> in order to easily parse .env file values.

<a name="branchnaming"></a>
# Branch naming
feature/{task id}-{kebab-case-short-description}

<a name="deployments"></a>
# Deployments
The deployment process for projects unless stated otherwise is.
- Feature branch > Develop branch
- Feature branch > Staging branch
- Feature branch > Master branch

<a name="merge-conflicts"></a>
# Merge Conflicts
Merge conflicts should be resolved and committed on the branch being committed into (e.g. develop, staging, master).