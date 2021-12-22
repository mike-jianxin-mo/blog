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

### RouteT
Type: Argument
sortOrder/Disable
```
Magento\Framework\App\RouterList
```

```
\Magento\Framework\App\RouterInterface
```

### Command
Type: Arguments
```
Magento\Framework\Console\CommandList
```

```
Symfony\Component\Console\Command\Command
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
    sales_order_history.xml
    ```
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

### Fee/Total 
Total is under the Quote Address
```
\Magento\Quote\Model\Quote\Address\Total\AbstractTotal
```

### Price
Similar to fee/total
```
Magento\Framework\Pricing\Price\AbstractPrice
```
```
\Magento\Catalog\Model\Product\Type\Price
```

### Carrier
Similar to fee/price, but no 
```
Magento\Shipping\Model\Carrier\CarrierInterface
```
```
collectRates()
getAllowedMethods() // the carrier name
```

### View Model
```
\Magento\Framework\View\Element\Block\ArgumentInterface
```