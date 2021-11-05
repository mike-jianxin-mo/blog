---
title: Magento - Cache
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Cache Operations

Ref:
- Good: https://www.mageplaza.com/devdocs/magento-2-block-cache.html
 
- https://magecomp.com/blog/magento-2-block-cache/

##### Cacheable settings
Block the whole page from full page cache.
```
<block class="Block\Class" name="blockname" cacheable="false" />
```

##### Cache lifetime
The block is non-cacheable when the cache_lifetime of the block is NOT fixed to a number bigger than 0. Blocks are non-cacheable at first.
```
    public function getCacheLifetime()
    {
        return null; // or 0
    }
```

##### ttl
