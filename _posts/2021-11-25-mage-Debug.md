---
title: Magento - Debug
author: Mike Mo
date: 2021-11-25
category: Magento
layout: post
---

### Show Collection Sql
```
\Magento\Framework\App\ObjectManager::getInstance()->get('Psr\Log\LoggerInterface')
    ->debug(__FILE__ . ' LINE ' . __LINE__,
        ['sql ' => var_export($collection->getSelectSql(true), true)]);

```

