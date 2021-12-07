---
title: Magento - EAV Attribute
author: Mike Mo
date: 2021-12-07
category: Magento
layout: post
---

### Setup 
- Class: EavSetup / EavSetupFactory
- Method: addAttribute()

### show in Admin
- custom
  - use_inform
- Others
  - update the form layout

### Cache
Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/attributes.html
As of version 2.3.4, Magento caches all system EAV attributes as they are retrieved. This behavior is defined in each affected module’s di.xml file as the attributesForPreload argument for <type name="Magento\Eav\Model\Config">. Developers can cache custom EAV attributes by running the bin/magento config:set dev/caching/cache_user_defined_attributes 1 command. This can also be done from the Admin while in Develop mode by setting Stores > Settings Configuration > Advanced > Developer > Caching Settings > Cache User Defined Attributes to Yes. Caching EAV attributes while retrieving improves performance as it decreases the amount of insert/select requests to the DB, but it increases the cache network size.