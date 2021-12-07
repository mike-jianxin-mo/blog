---
title: Magento - Update Block Template
author: Mike Mo
date: 2021-12-07
category: Magento
layout: post
---

### SetTemplate (deprecated)
```
<referenceBlock name="catalog.topnav">
    <action method="setTemplate">
        <argument name="template" xsi:type="string">Foo_Bar::buzz.phtml</argument>
    </action>
</referenceBlock> 
```

### Argument
```
<referenceBlock name="catalog.topnav">
    <arguments>
        <argument name="template" xsi:type="string">Foo_Bar::buzz.phtml</argument>
    </arguments>
</referenceBlock>    
```

### In line attribute
```
<referenceBlock name="core.module.block.name" template="[Vendor]_[Module]::path/to/your/template.phtml" />
```

### Theme override
```
<theme_dir>/<Vendor>_<Module>/path/to/file
```

### Plugin
The class may be used for multiple templates or the Vendor_Module prefix might be set. In these cases, a plugin is the best option.

```
<?php
namespace Vendor\Module\Plugin\Catalog\Block\Category;
 
class View
{
    public function beforeToHtml(\Magento\Catalog\Block\Category\View $subject)
    {
        if ($template === 'Magento_Catalog::category/products.phtml') {
            $subject->setTemplate('Vendor_>Module::catalog/category/products.phtml');
        }
    }
}

<type name="Magento\Catalog\Block\Category\View">
    <plugin name="module_catalog_category_view_override_template" type="Vendor\Module\Plugin\Catalog\Block\Category\View" />
</type>
```

Ref: https://www.classyllama.com/blog/template-override-m2
