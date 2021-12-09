---
title: Magento - Enable & Disable a Module
author: Mike Mo
date: 2021-12-08
category: Magento
layout: post
---

### Conflicting Modules
Ref: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html

In addition, there might be conflicting modules that cannot both be enabled at the same time.

Examples:

- Module A depends on Module B. You cannot disable Module B unless you first disable Module A.

- Module A depends on Module B, both of which are disabled. You must enable module B before you can enable module A.

- Module A conflicts with Module B. You can disable Module A and Module B, or you can disable either module but you cannot enable Module A and Module B at the same time.

- Dependencies are declared in the require field in Magento’s composer.json file for each module. Conflicts are declared in the conflict field in modules’ composer.json files. We use that information to build a dependency graph: A->B means module A depends on module B.

- A dependency chain is the path from a module to another one. For example, if module A depends on module B and module B depends on module C, then the dependency chain is A->B->C.

### Force command
To force a module to be enabled or disabled regardless of its dependencies, use the optional --force argument.

