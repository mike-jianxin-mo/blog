---
title: Magento - Plugin
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Plugin

###### Function Name
Plugin for <strong> _construct() </strong>

after/before_construct()


###### Plugin Not Applicable
Ref: https://magento.stackexchange.com/questions/194358/add-after-method-with-plugin-on-underscore-methods

- Objects that are instantiated before Magento\Framework\Interception is bootstrapped
- Final methods
- Final classes
- Any class that contains at least one final public method
- Non-public methods (I think you are using private method)
- Static methods
- __construct
- Virtual types