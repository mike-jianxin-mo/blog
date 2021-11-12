---
title: Magento - Attribute Backend Model
author: Mike Mo
date: 2021-11-11
category: Magento
layout: post
---

### Attribute Backend Model

Ref: https://newbedev.com/magento-2-add-custom-product-attribute-validation-from-install-script

The backend model extends from \Magento\Eav\Model\Entity\Attribute\Backend\AbstractBackend

It includes afterLoad, beforeSave, and some validation methods.

It can be used to convert data format and forms.

For example, a file name attribute.
