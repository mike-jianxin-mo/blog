---
title: Magento - Layout Handler
author: Mike Mo
date: 2021-11-18
category: Magento
layout: post
---

### Approaches to add layout handler
Ref: https://magento.stackexchange.com/questions/122913/how-to-add-custom-layout-handles-programatically-for-category-view-in-magento-2

##### The XML way
via the update tag

##### The PHP way
listen the <strong>layout_load_before</strong> event
```
public function execute(\Magento\Framework\Event\Observer $observer)
    {
        if($observer->getFullActionName() == 'catalog_category_view'){
            $observer->getLayout()->getUpdate()->addHandle('your_custom_handles');
        }
    }
```
