---
title: Magento - Commands
author: Mike Mo
date: 2021-11-04
category: Magento
layout: post
---

##### Definition: Commands are arguments of a type under the Console package.
```
    <type name="Magento\Framework\Console\CommandList">
        <arguments>
            <argument name="commands" xsi:type="array">
                <item name="cache-instagram-posts" xsi:type="object">Tde\Social\Console\Command\SaveInstagramImagesToLocal</item>
                <item name="refresh-instagram-token" xsi:type="object">Tde\Social\Console\Command\RefreshInstagramTokenCmd</item>
            </argument>
        </arguments>
    </type>
```