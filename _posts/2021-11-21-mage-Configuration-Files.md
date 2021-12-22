---
title: Magento - Configuration Files
author: Mike Mo
date: 2021-11-21
category: Magento
layout: post
---

### Configuration file list
- System
  - app/etc/config.php
  - app/etc/env.php
  - config.xml
  
- Module
  - register.xml
  - module.xml

- Request Flow
  - <strong>routes.xml</strong> has 's'
  - webapi.xml
  - webapi_async.xml
  - websoap.xml
  - graphql.php
  
- DJ
  - di.xml
  
- Index
  - indexer.xml
  - mview.mxl

- Cache
  - cache.xml
  
- Model
  - db_schema.xml
  - db_schema_whitelist.json 
    fields listed in the whitelist will be managed by Magento system!
    eg. remove one field. 
        only success when the field name in the whitelist.
  - <strong>extension_attributes.xml</strong> has 's'

- Cron
  - <strong>cron_groups.xml</strong> has 's'
    eg. ./vendor/magento/module-indexer/etc/cron_groups.xml
  - crontab.xml
    eg. ./vendor/magento/module-indexer/etc/crontab.xml

- Admin
  - menu.xml
  - acl.xml
  
- UI
  - Theme
    - theme.xml
    - registration.php
  - Layout & templates
    - <strong>layouts.xml</strong> has 's'
    - page layouts
    - layout handlers
  - Widgets
    - page_types.xml
    - widget.xml

- Event Extending Approach
  - <strong>events.xml</strong> has 's'
  
- Feature
  - sales.xml
  - product_types.xml
  - view.xml
    The properties of product images used on the storefront are stored in the view.xml configuration file. 
  - fieldset.xml
    Define the fields need to be copied from quote to order entity.

- Predefined Joints
  - custom_account.xml
  - checkout_cart_item_renderer.xml
  - add a new shipping method
  - add a router
  - add an indexer
  - add a cache
  - add a command line 
  - add a widget
  - add a controller
  - add a webapi endpoint
  - add a graphql endpoint
  - add a admin grid
  - add a admin grid filter
  - add a admin form
  - add a new attribute
  - add an extensive attribute
  - add an email template
  - add a slack feature
  - extend core feature with a plugin
  - extend core feature with a override
  - extend core feature with template updates
  - use a proxy
  - add a price modifier
  - copy a custom field from quote to order
  - add an index and its mview.xml settings