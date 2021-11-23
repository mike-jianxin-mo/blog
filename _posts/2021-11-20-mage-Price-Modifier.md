---
title: Magento - Price Modifier
author: Mike Mo
date: 2021-11-19
category: Magento
layout: post
---

### register 
Price modifiers are applied during catalog price indexing. In order to add your modifier declare it in di.xml as follows:

```
    <type name="Magento\Catalog\Model\ResourceModel\Product\Indexer\Price\BasePriceModifier">
        <arguments>
            <argument name="priceModifiers" xsi:type="array">
                <item name="yourPriceModifier" xsi:type="object">Your\Module\Model\Product\PriceModifier</item>
            </argument>
        </arguments>
    </type>
```

### class to implement it
and then create a class implementing 
```
Magento\Catalog\Model\ResourceModel\Product\Indexer\Price\PriceModifierInterface
```

### Ref
- https://magento.stackexchange.com/questions/144107/magento-2-use-of-pricemodifiers
- www.generacodice.com/en/articolo/2561210/magento-2-use-of-pricemodifiers