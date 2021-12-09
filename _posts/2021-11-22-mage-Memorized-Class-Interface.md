---
title: Magento - Memorized Class & Interface Names
author: Mike Mo
date: 2021-11-22
category: Magento
layout: post
---

### Event Extending
```
Magento\Framework\Event\ObserverInterface
```

```
checkout_cart_add_product_complete
```


### Extend Carrier 
```
Magento\Shipping\Model\Carrier\CarrierInterface
```

### Handler 
- Add a new Checkout UI component fields
    ```
    checkout_index_index.xml
    ```
- Category admin form
  ```
  catalog_attributes.xml
  ```
- Account section
  - Order history
    ```
    sales.order.history.extra.column.header
    sales.order.history.extra.container
    ```

### No Cart
Cart.php deprecated.

### Module Sequence
- layout
- view files
- setup
  
Not afffect the classes.

### Extensive attribute
```
Magento\Framework\Api\ExtensibleDataInterface
```
ExtensibleDataInterface?
In the example above the HamburgerInterface extends the ExtensibleDataInterface.
Technically this is only required if you want other modules to be able to add attributes to your entity.
If so, you also need to add another getter/setter pair, by convention called getExtensionAttributes() and setExtensionAttributes().

### Fee 
```
\Magento\Quote\Model\Quote\Address\Total\AbstractTotal
```

### Price
```
Magento\Framework\Pricing\Price\AbstractPrice
```
