---
title: Magento - Customise product price
author: Mike Mo
date: 2021-12-09
category: Magento
layout: post
---

### Extend class
```
\Magento\Catalog\Model\Product\Type\Price
```

### New a new basic price type

Create a new price type and add it to the set of basic types. 
```
<virtualType name="MyVendor\MyModule\Pricing\Price\Pool" type="Magento\Framework\Pricing\Price\Pool">
  <arguments>
      <argument name="prices" xsi:type="array">
          <item name="my_price" xsi:type="string">MyVendor\MyModule\Pricing\Price\MyPrice</item>
      </argument>
      <argument name="target" xsi:type="object">Magento\Catalog\Pricing\Price\Pool</argument>
  </arguments>
</virtualType>
```

### By a plugin
Create a plugin for the class methods of the price type, the process of calculating which we want to change, for example, around the getValue() method.

### By di virtualType
Override the class that corresponds to the type of price that we need for a specific type of product, using the di-file in the module:
```
<virtualType name="MyVendor\MyModule\Pricing\Price\Pool" type="Magento\Framework\Pricing\Price\Pool">
  <arguments>
      <argument name="prices" xsi:type="array">
          <item name="regular_price" xsi:type="string">MyVendor\MyModule\Pricing\Price\MyRegularPrice</item>
      </argument>
  </arguments>
</virtualType>
```

### By di perference
Completely override the price class using the preference instruction in the di-file module