---
title: Magento - Images
author: Mike Mo
date: 2021-12-07
category: Magento
layout: post
---

# Configuation file
view.xml

# Change default Image size
view.xml

# Add a new image type

Ref: https://www.emiprotechnologies.com/technical_notes/magento-technical-notes-60/post/set-custom-image-role-for-product-in-magento-2-507

### Add new image type
1. In admin panel, select Stores > Attributes > Product. Then click on 'Add New Attribute'. Let’s create attribute named 'Diamond Icon'. 
2. Now we need to assign that attribute in proper attribute set. For that, go to Stores > Attributes > Attribute set. Now select the particular attribute set in which you want to add your custom attribute. Drag and drop your custom attribute <strong>in images group</strong> as shown in the image below.

### Resize in View.xml

### Use in codes

- in phtml/php:
  - Ref: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-images.html
  - getVar('');
    ```
    <vars module="Magento_Catalog">
        <var name="breakpoints">
            <var name="mobile">
                <var name="conditions">
                    <var name="max-width">767px</var>
                </var>
                ...
            </var>
        </var>
        ...
    </vars>
    ```
    ```
    $block->getVar($name, $module = null)
    ```
    *** The setting can be get directly!!! ***

