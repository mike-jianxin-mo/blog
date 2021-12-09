---
title: Magento - Price
author: Mike Mo
date: 2021-12-09
category: Magento
layout: post
---

Ref: https://belvg.com/blog/the-functionality-and-basic-concepts-of-price-generation-in-magento-2.html

### Price types
The basic types of prices available for all types of products:

- base_price — product price at the default currency exchange rate;
- regular_price — product price at the rate of the selected currency;
- final_price — the total price of the product;
special_price — product price with a discount;
- tier_price — product price that depends on its quantity in the cart;
- custom_option_price — the price of options if the selected product has any;
- configured_price — product price including the options;
- catalog_rule_price — product price after applying the catalog rules.

### Main Class
All price type extens from:
```
Magento\Framework\Pricing\Price\AbstractPrice
```
The class structure is the same as the Total ones.
```
\Total\AbstractTotal
```

### Main Function
Each type of price has its getValue() and getAmount() methods. 
- The <strong>getValue()</strong> method returns the price value.
- The <strong>getAmount()</strong> method returns the total price value with all taxes included.

### Price Calculation Rules
The final_price of a product depends on its <strong>type</strong>. It is <strong style="color:red">the lowest value of a product's price</strong>.

- For ordinary products (simple, virtual),
  it corresponds to the lowest value from:
  -  regular_price, 
  -  catalog_rule_price, 
  -  special_price, 
  -  tier_price.

- For configurable products, 
  - the price of each option is selected as the minimum value from:
    -  base_price, 
    -  tier_price, 
    -  index_price, 
    -  catalog_rule_price.
   
  - At the same time, the options of a configurable product is determined. 
    - When choosing the minimum price, the status of the configurable option of the product and its availability for a specific site are checked. 

  - After determining the final_price of all the options, the price determined. 
    The final price of the configurable product is determined, which will be equal to the lowest price of its options.

- For group products, 
  The final_price of the grouped product is equal to the lowest final_price of all the products in the group.

- For bundle products, 
  the price is calculated in the same way as for simple products + bundle_option, which is the price of all the required options multiplied by their number.
