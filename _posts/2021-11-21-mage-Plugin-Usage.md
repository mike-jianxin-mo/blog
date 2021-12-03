---
title: Magento - Plugin Usage
author: Mike Mo
date: 2021-11-21
category: Magento
layout: post
---

### Limitations
Plugins can not be used on following:
- Class
  - Final classes
  - Virtual types
  
- Methods
  - Final methods
  - Non-public methods
  - Class methods (such as static methods)
  - __construct and __destruct

- Objects
  - Objects that are instantiated before Magento\Framework\Interception is - bootstrapped
  - Objects that implement Magento\Framework\ObjectManager\NoninterceptableInterface

### For Extensive Attribute
The afterLoad and afterSave plugin to update the extensive attributes

### After plugin for the Block toHtml method

