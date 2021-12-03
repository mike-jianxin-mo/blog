---
title: Magento - Layout Process
author: Mike Mo
date: 2021-12-03
category: Magento
layout: post
---

Ref: https://belvg.com/blog/magento-2-certification-layout-merging-overview.html

### Merge Order: The sequence
Ref: https://devdocs.magento.com/guides/v2.2/extension-dev-guide/build/module-load-order.html

Base on the sequence in the module.xml

<sequence> declares the list of components that must be loaded before the current component is loaded. It’s used for loading different kind of files: configuration files, view files (including CSS, Less, and template files), or setup classes. Setup classes are classes in the component that create or update database schema or data.

<strong> Note that <sequence> does not affect the loading of regular classes (non-setup classes). </strong>


### Merge Order: The Area
For greater clarity, I suggest taking a look at the general layout merging order:

1. Basic module files are loaded.
2. The request area module files are loaded (frontend or adminhtml).
3. The files are sorted according to the priority of the modules (the module’s load order is described above).
4. Theme files are loaded (the files of basic, parent and current themes). The younger the theme, the higher priority is given to the instructions in the extending and overriding layout files. The current theme has the highest priority.

### Conflict solving
If there are two or more conflicting instructions from different modules in the layout files during merging, then the one whose module is loaded last will win and be used.

### Methods
prepareLayout()

toHtml()

### Override a Layout
Ref: https://belvg.com/blog/overriding-layout-files-in-magento-2.html
