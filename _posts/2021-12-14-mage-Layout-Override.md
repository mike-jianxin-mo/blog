---
title: Magento - Override Layout Files
author: Mike Mo
date: 2021-12-14
category: Magento
layout: post
---

Ref: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-override.html

### Customization mistakes
Although the layout overriding mechanism provides great customization flexibility, it’s possible to use it to add logically irrelevant changes. We strongly recommend you not make the following changes:

- Changing block name or alias. The name of a block should not be changed, and neither should the alias of a block remaining in the same parent element.
- Changing handle inheritance. For example, you should not change the page type parent handle.

### Override base layouts
<theme_dir>/Magento_Checkout/layout/override/base/checkout_cart_index.xml 
will override 
Magento_Checkout/view/frontend/layout/checkout_cart_index.xml

### Override Theme layout
<theme_dir>/Magento_Checkout/layout/override/theme/Magento/luma/checkout_cart_index.xml 
will override 
app/design/frontend/Magento/luma/Magento_Checkout/layout/checkout_cart_index.xml

