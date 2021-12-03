---
title: Magento - DB Schema convertor
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### DB Schema Convertor

```
bin/magento setup:install --convert-old-scripts=1
bin/magento setup:upgrade --convert-old-scripts=1
```
### Remove Foreign Key
<strong>disabled="true"</strong>
```
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
  <table name="product_alert_stock">
   <constraint xsi:type="foreign" referenceId="PRODUCT_ALERT_STOCK_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID " table="product_alert_stock" column="customer_id" referenceTable="customer_entity" referenceColumn="entity_id" onDelete="CASCADE" disabled ="true"/>
  </table>
</schema> 
```
Ref: https://magento.stackexchange.com/questions/337346/why-setup-upgrade-command-revert-back-already-dropped-foreign-key-in-magento-2-4