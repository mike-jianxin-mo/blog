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
Foreign key must be declared in schema xml file before it can be managed with it.
<strong>disabled="true"</strong>
```
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
  <table name="product_alert_stock">
   <constraint xsi:type="foreign" referenceId="PRODUCT_ALERT_STOCK_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID " table="product_alert_stock" column="customer_id" referenceTable="customer_entity" referenceColumn="entity_id" onDelete="CASCADE" disabled ="true"/>
  </table>
</schema> 
```
Ref: https://magento.stackexchange.com/questions/337346/why-setup-upgrade-command-revert-back-already-dropped-foreign-key-in-magento-2-4

### Disable a module with DB Schema, the tables will be dropped!
Question: what will happen to the database when you disable the module?
Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html

- When a module is disabled in app/etc/config.php, its database schema configuration is no longer read on upgrade or install. 

  As a result, subsequent system upgrades rebuild the database schema without the module’s tables, columns, or other elements. 

- Please note that the db_schema_whitelist.json file of disabled modules is still read during upgrades of installs, so the declarative schema system can perform the necessary operations. 

  Practically, this means that <strong>if you disable a module which uses declarative schema and run bin/magento setup:upgrade, its database tables will be dropped</strong> (see more details and discussion at https://github.com/magento/magento2/issues/24926). 

### Old schema script Vs new Db declarative XML
- Disadvantage of the old approach
  The main disadvantage of this approach is that Magento applies changes blindly. For example, in one version a new database column might be introduced, only to be removed in the next. Declarative setup eliminates this type of unnecessary work.
- For foreign key, use the old approach to remove it. The new declarative approach can not remove it. If the foreign key is not created in it before.
- 


### Priority before the Data updates
Magento prioritizes the declarative schema and executes the declarative install schemas before the data and schema patches.