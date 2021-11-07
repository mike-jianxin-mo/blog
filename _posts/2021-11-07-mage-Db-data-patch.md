---
title: Magento - DB: Data Patch
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### Data Patch
With version 2.3, aside from InstallData and UpdateData classes, Magento introduced data patches, a new way for modules to apply data changes.


##### Location
```
Setup/Patch/Data
```


##### Execution Order
Magento prioritizes the declarative schema approach and executes updates from the db_schema.xml before the data and schema patches.

Ref: 
- https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/data-patches.html
- https://store.magenest.com/blog/apply-data-patch-in-magento-2/