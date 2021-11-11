---
title: Magento - Order Id
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Format of order id

Ref: https://magento.stackexchange.com/questions/101341/magento-2-what-is-the-correct-way-to-change-default-order-id

Format for new order id is defined by default by constant in

Magento\SalesSequence\Model\Sequence :

const DEFAULT_PATTERN = "%s%'.09d%s";

It's pattern for sprintf() function that creates new id. To remove leading zeros you have to pass your pattern to constructor like this:
```
<type name="Magento\SalesSequence\Model\Sequence">
    <arguments>
        <argument name="pattern" xsi:type="string">%s%s%s</argument>
    </arguments>
</type>
```

or extend Sequence class and change as you need
