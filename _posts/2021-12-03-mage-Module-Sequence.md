---
title: Magento - Module Sequence
author: Mike Mo
date: 2021-12-03
category: Magento
layout: post
---

Ref: https://devdocs.magento.com/guides/v2.2/extension-dev-guide/build/module-load-order.html

### Position
- composer.json
- module.xml
  

### Control elements
<sequence> declares the list of components that must be loaded before the current component is loaded. It’s used for loading different kind of files: configuration files, view files (including CSS, Less, and template files), or setup classes. Note that <sequence> does not affect the loading of regular classes (non-setup classes). Setup classes are classes in the component that create or update database schema or data.

- configuration files
- view files (including CSS, Less, and template files),
- setup classes
   Setup classes are classes in the component that create or update database schema or data.

### Limits
<strong>Note that < sequence > does not affect the loading of regular classes (non-setup classes). </strong>
