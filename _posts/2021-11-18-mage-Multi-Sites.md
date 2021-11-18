---
title: Magento - Multi-Sites
author: Mike Mo
date: 2021-11-18
category: Magento
layout: post
---

### Multi-Sites

##### Multi-store-viewes
Ref: https://magento.stackexchange.com/questions/268940/magento-2-store-view-multiselect-in-system-xml

```
<field id="store_view" translate="label" type="multiselect" sortOrder="13" showInDefault="1" showInWebsite="1" showInStore="1">
      <label>Store View</label>
      <source_model>Magento\Store\Model\System\Store</source_model>
</field>
```