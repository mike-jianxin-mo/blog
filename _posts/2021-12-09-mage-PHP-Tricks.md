---
title: Magento - PHP Tricks
author: Mike Mo
date: 2021-12-09
category: Magento
layout: post
---

### Override settings
```
    public function render($priceCode, SaleableInterface $saleableItem, array $arguments = [])
    {
        $useArguments = array_replace($this->_data, $arguments);
        ... ...
    }

```
