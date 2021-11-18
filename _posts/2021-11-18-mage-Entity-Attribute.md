---
title: Magento - Customise the Entity Attribute
author: Mike Mo
date: 2021-11-18
category: Magento
layout: post
---

### Customise the Entity Attribute

Ref: https://magento.stackexchange.com/questions/3972/attribute-backend-type-static

##### Two step process

- Step 1: Add a column to the entity table
  It can be replaced with updates in the db_schema.xml.
  ```
    $installer->run("
        ALTER TABLE `{$installer->getTable('catalog/product')}` ADD `has_options` SMALLINT(1) NOT NULL DEFAULT '0';
    ");
  ```

- Step 2: Add an attribute record
  Type: <strong>Static</strong>
  ```
    $installer->addAttribute('catalog_product', 'has_options', array(
        'type' => 'static',
        'visible'=>false,
        'default' => false
    ));
  ```