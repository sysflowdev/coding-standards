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

<a name="branchnaming"></a>
# Branch naming
feature/{task id}-{kebeab-case-short-description}

<a name="deployments"></a>
# Deployments
The deployment process for projects unless stated otherwise is.
- Feature branch > Develop branch
- Feature branch > Staging branch
- Feature branch > Master branch

<a name="merge-conflicts"></a>
# Merge Conflicts
Merge conflicts should be resolved and committed on the branch being committed into (e.g. develop, staging, master).