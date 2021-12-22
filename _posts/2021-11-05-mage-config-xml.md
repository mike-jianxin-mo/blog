---
title: Magento - Config.xml
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Config.xml

The config.xml file is used to set default values for system configuration (in Admin under Stores > Settings > Configuration), set in <module_folder>/etc/adminhtml/system.xml.

All the config.xml files will be merged together into one tree. If you overwrite another module's config, it will depend on load order (you would need to specify the other module as a dependency).

Also keep in mind that once you change system config values in the admin and save them, then the values in config.xml will no longer apply; they will be overwritten in the core_config_data table. They are meant only to specify defaults.

<strong>It only uses the last id field in the system.xml</strong>

### System.xml
Ref: https://webkul.com/blog/create-dependant-field-admin-configuration-magento-2/
- Dependent settings
  Based on one value
  ```
    <depends>
        <field id="custom">1</field>
    </depends>
  ```
  Based on multi-values
  ```
    <depends>
        <field id="custom" separator=",">0,1</field>
    </depends>
  ```